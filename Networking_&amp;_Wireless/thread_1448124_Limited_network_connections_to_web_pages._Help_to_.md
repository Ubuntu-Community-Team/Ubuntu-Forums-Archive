---
title: "Limited network connections to web pages. Help to solve."
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by Makliugas on 2010-04-06
Good evening to everyone !

How ya doin' ? I'm quite new to ubuntu/linux OS, but greatly interested in. Recently installed kubuntu 9.10 and faced a few problem with limited internet connection. So here is my prob:
I can connect to webpages, download from them and so on .... But there is absolutely no connection when I'm trying to use synaptic or wget, apt-get functions by terminal. I'm using LAN connection with over ~800 user there. I need also to use proxy server... Can't solve this problem, can't find information closely related to my problem. Thank you guys in advance. I like ubuntu pretty much and want to use it further. Please replay as soon as you can ! ):P HELP ):P

Here is the message I get sometimes: 

root@nobody:/home/nojnoj# sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory

And sometimes it starts to connect and just drop out after 5min at 0% ...

just like that : 

nojnoj@nobody:~$ wget [http://ftp.litnet.lt/pub/ubuntu-cd/karmic/ubuntu-9.10-desktop-i386.iso](http://ftp.litnet.lt/pub/ubuntu-cd/karmic/ubuntu-9.10-desktop-i386.iso)
--2010-04-06 19:14:05--  [http://ftp.litnet.lt/pub/ubuntu-cd/karmic/ubuntu-9.10-desktop-i386.iso](http://ftp.litnet.lt/pub/ubuntu-cd/karmic/ubuntu-9.10-desktop-i386.iso)
Resolving ftp.litnet.lt... 193.219.61.67, 2001:778::a
Connecting to ftp.litnet.lt|193.219.61.67|:80...\


BUT IF I GO MANNUALLY TO THAT SITE I CAN EASILY DOWNLOAD THAT FILE .......... Completly confused.KPACKAGEKIT(Kubuntu 9.10) also refuses downloading any updates,codecs etc...

---

### Post by TheSqueak on 2010-04-07
Are you using a proxy to connect to the internet?

---

