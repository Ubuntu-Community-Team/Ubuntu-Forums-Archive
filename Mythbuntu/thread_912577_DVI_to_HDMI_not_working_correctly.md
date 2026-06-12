---
title: "DVI to HDMI not working correctly"
date: 2008-09-06
forum: Mythbuntu
---

### Post by ctucker10 on 2008-09-06
I just bought a new 37-inch Toshiba LCD TV. It replaced a 32-inch Westinghouse LCD TV. I connected the old set to the Mythbuntu box using the DVI-out from my Nvidia graphics card to one of the HDMI inputs on the TV. I used the onboard AC97 audio out to the "PC" audio input on the TV. I hooked up the new TV set the same way.

When the old setup booted up everything worked as one would expect. I could see the startup messages as Mythbuntu came to life. When it was done mythfrontend was launched and ready for commands.

When the new setup boots up the display goes nuts--it rhythmically blinks and displays a psychodelic, multicolored pattern--for a little more than a minute, until the gdm window manager starts, then my desktop appears, mythfrontend starts, and everything looks and works as it should.

I tried messing around with my xorg.conf file, but that just made things worse. I reverted back to the original file.

I also tried hooking up a DVI to VGA cable instead of the DVI to HDMI. Fantastic! It worked. I was able to view startup messages. I could leave it like that, but picture quality suffers when using the VGA input instead of the HDMI input on the TV.

The only thing I can think of to explain this is that my video card does not have enough horsepower to drive my new TV's bigger monitor (to the HDMI input).

Does anyone have any idea what's going on with my new setup and how to fix it?

---

### Post by Roebi on 2008-09-08
Hello,

Not all the HDMI inputs are the same on a television. I suggest looking into the manual.
On my Sony LCD TV, I need to use the second HDMI input. The same is true for yjr Samsung of one of my cousins. He wasn't happy with the TV when hooked up to the computer, until I pointed him out to the manual. Switching the HDMI port resolved his complaints.

So, maybe worth trying.
Roebi.

---

### Post by ctucker10 on 2008-09-08
You're right Roebi. The HDMI inputs are not the same on my TV. The manual says that I must use HDMI #1 when connecting to a DVI device. That connection carries only the video information to the TV. For the audio connection the manual tells me to use the "PC" audio input on the TV. The HDMI #2 input is connected to HDMI output on an upconverting DVD player (audio and video in the same cable).

That's exactly what I have done. And after Mythbuntu finishes its startup procedure everything works as it should... good video, good audio, correct aspect ratio,,,etc.

I almost forgot, the manual also says that I must turn on the TV before starting the computer. I've done that too.

To be honest this is mostly an annoyance. But as most experienced linux users know, watching the startup messages can sometimes give you the clues you need to correct issues on our machines. At least I know I can see these messages in the logs and if I want to see them as they happen I can hook up my DVI to VGA cable.

One more thing, I bought my HDMI cables from [http://www.cablesforless.com/](http://www.cablesforless.com/). These cables do not have the HDMI logo. Is it possible that these cables are not as good as the overpriced HDMI cables in the retail stores?

---

### Post by SiHa on 2008-09-08
Just a thought - what's the minimum resolution your manual says the TV will support on HDMI? Sounds to me that the 640x480 (or 800x600) that the system defaults to at boot is out of range - probably trying to drive the refresh too high?.
frinstance, my 32in LCD supports about 16 different resolutions at up to 85Hz on the PC input, but only about 10 on the HDMI @ 50/60Hz.

I think I've read in these forums how to get the system to boot with a different video mode, but can't remember where. Sorry.

---

