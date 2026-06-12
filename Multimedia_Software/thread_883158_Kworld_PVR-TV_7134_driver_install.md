---
title: "Kworld PVR-TV 7134 driver install"
date: 2008-08-07
forum: Multimedia Software
---

### Post by skoberlink on 2008-08-07
hey guys just got my new tv tuner card installed just in time for school.  It's a cheap little card but will work for me.  I can't get the driver install to work so any suggestions on how to install for this card in particular?  If not any general instructions/suggestions?  

If I can't get it to work I may just finally install windows.  I was probably going to do that eventually for school (the odd program they need me running and my roommate doesn't use linux but he will be using this comp) but it just seems like a waste of hard drive space...

---

### Post by skoberlink on 2008-08-07
bump

This card is also known as the Kworld PlusTV Analog Lite PCI

[http://ubuntuforums.org/showthread.php?t=405327]("http://ubuntuforums.org/showthread.php?t=405327")

That thread mentions this card but I couldn't get that to work but I'm not entirely sure I was doing it right in the first place.  could someone clarify for me?

---

### Post by buntunub on 2008-08-07
Your going to have to do a great deal of google'ing for this one bud. I also got this card and finally (kinda sorta) got it working properly only via mplayer or tvtime using a sox pipe. The card uses the saa7134 chip set and that just is not very well supported in Linux atm. In Mythtv the video only works when the audio doesn't. I finally threw in the towel and sprung for another Hauppauge wintv pvr-150 card to keep my other one company. That card is extremely well supported and works out of the box on Mythbuntu.

---

### Post by skoberlink on 2008-08-07
haha yeah I know I've been googling for several hours now.  Everyone else seems to either be asking the same question about this chipset or giving vague instructions saying this worked for me maybe it'll work for you...

video4linux has the drivers for this but ubuntu can't seem to recognize it for some reason.

most methods seem to say editing the /etc/modprobe.d/options with this line

options saa7134 card=<card number (in my case 63)> tuner=<tuner number (don't know this one for sure...)>

I've tried a few values for tuner based on recommendations and a list of numbers I found on another forum topic.  but the few i tried haven't worked...this is a tough one

---

### Post by buntunub on 2008-08-09
[Here]("http://ubuntuforums.org/showthread.php?t=884438") is my howto

---

### Post by cariboo on 2008-08-09
I've an saa7134 based tv tuner card I've never had to enter the tuner number, just the card number. My card is an MSI tv@nywhere, once I found the proper card number it just worked. I admit I had to brute force the card number and it actually shows up as an Aopen card of some sort, it used to be listed in dmesg, but I don't see it any more (I'm running Intrepid alpha 3 so that might have something to do with it.) The card works fine.

Jim

---

### Post by buntunub on 2008-08-09
> **cariboo907 said:**
> (I'm running Intrepid alpha 3 so that might have something to do with it.) 
Jim

It does indeed. Ive seen some recent noise about the google threads about support for this card being more tightly integrated into the 2.6.26 kernel.

---

