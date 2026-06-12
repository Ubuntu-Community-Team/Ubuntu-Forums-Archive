---
title: "Stumped with wireless Atheros 802.11 ubuntu 8.10"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by going_north on 2009-03-11
Hey.  First, thanks for the great forum which has been a huge help just reading through for a complete newb to linux such as myself. 

Here's my story so far. I installed ubuntu 8.10 and couldn't get my wireless to work. I messed with it a little bit and then decided I would try linux mint (version 6) instead since it supposedly worked a bit better dealing with those issues out of the box.  

Well my wireless still isn't working.  

I'm using an HP dv7-1245dx with an AMD turion x2 64 dual core processor, 4 gigs of ram and running the 64 bit version of mint. My wireless adapter is "AR242x 802.11abg Wireless PCI express adapter"

when I run "lshw -C network" in the terminal it says network UNCLAIMED.

I went through "Administration > Windows Wireless Drivers" and loaded the driver from my vista partiton (which appears to have already been there anyway)  and checked to make sure that it was activated by looking at my hardware drivers.  

It says that it's activated but not currently in use... :(

Another thing that concerns me is that there is a control on the laptop to turn the wireless on and off. (blue light on; orange light off)  In vista it turns on and off no problem but in ubuntu I can't make it turn on.  

One other thing, I have no way to connect my laptop to the internet without a wireless connection.  I'm currently using my desktop (also on wireless) but unfortunately my situation does not allow for me to plug in directly.  So anything I add to my linux system in the meantime to work on a fix will have to be done via usb drive.

Like I said before I'm completely and utterly new to all things linux or ubuntu and to be honest not the most computer literate person to begin with.  I'm posting as a bit of a last resort since I don't like to put my ignorance out there in public unnecessarily, but after reading and googling most of the night away I'm still apparently not much closer to a fix.

Thanks so much for any help with this.

---

### Post by pewterbot9 on 2009-03-12
I'm in the same boat, pardner! No ethernet highspeed access at home, only dialup. What I've done, is install dialup in my Ubuntu 8.10, using the basic "pon" command. Instructions are here:

[http://tinyurl.com/ybcu68](http://tinyurl.com/ybcu68)

Actually, they give four ways to set up dialup. I suggest going right away with the third: it's elegantly simple, and worked like a charm...whereas the first two were convoluted, and a waste of time. So when that page loads, jump right on down to:

Alternative Way 2 (using pppconfig & pon/poff)

Now, it will take much longer to download your Linux packages, but it's really worth it IMO. Just make sure to set aside the time, and do something else while waiting for download to complete.

I use an Actiontec USB modem, BTW...works great w/Linux. Got it fer around $30 from eBay.

---

### Post by SnowRider on 2009-03-12
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)                 Try 4.13 in this link

---

### Post by pewterbot9 on 2009-03-13
My wifi chip is the Atheros 5007G...and after scouring many Ubuntu help pages and message boards, I've concluded there's really nothing that will help, until the Linux community comes up with a good driver for it. For those who don't want to wait, this might be the perfect solution:

This guy has an excellent solution for two good USB wifi adapters suited for LInux:

Ubuntu wireless - 8.04 - what works
[http://www.youtube.com/watch?v=ewaym7rbAUE](http://www.youtube.com/watch?v=ewaym7rbAUE)

Go to his page, you'll see this blurb:

"Wireless without the nonsense for Ubuntu Linux. No headaches, just working wireless - models described are the Edimax EW-7318USG and EW-7318UG - Goto NewEgg.com for both - just use site search. "

I just checked NewEgg for the Edimax: it's $25 (comes to $33 after shipping/tax). The page:
[http://tinyurl.com/btklna](http://tinyurl.com/btklna)

But eBay has Edimaxes for $20. (Shipped from United Kingdom, doesn't state shipping cost.) The page:
[http://tinyurl.com/c8qpcv](http://tinyurl.com/c8qpcv)

---

### Post by mplinux on 2009-03-15
I was on the same boat. I'm running a dual boot Vista (64-bit)/Ubuntu 8.10 (64-bit) on my Toshiba Satellite L305D-S5893. I have the SAME WIRELESS CHIPSET you have. This is what I did to fix the problem. See this thread: [http://ubuntuforums.org/showthread.php?t=1095214]("http://ubuntuforums.org/showthread.php?t=1095214")


hope this helps!

---

