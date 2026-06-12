---
title: "Capture levels way too low with Audigy 2 LineIn/Aux.  Am I missing something?"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by KillrBuckeye on 2006-06-17
Guys I keep learning a bit more about how to set up my Ubuntu installation for recording, but I have run into a major problem.  I cannot get adequate levels for my guitar input!  I have my guitar volume maxed out, my preamp volume (Line6 POD) maxed out, Audacity record volume maxed out, and my SB Audigy 2 Platinum capture volumes all maxed out!  As you can see from the attached pic, I cannot get decent levels!  Max is -10 dB or so.  Windows recording works fine for me, so what gives?  There is no option to boost the line level input or auxillary inputs (stereo RCA inputs) in the ALSA mixer, so I have no idea what to do?

I also posted this in the video/sound section, but nobody seems to be responding.  Hopefully some of you audio experts will be able to help me.  Thanks.

PS:  I have tried a different source as well. I used the Line Out on my 100W Marshall head, jacked the amp volume all the way up, and all I got was a clipped signal that's still around -10 dB.  Again, I verified that the capture volume was at 100%. :(

---

### Post by KillrBuckeye on 2006-06-17
Sorry, I just want to add this screenshot from Windows which shows that this hardware is perfectly capable of recording at higher levels.  You can see that I can easily get the signal to clip:

---

### Post by dolson on 2006-06-18
Did you try adjusting the volume levels for your line input or analog mix or whatever is listed on the Playback section?

I'd have to check on my other system, but I thought that I remembered you needed to crank up the Playback volume to record at louder levels. Pretty non-intuitive, yes.

---

### Post by KillrBuckeye on 2006-06-18
My playback volumes are all cranked too.  :(

---

### Post by Snover on 2006-06-30
This seems to be a recurring problem but I couldn't find any mention of it in the bugtracker so I submitted it. [https://launchpad.net/distros/ubuntu/+bug/51423](https://launchpad.net/distros/ubuntu/+bug/51423)

---

### Post by KillrBuckeye on 2006-06-30
I posted this on the Creative forum, and I actually got a response from someone involved with the ALSA project.  This problem had been reported in the ALSA bugtracker over a year ago, was given a high severity rating, but is still open (no action has been taken).  The person responsible for this issue claims that he can't do anything since he doesn't have an Audigy 2 or equipment to test levels... I offered to help but got no response.  Looks like I can forget about ever making a full switch to Linux.

[http://forums.creative.com/creativelabs/board/message?board.id=profaudio&message.id=1627]("http://forums.creative.com/creativelabs/board/message?board.id=profaudio&message.id=1627")

---

### Post by Snover on 2006-06-30
I was actually subscribed to that bug; I tried to find it and link to it on the Ubuntu bug but I was unable to find it because their bugtracker was returning 0 bugs, even when clicking "View Issues". I added a link in the description. Maybe a bounty should be put out for it.

[size=1](Rather amusing how quickly pzad unassigned himself from the bug after your last comment on it, though...)[/size]

---

### Post by dolson on 2006-07-02
Can you plug your output into your Line input? This is what I use and it works fine for me.. In the other forum you posted you were using Aux2. I don't even have an Aux2, as I don't have a breakout box. But my Line works fine for me.

---

### Post by Snover on 2006-07-02
Arg. Ubuntu forum ate my post. Let's try again.

The Audigy2 Platinum Pro is actually surprisingly different from the regular Audigy2. The card itself only has internal headers for analogue CD, digital CD, and power -- it does not have Aux, Phone, or other such headers that are present on the basic Audigy2 card. Additionally, the I/O backplate has only 3 outputs (front, rear, center/LFE/side/digital), an IEEE1394 port, and the connector for the breakout box -- there are NO external inputs on the card itself.

On the breakout box, these are the mappings between the labels on the box itself and what alsamixer reports:

Alsamixer -> Breakout box

Master -> Master volume (I added this to the list specifically because there is a Master volume knob on the breakout box but it does not function in Linux)
Headphone -> nothing (there is a headphone jack on the breakout box; it functions, but the volume slider in alsamixer does not work and there is no option in Linux to mute the speakers when headphones are plugged in, which is an option in the Windows driver)
Line -> nothing (should go to Line In 1/Mic In)
Line2 -> Line In 1/Mic In (should go to Line In 2)
CD -> internal CD connector
Mic -> nothing (should probably not exist on this model)
Phone -> nothing (should probably not exist on this model)
IEC958 Optical -> Optical In (??; I don't have equipment to test this)
PC Speaker -> nothing (should probably not exist on this model)
Aux -> nothing (should probably not exist on this model)
Aux2 -> Line In 3
Audigy CD -> internal CD digital connector (??)
?? -> Line In 2 (does not work right now)
?? -> SPDIF In (may be connected to IEC958 Optical; I don't have equipment to test this)

There are also controls in alsamixer for:

HD Analog Center/LFE
HD Analog Front
HD Analog Rear
HD Analog Unknown (should be Side??)
HD SPDIF Center/LFE
HD SPDIF Front
HD SPDIF Rear
HD SPDIF Unknown (should be Side??)

I assume these are volume controls for the 24/96 chip on the card and for the strange "Digital Out" 1/4" jack on the back of the breakout box, but I don't have a way of confirming this right now. There are also Optical Out and SPDIF Out on the breakout box as well; I have no idea what those are linked to as I don't have any equipment to test with them.

---

### Post by Ma_USMC on 2006-07-08
Wanted to toss two cents in, but as more of an FYI, I noticed through test on my Audigy 2 ZS Platinum that an input (In this case my mic, I assume other inputs could be affected by this) was recording at very low levels simultaneously with sound from the computer.  I tested this by recording my voice with music from Exaile/Rythmbox running in the background and muting and unmuting my mic.  Voice was recorded on the unmute and music was heard throughout at the same volume.

Seemed to me that the reason why volume was so low, was that it was sharing input from the normal output.  Perhaps isolating just one input would increase levels.

---

### Post by LeDechaine on 2008-03-01
Resurrecting an old thread, but it seems like this bug is fixed. :)

Line in 2 is line in 2, line in 1 seems assigned to nothing (and mono, don't know if it's normal), but I can hurt my ears by cranking the volume. ;)

---

