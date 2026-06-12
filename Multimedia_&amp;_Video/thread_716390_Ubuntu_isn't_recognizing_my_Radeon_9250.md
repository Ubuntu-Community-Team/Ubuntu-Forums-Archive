---
title: "Ubuntu isn't recognizing my Radeon 9250"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by aquinashub on 2008-03-05
Hey All,

I just installed a Radeon 9250 PCI in my Dell Optiplex GX260, which is currently running Ubuntu Gutsy. The boot up gets to the splash screen, but then hangs at about one fifth of the progress meter. I gave the Live CD a shot, and got the same result.

I am guessing that where it hangs may be the point where Ubuntu is trying to load up something video related and doesn't know how to deal with the new card? Possibly xorg.conf? If so, what elements of xorg.conf would I change - and to what do I change them?

In any case, I'm also out to find a driver for that card, but haven't been able to discern which drivers are best. Open source or the proprietary ATI drivers?

Wish there was a "universal thanks" button, I'd click it, and give you all one!

aquinashub

---

### Post by sanddgroper on 2008-03-06
Hi
Have you read the sticky at the top of this thread on installing drivers
for ATI cards.
I know nothing about ATI cards.Nvidia for me

Cheers
Sandy

---

### Post by aquinashub on 2008-03-06
Thanks Sandy, yeah, I've been through a few things

I've been through a couple how-tos: the sticky above to install the driver from both the Ubuntu repositories and the restricted drivers from ATI - there's a combatwombat how-to I went through, and another that I can't remember (on other computer)- all of them seemed to be similar enough, but I wanted to make sure I wasn't missing any steps, so I checked them all out...

As it stands, I have the latest fglrx 4.43.3 driver installed directly from ATI, which all compiled and installed nicely. I ran "sudo aticonfig --initial" which output something similar to:

"Found section in /etc/X11/xorg.conf
Nothing to do... terminating."

So, figuring that fglrx has set itself up in xorg.conf, I reboot, change my BIOS's video to "auto" instead of "onboard," and plug my monitor into the new ATI card. Same thing: my system hangs at about one-fifth loaded at the splash screen. Under any of the circumstances I've given Ubuntu to recognize and use this card, it has always froze up at that point when my monitor is plugged into it and my BIOS is set to auto.

Funny thing is, my restricted drivers manager says zip about fglrx, yet Ubuntu is detecting my ATI card both in "Screens and Graphics" and using "lspci" at the terminal - restricted drivers have been successfully manually installed - xorg.conf is using "fglrx" as the ATI driver - I just can't seem to make Ubuntu use the card!

Have I missed anything maybe?

Much thankyous,

aquinashub

---

### Post by sanddgroper on 2008-03-06
Hi
Ah you have onboard graphics.
Have a look at what this guy did its for nvidia but maybe you
have the same problem with ATI.
[http://ubuntuforums.org/showthread.php?t=713452&page=3](http://ubuntuforums.org/showthread.php?t=713452&page=3)

Cheers
Sandy

---

### Post by CaptainPedro on 2008-03-16
I had the same problem with my computer. I have an HP, and the graphics card is a Radeon 9250 PCI.

I was able to get some other distro's to boot (I tried Fedora, Mandriva, and Mepis) by putting "pci=nosort" and "agp=off" (without quotes) in to the boot options. It wouldnt work with 7.10, but it seems to work fine in 8.04 alpha 6. 

The only thing I havent figured out (in 8.04) is what driver to use, or how to use it. Everything seems to be going way slower than it did with the onboard graphics. Im going to keep working on it though... :)

---

### Post by Furiattl on 2008-03-18
Do not install the fglrx- I had to reinstall ubuntu after I've done it.
The best drivers for Radeon 9250 is the open source ati driver.

As for the on board gfx- I would disable it in BIOS and double check the if the Radeon is set correctly PCI or AGP (*4, *8) 

To have the visual effects running fine I had to install emerald (in synaptic)
I'm quite happy with what I've got now except for the tv-out still not working :confused:

---

### Post by aquinashub on 2008-03-19
Hey Everybody yet again!

I left the situation for a little while, I had some work to do that required a stable system, so I took the card out for that time. But now I'm back!

Thanks everybody for your replies, too!

I've decided that the open source drivers are the way to go, although I haven't been able to get it working (yet) under Gutsy. I just installed Hardy Alpha 6, so I'll throw the card in there and let everybody know how that goes -- ahem -- as soon as I figure out why I'm no longer able to boot up into Gutsy!

Yeah, Furiattl, you're definitely right - don't install the fglrx drivers. [This version of fglrx]("http://ati.amd.com/support/drivers/linux/previous/linux-rf-8-29-6.html") was released in September of 2006, as the last of ATI's proprietary drivers that would support Radeon cards with R200 chipsets (8500 through 9250). Isss old, and the open source drivers are always new!

Open source, here we go!

---

