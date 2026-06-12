---
title: "Completed &quot;Sound Solutions Guide&quot; with 2 sound cards and still no sound. . ."
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by Neophyte on 2006-12-24
Welp, I am a Linux n00b. . .I've had Ubuntu Dapper Drake 6.06 for a few weeks now (I hosed the first install trying to get the Nvidia drivers lol).  I dual boot with Windows XP.  I was a hopeful convert, but this sound issue is enough to turn me off of Linux.  Long story short. . .

-2nd install had perfect working onboard sound (SiS chip set, driver intel0x8)
-A few days later I installed Enemy Territory and to get sound working I found out I needed to login as root and -echo "et.x86" blah blah blah /oss  before each game session.  Sound was perfect ingae and afterwards and I was fine with the extra step to play my game.
-a few days after I viewed a video online of someones truck doing burnouts.  Something happened to the sound.  I went to play some ET afterwards and my sound was horrible and lagged the game.  Going back through the logs I saw under Sound Initialization "System sound is muted" and some sound specs?
-I still had sound throughout, but ingame it was terrible.  I came here and went through the Comprehensive Sound Problem Solutions Guide v0.5e to the point of purging and reloading the drivers from a fresh kernel.  Same problem. . .And steps 1-4 all seemed to say that Ubuntu knows the sound chip set is there. . .
-So, today I go and treat myself to a new sound card.  I have read on the net that some chip sets can be buggy with linux so i figure a $30 card would be worth some sound.  I purchased a Sound Blaster Audigy SE card.  It works perfect in windows, so I know the speakers are hooked up correctly.
-I had problems right from the git go.  Upon installing the card and rebooting, well. . .there was no rebooting.  Nothing.  I had to remove the card, reboot into the BIOS and I changed a setting. . .I don't remember what it is called but I think it forces the board to load everything fresh (forced recognition?) and it worked.  I haven't had any problems with it in Windows and doesn't seem to have any negative effects on either OS.
-I had no sound at all in Ubuntu.  I repeated steps 1-4. . .my card shows up, Ubuntu is seeing it.  Though, It shows 4 identical "ca0106" devices (device-0 thru-3) in step 1.  I recompiled the driver according to the guide.  I received no errors.  I tried to do it again to see if it missed something, and it basically said "I ain't doin' it becuase it's all up to date and besides, I've done it already" ](*,) 
-The command "alsamixer" outputs: "alsamixer: function snd_ctl_open failed for default: No such device"  That command worked fine (I guess) before the driver compilation.  Maybe its still a driver issue?  As far as I can tell I don't have anything muted. . .


I appreciate yalls help with this :mrgreen:   I can't completely sever my ties with Windows, but I do like having a viable alternate, though if this sound problem can be worked out Windows will become the alternate.

Thanks!

---

### Post by Neophyte on 2006-12-24
I have sound!!  A google search of the alsamixer error brought me back here to a rather unrelated thread and presented "alsamixer -c 0" which. . .tada, brought up the mixer panel.  And all it took was turning off SPDIF Out.  It was on for some reason, I have no idea what it does, but I turned it off and I have sound, at least in the desktop. . .

---

### Post by Neophyte on 2006-12-25
Ok. . .I have sound, but its just static on boot up today.  I guess I'm going to try a third hand of "Comprehensive Sound Problem Solutions Guide v0.5e" and more forum searching  ](*,)

---

### Post by budgie9 on 2006-12-25
> **Neophyte said:**
> Ok. . .I have sound, but its just static on boot up today.  I guess I'm going to try a third hand of "Comprehensive Sound Problem Solutions Guide v0.5e" and more forum searching  ](*,)

This could be related but you will have try it for yourself.
In my Alsa mixer, if I put the PCM and Master up too high, I get the same sort of sounds with my SB card. For me it is a bit of a balancing act with these sound controls.Having a Logitech USB webcam installed that has it seems a mic that never wants to be off, it to can play funnies with the sound.

---

