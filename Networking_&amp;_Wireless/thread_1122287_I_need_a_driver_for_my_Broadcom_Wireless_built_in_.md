---
title: "I need a driver for my Broadcom Wireless built in system"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by robinbj on 2009-04-10
I have searched for drivers for my
Broadcom 4321ag 802.11a/b/g/draft-n Wi-Fi Adapter
and I can only find ones that are designed for Vista, which is what my HP Touchsmart tx2 with an AMD Turion X2 64 bit driver came with. Any ideas? 

Bradley Robinson

---

### Post by Favux on 2009-04-11
Hi Bradley,

Have you checked System>Administration>Hardware Drivers to see if you have the proprietary Broadcom STA wireless driver (wl) activated?

A thread you may find useful:

[http://ubuntuforums.org/showthread.php?t=1038898&highlight=tx2*](http://ubuntuforums.org/showthread.php?t=1038898&highlight=tx2*)

Be sure to read through it before you do anything.

---

### Post by superprash2003 on 2009-04-11
if that doesnt help try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

---

### Post by robinbj on 2009-04-11
> **superprash2003 said:**
> if that doesnt help try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

Thanks for the help, however im so new at using anything computer related i would need uber step by step simple easy to follow. Im afraid that i would screw everything up

brad

---

### Post by dmizer on 2009-04-11
Try it. If you get stuck or don't understand something, just ask :)

---

### Post by ubudog on 2009-04-11
Yeah thats what I did and after I enabled broadcom wireless,  it worked fine.

---

### Post by pompouspilate on 2009-04-12
I am very new to using unbuntu, but don't you have to be connected to the internet to access the broadcom linux drivers through the System>Administration>Hardware Drivers ?  When I go there its just a blank window saying there aren't any proprietary drivers in use on the machine and no options for adding anything?  If so kind of funny you have to access the internet to get the internet working....

I've tried about 10 different walkthroughs for this issue.
Either they suggest A) just go to System>.... which doesn't work
or B)I play with ndiswrapper for hours to no avail.

---

### Post by robinbj on 2009-04-12
I've tried about 10 different walkthroughs for this issue.
Either they suggest A) just go to System>.... which doesn't work
or B)I play with ndiswrapper for hours to no avail.[/QUOTE]


I have found that the best way so far to connect is thru you ethernet  i have yet, tho, to have the inernet re-set in my campus living building. The IT department out here stinks and are extreemly slow at responding to issues. their more worried about getting the IT system on FACEBOOK than they are about getting their server systems to work....

---

### Post by Favux on 2009-04-12
Hi pompouspilate,

You are correct.  It's a catch 22.  Hopefully you have an ethernet cable you can wire into the router until you get Broadcom STA installed and activated.

---

### Post by Ayuthia on 2009-04-13
> **pompouspilate said:**
> I am very new to using unbuntu, but don't you have to be connected to the internet to access the broadcom linux drivers through the System>Administration>Hardware Drivers ?  When I go there its just a blank window saying there aren't any proprietary drivers in use on the machine and no options for adding anything?  If so kind of funny you have to access the internet to get the internet working....

I've tried about 10 different walkthroughs for this issue.
Either they suggest A) just go to System>.... which doesn't work
or B)I play with ndiswrapper for hours to no avail.

You do not need to have a working internet connection for the Broadcom STA driver.  However, the Broadcom STA driver only works with the 4311, 4312, 4321, 4322, and some 4328 cards.

If you want to use the open source version (b43), you will need a working internet connection to make it work because it does need some information from a proprietary firmware file to make it work.

If you are not able to get the wirless card to work, please post the results of:
```
lspci -nn
lshw -C network
```
This will help us identify your wireless and wired cards.  In some cases the wired card can cause conflicts with your wireless card.

---

### Post by robinbj on 2009-04-15
> **Ayuthia said:**
> You do not need to have a working internet connection for the Broadcom STA driver.  However, the Broadcom STA driver only works with the 4311, 4312, 4321, 4322, and some 4328 cards.

If you want to use the open source version (b43), you will need a working internet connection to make it work because it does need some information from a proprietary firmware file to make it work.

If you are not able to get the wirless card to work, please post the results of:
```
lspci -nn
lshw -C network
```
This will help us identify your wireless and wired cards.  In some cases the wired card can cause conflicts with your wireless card.

I think it works fine now however i have issues with the University wireless internet that runs on WPA2 Enterprise which most of the Linux users on campus face.

brad

---

