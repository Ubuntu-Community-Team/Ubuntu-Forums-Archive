---
title: "cant telnet into ubuntu!!!"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by totalacedude on 2009-11-27
hi guys!
 
am a noob to ubuntu and learning fast.
i want to be able to telnet to my machine from a windows pc just using telnet on windows pc.
 
i have setup telnetd on ubuntu machine as well as gftp, ports 21 and 23 are listening, 
 
i can ftp into ubuntu ok, but i cant telned into it!
 
i can telnet out of ubuntu using the basic telnet command
 
no firewall is up (yet) as i want to get it all working ok before i tighten it up!
 
any ideas guys!
 
like i say im new so itll prob be a nice easy 1 for some of u :)
 
cheers ian

---

### Post by SlugSlug on 2009-11-27
use putty on your windows machine and install ssh on your ubuntu - telnet = poor

---

### Post by totalacedude on 2009-11-29
thanks for the reply, 

but although i agree that telnet is bad i want to be able to telnet it from a few different windows pc's at work, some of which will not allow me to install other items!

i know telnet is pants, but its pritty much the only thing i can use !!

i have tried to telnet into it on my internal network ie 192.168.1.1 to 192.168.1.2 etc but still nothing!

i can telnet from ubuntu machine to windows pc ok!
 any pointers pls :)

---

### Post by Iowan on 2009-11-29
In case it helps, [here]("http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html") is a telnet server How-To I found... though it sounds like setup isn't your problem.

---

### Post by SlugSlug on 2009-11-30
Putty does not need a install, maybe you can use that at work,  


sounds like you dnt have the telnet server installed..

---

