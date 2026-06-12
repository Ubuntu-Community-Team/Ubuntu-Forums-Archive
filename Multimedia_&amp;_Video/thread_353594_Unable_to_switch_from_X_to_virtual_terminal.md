---
title: "Unable to switch from X to virtual terminal"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by didu on 2007-02-04
Hi guys,

I've just installed edgey a few weeks ago and I just cannot switch from X to the virtual terminals using ctrl-alt-f123456. I've done a search in this forum and nothing seems to match my problem.

Here is the problem. When I press ctrl-alt-f1 in X, X disappears (which is normal) and gets replaced by a totally garbled screen! It's as if the framebuffer is filled with total garbage. I cannot see the login prompt at all. I think I might still be able to login, but it's hard to tell.

The interesting thing is that this problem has existed even before I installed the ATI driver for my computer, I thought installing the driver would make it go away, but it hasn't.

Here is the info of my computer:

Dell optiplex 745:

Ubuntu 6.10 edgey.

ATI X1300 graphics card, with driver version 8.33, 3D acceleration is working.

I do have the right contents for /etc/inittab.

Any help would be greatly appreciated.

Thanks a lot.

-D

---

### Post by amohanty on 2007-02-04
can you do the following:

telinit 1


You may have to sudo it.
AM

---

### Post by p!=f on 2007-02-04
Try to boot without "vga="kernel option to see if it helps.

---

### Post by didu on 2007-02-04
> **amohanty said:**
> can you do the following:

telinit 1


You may have to sudo it.
AM

Thanks, but that didn't work at all.

---

### Post by didu on 2007-02-04
> **p!=f said:**
> Try to boot without "vga="kernel option to see if it helps.

You mean in menu.lst of /boot/grub? My menu.lst has never had that option. Thanks a lot for the help though!

It seems that I can actually use the virtual terminal but the screen is just messed up. I managed to log in even though I couldn't seen anything and restarted gdm ... and the virtual terminal is still messed up. How weird ...

---

### Post by amohanty on 2007-02-05
Try dropping into the recover console and once you get the prompt, type Ctrl-D
That will quit you out of console and start GDM. 

Does that work.

AM

---

### Post by didu on 2007-02-05
> **amohanty said:**
> Try dropping into the recover console and once you get the prompt, type Ctrl-D
That will quit you out of console and start GDM. 

Does that work.

AM

Yeah that works but it still doesn't solve the problem that the virtual terminals don't work very well after X starts ... thanks for the help though.

---

### Post by amohanty on 2007-02-05
WHen you drop back to a virt console and things go wrong, can you look at the contents of /var/log/Xorg.0.log and see if you can find anything wrong.

AM

---

### Post by didu on 2007-02-05
> **amohanty said:**
> WHen you drop back to a virt console and things go wrong, can you look at the contents of /var/log/Xorg.0.log and see if you can find anything wrong.

AM

I just had a look at it, and there doesn't seem to be anything unusual. Here is all the warnings:

```

(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used

```

There is no errors.

Thanks a lot.

-D

---

### Post by didu on 2007-02-05
any ideas people? :(

---

### Post by amohanty on 2007-02-06
I see that there are some fglrx warnings. Try 
sudo dpkg-reconfigure xserver-xorg

use the ati (not fglrx) drivers and check if this happens
use the vesa drivers and check if this happens

I know you mentioned that it happened before you installed ati drivers, but I would suggest looking at the logs after each attempt and see if you can spot something funny.

BTW why do you have to do a ctrl-atl-f1?? just wondering...

AM

---

### Post by didu on 2007-02-06
> **amohanty said:**
> I see that there are some fglrx warnings. Try 
sudo dpkg-reconfigure xserver-xorg

use the ati (not fglrx) drivers and check if this happens
use the vesa drivers and check if this happens

I know you mentioned that it happened before you installed ati drivers, but I would suggest looking at the logs after each attempt and see if you can spot something funny.

There doesn't seem to be any difference at all. This problem has existed since the beginning, even when vesa was the driver. The xorg log is rather useless, as it doesn't say anything.

> **amohanty said:**
> 
BTW why do you have to do a ctrl-atl-f1?? just wondering...


How else do you switch to the virtual terminal? I'm not talking about a terminal inside X here, when I say virtual terminal, I mean outside X -- it's where you go to turn X off.

Thanks for the advice.

-D

---

### Post by amohanty on 2007-02-06
But if all you want to do is to kill gdm you can:

Ctrl+Alt+Backspace

from any terminal:

killall gdm

I am sorry, I dont mean to be a pest, but I still dont understand why you want to switch to the virtual terminal.

Is there something you can do only there and not within X??
AM

---

### Post by kvonb on 2007-02-06
Not much help, but try booting from the Ubuntu CD, and try it from there, this will eliminate any possible software problems.

If you can manage to download another Linux CD, say Damn Small Linux (it is ony 50 megs I think), burn that and boot it, then try the <CTRL><ALT><Fn> to see if it works.

I'm wondering if you are having a hardware problem, you could also look in your BIOS and make sure that the AGP settings are correct, maybe try AGP2x, then 4x, then 8x, also make sure that the frame buffer is set to 128 megs.


I'm just clutching at straws, but if you go step by step, hopefully we can sort it :).

Regards, KEv :)

---

### Post by kvonb on 2007-02-06
> **amohanty said:**
> But if all you want to do is to kill gdm you can:

Ctrl+Alt+Backspace

from any terminal:

killall gdm

I am sorry, I dont mean to be a pest, but I still dont understand why you want to switch to the virtual terminal.

Is there something you can do only there and not within X??
AM


hahaha, that's like going to the doctor with a pain "when I do this", and being told "don't do that then"!

---

### Post by didu on 2007-02-06
> **amohanty said:**
> But if all you want to do is to kill gdm you can:

Ctrl+Alt+Backspace

from any terminal:

killall gdm

I am sorry, I dont mean to be a pest, but I still dont understand why you want to switch to the virtual terminal.

Is there something you can do only there and not within X??
AM

No, I don't want to kill gdm or X. The virtual terminals are there for a reason -- to let you access your computer without using X. Without the virtual terminals, I need a second machine in order to access my computer and this is very inconvenient. Running X also takes up CPU and RAM, so if I ever need the maximum amount of CPU and RAM that my machine can give me, I will turn off X and run the process from a virtual terminal.

killall gdm is not the way to go -- if I do so, I will lose access to my machine. You should never ever killall gdm, the proper way to turn off gdm is "invoke.rc gdm stop".

-D

---

### Post by didu on 2007-02-06
> **kvonb said:**
> Not much help, but try booting from the Ubuntu CD, and try it from there, this will eliminate any possible software problems.

That's a good idea. I will try it in a minute.

> **kvonb said:**
> 
If you can manage to download another Linux CD, say Damn Small Linux (it is ony 50 megs I think), burn that and boot it, then try the <CTRL><ALT><Fn> to see if it works.

My office mates have the exact same machine as mine and they've got susi installed and their virtual terminals work fine. So I doubt it's the machine's problem -- unless I'm rather unlucky. But they are running a slightly more advanced kernel.

> **kvonb said:**
> 
I'm wondering if you are having a hardware problem, you could also look in your BIOS and make sure that the AGP settings are correct, maybe try AGP2x, then 4x, then 8x, also make sure that the frame buffer is set to 128 megs.

Yeah, that's a good idea, I actually think it's a kernel config thing, the sysad in my uni guessed it was an acpi problem, but he wasn't sure, I might change my boot options to see if that makes a difference.

> **kvonb said:**
> 
I'm just clutching at straws, but if you go step by step, hopefully we can sort it :).


These are very good straws, thanks a lot for suggesting them.

-D

Update: I rebooted my machine with the Edgey installation CD, and the same problem persists. I also included the "pci=noacpi" in my boot options and it caused the machine to hang during starting-up. So I've got no idea now. The only thing left is to copy down my office mate's BIOS settings and grub settings. I doubt the BIOS thing would work -- I had a look at the BIOS and the only video option is about whether to automatically determine whether to use the onboard video card or the separate video card. But I will try. 

It's also a bit funny that when I log in in single user (recovery) mode, the fonts/resolution of the screen actually changes when it comes to the point that I have to put in the root password. I've never seen this before. Do you think it could be a font problem? The initial booting up font/resolution is what I'd expect from the virtual terminal.

---

### Post by kvonb on 2007-02-06
another couple of straws:

Can your video card do bios updates?  I had an original Riva TNT and that used to have bios updates, if your card does, maybe look into that.

Mainboard bios update?

Try a different video card (just boot from the Edgy CD), maybe borrow your friends that is the same!

I'm coming from a hardware angle because the garbled screen problem that you are having, when booting from different O/Ss makes me think that it's not a software problem, well not from the OS anyway.

I could be totally wrong though!

I have seen the fonts change on boot, but I can't remember where or when.

Actually, now I think a bit more, it was my old ATI 9200se that did that, but the VTs worked perfectly.

A few things to try there, good luck :).

---

### Post by didu on 2007-02-06
> **kvonb said:**
> another couple of straws:

Can your video card do bios updates?  I had an original Riva TNT and that used to have bios updates, if your card does, maybe look into that.

You mean downloading a more up-to-date version of the video card bios and putting it on? I'm not sure, my card is ATI X1300, I haven't seen any bios updates yet.

> **kvonb said:**
> 
Mainboard bios update?

Um ... 

> **kvonb said:**
> 
Try a different video card (just boot from the Edgy CD), maybe borrow your friends that is the same!

Trying a different video card is impossible, this computer belongs to my uni and its case is always locked and the tech service people may chop me into small pieces if I were to suggest changing the video card.

I did try booting from Edgy's live CD and had the exact same problem  ... I will try booting from 6.06's live CD tomorrow. My friends don't have ubuntu, they are die-hard suse idiots ... and as far as I know suse doesn't have live cds ... 

> **kvonb said:**
> 
I'm coming from a hardware angle because the garbled screen problem that you are having, when booting from different O/Ss makes me think that it's not a software problem, well not from the OS anyway.

I've seen the garbled screen before, but only when vesa was the video driver and just before X initialises, I've never seen it with the VT. I think it's either a problem with X or the kernel config. I will try 6.06's live CD tomorrow and I have a feeling that would work. I'd be surprised if it was hardware, I mean, this is a brand new latested model of Dell enterprise PC ...

> **kvonb said:**
> 
I could be totally wrong though!
I have seen the fonts change on boot, but I can't remember where or when.
Actually, now I think a bit more, it was my old ATI 9200se that did that, but the VTs worked perfectly.
A few things to try there, good luck :).


Oh well, thanks for the suggestions. This is more of an annoyance than a must.

---

