---
title: "Ubuntu 9.1 with Linksys wireless g WPC54G card"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by Mdecarlos on 2009-11-22
Hello. I just downloaded the ubuntu 9.1 last night and installed it on my Thinkpad T22. Everything went smooth up to connecting to the internet wirelessly. I have a Linksys wireless g WPC54G v4 card. I've been reading numerous threads prior to posting this query but most (at least from what I've found) either contained commands that I have no idea on how to run it or threads with similar issue but different Ubuntu version or different wireless card model. Any help would be much appreciated as I look forward to my experience with this OS.
 
 
Many thanks
 
Miguel

---

### Post by AFI420 on 2009-11-22
welcome to ubuntu

---

### Post by Mdecarlos on 2009-11-22
Thank you.  I'm very excited about this new OS.  It's working well with wired connection.  However, my router is in my bedroom and I'm hoping to get unleashed.  At least up to my living room and I'll go from there :D.

---

### Post by AFI420 on 2009-11-22
ya Im going on a week now trying to figure out my wireless. I got a 40ft network cable from work today and am going to go wired until I can get wireless going.

---

### Post by Mdecarlos on 2009-11-22
I know what you mean AFI420.  I just learned how to use the 'Terminal' function a minute ago from reading other forums.  So in case someone reads this post, here's how I got my device name and what I have:

At the 'Terminal' (under: Applications, Accessories, Terminal), I typed in:  lspci.  Here's what I got:

06:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

I hope that help.  I think I need to install the driver (not sure where to get that) and hopefully, Ubuntu will pick it up from there.

Good luck to you and our plight ;)

---

### Post by Mdecarlos on 2009-11-22
Oh, I suppose you could try the same command and post your results here.  Hopefully, a guru finds this query and assist us and get us unleashed.

---

### Post by AFI420 on 2009-11-22
I think if it isnt automatically working in ubuntu, you need to use ndiswrapper with the windows drivers or find out what chipset you have and see if they have a linux driver for it. I understand that this OS is much better because it is soo customizable but it makes things quite hard for beginners. If youve never used a UNIX or Linux OS I would suggest you google Linux Intro and read the first pdf that comes up.

Theres actually a post for my exact wireless adapter (wusb54gc ver 3) but i still cant get mine working, probably because im a noob, but its a learning experience.

---

### Post by Mdecarlos on 2009-11-22
k, I'll read up on Linux intro.  Thanks.  By the way, I found this thread - I hope this works for you:

[http://ubuntuforums.org/showthread.php?t=446375&highlight=Linksys+WPC54G](http://ubuntuforums.org/showthread.php?t=446375&highlight=Linksys+WPC54G)

This is a post from [sdegrace]("http://ubuntuforums.org/member.php?u=293574")

---

