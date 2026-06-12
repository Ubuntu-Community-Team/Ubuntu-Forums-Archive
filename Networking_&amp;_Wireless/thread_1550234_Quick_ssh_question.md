---
title: "Quick ssh question"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by oomar on 2010-08-10
Now I'm in mexico and i've been using ssh to route my internet connection back home so its more secure yadada and its just a test to make sure my tunneling is actually working. Well it is.

Now in the past I have done port scans of myself and I have a few ports open. 80 (http), 10000 (webmin), 3128 (squid proxy), 50 (ssh), 5555 (ssh). Those are the ports I have configured to be open... in the past these were the ports that nmap found open.


NOW when I do a port scan with Nmap, 80 is open, 3128 is open, 10000 is open, 5555 is open, then... 113/tcp is CLOSED... what..? Where did that come from? and then 50 isnt even MENTIONED even tho I actually have a ssh connection active AS Im doing the portscan. 

So does ssh use 113? it is the "auth" port. and why do you think 50 isnt even picked up by nmap?

Thanks

---

### Post by oomar on 2010-08-11
Anyone...? lol I thought a quick question like this would have been answered pretty darn quickly. lol

---

### Post by endotherm on 2010-08-11
TCP113 is the Identd service. here is the man page:
[http://manpages.ubuntu.com/manpages/jaunty/man8/identd.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/identd.8.html)

from teh description:
> 
  **identd** operates by looking up specific TCP/IP connections and returning
       the  user name of the process owning the connection.  It can optionally
       return other information instead of a user name.so what this tells me, is that the port test on 113 was not related to ssh or any of your other server daemons, but rather with nmap/zenmap attempting to fingerprint the os and the user running each of the services.  what scan options are you using (not that I'm an nmap expert). 

Edit: confirmed here: [http://nmap.org/nmap_doc.html](http://nmap.org/nmap_doc.html) (do a page search for identd)
> 
   
[LIST]
[*]TCP reverse ident scanning : As noted by Dave Goldsmith in a 1996 Bugtraq post, the ident protocol (rfc1413) allows for the disclosure of the username of the owner of any process connected via TCP, even if that process didn't initiate the connection.  So you can, for example, connect to the http port and then use identd to find out whether the server is running as root. This can only be done with a full TCP connection to the target port (i.e. the -t option).  nmap's -i option queries identd for the owner of all listen()ing ports.
[/LIST]
 
so nmap was doing it just to see what user was running each of your server apps. 

as for port 50, do you have fail2ban or denyhosts running on the server? try sshing in and run
```
netstat -tlup
```
to see the ports and servers you have running. confirm that you still have an app on 50, and that it is allowed on whatever firewall you employ.

---

### Post by oomar on 2010-08-11
sudo nmap -O [myserverip]

(sudo is required for -O)

that makes sense... except it used to not come up in previous nmap scans. hmmm It could be nmap... but I don't know how it could be doing that on and off thing.

---

### Post by endotherm on 2010-08-11
> **oomar said:**
> sudo nmap -O [myserverip]

(sudo is required for -O)

that makes sense... except it used to not come up in previous nmap scans. hmmm It could be nmap... but I don't know how it could be doing that on and off thing.

I've added some to my post above, since you read it last. sorry, should have just replied.

---

### Post by oomar on 2010-08-11
Ok... Well then I guess I'm just curious whether -O implements the -i option?

and I don't have either fail2ban or denyhosts as I use public key authentication so script kiddies cant touch me :D Im considering installing it but neither are installed at the moment.

Now I KNOW I have port 50 open and ssh listening on it because... well I'm using it right now. lol I'm tunelling my connection over it as we speak so its definately working. PLus I just checked the SSh server config file and its listening on 50 and 5555 as I set it up.

---

