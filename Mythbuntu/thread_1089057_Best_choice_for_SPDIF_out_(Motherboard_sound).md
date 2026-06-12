---
title: "Best choice for S/PDIF out? (Motherboard sound)"
date: 2009-03-06
forum: Mythbuntu
---

### Post by gungfujoe on 2009-03-06
I've been having nothing but trouble with my Gigabyte GA-EP45-DS3L motherboard.  It occasionally reboots itself upon initial power-up (power issues), it fails to work with an awful lot of RAM (I've tried Corsair, Patriot, and OCZ RAM; ONLY the Patriot has worked, even though the Corsair modules are specifically on Gigabyte's compatibility list), and I can't get audio from MythTV's DVR functionality (live TV and recorded shows).  I strongly recommend AGAINST buying this motherboard, to anyone who is looking for a cheap one.  On the flip side, if anyone wants to buy a gigabyte GA-EP45-DS3L motherboard for a low price, let me know. :)

This motherboard uses the Realtek ALC888 codec for audio.  I assumed that pretty much any standard on-board audio chip would work fine in Ubuntu, but I had to manually upgrade the ALSA drivers beyond the ones available in the repositories in order to get ANY sound at all, and now I get sound everywhere but MythTV's DVR functions (I can watch videos through MythTV, but that uses VLC or MPlayer, and not MythTV's internal video routines).  That kind of makes my HTPC pretty useless.

I've given up on this motherboard, so I'm looking for a new one, but I don't want to get burned yet again by unforeseen hardware compatibility issues.  What on-board audio chips are known to work well with Ubuntu?  With MythTV?  And specifically with S/PDIF passthrough, and not just through the 1/8" stereo analog outputs?

If you want to go further and recommend a specific motherboard, that'd be cool, too, but keep in mind that this is for a pretty low-end Intel (LGA775) based system (current specs are below in my sig).  Buying a high-end $300 motherboard simply doesn't make sense for this system.

---

### Post by theteju on 2009-03-08
I have the same question, Looking for a motherboard with best sound option. I do not want to compromise sound quality at all. Hopefully someone answers soon.

thanks. 

Teju.

---

### Post by NautiusMaximus on 2009-03-08
I have a Gigabyte GA-M78SM-S2H motherboard. I can't promise the onboard sound is the best that there is, but it's certainly pretty good. I have it working with Mythbuntu 8.10 with a co-ax S/PDIF connection. In theory, it should also work with an optical S/PDIF connection, although it doesn't come with one included and you have to buy it as an accessory.

I'm afraid it won't be suitable for gungfujoe, sadly, as it's an AMD rather than an Intel board.

---

### Post by gungfujoe on 2009-03-08
> **NautiusMaximus said:**
> I have a Gigabyte GA-M78SM-S2H motherboard.
Ironically, that has the same ALC888 audio codec that absolutely _refuses_ to work within MythTV's DVR for me, and which didn't work at all until I had hacked in ALSA drivers (1.0.19) that are newer than the ones available in the Ubuntu respositories (1.0.17, I believe).

Did yours work with Mythbuntu "out of the box," without [manually upgrading the ALSA drivers]("http://ubuntuforums.org/showthread.php?t=1046137")?

---

### Post by NautiusMaximus on 2009-03-08
> **gungfujoe said:**
> 

Did yours work with Mythbuntu "out of the box," without [manually upgrading the ALSA drivers]("http://ubuntuforums.org/showthread.php?t=1046137")?

No, it didn't work "out of the box". I had to manually upgrade the Alsa drivers. But that was a fairly painless process once I'd established that it needed doing.

It's probably also worth mentioning that I was hoping to be able to choose whether the sound came through S/PDIF to my surround sound speakers or through HDMI straight to my TV. I still haven't figured out how to get it working with HDMI, although that's a low priority at the moment since using the S/PDIF all the time is a pretty painless workaround.

FWIW, I'm not sure ANYTHING has worked "out of the box". My Mythbuntu experience so far has been a whole series of deciding what feature I'd like to use, fiddling around with the machine for a while, getting some help from this forum, and then fiddling around some more. But I'm getting there, slowly but surely.

---

### Post by dad311 on 2009-03-08
I have the Gigabyte MA78G-DS3HP.  SPDIF works great with no issues and no extra configuration steps needed.  Because this board comes with a ATI graphics cards on-board I added a PCI x16 NVIDIA card.

This board is very stable, and everything works, Ethernet, video, sound, disks, etc.....

---

### Post by Monsieur Gonzalez on 2009-03-08
Sorry, I copied the MB model from my desktop PC. The Mythbuntu box MB is this one, [GA-73PVM-S2H]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2691") here, everything works out of the box on 8.04 and 8.10. Ethernet, onboard video (Nvidia);as for the audio part, ALC889A HD audio , with optical S/PDIF, and it doesn't resample should you choose to keep the original audio quality.

Good basic mb, rock solid.

---

