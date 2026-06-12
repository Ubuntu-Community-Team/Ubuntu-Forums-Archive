---
title: "Samba and Firestarter - the real story"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by dsmalley on 2006-06-06
Hi,

I've noticed several posts on the forums dealing with Samba problems when the Firestarter firewall is installed on an Ubuntu system. After playing with it for half a day, I think I know why. First, some basics:

Assume two or more PC's on a small network, behind a NAT router. At least one of them is running Ubuntu, the other one can be either another Ubuntu PC, or a Windows box. Both machines get their IP's dynamically using the DHCP service of the router.

In order resolve each other's hostnames on the local LAN, the Ubuntu machine(s) must be running winbind. This allows an Ubuntu system to send and receive netbios broadcasts for name resolution. The coreography of this transaction works like so:

The requesting machine sends a netbios broadcast *from* a pseudo-random port above 32767 *to* port 445. All other machines on the local LAN receive this broadcast, which is looking for hostame "whatever". The machine with hostname "whatever" (if it exists), responds to the requesting machine on the pseudo-random port used in the broadcast, sending its IP, and the requesting machine then has the IP for the requested name. This transaction works fine with an Ubuntu machine on either end assuming it is running the samba and windbind daemons, without Firestarter active.

When Firestarter is activated (which is really just a front-end for iptables), all ports are blocked, so this stops working. The first step to make it work again is to create an inbound rule for the Samba service which opens ports 137, 138, 139, and 445 for TCP and UDP packets. It is reasonable to specify the rule as applying all IP's on the local LAN, which would look something like this: 192.168.1.0/24. This means any machine with an IP having 192.168.1 as the first three numbers is allowed to access these ports; depnding on the configuration of the NAT/DHCP router, these numbers might be different. You do this rather than specifying full IP's, because they may change, since they're being assigned by the router's DHCP server. So far so good.

It turns out that the Ubuntu machine(s) will still have a problem, because the netbios broadcast requests from other machines will be blocked by default. You can unblock them by going to Preferences->Advanced Options, and unchecking "Block broadcasts from external network". But there will still be a problem:

When the Ubuntu machine(s) request a hostname, they will send the broadcast, the machine with the hostname (either a Windows or Ubuntu system) will respond on the pseudo-random port the requester used, and its response will be blocked as an unauthorized connection attempt on that port. This blocking can be seen in the Events tab of the Firestarter GUI, if it is running.

THIS SHOULD NOT HAPPEN. Why? Because iptables is what is called a "stateful" firewall. It has a rule which says that *any* packet on *any* port which is received as a response to an outgoing request will be accepted. This happens all the time when you use the internet. When you connect to a web site, the connection is actually from some port on your machine like 38000, to port 80 on the web site's server. The server sends your response on that port, not port 80. iptables allows this connection without an explicit rule for the port 38000 (for example), because it is recognized as a response to your original request.

So the problem here is that the response to the naming request is being dropped. You can't really fix this by adding explicit port rules, because the port number will change over time. If you use nmblookup now, you may see the blocked response in the Events tab as port 32768. You can add a rule for this port, but then 10 minutes later, you'll find the blocked response is now on port 32783. You could open all ports to the local LAN for ports above 32768, but at that point, you might as well forget about filtering by service (i.e., Samba) and use the "Allow connections from host" rules, and open all ports to all machines on the local LAN. This might not be such a problem, but it could be. For example, I run a development web server on my workstation, and I really don't want it accessed from any other machine, even those on my LAN. Of course, you can configure apache (the web server) to reject connections from anything other than localhost, but that is really a job better handled by the firewall.

So, I am not an iptables guru. I am wondering if it is possible to make iptables recognize requests/responses for netbios naming broadcasts? If not, can Samba be configured to use a specific port for the broadcast, which can then be opened explicitly for the response? And depending on what can be done at this low-level, is it then possible to make Firestarter add this as part of the Samba service? I don't seem to remember this problem with Samba on other distros, but it's been awhile since I used anything other than Ubuntu, so maybe they have this issue too, and I just don't remember it.

I should mention this is only a problem if you're trying to use hostnames for dynamically assigned IP's. Just adding the Samba service works fine if you want to access shares with raw IP addresses. But that's not very convenient when they are assigned with DHCP.

Dave

---

### Post by dsmalley on 2006-06-06
Answered my own question.

In /etc/firestarter/inbound/setup, there are two lines which look like this:

```

# Allow response traffic
$IPT -A INBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INBOUND -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT

```

These set up the general rule for allowing responses to be forwarded. Changing them to:

```

# Allow response traffic
$IPT -A INBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INBOUND -p udp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

```

(adding state NEW for udp) lets through the response to a netbios name request broadcast. The status NEW is required, because for a broadcast, no connection is established (a broadcast does not go to any specific machine, nor does it require a response in order to "succeed" (at the IP level). It does, however, mean it is a response to an outgoung request. It is not the same as state INVALID, which would correspond to an "unsolicited" incoming packet, which would effectively mean anything goes.

So, I can now have netbios name resolution while still using service based rules in Firestarter. Linux is wonderful, you know.

Dave

---

### Post by cuz on 2006-06-07
Hi,

I'm totally new to Linux (after a couple of failed Gentoo installation efforts). Over the last couple of days I've been making active use of this forum to configure Samba and Firestarter and to get them to play together. I was tearing my hair out and about to accept less than best. But this post, Dave, was the solution. It was clear and explicit about why the change should be made. And best of all, it worked! (My clue as to why something like this must be the case was that in the Events tab of Firestarter, each attempt to survey the surrounding Windows network would generate several sun-rpc portmap connections blocked in random ports above 32000.

So I registered to say, "Thanks for letting me move forward with my life," and to add (for other complete newbies) that the permissions for the /etc/firestarter/inbound folder and the setup file must be changed to writable before editing (and then, of course, changed back).

Thanks again (and thanks to all the efforts of other I've used to begin my now inevitable shift away from Windows).

cuz

---

### Post by dsmalley on 2006-06-08
Hi cuz,

Glad it helped you out. Since nobody responded to this post, I started wondering if my system(s) were somehow possessed and I was the only one having this problem :) 

Actually, I have changed my inbound/setup file slightly from what I indicated above. I left the first two lines as installed and instead added a third one below it:

```

# Allow response traffic
$IPT -A INBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INBOUND -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow response to netbios name broadcasts from the local network.
$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT

```

"$NET" is defined in the script which calls this one as the local subnet (your IP with a mask of 255.255.255.0), so this only allows NEW connections from machines on the same subnet, which is usually the case for small LAN's behind a NAT router.

Incidentally, I've found that even with these changes, Nautilus is quite unreliable for browsing a Windows network. What is so frustrating about it is it works (or fails) intermittently. However, I've found that whenever it fails (indicating the workgroup is empty, or that some share is inaccessible), I can ALWAYS get the correct behaviour from findsmb (list machines and workgroups), smbtree (list shared resources), smbclient (connect and access files), or smbmount (mount a samba folder in the local filesystem) from the command line. For that matter, doing CTRL-L in Nautilus and manually entering the smb path usually works too, but that implies you already know the resource you want.

Dave

---

### Post by cuz on 2006-06-09
Thanks for the update.

For what it is, I haven't experienced any unreliability. Slower response than Konqueror, yes, but unreliability, no. Based on another post (somewhere), I changed my smb.conf file's [global] section to include 'os level = 10' so that my XP machine, which is still the center of the network and has a default os level of 16 would win the election for browse master. Perhaps that could be contributing? I can't really say since I've made many changes along the way, but my feeling is that the connections were more unreliable prior to that change.

Best,
cuz

---

### Post by dsmalley on 2006-06-10
I forgot to mention one other useful thing: when winbind is installed, it's always nice to add "wins" to the hosts: line in /etc/nsswitch.conf.

```

hosts:          files dns mdns wins

```

This will allow ordinary TCP/IP programs to resolve hostnames with netbios, so you can, for instance, do "ping <hostname>" instead of "ping 192.168.1.xxx". Of course, ping isn't all that wonderful, but it's a lot easer to do "ftp hostname" or "ssh hostname" or browse to "http://hostname" than using raw IP's for the local machines (assuming of course they are running the given service and the forewall on the target machine allows access to the right ports).

Dave

---

### Post by gwi on 2006-06-20
And what if I have a Linux host in a LAN with Internet connection (interface eth0, subnet 192.168.11), running VMWare server with virtual host-only network (interface vmnet1, subnet 192.168.25)?

I want Samba shares to be reachable from the VMWare machines on the host-only network, but not from the LAN (with its Internet connection).

I added Samba (SMB) with ports 137-139 445 and IP 192.168.25.0/24 to the allowed services for incoming traffic. But I still can't access the share from the VMWare machines (which run Windows 2000 and XP). When I disable the firewall, I can access the share.

(I am a total iptables newbee #-o)

---

### Post by akudewan on 2006-06-22
dsmalley: Wow. I can't thank you enough. Samba is working just fine, and I can browse the machines on my network with ease (using konqueror).

This thread deserves to be pinned/sticky. You should really post this as a Howto  in the Howto forum. I'm sure it will help lots of people :)

---

### Post by B7may on 2006-06-27
I have the same problem and changed the setup file the same.  Now from the machine that has firestarter installed, I can access my main network.  (In other words, I have a larger network and connected to that is the machine with Firestarter that controls a smaller network.)  But any machine that is connected to the network controlled by firestarter cannot get to the main network.  I am lost as to what i should do.  Any ideas?

---

### Post by scrooge_74 on 2006-11-15
> **akudewan said:**
> dsmalley: Wow. I can't thank you enough. Samba is working just fine, and I can browse the machines on my network with ease (using konqueror).

This thread deserves to be pinned/sticky. You should really post this as a Howto  in the Howto forum. I'm sure it will help lots of people :)

NOW I CAN HAVE MY LIVE BACK!!! This really needs to be pinned, lots of people with the same problem.

---

### Post by p2im0 on 2006-12-03
Excellent work, Dave.  I've browsed these forums for a long long time and I must say this is the first post that has given me real incentive to want to join and thank the poster.

There are very few of us left that can appreciate a real effort of word choice, formatting, and detailed documentation.  Thanks for your time with this.  You saved many people hours of frustration.  Keep up the good work.

-Brett

---

### Post by Tookelso on 2006-12-05
Thanks a bundle from me, too! A++ :p

---

### Post by addisor on 2006-12-07
I'm not so lucky, still only works with firestarter off! even with line. I've not really been using samba, more samba with utf8 encoding using cifs. 

# Initialize
$IPT -N INBOUND 2> /dev/null
$IPT -F INBOUND

# Temoporarily set the field separator for CSV format
OLDIFS=$IFS
IFS=','

# Allow response traffic
$IPT -A INBOUND -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INBOUND -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT

# Hosts from which connections are always allowed
while read host garbage
        do
                $IPT -A INBOUND -s $host -j ACCEPT
        done < /etc/firestarter/inbound/allow-from
Any advice so I dont turn off firewall every time i share. Can't get into linux desktop from XP wireless laptop either.

---

### Post by TheValk on 2006-12-07
Thanks from me also.
I installed firefighter and found that I lost all communication from my Windows XP box and my Ubuntu 6.10 Samba and Apache servers.
After setting up a few rules I regained connection using IP addresses but not computer names.
A quick search on Firefighter and Samba and your post was near the top. Your solution worked a treat and I wouldn't have fixed the problem without it.
This definitely needs a sticky :-D

---

### Post by S-Keiko on 2006-12-21
For those of you who don't feel comfortable allowing any trusted(?) lan machine to access any UDP port on your box, here is a work around : 

Make your samba act as a WINS server (simply set  "wins support = yes") and have the other boxes use it or set it up in the dhcp server if you use one.

This way, the name resolving won't rely on broadcast anymore.

++

---

### Post by FranklinFarm on 2006-12-21
Thank you for the post. I can now see all of my windows boxes on my local lan. I had to add winbind, set rules in firestarter for samba share, edit /etc/firestarter/inbound/setup per DSMALLEY suggestion and finally edit hosts in /etc/nsswitch.conf

Very helpful post!:KS

---

### Post by liamk on 2007-01-21
:\

even if I add rule in /etc/firestarter/inbound/setup

$IPT - A INBOUND -p all -j ACCEPT

and iptables -L print in INBOUND section:

ACCEPT all anywhere anywhere

**I still cant access to samba shares :lolflag: ** I need to stop firestarter by typing 
/etc/init.d/firestarter stop, then connect to smb shares and start firestarter.

Any ideas :frown: ?

---

### Post by liamk on 2007-01-22
now I know what was wrong but i still dont know WHY it was wrong.

First I add in firestarter a trusted host (accept all from that host). Any service (ftp, ssh, swat etc) worked fine for that trusted host but not samba. So I've tried many things even allow inbound all from anywhere/anywhere but no effect :/  samba still need firestarter to go down to accept connections.

Today **I've removed the trusted host** and leve only allow service smb for that host and it **WORKED**.

So if you plan to use samba and firestarter do not add any trusted hosts ! unless you want to block samba for that host :lolflag:


next day ***********************************

**It worked only until restart :/**

If I block trafic in firestarter (close smb ports for all)  it takes much more time for client to show connection error mesage and firestarter log this connection as intruder attack. If I open smb ports, firestarter allows trafic between server and clinet but samba does not allow to connect the client. So imho the problem here is samba not firestarter... although if firestarter is down smb works perfect :)

next day ***********************************

**SOLUTION**
I've read once again first two posts by dsmalley in this topic - this time very carefully and  "I solved" the problem. The problem was (exactly as dsmalley wrote) name resolution. So if you have problem with firestarter and samba even with open smb ports you have two choices:

1. acces to samba shares without name resolution by **typing in explorer.exe  \\samba_server_ip **
2. read dsmalley posts until you fully understand what he wrote there and **remember to unchecking "Block broadcasts from external network"** which I forgot :/ and spend 3 days to make it work :)

---

### Post by wayanwolvie on 2007-01-26
Hi,

I have edited /etc/firestarter/inbound/setup and /etc/nsswitch.conf . I also have installed winbind. And yes, now I can ping any other computer in my subnet with it's netbios name. But  it doesn't apply with computer outside my subnet. I have put the WINS server address in smb.conf. But it still doesn't help. How should I do? Is there any way to let my ubuntu / winbind knows where the WINS server is?

---

### Post by tiagobt on 2007-02-05
I've already done the following:

[LIST]
[*]Allow the service Samba in Firestarter (gates 137-139 and 145) for everyone.
[*]Uncheck the box "Block broadcasts from external network" in Firestarter's advanced preferences.
[*]Add the new line in /etc/firestarter/inbound/setup (see Dsmalley's post).
[*]Install winbind using apt-get (although I didn't need it before and I still don't know what it does).
[*]Edit the file /etc/nsswitch.conf (see Dsmalley's post).
[/LIST]

After that, Firestarter allows me to see all computers in the Samba network, but refuses to connect to a network computer running Windows XP. I used the command line just to make sure the problem was not related to the unreliability of the user interface. When I enter the command "smbtree", I get the following error:

```
cli_start_connection: failed to connect to VAIO<20> (0.0.0.0)
```

Notice that VAIO is the Windows XP computer I'm trying to access. At the same time, Firestarter blocks a connection with the following details:

[LIST]
[*]Gate: 32823 (but changes every time)
[*]Origin: VAIO
[*]Protocol: UDP
[*]Service: Sun-RPC portmap
[/LIST]

What am I doing wrong? How can I fix it?

Thanks,
Tiago

---

### Post by Gen2ly on 2007-02-15
Appreciatel it, just what I needed.

---

### Post by s13_mills on 2007-03-14
I too am very grateful for this thread, samba and firestarter were causing me no end of trouble, not to mention somewhat of a security risk!
The author of this thread should be commended for his thorough answer, and for the eloquence of it! Linux really is beautiful, you just have to know how to use it!

---

### Post by DeusEx on 2007-04-05
adding:

> **dsmalley said:**
> 
```

# Allow response to netbios name broadcasts from the local network.
$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT

```

to /etc/firestarter/inbound/setup did the trick! thanks for the article.

---

### Post by millenium-hand on 2007-05-21
Hey dsmalley

Thanks! Found this thread on google. 
This has solved a major bother for me that I've had for a long time...
Whenever I wanted to browse the LAN I've had to switch off the firewall... not safe, and not convenient.

Thank you

---

### Post by morvael on 2007-07-11
Thanks for a very useful thread - it solved my problems.

---

### Post by Endorpheus on 2007-07-15
> **B7may said:**
> I have the same problem and changed the setup file the same.  Now from the machine that has firestarter installed, I can access my main network.  (In other words, I have a larger network and connected to that is the machine with Firestarter that controls a smaller network.)  But any machine that is connected to the network controlled by firestarter cannot get to the main network.  I am lost as to what i should do.  Any ideas?

Do you have ip forwarding enabled for your box running firestarter?  Just curious.

---

### Post by amireldor on 2007-09-17
Did anyone notify the FireStarter Developers about this firestarter/samba issue? It's like a minor-bug... i'm gonna check if someone posted a bug on this and hope it gets fixed in Gutsy.

---

### Post by DJ_Peng on 2007-09-17
Great Mother, I've been looking for this solution. That third line of code did the trick for me as well. This thread **has** to get a sticky. I've been pulling my hair out trying to figure out why the hell I lost the ability to browse the other boxes on my network once I installed or updated Samba. Now to remember this once I get upgraded to Gutsy. Just in case it's needed yet again.

---

### Post by phyre-x on 2008-02-23
an invaluable piece of information. finally got my firestarter to recognise hostnames so i dont have to have ports open to all the network since i get a pair of random IP's each time i log in due to a large network. Thanks a lot to the author, my firewall rules just became a million times easier to follow.

---

### Post by dmizer on 2008-06-10
> **dsmalley said:**
> I forgot to mention one other useful thing: when winbind is installed, it's always nice to add "wins" to the hosts: line in /etc/nsswitch.conf.

```

hosts:          files dns mdns wins

```

This will allow ordinary TCP/IP programs to resolve hostnames with netbios, so you can, for instance, do "ping <hostname>" instead of "ping 192.168.1.xxx". Of course, ping isn't all that wonderful, but it's a lot easer to do "ftp hostname" or "ssh hostname" or browse to "http://hostname" than using raw IP's for the local machines (assuming of course they are running the given service and the forewall on the target machine allows access to the right ports).

Dave

something really important to know about /etc/hosts is that the order DOES make a difference here.  if you use the above configuration in tandem with openDNS.org, you will end up with non-functional name resolution.  this is because dns is resolved before wins, and opendns.org will send the unknown local name to a 401 page like this: [http://guide.opendns.com/?url=whatever&client=ff20](http://guide.opendns.com/?url=whatever&client=ff20) (assuming your local computer name is "whatever").

but, if you order your hosts file like so:
```
hosts:          files [COLOR="Red"]wins[/COLOR] dns mdns
```
then wins is resolved before dns, and local name resolution works again.  ping and local name resolution also works much faster this way because it doesn't have to wait for dns to time out.

---

### Post by Thelasko on 2008-06-30
Just use [Gufw.]("http://gufw.tuxfamily.org/")  It's way better than firestarter.

---

### Post by Stoneface on 2008-07-21
I changed the file permission to chmod 777 for /etc/firestarter/inbound/setup and I made the changes  I added the line 
```
# Allow response to netbios name broadcasts from the local network.
$IPT -A INBOUND -s $NET -p udp -m state --state NEW -j ACCEPT. 
```
Later on I changed the file permissions back to 644. Is that correct? Or should it be 666?

---

