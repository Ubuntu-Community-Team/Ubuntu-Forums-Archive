---
title: "Lirc &amp; MCEUSB2 *slow*"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by saintm on 2007-01-17
Hi everyone,

I finally got my MCE Remote (RC-6) working in Edgy under LIRC.  I had to use irrecord though to create the lircd.conf file since it refused to work with any find on the 'net.  Running irw or using MythTV is a painful experience though since the key presses are *Slow* to respond.

I saw that a patch came out for the problem, but that it wasn't necessary anymore in Edgy since it was included now anyway.  Unfortunately, it seems I still have the problem :(.

What is troubling me is 
[LIST=1]
[*]Why did I need to create a raw lircd.conf file (is something wrong with my remote that it isn't sending "standard" codes through)?
[*]Is this causing my slow response?
[/LIST]
Just a definition of what I mean by slow.  I fired up irw and pressing page up is painful to watch the results with.  It will show, then wait a second or three and then show two suddenly and then wait a while and then again it will come up. 

BTW, this is the standard standalone remote package.  It was not bundled in with my Hauppauge PVR-500 card at all.

What are the things I need to look at to start troubleshooting this?

Thanks!!

---

### Post by majoridiot on 2007-01-17
did you use mario's outstanding guide for lirc on edgy?

[https://help.ubuntu.com/community/Install_Lirc_Edgy#head-a1dba57858ffd46f283504b106d6d355794890bc](https://help.ubuntu.com/community/Install_Lirc_Edgy#head-a1dba57858ffd46f283504b106d6d355794890bc)

i used it to install lirc on dapper... the mceusb2 patch and config he provides, installed and works 
flawlessly with my RC-6.

it might not be a bad idea to use the patches he provides, regardless of whether or not edgy has
been "fixed" or not.

---

### Post by saintm on 2007-01-18
Hmm, you make an excellent point.  I did follow the guide, but ommitted doing the patches believing that it should all be working now.

I will give it a try this evening.

Holding thumbs!

Thanks!

---

### Post by Dubstar_04 on 2007-02-25
I am also having problems with a slow remote, and mulitple button presses are ignored. How is the patch installed? 

Is it part of marios files?

---

### Post by superm1 on 2007-03-04
> **Dubstar_04 said:**
> I am also having problems with a slow remote, and mulitple button presses are ignored. How is the patch installed? 

Is it part of marios files?
Go to the bottom of the lirc page.  There is a repository listed there that has a mceusb2 patched version of lirc.  It includes transmitter support and a speed patch.

---

### Post by Syo on 2007-03-07
I tried the mario packages However when I rebooted to see if everything was gonna hold water I noticed  /dev/lirc was no longer present. 
I still have /dev/lircd 
If I reinstall the edgy official packages /dev/lirc comes back again.

---

### Post by superm1 on 2007-03-08
> **Syo said:**
> I tried the mario packages However when I rebooted to see if everything was gonna hold water I noticed  /dev/lirc was no longer present. 
I still have /dev/lircd 
If I reinstall the edgy official packages /dev/lirc comes back again.
After you had my packages loaded, did you try to rmmod and modprobe lirc_mceusb2?  It's possible that it isn't automatically loading the driver for some reason or another.

---

