---
title: "NSLookup returns incorrect data"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by dakin on 2013-01-18
Hi All,

I have Ubuntu server 12.04.1 64bit in a virtualbox VM using bridges networking under Mint14 following this guide to setup samba4 as an exercise of interest. ([http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04](http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04))
All went well until I got to the Kerberos setup section and it failed to pass the testing mentioned in the guide.  I've been chewing on this for about a week now and found this [https://help.ubuntu.com/community/Kerberos](https://help.ubuntu.com/community/Kerberos) post which mentions nslookup tests, that then says if the FQDN is not returned with a reverse lookup then kerberos wont work.  It doesn't!
Nslookups return the following;

root@server:~# nslookup server
Server:          10.200.10.1
Address:         10.200.10.1#53

Name:  server.free.local
Address: 10.200.10.80


root@server:~# nslookup 10.200.10.1
Server:          10.200.10.1
Address:         10.200.10.1#53

** server can't find 1.10.200.10.in-addr.arpa.: NXDOMAIN

Reverse lookup on .80 returns the same.

Now this may be incorrect but I'm actually stuck on the first nslookup because it returns 10.200.10.80 as the IP address of server.free.local which is incorrect and I cannot figure where it is getting this address from.
During the initial installation I used .80 but one of the first steps in the guide was to manually configure the IP which I set to the .1 address.
I thought it maybe in a config file somewhere that I had missed or wasn't mentioned in the guide so I've done searches for the IP address using 'grep -r "10.200.10.80" /etc', also /var /run and maybe a few others as well, the only place it finds the address is in the syslog from the original setup.
I've change the resolv.conf from my router to google dns and no change, thinking possibly the router had reference to the old address, even though the router console shows the address as not used.
.80 cannot be pinged and there are no other machines named "server" on the network.  I've flushed the dns cache to no avail.

Now that I've run out of ideas and don't seem to be able to locate an answer in many many searches in google and forums I thought I'd ask for some assistance before doing the re-install thingy.  A re-install is really no big deal and definitely would have been faster, but nowhere near as much fun because I could miss out on learning something useful.

Anyway if someone has some useful pointers I would appreciate it.

---

### Post by elgordodude on 2013-01-18
Someone correct me if I'm wrong, but I don't think nslookup is supported anymore, you should use the dig command now.

Unfortunately that shouldn't matter too much. Have you tried directly mapping the server in the /etc/hosts file? That should supersede DNS. Alternatively I'd try giving the server a new static address, say .50 and see if a good flush got it going.

> **dakin said:**
> A re-install is really no big deal and definitely would have been faster, but nowhere near as much fun because I could miss out on learning something useful.

I know that feeling, but be grateful for the flexibility...

---

### Post by dakin on 2013-01-19
Thanks elgordodude.  I did have the records in the Hosts file and resolv etc set to the correct address.  

Hmm, maybe nslookup shows my age? or that I manage windows servers or something.  Ha.

The strange thing is I can ping the host name and fqdn and both return the correct IP.  OK just removed the hosts entry for the machine and now ping returns .80 so it's definitely tied to dns somehow.
I've done as you suggested, changed the IP address in all config files that it was contained in and ran rdns flush.  Then a reboot.

Did a man dig, and then had a dig and it returned the dreaded 80.
The dig contained the following;
;; QUESTION SECTION:
;server.free.local.        IN   A

;;ANSWER SECTION:
server.free.local.   900   IN   A   10.200.10.80
...
;; Query time: 13msec
;; SERVER: 10.200.10.30#53(10.200.10.30)

what the?

That to me says;  Hi I'm the DNS server at .30 and my own dns record is .80.

So this got me thinking that maybe rndc flush wasn't working as it should.  rndc reload returns;

rndc: connect failed: 127.0.0.1#953: connection refused

Maybe, and maybe not.  Yes rndc had a permissions issue on the rndc.key file which when fixed did not change the above name issue but now rndc reloads successfully.

So now back at same place I was at the beginning.  DNS running on .30 but reporting itself as .80.  

Any more ideas?

---

### Post by dakin on 2013-01-20
Based on this [http://zewaren.net/site/?q=node/40](http://zewaren.net/site/?q=node/40) I make the assumption that this is what is happening.

Samba4 now contains and initialises dns records for the domain from a database via this line 
include "/var/lib/samba/private/named.conf"
added to the /etc/bind/named.conf file.  Then in that consequently called named.conf file it calls the module dlz_bind9.so which loads from samba database relative dns records.  In my case this must include the 10.200.10.80 record that keeps appearing from my earlier posts.
Dumping the dns cache doesn't show it, hence I cannot see any other explanation.

As that post is the only reference I have found and the corrective action it talks about requires deleting files I cannot find on the system at this point, I have reverted the server IP back to .80, as for the time being it will not affect anything.
My intention is to build the system to an operational state then wipe it out and start again a few times to become familiar with the setup.  I can fine tune IP addressing etc. along the way.

Thankyou for your input elgordodude.

---

