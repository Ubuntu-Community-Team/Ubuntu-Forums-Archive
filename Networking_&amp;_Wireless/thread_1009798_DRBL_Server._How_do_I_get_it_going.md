---
title: "DRBL Server. How do I get it going?"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by Roasted on 2008-12-13
I'm trying to set up CloneZilla Server Edition, which requires a DRBL server.

I followed a guide online which told me how to get up the DRBL server. I'm using Ubuntu 8.10 32 bit. 

Here's the guide:
[http://clonezilla.org/clonezilla-server-edition/](http://clonezilla.org/clonezilla-server-edition/)


I don't know how to get this "started". I installed the DRBL server... but NOW what? How do I get CloneZilla moving? How do I get the DRBL server "activated"? 

I just assumed I'd have to install CloneZilla to my computer and, using the DRBL server, it would bring up a GUI with the screen that you see in the guide. But I'm not sure what to do, exactly.

---

### Post by Roasted on 2008-12-14
*bump* 

Any idea, anybody? I NEED to get this running.

---

### Post by Roasted on 2008-12-16
Okay, I got it part way going. I think. This is so unusually confusing that I wonder how anybody can get this to work... anyway... so I ran that one command, drblpush -i... but it didn't work. So I just ran drblpush (there's more before it, I just know it ends with drblpush) and I got some switch options. So I tried -o to set something. Didn't work. So I tried -i again. BAM. Magically worked! 

So there's several things here with CloneZilla Server (running on DRBL) that I don't get.

For one... my goal is to have 1 computer (server) hooked up to 1 switch with a various amount of ports, then hooked up to the clients who need to be cloned. This will be a private lan that has NO outside connection... yet at one point, it REQUIRES me to put in an external IP address before continuing? Really? I don't want an external IP address. I just want to run DHCP and hook up what computers I need and click clone and BAM. Done.

How is this CloneZilla Server this complicated to set up? What am I doing wrong? Is there a guide with pictures that actually tells me what I'm doing instead of being so vague?

---

