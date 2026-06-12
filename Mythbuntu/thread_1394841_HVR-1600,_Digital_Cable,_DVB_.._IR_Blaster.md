---
title: "HVR-1600, Digital Cable, DVB .. IR Blaster?"
date: 2010-01-31
forum: Mythbuntu
---

### Post by tdiaz on 2010-01-31
I have had squat luck with getting FireWire to work other than it changes the channel through about 5 different ones, nothing ever locks on. Probably 5C which means political problems. 

Should I be using the digital box via the coax plugged into the ATSC connection on the HVR-1600? Or should I put it on the "TV" connection? 

With the Input Connection DVBInput (for the ATSC/QAM connection) there is no way to change the channel via external script. 

It seems the only way to use the IR Blaster is with the cable box input on the "TV" input, thus defeating the whole HD thing in the first place. 

The cable box is an SA4240HDC, and I have an HVR-1600 and PVR-150. I had intended on hooking the SA box to the QAM portion, and plain standard cable to the "TV" on the HVR-1500 and the PVR-150, so I could have two analog sources and one digital source, to get the HD/digital channels that are not on the standard analog cable service.

---

### Post by Calmor on 2010-02-02
Hello,

It sounds like we have nearly identical setups - a PVR-150 and an HVR-1600, with a SA cable box (mine's a 4250HDC, but close).  I'm running 8.10 x64 with J.Y. Avenard's repository for VDPAU.

I don't have the latest HVR-1600 drivers installed, so I don't use the QAM options.  I do know that my cable company provides Clear-QAM directly through the pipe, I just haven't played with it enough to get it to work correctly.

I do run the box via firewire, but I must say it's almost like black magic.  I can offer the following:

[LIST]
[*]The SA boxes seem to swap firewire ports for transmission of video data after a box reset.  The channel changing always seems to work, but sometimes it won't tune anything in at all.  If you never have any luck at all on one port, try the other.
[*]If you change channels with the remote (and not firewire), it can break the connection with the PC (and usually does in my experience).
[*]HD has more video timeout/errors than SD - in fact I don't remember getting any errors at all on SD.  I don't know how much this is related to 5C.  I sometimes think so, but I've never seen a message relating to 5C.
[*]Sometimes the connection breaks just because it wants to
[/LIST]

The ONLY thing *I* have found to reliably keep my system running the firewire connection (and recording the right show) is to do the following (ymmv):

[LIST]
[*]Never, ever change channels with the remote or turn off the box - turning off is usually ok but sometimes it will record the wrong show due to not being able to change the channel correctly or in time.
[*]If it won't tune anything at all, try a box reset.  Pulling the power is one way, but the software reset seems to work better.  On mine: hold down the pause key on the remote until the mail icon appears on the display.  Then, hit the page down button, then hit stop three times.  It'll count r-1, r-2, and then stay at r-2 until it shuts off.  Yours may be different.  This takes several minutes, but usually fixes any comms problems.
[*]If the PC reboots for any reason, it may need the previous box reset to bring it back up.
[/LIST]

Good luck!

---

### Post by Calmor on 2010-02-03
By the way, forgot a couple of things:

I doubt that the cable box will output QAM signals.  My understanding is that it only outputs on the Ch. 3 frequency, not digital.

Sometimes when the cable box and PC aren't talking, all kinds of odd things can happen.  Just last night I had a few errors about the backend not running.  Everything appeared normal.  A reboot of the PC didn't help.  What I found was that the firewire had gone south, requiring a box reboot.  It usually doesn't stop the backend, but it can - this wasn't the first time it happened to me.

---

### Post by Maheriano on 2010-02-03
ATSC is over the air, you shouldn't be plugging anything but an antenna into it. Did you install the drivers from Hauppauge's website?

---

### Post by mookie60 on 2010-02-03
I'm using the 1600 for QAM channels (via cable).  Check the wiki page for the 1600,  [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

About 1/3 of the way down the page, there's a Note (pink box) which mentions that a recent kernel update screwed up (my techincal term) a few things.   These problems made it impossible for the QAM tuner to lock on to any channels.   If you've been doing the regular updates, this may well be the problem.  If you follow the Drivers, Firmware, and Reboot sections right below the Note, it should correct the problem.  Being new to linux, I fumbled a bit through this fix, so I've turned off my updates till this problem gets sorted out. 

Also, I didn't see where you mentioned what version of Myth you were running.   I used 9.04 successfully with the 1600, then tried 9.10 which I couldn't get to work (wouldn't scan either the analog or digital channels), so have switched back to 9.04.

---

### Post by Calmor on 2010-02-04
Maheriano,

*Some* of the HVR-1600s do ClearQAM, meaning you can get unencrypted digital content through the cable line.  Not all have this functionality, but many (mine included) do.  You can Google how to check which models include the QAM tuning option.  

mookie60,

Not sure if you were commenting to the OP or myself, but I just haven't played with it too much since I am able (with about 95% reliability) to use the cable box, meaning I can get everything that the QAM would deliver and more.

I've also heard of a new(ish) card, supported out of the box in 9.10 (MythTV 0.22), that takes component inputs, meaning we can just tap the HD right out of the cable box, no firewire hassles, no 5C flag issues, etc.  Sounds like a dream.  But, as with everyone, money's tight, and the box works pretty well as it is...

---

### Post by mookie60 on 2010-02-04
Calmor, 

I probably should have elaborated on the cable box/firewire issue, but I don't have any experience with them; I connect directly from the wall (no set top box, no antenna) to get all my qam stations . . . well, at least I get the channels I'm most concerned with, the tv gets more than the 1600 does.  I'm also one of the "lucky" ones who has the version of the card that supports QAM. 

I just wanted to stress the importance of the driver issue for anything to do with the digital/qam side of the 1600.  

With the economy as it is, I haven't even bothered to look at new cards, despite my desire to smash the digital half of the 1600.  The 1600 was the only new thing I bought (the pc and graphics card bought at a salvage yard) and it was such a disappointment.  . . . . a million thanks to the folk(s) who've done the work to make this thing function.

---

