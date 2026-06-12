---
title: "Got the sound working accidentally."
date: 2011-08-18
forum: Multimedia Software
---

### Post by Rakali on 2011-08-18
Hi folks. My 8 year old gigabyte mainboard died a few weeks back, so I finally got myself into gear and bought a boat load of new bits to put in the box, including a GA-H61M board for an i5 intel chip. My preference would have been AMD again, but there's been some chat about that they're not so reliable atm... 

So I put all the bits together. Despite the geek at the local shop looking askance at a woman doing diy after the last one managed to put a pci card in backwards and blow the system up, then blame him for it because he supplied what was obviously a faulty card (!)

Anyways. You know that glorious feeling when the box is all together and you flick the power button for the first time... And it all just runs. Put the Ubuntu cd in the drive... and it all just runs. Well, except for the onboard peripherals. But it loaded a boat load easier than windows ever has. For me, anyway.

The only issue I'm having is that to save $ I bought the smaller board. There's room for graphics and 2 pci cards. But the heatsink on the graphics adpater covers one of the pci slots LOL. This means that I could have either internet connection or sound, but not both, since the onboard lan and sound wouldn't work but a card for either does without any further tweaking. Hmmm.

Tried sudo apt-get install-essential which didn't do much for either. Then grabbed the gigabyte cd that came with the board and went back to trying make their drivers work after installing ndisgtk. Lo and behold, the install exe, which had a weird icon that definitely wasn't wine, worked and announced that it had installed the realtek onboard audio driver.

I've since tried network resetting to try and get the onboard lan going... but it hasn't been successful. So am about to have another go with this oem cd. I realise this isn't technically a solution, since I don't understand what happened... but thought I'd remark on it because a. it's done what ubuntu wanted, which is to be automated for newly ex-windows users who wouldn't know a terminal if it bit them on the backside and b. someone else might find it useful.

Also to say thanks to everyone involved in Debian and the forums coz you're all legends and without this I'd be still paying or cracking to get what I need. Thanks heaps. :p

---

