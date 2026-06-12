---
title: "Help with networking and more"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by troegs on 2009-02-14
Hey all. I'm a new linux/ubuntu switcher and I couldn't be happier. I bought a new laptop with the expressed purpose and intent of making it a linux machine. Now that I've been using it for about a month, (and have left my old windows machine virtually untouched) I'm wanting to set up my old machine as a linux machine as well. What I'm curious about is how to go about setting up my old machine as a fileserver that I can access from anywhere with my current machine. Once I get my old machine with linux loaded on it, what do I need to do in order to set it up as a fileserver? I'd like it to also still be a semi functional machine in case my main ever bites it.

Thanks for any help in advance,
T.

---

### Post by FishRCynic on 2009-02-14
depends on your network setup and what you want to accomplish
need to know more info

eg
old pc --> ethernet to router
laptop --> wireless to router

router --> internet

samba is already installed 
(samba will allow microsoft pcs to work on
your network)
but you may have to install
samba server
search this forum
for various different ideas to work with
[there are lots of smart peoples here and all
are willing to help]

see this thread for solving name resolution issues
using samba  (its sort of misnamed but the ideas are correct)

[http://ubuntuforums.org/showthread.php?t=388337](http://ubuntuforums.org/showthread.php?t=388337)


if you want to access the fileserver over the internet
you will have to configure your "router" to do so
using/enabling/installing secure ftp or remote desktop - 
(i wouldn't open samba to the internet) 

not much help - but maybe gets you started
and it is much easier than it looks

---

### Post by superprash2003 on 2009-02-14
if its a linux only network you could use NFS , else you could go with samba..

---

