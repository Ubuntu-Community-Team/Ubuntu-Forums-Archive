---
title: "How good are the ATI drivers these days?"
date: 2009-09-07
forum: Multimedia Software
---

### Post by ticket on 2009-09-07
nVidia cards use VDPAU drivers to playback HD videos.
ATI has Avivo to do the same (I think).

Are the latest ATI Linux drivers able to: 

- accelerate (Avivo?) playback of HD video? and
- provide 3D accelerated OpenGL?  and
- allow compiz to run smoothly?

Reason for asking is that my old 1.5GHz PC has a spare AGP and a PCI (not express) slot.

I can easily get the above features by plugging in an nVidia 8400GS.  But ATI do an AGP version of their Radeon HD3850.  The larger AGP bandwidth, plus the better Radeon hardware should, I think, out-perform the nVidia PCI 8400GS solution.   But only if the ATI Linux drivers can deliver accelerated 2D and 3D. 

Do I go nVidia 8400GS PCI or Radeon HD3850 AGP?

---

### Post by Dipper on 2009-09-07
If using ATI, this is your best bet: [http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/)

I would skip Jaunty just like Windows users skip Vista.  Hopefully, Karmic will deliver updated 3D capability to ATI users.  I have heard nothing from those working on it and an update would definitely be appreciated.

---

### Post by ticket on 2009-09-07
Thanks Dipper.  But ... arrgh, I just upgraded to 9.04!
I read somewhere there is a new ATI driver supporting 9.04.  I wonder how it went ...

I'd like to get the HD 3850 - but it must support playback of HD video.

Watchable full screen screen flash would be a bonus!

---

### Post by patasenko on 2009-09-07
From my own experience i would say that with Ati Jaunty is slower than Karmic.

---

### Post by GiantSpider on 2009-09-08
Hey I have ubuntu 9.04 and an ATI HD 4890 and I'm not sure which drivers to use. I have some older cards but it would be a pain to uninstall and install an older graphics card because the driver isn't supported.

edit:originally had 4980 hahaha I always mix up numbers and letters.

---

### Post by markbuntu on 2009-09-08
ATI has had avivo code in their linux driver for quite a while now but they have not released any specs so the mplayer and totem and vlc etc folks can include it so, not yet for hardware accelerated hd playback. Maybe in a few months.....

If you are going to use the HD3850 agp be sure to use the latest driver from ati since the one in the repos (Catalyst 9.4) does not support the agp version. Catalyst 9.4 does not support many of the newer 4xxx series cards but Catalyst 9.8 does.

So, your best option is to skip the driver offered when you install Jaunty and download the latest from the ati site and install that instead. If you have already enabled the driver then you need to remove it before installing a newer one.

If you are upgrading you asolutely must remove any Catalyst/fglrx driver before doing so. And do not use ENVY to install ati drivers.

You should have no problem with full screen flash. I have a hd3650 and it works fine for me and has for a long time.

---

### Post by Yellow Pasque on 2009-09-08
ATI's answer to VDPAU is called XvBA, but it's still vaporware and has been for over a year: [http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA](http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA).

'Out-of-the-box" 3D support for R600/R700 chips in the open-source ATI drivers should come in Ubuntu 10.04: [http://www.phoronix.com/scan.php?page=news_item&px=NzUxNg](http://www.phoronix.com/scan.php?page=news_item&px=NzUxNg)

One can technically install open-source 3D support for recent ATI cards in Ubuntu Jaunty, but the procedure isn't really n00b-friendly: [http://ubuntuforums.org/showthread.php?t=1257453](http://ubuntuforums.org/showthread.php?t=1257453)

---

### Post by ticket on 2009-09-08
> **markbuntu said:**
> ATI has had avivo code in their linux driver for quite a while now but they have not released any specs so the mplayer and totem and vlc etc folks can include it so, not yet for hardware accelerated hd playback. Maybe in a few months.....
....
You should have no problem with full screen flash. I have a hd3650 and it works fine for me and has for a long time.

Thanks Markbuntu. Sadly, I was hoping to get HD playback with the HD3850 - seems not possible? 

The release notes for the Linux Catalyst 98 driver says (under 'known issues' section) :

[I]Error message may appear while playing H264/VC1/mpeg2 media files with
Hardware Acceleration[/I]

This to me implies the ATI driver supports h/w accelerated decoding. I read somewhere else that it may be implemented as a pixel shader when using the normal XV driver. This would imply mplayer etc would not need access to the driver internals / API. This is all so confusing. Can anyone confirm accelerated decode with the 98 driver?  

Your advice on the install is noted.  If I do get the HD3850 card, it will be installed very carefully!  But no point if it leaves my P4 1.5GHz rig with no HD video playback (while the nVidia card can guarantee at least that).

Intrigued to see you think full screen flash will be ok. What CPU do you have?  My rig currently can not deal with that at the moment (it is using an nVidia 6200 PCI). I wonder if installing a nVidia 8400GS would solve the flash full screen issue (i.e. very jerky playback).

Would be great to hear from other ATI users.


EDIT: From [http://www.phoronix.com/forums/showthread.php?t=18578](http://www.phoronix.com/forums/showthread.php?t=18578)
>  gsacks:   	
Ho-hum. No XvBA support. So glad I switched to Nvidia for my HTPC. My 780g board is now relegated to the living room web browser 'net top'. Glad to see AMD making progress, but the lack of accelerated video support on par with VDPAU is really just sad at this point. Just sad. I'll say it again. Sad. 

---

### Post by Yellow Pasque on 2009-09-08
> If I do get the HD3850 card, it will be installed very carefully! But no point if it leaves my P4 1.5GHz rig with no HD video playback
If you must have HD video accelerated decoding in Linux, then there's no point in getting a RadeonHD.

---

### Post by ticket on 2009-09-09
> **Temüjin said:**
> If you must have HD video accelerated decoding in Linux, then there's no point in getting a RadeonHD.

An nVidia 8400GS it is then. Shame to waste the AGP port, though.  Another sale lost by ATI.

---

### Post by markbuntu on 2009-09-09
> **ticket said:**
> ...

Intrigued to see you think full screen flash will be ok. What CPU do you have?  My rig currently can not deal with that at the moment (it is using an nVidia 6200 PCI). I wonder if installing a nVidia 8400GS would solve the flash full screen issue (i.e. very jerky playback).

Would be great to hear from other ATI users.


EDIT: From [http://www.phoronix.com/forums/showthread.php?t=18578](http://www.phoronix.com/forums/showthread.php?t=18578)

I have a AMD Athlon 6000 X2 cpu w 6GB 800mhz ram and flash full screen uses less than 20% cpu. That tells me that it is being directly rendered by the gpu instead of the cpu and the cpu is handling the download easily.

There are a number of things that can make flash playback less than good that are not gpu dependent. A slow internet connection, a slow cpu, not enough ram. 

If you only have 1GB ram or less, you should get more, it will really help a lot, maybe more than a new gpu and is way cheaper. A P4 1.5 Ghz is pretty marginal but would benefit a lot from more ram.

But Temujin is correct. If you really need HD and cannot wait then you should go with nvidia but you really need a better cpu to get the kind of performance you are seeking.

---

### Post by ticket on 2009-09-13
Well I went & bought and installed a PNY Geforce 8400GS 512MB PCI and a 400W Corsair PSU.

Result : unbootable PC. 

Couldn't even get into the BIOS. And the power switch wouldn't turn off the PC - it just powercycled/rebooted. Had to turn off using the main PSU switch at the rear. This 8400GS card seriously disrupted the system.

I tried installing the 8400GS card in the nearest and farthest PCI slots, and with all other PCI cards removed. Same result.

Removed the 8400Gs, re-installed the 6200 PCI card and, with no changes to the BIOS, the system was back to normal.

The computer is a Dell Precision 340 with 512MB ram and 1.5GHz P4. There is an unused AGP x4 slot. No on-board graphics.

Anyone got any ideas on how to get a 8400GS working on this rig? 
Looks like I may be returning the 8400GS.

Yet I have seen reviews from other users of 7-year old Dell 2400 machines saying the 8400GS worked and performed well. (e.g. here:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4410190&CatId=319](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4410190&CatId=319) -last review item) 

Maybe it's my BIOS?  How do you upgrade the BIOS on a Linux-only machine?
EDIT : Here's how I did it: [http://ubuntuforums.org/showpost.php?p=7974491&postcount=94](http://ubuntuforums.org/showpost.php?p=7974491&postcount=94)

---

### Post by universknight on 2009-09-16
> **markbuntu said:**
> 
I have a hd3650 and it works fine for me and has for a long time.

Hi markbuntu,
i have a very similar config to you and have some problem
Here is my config:
AMD Athlon X2 6000+
6GB of ram 
ATI HD3650 display card
#Using Catalyst/fglrx provided by Jaunty
Using latest driver from ATI

and my problem is when i enable the desktop effect
Resizing the windows is very slow, 

#FIXED
the screen flash when watch video using mplayer output as gl
and make the system full load when output as xv
only output as X11 works.
###

any idea about my problem?
===
some update
i have updated the latest driver from ATI,
the video flash problem is fixed, but still resizing and raising up the window is really really slow

---

### Post by markbuntu on 2009-09-16
I am not using desktop effects at the moment because I am using xinerama to get my three monitors working but I have used effects in the past without problems. In the compiz config settings manager there are some options you can try in the Workarounds section. Mine has the following boxes checked.

Legacy Full Screen Support
Java Window Fix
AIGLX Fragment Parameter Fix
FIx screen updates in XGL with fglrx

Give that a try

---

### Post by ticket on 2009-09-16
I managed to figure out how to flash my BIOS from A01 to the last issued one by Dell for this machine, which is A07  (using a CD method).

I will attempt to plug in the 8400GS card tomorrow to see if that has fixed anything.

---

### Post by ram130 on 2009-09-16
> **ticket said:**
> I managed to figure out how to flash my BIOS from A01 to the last issued one by Dell for this machine, which is A07  (using a CD method).

I will attempt to plug in the 8400GS card tomorrow to see if that has fixed anything.

If not, then boot up in Recovery Mode and choose the option to fix X server.

---

### Post by universknight on 2009-09-17
> **markbuntu said:**
> I am not using desktop effects at the moment because I am using xinerama to get my three monitors working but I have used effects in the past without problems. In the compiz config settings manager there are some options you can try in the Workarounds section. Mine has the following boxes checked.

Legacy Full Screen Support
Java Window Fix
AIGLX Fragment Parameter Fix
FIx screen updates in XGL with fglrx

Give that a try
Thanks for the advice,
but the result comes up nothing~!~

---

### Post by ticket on 2009-09-17
> **ram130 said:**
> If not, then boot up in Recovery Mode and choose the option to fix X server.

The machine gets to the grub boot menu ok, but it then freezes no matter what option is chosen.  I did manage to upgarde the PC BIOS from A01 to A07, but I didn't try the card again because ...  :

Today I had the opportunity to plug the 8400GS card into a different machine - a Dell Dimension XPS Gen4, 3.6GHz P4, running Windows XP SP3.

I loaded the machine with the latest nVidia drivers for Windows XP, and set the BIOS to make the PCI slot the primary adaptor (the default was the existing 6800 PCIE).

On power-up, I saw the 8400GS announce itself in text, then the Dell BIOS splash screen, and then the splash screen for Windows XP appeared. All good, it got a bit further. But after that, the screen went blank and the system froze.

I am sending the 8400GS card back for a replacement - clearly this card is faulty, or it only works with the PNY drivers - which isn't an option for me.

I'll post what happens when the replacement eventually arrives.

This is all hard work, but I'm learning - I now know how to create a DOS boot CD to flash the BIOS.

---

### Post by ram130 on 2009-09-18
Hmm, was about to say its faulty too. I wouldn't think the bios would be at fault either way. But I do hope the new replacement works for you, sounds like a problem I use to have. It fixed it self tho.

> **ticket said:**
> The machine gets to the grub boot menu ok, but it then freezes no matter what option is chosen.  I did manage to upgarde the PC BIOS from A01 to A07, but I didn't try the card again because ...  :

Today I had the opportunity to plug the 8400GS card into a different machine - a Dell Dimension XPS Gen4, 3.6GHz P4, running Windows XP SP3.

I loaded the machine with the latest nVidia drivers for Windows XP, and set the BIOS to make the PCI slot the primary adaptor (the default was the existing 6800 PCIE).

On power-up, I saw the 8400GS announce itself in text, then the Dell BIOS splash screen, and then the splash screen for Windows XP appeared. All good, it got a bit further. But after that, the screen went blank and the system froze.

I am sending the 8400GS card back for a replacement - clearly this card is faulty, or it only works with the PNY drivers - which isn't an option for me.

I'll post what happens when the replacement eventually arrives.

This is all hard work, but I'm learning - I now know how to create a DOS boot CD to flash the BIOS.

---

### Post by ticket on 2009-10-02
The PNY 8400GS card I returned was confirmed to be faulty by the reseller.

The replacement has now arrived.

Unfortunately testing the replacement in the Linux Dell Precision 340 1.5GHz PC (and with the latest A07 BIOS) produces exactly the same problem: - PC fails to boot, and the presence of the card interferes with the PC power management - the front power button power cycles (reboots), instead of powering on/off.

Next week I will try the replacement card in a Dell Dimension XPS
3.6GHz. I will let you know how this goes.

I think it unlikely for me to get two bad cards. Either the reseller
got a bad batch, or the PNY 8400GS card is not compatible with Dell
motherboards or P4 processors.

Do I need to use different BIOS interrupt settings for this card?

The 8400GS card has a pair of exposed pins next to the video DVI
connector, labelled J6. Anyone know what these pins are used for?

---

### Post by ram130 on 2009-10-03
Looks like you better off buying a new or different brand card. The problem seems to be hard to really find.

---

### Post by ticket on 2009-10-07
> **ticket said:**
> 
Next week I will try the replacement card in a Dell Dimension XPS
3.6GHz. I will let you know how this goes.

Surprise, the card worked when plugged into the Dell Dimension XPS, using latest nVidia drivers.

I tried plugging it back into the Dell Precision. I managed to cure the strange power management behaviour by turning off some options in the BIOS (maybe using S1 instead of S3 did it).  But the problem remains - the system gets to the point where grub has is loading the OS and the message "Starting up ..." appears, after which the graphics mode should get enabled, but instead the system freezes in the text mode.  And with the card in, I can't enter the BIOS - pressing F2 in the BIOS splash screen results in a blank screen & frozen computer.  

I managed to salvage an xorg log from when the 8400 card was fitted and when using the failsafe xorg.conf.  It reads exactly the same as the report for when the 6200 was fitted, except it cuts short (files are attached). It looks like it was perhaps trying to set a graphics mode and refresh frequency on the monitor and failing.  Strange that an older 6200 card could manage this Herculean feat, though.

Any clues from the logs?

(Edit: also tried booting from Linux Mint and knoppix live CDs - they all freeze at the ISOLINUX text message).

> **ticket said:**
> The 8400GS card has a pair of exposed pins next to the video DVI connector, labelled J6. Anyone know what these pins are used for?
PNY says they are for spdif (sound!).  Weird.

---

### Post by ylo58 on 2009-10-10
One thing to try is disabling the frame buffer on console. This can be done by specifying ```
vga=normal 
```in the boot options line.

I am in a similar situation, trying to get HD video from a P4 with PCI and AGP slots only.

---

### Post by ticket on 2009-10-10
ylo58, which file should I be editing to insert "vga=normal" in?
Is it menu.lst?  Could you provide a mini example?

Incidentally, will doing this give me a bootable system?  How did it help you?

(Sorry for the raft of questions ...)



PS:
Found this at [http://forums.fedoraforum.org/showthread.php?t=219737](http://forums.fedoraforum.org/showthread.php?t=219737)   (post #9) :
> I found the solution to my problem. Use the kernel parameter

agp=off

My motherboard doesn't even have an AGP slot, which is why I got a PCI video card.
Apparently there was a conflict with the resources the kernel was reserving for an AGP
video card and what the PCI card needed. Once I used agp=off, everything worked
perfectly.

Again, I'm not sure what file to edit.

---

### Post by ylo58 on 2009-10-11
Yes, it is the menu.lst file, the line beginning with *kernel*. The *agp=off* goes to the same line. You can try it without editing too, it is possible to enter kernel options when the grub boot menu appears: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions).
I can not promise that this will help you, it is just another thing to try. I have not decided yet, which card to get for HD. At the moment I use 7600GT.

---

### Post by ticket on 2009-10-11
I tried inserting the following boot options:

vga=normal  (also tried vga=318)
noacpi
agp=off

in various combinations, and also trying with the recovery ones as well, all to no avail.  After hitting 'b' to boot, the system reports it is booting from the selected disk, prints "Starting up ..." and after that, nothing.  No disk activity seen and system is hung.

The most telling fault with this card & machine is that one cannot enter the bios by pressing F2. If you try that, you get a blank screen.

I conclude the problem is an electrical motherboard incompatibility.
I found that the PCI 2.1 and 2.2 specs say:

> The maximum power allowed for any PCI board is 25 watts, and represents the total
power drawn from all power rails provided at the connector (+5V, +3.3V, +Vi/o, +12V, -12V, +3.3Vaux).

But the PNY engineer told me the idle power draw for the  8400GS card is 31 watts!  So it is not even compliant with the PCI electrical standard.

So this card is going back. Dunno how it managed to work with other Motherboards - perhaps their PCI connectors are more beefy?

Returning this card now.  This leaves me with staring at the empty AGP connector on this PC and wondering if ATI will ever provide a linux driver that can accelerate HD decoding ...

---

### Post by ticket on 2009-10-11
For what it is worth, these guys have had similar problems:

[http://forums.nvidia.com/index.php?s...t=#entry564828](http://forums.nvidia.com/index.php?s...t=#entry564828)

[http://forums.nvidia.com/index.php?s...ded&pid=430511](http://forums.nvidia.com/index.php?s...ded&pid=430511)

[http://www.hawkee.com/shop/review/308828/](http://www.hawkee.com/shop/review/308828/)

[http://www.nvnews.net/vbulletin/show...57&postcount=1](http://www.nvnews.net/vbulletin/show...57&postcount=1)

[http://en.community.dell.com/forums/t/19247838.aspx](http://en.community.dell.com/forums/t/19247838.aspx)

[http://www.techsupportforum.com/hard...0-gs-help.html](http://www.techsupportforum.com/hard...0-gs-help.html)

[http://www.computing.net/answers/har...ver/55396.html](http://www.computing.net/answers/har...ver/55396.html)

[http://www.techimo.com/forum/technic...hics-card.html](http://www.techimo.com/forum/technic...hics-card.html)

So back to my original query after this diversion - How good are the ATI linux drivers these days? - in particular, are they any closer to accelerating HD video?

---

### Post by Yellow Pasque on 2009-10-11
> **ticket said:**
> So back to my original query after this diversion - How good are the ATI linux drivers these days? - in particular, are they any closer to accelerating HD video?

No one from ATI has given a definitive answer in relation to the Catalyst driver. They won't even say if they plan to ever release a public implementation of XvBA. 

As far as open-source drivers, they may support VDPAU once a solid Gallium3D implementation of it is in place. I'm thinking it will be a good year (at least).

Bottom line: don't buy an ATI card and expect HD video decoding any time soon.

---

### Post by ticket on 2009-10-11
> **Temüjin said:**
> 
Bottom line: don't buy an ATI card and expect HD video decoding any time soon.

Darn! That was the position 1 month ago (maybe more ...).

Maybe shell out for a HD3850 and wait .... ?

---

### Post by Melcar on 2009-10-11
XvBA is being worked on.  It will be done through VA-API.  Obviously it's still in testing and as such closed to the general public.  Proper HD acceleration for fglrx is coming, but I can't say when.
As for general performance with the drivers, raw 3D performance is on par with the Windows drivers and 2D performance is very good (slightly better under composition even).  WINE compatibility will always be a sore point for the drivers since that program is very nvidia dependent, but things have gotten better.
In terms of open source drivers, work on Gallium3D for r3xx-r5xx chips is "[mostly done]("http://www.phoronix.com/scan.php?page=news_item&px=NzYwMA")".

---

### Post by ticket on 2009-10-11
Thank you Melcar.

What's the best URL to monitor for these sorts of developments?

---

### Post by Melcar on 2009-10-11
It's all under testing, so only those with NDAs have any form of access.

---

### Post by tuxxy on 2009-10-11
In a word....terrible ):P

---

### Post by ticket on 2009-12-12
Some progress at last:

Published on November 03, 2009

> Effectively this makes it possible for ATI customers to use VA-API, which in turn uses XvBA atop hardware with UVD2 support. This current implementation can accelerate only MPEG-4 AVC (H.264) and WMV9 (VC-1) formats at this time, which is more limited than NVIDIA's VDPAU implementation in their proprietary driver.

[http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1)

Maybe I will use that AGP slot one day ...

---

### Post by Yvan300 on 2009-12-12
The open source drivers have gotten significantly better since intrepid ibex. In karmic koala, i can now play my favourite first person shooter, urban terror, right out of the box. They do not provide full 3d support but they are excellent in what they do, seriously. Compiz runs smoothly and there are no graphics bugs etc.

---

### Post by ticket on 2009-12-12
Good to hear that, Yvan!
What card are you using?   Can it play 720p or 1080p videos properly?
Very interested to know!

---

### Post by Yvan300 on 2009-12-12
I'm running an ati raedon xpress 1150. Since ATI has classified it as a legacy card, i was forced to use the open source drivers. In karmic they work reasonably well. Except for shadows etc. But still i can play my games with a reasonable fps.

---

### Post by matt.matolcsi on 2010-02-28
> **ticket said:**
> Well I went & bought and installed a PNY Geforce 8400GS 512MB PCI and a 400W Corsair PSU.

Result : unbootable PC. 

Couldn't even get into the BIOS. And the power switch wouldn't turn off the PC - it just powercycled/rebooted. Had to turn off using the main PSU switch at the rear. This 8400GS card seriously disrupted the system.

I tried installing the 8400GS card in the nearest and farthest PCI slots, and with all other PCI cards removed. Same result.

Removed the 8400Gs, re-installed the 6200 PCI card and, with no changes to the BIOS, the system was back to normal.

The computer is a Dell Precision 340 with 512MB ram and 1.5GHz P4. There is an unused AGP x4 slot. No on-board graphics.

Anyone got any ideas on how to get a 8400GS working on this rig? 
Looks like I may be returning the 8400GS.

Yet I have seen reviews from other users of 7-year old Dell 2400 machines saying the 8400GS worked and performed well. (e.g. here:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4410190&CatId=319](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4410190&CatId=319) -last review item) 

Maybe it's my BIOS?  How do you upgrade the BIOS on a Linux-only machine?
EDIT : Here's how I did it: [http://ubuntuforums.org/showpost.php?p=7974491&postcount=94](http://ubuntuforums.org/showpost.php?p=7974491&postcount=94)

Did you find that the BIOS upgrade worked for you? I'm in the same situation.

---

### Post by ticket on 2010-02-28
> **matt.matolcsi said:**
> Did you find that the BIOS upgrade worked for you? I'm in the same situation.

I successfully upgraded the BIOS, but it didn't help.  I have concluded the The PNY Geforce 8400GS PCI isn't compatible with the Dell motherboard.  I didn't bother trying any other brand of card.

---

