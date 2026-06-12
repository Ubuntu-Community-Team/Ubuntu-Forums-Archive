---
title: "cricket pantek 185 cell modem"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by cudayne on 2010-05-10
hello i am trying too setup this thing too work an just havnt been able too do it. I followed the thread about the 600 serieries of modems but the flip/flop thing is only for a 600 cricket modem an when i go too follow the rest of the post it says no file exists. Is there another post on this brand of cell modem i am missing.

ATM i am using a duel boot of xp an ubuntu 10.04 wich was a complete fresh install. 

I am pretty slow with linux stuff but any help would be apperciated.

---

### Post by foresthill on 2010-05-10
Was the modem working in 9.10? Did you try flipping the modem in Windows or a previous Ubuntu version and then rebooting?

If this is a USB modem, you will probably have to find a way to get on the net and install USB_modeswitch from the Synaptics Package Manager.

EDIT: I discovered that, for some reason, you need to run the Update Manager first, before USB_modeswitch will show up in Synaptics.

---

### Post by cudayne on 2010-05-10
No i couldnt get it too run in 9.1 wich is why i did the fresh install of 10.04. hum is there a way too do this without geting 10.04 online first? i cant get online cause i cant get the modem too work in 10.04 :P classic snafu hehe.

---

### Post by foresthill on 2010-05-10
Is the modem not being detected? What's the problem exactly? Will it work in Windows?

I suppose you saw this thread:

[http://ubuntuforums.org/showthread.php?t=1146110](http://ubuntuforums.org/showthread.php?t=1146110)

---

### Post by cudayne on 2010-05-10
ya i saw the post it wont detect the hardware at all. works fine in windows as it is the way i get on the net now.

Step 1:
Download the .deb file for your selected architecture (32bit or 64bit) && install it

is where it fails as the .deb file is for the 600 series of modem

---

### Post by pdc on 2010-05-10
[http://ubuntuforums.org/showthread.php?t=1146110&page=17](http://ubuntuforums.org/showthread.php?t=1146110&page=17)

is post #169 of any help ?

---

### Post by foresthill on 2010-05-10
As far as I know, the only thing the deb file does is "flip" the modem, keeping it from being detected as a storage device (which is what happens when you plug it in initially) and instead causing it to be detected as a modem. There is no driver or anything like that contained in the file, just a set of commands that "flip" the device.

The Cricket software does this same thing when you plug the modem in while running Windows. You'll notice that when you first plug in the device, Windows will detect it as a flash drive. Then (on my A600 at least) the lights flash red, and then green. Then the green blinks several times (usually 8 or 9 times) and eventually it stops blinking, and a signal strength meter appears as a set of blue bars. At this point it has been flipped and will work as a modem.

So my thought is, why not let the device "flip" in Windows, then reboot into Ubuntu. As long as the modem gets an uninterrupted flow of power, it should stay "flipped".

And so once you boot into Ubuntu, the device ought to be detected as a Mobile Broadband device (rather than a storage device) by Network Manager (since it's already flipped) and you should be able to configure it at that point.

This is how I got my A600 working today on a dual boot system of XP and Lucid 10.4. I did not have USB_modeswitch installed, rather I used Windows to flip the modem for me, and then rebooted. I then configured the modem in Network Manager, got on the internet and downloaded USB_modeswitch (using the Synaptics Package Manager) and everything works great now.

YMMV, but good luck.

---

### Post by cudayne on 2010-05-11
ya i tride that today an it isnt seeing the modem.. ill play with it a bit more tomorrow i know its something small.

---

### Post by cudayne on 2010-05-13
the starting in windows an rebooting itoo umbuntu worked. an its like a whole differnt modem its way faster then it ever was in windows.

---

### Post by grandpa2 on 2010-06-13
[http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)
 

 [http://ns2.canonical.com/karmic/all/cricket/download](http://ns2.canonical.com/karmic/all/cricket/download)
 

 Must setup in window a machine first and turn on for at least 15min to  
 get update from CRICKET for new user. Then it works in 10.04
 on a netbook  acer aspire 1. It is very slow but works. 185C USB.
 

 Grandpa2

---

