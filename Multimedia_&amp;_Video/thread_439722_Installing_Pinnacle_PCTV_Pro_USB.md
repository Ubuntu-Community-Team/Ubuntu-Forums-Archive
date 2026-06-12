---
title: "Installing Pinnacle PCTV Pro USB"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by Ender Wiggin on 2007-05-10
I'm a newbie to Linux, but I really like it. I've been trying to install my PCTV tuner, Pinnacle PCTV USB Pro, but I'm a little lost.

I went to this site:[http://linux.bytesex.org/v4l2/bttv.html](http://linux.bytesex.org/v4l2/bttv.html)

but could anyone walk me through what I need to do to install my PCTV tuner?

Thanks in advance

---

### Post by Ender Wiggin on 2007-05-11
I can't find a solution to any USB PCTV device, the only solutions I've found are for PCI cards and those didn't work. 

Does anybody have any suggestions?

---

### Post by Ergo on 2007-05-12
A search with "Pinnacle" will get you a long list of folks with the same problem.  Unfortunately no one has written any drivers for this to date.  What is the real shame is that Pinnacle barely classifies as working when installed on it's OS of choice.  Mine crashes constantly and freezes often . . . I am in the process of trying to study up on USB device driver writing, but I am not holding my breath, the silly thing is proprietary after all.  I suggest a good PCI capture device like HDTV 5500 (it comes with it's own software and it is made for linux).   Good luck.

---

### Post by Nikkus on 2007-05-14
Hi Ender(Pretty nickname ;))

Greettings from Barcelona Spain, right now, i have THE SAME problem like you! :(

BUT, searching with Mrs. Google i find it:

[http://usbvision.sourceforge.net/](http://usbvision.sourceforge.net/)

Here in the "Supported device" list we can see it:

0x2304 - 0x0112	 Pinnacle Studio PCTV USB (NTSC) with FM radio
0x2304 - 0x0210	Pinnacle Studio PCTV USB (PAL) with FM radio
0x2304 - 0x0212	Pinnacle Studio PCTV USB (NTSC)
0x2304 - 0x0300	Pinnacle Studio Linx Video input cable (NTSC)

This night(when i arrive in my house) i will try it!

Good luck!! And apologize my very poor english.. :(

---

### Post by jpmswiss on 2007-05-15
Well I hope that somebody get this going.

Actually I  have two Pinnacle Tuners (lucky me):

1. PCI PCTV 100i
In linuxMCE I actually got the card to perform a channel search and it found all the channels. 
But then I faced the famous black screen issue in linuxMCE (didn't work).

After clean Feisty install - the card is recognized in Myth but the data cannot be saved in the database.
But if that problem is solved maybe it still wont work (linuxMCE problem?).

2. USB PCTV Pro
Haven't begun to research this one yet.

All I wanna do is watch some TV.

Any other recommended TV programs that don't require a Computer Science degree to install???

It is very complicated.

Good luck to all.
John

---

### Post by Ender Wiggin on 2007-05-16
]hey Nikkus, thanks for the link. :( 

Unfortunately I have the PCTV Pro, not hte Studio version. But I did try that driver, just to see if it works. Didn't work. :(

---

### Post by Nikkus on 2007-05-17
hi Ender!

Well, right now i can't compile the driver. i keep try compile it. but, after all, i will search for anothers driver/solution or somethings else... :(

---

### Post by Nikkus on 2007-05-17
Hi!!

great news, folks!

Searching in Google, i find this page of ubuntu community in France:

[http://forum.ubuntu-fr.org/viewtopic.php?id=42434](http://forum.ubuntu-fr.org/viewtopic.php?id=42434)

look exactly this part:

"La Pinnacle PCTV USB Stick et  Pinnacle PCTV Hybrid Pro Stick sont supportés sous Linux grâce au driver Em2880."

i don't undestand French, maybe it sound like it:
"The Pinnacle PCTV USB Stick and  Pinnacle PCTV Hybrid Pro Stick are supported in Linux with the driver Em2880"

The link is [www.linuxtv.org](www.linuxtv.org)

This afternoon i will try this driver, and search in this site :P

Best regards! AND GOOOD LUCK!!!!!!!!! :)

More information here:
[http://mcentral.de/wiki/index.php/Em2880](http://mcentral.de/wiki/index.php/Em2880)

---

### Post by my_key on 2007-05-19
I don't know if some of you got it to work or not. 
I found a guide on:
[http://www.marcushellberg.com/pages/projects/digital-tv-in-linux.php](http://www.marcushellberg.com/pages/projects/digital-tv-in-linux.php)

I haven't tried the guide as I don't own such a device, but i hope it helps...

---

### Post by my_key on 2007-05-19
Oops. I made a double post. Sorry 'bout that.

Well guess i'll use this space to give you another guide of a ubuntu edgy installation of the device you asked about: [http://xrob.wordpress.com/2006/12/29/pinnacle-pctv-hybrid-pro-ubuntu-edgy-610-installation/](http://xrob.wordpress.com/2006/12/29/pinnacle-pctv-hybrid-pro-ubuntu-edgy-610-installation/)

Hope you get it to work.

peace,
Michael

---

### Post by Nikkus on 2007-05-21
I will try it this afternoon!!!!


THANXSSSSS!! :D:D:D:D

---

### Post by Nikkus on 2007-05-22
Heyyyy!!!!

it's work!!! :D
it work very fine!

[http://www.marcushellberg.com/pages/projects/digital-tv-in-linux.php](http://www.marcushellberg.com/pages/projects/digital-tv-in-linux.php)

---

### Post by usergentoo on 2007-05-22
I have mine working but without any sound.

---

### Post by jpmswiss on 2007-06-10
Great picture...but no sound. 

I also have searched and searched but still no solution.

Looks like I'll have to buy a new card! 

Any recommendations for a slightly old PC?

---

### Post by vincentb on 2007-07-16
Hi,

I use this 'old' tv tuner card in my PC:

05:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: LeadTek Research Inc. WinFast TV 2000
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at c5000000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>

And it works well. I use it with TV TIME to watch television. I have never tried to use it with MythTV ... thus be careful as I know that MythTV is sometimes tricky to install and configure. Thus maybe worth having a look on ebay for this.

My only problem: it does not work with Vista... but who really cares ...

Good luck,

Vincent

---

