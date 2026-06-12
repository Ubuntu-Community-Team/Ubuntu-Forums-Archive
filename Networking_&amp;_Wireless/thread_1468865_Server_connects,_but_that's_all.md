---
title: "Server connects, but that's all"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by roystreet on 2010-05-01
Hello,
   I have ubuntu server 9.04 running & it is connected to my Cisco router.  It will get an IP address from the router, but that's all.  What do I mean by that's all?  Well, I can't got to the webmins website - It takes tooooo long to connect & my brower (On another machine on the same network) gives up trying to connect.  I try to use PuTTY & it won't connect to it.  It just so happens to be that there is a clean install (From awhile back) of Win XP on the server machine.  So I plugged up a monitor and such & made it boot into XP.  I could open up XP & connect to the internet.  I could surf with no problem.  If it's booted up in XP, then I can also see it on the network from other computers.  
So the issue is somewhere my Linux configuration is not setup correctly (Anymore) so that I can reach it.

I was doing some work on it last night via webmin & I may have messed something up in there.

I appreciate all of the help you can give.

~roystreet

---

### Post by Iowan on 2010-05-01
Are you trying to connect by name or IP address? You didn't mention if the address is a static lease or a DHCP lease (that could change on occasion).

---

### Post by lisati on 2010-05-01
I use webmin too, and had to set my router to allow port 10000 through to my server.

---

### Post by roystreet on 2010-05-02
> **Iowan said:**
> Are you trying to connect by name or IP address? You didn't mention if the address is a static lease or a DHCP lease (that could change on occasion).

I'm sorry about that. I've tried connecting via name in win explorer.  I've tried connecting via ip (using [https://...:10000](https://...:10000)) I'm using the old "proven" ways that I've never had a problem with. It's very odd & I'm almost certain I changed a setting in Webmin to cause this to happen, but I'm not sure.  When it is booted up in ubuntu & I try to ping it from another machine (Win) there is no response. Yet my router shows it has given it an IP address.  When I boot the same machine up in XP it will talk just fine to anyone out there!  

*It's a DHCP assigned address.  Which I check the for the most current one.  

Thanks!

---

### Post by roystreet on 2010-05-05
Are there no more thoughts on this issue?  If not, then I have lost my server & I will just install server 10.04.  Hopefully I won't lose anything important in the process.
.
Are there any reviews or documentation that latest version?  I've downloaded the server pdf brochure from the ubuntu site, but the doc states it's for for version 8.04
.
Thanks, roystreet

---

### Post by Iowan on 2010-05-05
I just discovered that there is a 10.04 [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html"). (There's also one for [9.04]("https://help.ubuntu.com/9.04/index.html")) Which way would you like to pursue?

---

### Post by roystreet on 2010-05-06
10.04 is the direction I will go!  How did you find that?  I wish I could figure out why that machine doesn't want to cooperate - It was working so well.

Thanks for the link!
~roystreet

---

### Post by Iowan on 2010-05-06
> **roystreet said:**
>  How did you find that? :-$
 Hope Lucid works for you - keep us posted!

---

