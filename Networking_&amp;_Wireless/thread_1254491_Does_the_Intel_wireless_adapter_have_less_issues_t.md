---
title: "Does the Intel wireless adapter have less issues than the Atheros on a Thinkpad?"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by pbateman on 2009-08-31
Hey guys,
I have a Thinkpad z60t with the Atheros wireless adapter. Now after lots of trial and error I've gotten it to work by using the madwifi drivers. Whereas before without the madwifi drivers I would lose connection every 5-10 minutes now my conneciton is solid (once it finally connects) and will not drop.
However one issue still persists. The adapter will not automatically connect at bootup I have to manually connect it (yes I have checked the 'connect automatically'box), and when I do it takes about 10 minutes of trial and error before it finally connects. Once I pick the connection from the list it will just sit there trying to connect, eventually I may get the password prompt(even though I configured the password already in the connection options), I'll delete the endless characters in the password field and enter my password again, but still hangs there trying to connect. This will go for about 10 minutes at least, sometimes i have to delete and recreate the network connection, among other things before it finally connects.
The 'good' thing is once it finally connects it stays connected for good...until I turn off the laptop, then its back to the whole ordeal.
I know the Thinkpad came with an option of an intel wireless adapter, and I am thinking if I was to get a hold of one of those and replace my Atheros adapter, would I be better off or would I still have the same issues?.
By the way, my connection is a 'hidden' connection, I thought it might just be an issue because its hidden, so I tried to connect to a connection that does broadcast the SSID but the same thing happened...just hangs there trying to connect...so i guess its not a matter of connection type. If i boot up into windowz with the same laptop, the card connects right away so its not a card issue as far as it being bad.
I guess to sum it up, I'm trying  to see those of you who have Thinkpads with the Intel adapter as opposed to the Atheros and see how has it worked for you?
Thanks!!

---

### Post by privatejarhead on 2009-08-31
well, i have a toshiba with an intel wireless adapter and after some of the hassles that you face, i got it to work for good after a few tries. i dont recall really having to do any heavy configuring, but after a few tries, my laptop recognizes my network. since i have an open network (with a password of course), im not sure what the intel wireless will do with that.

---

### Post by nostriluu on 2009-09-15
I had a Thinkpad X60 with Atheros wireless chipset. For some reason, in some locations it would not connect to the local access point, even when other devices had no problem. Very frustrating. 

I recently upgraded to a T400S, with Intel 5300 wireless. It has the exact same problem! When I boot into Windows XP, it can connect no problem.

I note there is a firmware workaround for Intel 5100 issues. Does anyone know if there's a fix for the 5300?

---

### Post by shel-hall on 2009-09-15
I can't guarantee anything, of course, but I replaced the Atheros-based mini-PCI WiFi card in my Toshiba R100, and the Intel replacement works *much* better, both with Ubuntu and with Windows XP.

Several folks whose opinions I respect think Atheros WiFi stuff is pretty bad; the replacement in the R100 is my sole experience with them, as far as I can recall.

Both the Toshiba R100 and the Thinkpads are picky about which internal cards they will accept; check the lists at ThinkWiki.org before buying something.

-Shel

---

### Post by jml on 2009-09-15
I agree with shell-hall's warning.  The Thinkpad line of laptops (and presumably others) are hard coded to only work with a wireless card that is on the manufacturer's "white list" of approved cards.  Trying to use any other card will not work.  I came up against this problem when I bought an intel card for my Thinkpad R40.  The computer noted the card's presence as an unknown wireless card and simply would not work.  Now theoreticaly you can modify the ThinkPad's BIOS and trick it into accepting a generic card, but you risk turning your laptop into a brick.  Good luck.

Joe

---

### Post by pbateman on 2009-09-16
Thanks for the help guys...i think I'll stick to the Atheros card on this one. I was able to make it work more reliably by broadcasting my SSID, seems it just doesn't like hidden networks. I am however planning on buying a t400s in the near future, so nostriluu's post kind of worries me. I know they offer the 5300, the 5100 and i believe an Atheros card with it.

---

