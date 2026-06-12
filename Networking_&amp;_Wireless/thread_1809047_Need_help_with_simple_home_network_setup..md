---
title: "Need help with simple home network setup."
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by IanP7 on 2011-07-21
I have a desktop and a laptop computer both running Ubuntu 10.04, Linux 2.6.32-33-generic and GNOME 2.30.2.  Both connect to the internet through a Thomson Gateway TG585v7 Router. The desktop uses a wired connection, the laptop wireless.
I want the 2 computers to communicate with each other. Having searched the internet it seemed that SSH was the way to go.
I installed sshd on the desktop and managed to ssh to localhost (using password authentication initially). My router gives me the ip addresses for itself and both computers and both computers can ping all three addresses, however if I try to ssh from the desktop to 'the ipaddress of the desktop' (or anything but localhost) the connection times out. (I can't ssh from the laptop to the ipaddress of the desktop either) I don't know where to go from here!

I'm sure lots of people have this set up and the documentation is out there somewhere but I can't find it! 

I switched from Windows to Linux about 12 months ago and worked as a test analyst on large Unix systems many years ago (before I retired). I am quite happy using a terminal etc but I don't pretend to know much about networking. Hope someone can help.

---

### Post by Bucky Ball on 2011-07-21
Are you using static IP addresses? As you would know, everytime you reboot your machine it will get a new IP if not and that can make it boring as you need to discover the new IP everytime you want to network to that machine.

I simply use Places>Connect to Server, and choose SSH. Input the IP address of the machine you are wanting to connect with, input the *user name and pw of the machine you are trying to connect to*.

---

### Post by IanP7 on 2011-07-21
Thanks for quick response. I think NOT, but would need to check the router - unfortunately have to go out now!!

---

### Post by IanP7 on 2011-07-21
Although the ip address to the internet is dynamic, it appears that my  local network addresses are static. (I say this because I switch my  computers (and router) off overnight and ifconfig is consistently  returning the same addresses). However, whilst I was out today I was  wondering what else could be stopping me connecting and I remembered my  firewall (stupid or what?). i'm using UFW with incoming set to 'deny'. I  unset this and was able to get a connection, so now I have to read up  on UFW and also match user names on laptop to desktop and I may be  there!

Thanks again for reply - it started me thinking!

---

