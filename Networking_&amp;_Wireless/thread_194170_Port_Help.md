---
title: "Port Help"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by crawfjs on 2006-06-11
I have installed tomcat on a breezy badger system.  Running on port 8080 works fine, but if I change the server.xml file to port 80 (restart server), it won't serve at all.  I'm wondering if something is conflicting with that port and how to check.

---

### Post by killernurd on 2006-07-07
I'm having the same problem...

I feel like it's something simple, just beyond my grasp.

I installed nmap and portscanned myself, to figure out what was going on. When I had tomcat5 listening on port 80, nmap reported that port 80 was closed, still, but when tomcat was listening on port 8080, it was reported as open.

I have a sneaking suspicion it has to do with the Apache2 config files; tomcat5, despite being independant, still uses some apache libraries and is therefor dependant on apache2-common. I think that if I play with the Apache2 config, it'll work on port 80....

---

### Post by crawfjs on 2006-07-07
The reason for this is, Ubuntu only listens on ports where there are daemons listening (for security reasons), therefore, by changing the server.xml, it doesn't appropriately notify the system that there's a daemon listening.

I figured it out (or atleast a workaround).  Do a google search for iptables and redirecting 80 to 8080.  If you use the PREROUTING switch, the result it transparent to the user.  Therefore, 8080 doesn't show up in the address bar.  

Regardless, I would like for this bug to be fixed, but this is a "tough to find" workaround.

---

### Post by killernurd on 2006-07-10
I actually found that workaround right here in the forums, but you're right - it was tough to find, and I'd rather have a more permanent solution anyway.

The iptables redirect is what's in place right now, though, 'cause it does work :)

Also - I do know that Ubuntu only opens ports that have daemons listening; what I don't understand is why it refuses to allow Tomcat to listen on port 80 - it'll listen on any other port.

---

### Post by crawfjs on 2006-07-10
Well, I wish I had an answer to that myself.  It just doesn't make sense.  Perhaps this is an issue that stems from Debian rather than Ubuntu.

---

### Post by killernurd on 2006-07-18
Gawd, I feel stupid.

It's because Tomcat is run as the 'tomcat' user.

Anything wanting a port number of less than 1024 needs to be run by root.

Argh.

Off to config Apache with mod_jk....

---

### Post by BrianB2 on 2006-07-27
The current distribution of tomcat installs so that it runs chrooted. This is a GOOD THING and should not be subverted. It is ducking the issue to run tomcat as root.

Tomcat works perfectly well as a standalone web server. One should not create an over-complex apache-AJP-tomcat combination unless this is really what you need. It is not a valid solution to this problem.

Using iptables to portmap traffic from 80 to 8080 is an ingenious circumvention, but hardly a solution.

I think the fundamantal problem is one of unix permissions. Other products run chrooted and can still listen on port numbers lower than 1024. I've looked at how mysql and hamachi do it, but can't figure it out by looking at the installed files.

There MUST be a standard linux way to achieve this objective, i.e. to give the user tomcat5 permission to open/read/write a socket on port 80.

I feel stupid, but I've been trawling the web and cannot find out whether it is even possible. Can anyone point me in the right direction?

---

