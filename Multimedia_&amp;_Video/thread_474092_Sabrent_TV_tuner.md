---
title: "Sabrent TV tuner"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by chris8sirhc on 2007-06-14
hello, in the past I have always gotten great help from these forums, so I figured this would be a good place to post my question.  I have just installed a Sabrent TV tuner Video capture card into an open PCI slot in my computer.  What do I need to do as far as drivers and such go to get it to run?  I opened up Hardware manager, and the card is showing up just fine, but I cant figure out if i need some drivers or if i just need to find some software that knows how to use this card.  Thanks for your time, Chris.

here is a link to the product:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1951869&CatId=1427](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1951869&CatId=1427)

---

### Post by jasmuz on 2007-06-14
First of all..
Check what chipset your card has.. if its SAA7130 or SAA7134 from Phillips, then you dont need any drivers, its already built in to the kernel.

I do recommend using the Tvtime application for testing and using the card.

---

### Post by Weidbrewer on 2008-04-15
I was just looking at this card on Newegg as a secondary Tuner....did you ever get it working on your system?

---

### Post by wolfen69 on 2008-04-15
from a review on newegg.com:

"Cons: Included batteries were dead, IR remote tray app has a *HUGE* memory leak and does not uninstall with the software, timeshift has no way of FF or RW, only pause/resume. Video window can not be resized, only one size plus fullscreen. The card has **no EEPROM for linux operation**, and the chips seem to be changed constantly making linux operation extremely hit or miss (the saa714x didn't even list the tuner and DA converter chip on my card). Pressing remote buttons can cause a random effect if the remote is not pointed directly at reciever wart including powering off when trying to change channel. There is wiring in the PCB for using a CD audio cable to forward sound to the sound card inside the PC but it has no plug soldered to the solder pads, what a waste for a penny of savings. The configuration is counterintuitive and very sloppy."

everything i found on google indicated that this card will not work.

perhaps [http://www.linuxtv.org/](http://www.linuxtv.org/) can give you some answers.

---

### Post by Weidbrewer on 2008-04-15
My internet foraging turned up mainly the same.   Figured I'd ask on the off-chance that the submitter got it to work.



I should really just hike up my wallet and buy another pcHD 5500...

---

### Post by vbman11 on 2008-04-27
I have the exact same card! I had it working perfictly in 32bit hardy but when I install 64bit over it I forgot to backup /etc/modprobe.d/saa71304:cry:. I think I had it working as a Kworld(saa7134)? I know it is a saa7130 for a fact though. and when I had it working it didn't show all the lower channels!  I know there is a way to get it working, but I can't remember how. you can see [here]("http://ubuntuforums.org/showthread.php?t=769435") how I have it now.

---

