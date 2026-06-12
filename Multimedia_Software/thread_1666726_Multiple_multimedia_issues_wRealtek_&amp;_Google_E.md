---
title: "Multiple multimedia issues w/Realtek &amp; Google Earth graphics"
date: 2011-01-14
forum: Multimedia Software
---

### Post by UncleClover on 2011-01-14
Hello everyone. :-)

I've been trying to solve these problems for the past 6 months or more, and while I've managed to work up to a minimum acceptable performance quality, things still are kinda' sucky. 

Here are my system stats: 64-bit, 1.1GHz Intel Pentium, Kubuntu (latest), 1.7GB SDDR, ++GB HD space; onboard sound = Realtek ALC658D.

I'll start with the audo issue:

The card seems to be incapable of operating in 2-channel mode. I have to put it into 4 or 6 channel mode and make sure the "<Duplicat>" tag in Alsamixer is not muted. I also cannot mute any of these without losing sound entirely:  PCM, Surround, Center & LFE. The "Surround" option is set to "Shared", the other option is "Independ" but this, too, makes the little happy noises go buh-bye. As it is, I can hear okay, but it's not in stereo. It seems to be re-routing a surround-sound setting or extra speaker into the headphone jack instead of the actual right/left feed. I had tried using a CreativeLabs Soundblaster 5.1 card and had the exact same issue, which could not be fixed.

At one point, I had found a post giving some sort of configuration file-fix that I had copied and pasted into my settings that actually made it work, but this was lost after an idiot-user-induced crash of the entire OS and I have looked and looked and looked for that post again and cannot for the life of me find the bloody thing. :-\

I just want to be able to hear in stereo. I have extra speakers I can plug in for surround sound if/when I'm in the mood, but I make music, and like to do so with headphones in order to be sure I can hear all the subtle nuances I'm trying to produce. I did not have anything even remotely resembling this problem in XP or even in one of the earlier versions of Fedora I'd used once upon a time. But Ubuntu/Kubuntu (have tried both) seems to be incapable of down-mixing. I need all channels downmixed into 2 in such a way that when I slide the volume balance all the way to the left, there is no sound coming from the right and vice versa. As it is, I can tell that different tracks of sound are fluctuating with the volume control, but the card absolutely refuses to treat the extra channels as 2-channeled stereo.

Help?

Okay, that's my biggest issue. The next one isn't so critical, but it's a nuisance just the same: In Google Earth, if I zoom all the way to the ground, these flickering triangle shapes jump in & out of the picture. Depending on my settings in the preference dialog, these triangles will do anything from flickering on-and-off mostly at the edge (with just enough long lines to keep the center of the screen glitchy-looking) or the triangles will grow and grow as I zoom until the entire screen is filled with them and the globe is lost.

This was really bad in Fedora and the prior version of Ubuntu. I'd found out enough to learn that it had to do with 64 vs 32 bit incompatibilities, my understanding of which enabled me to get as far as I have with it. But I just can't seem to make the triangles and flickering lines go away.

If it happens to be relevant, I noticed once when playing with the various display options that when I turned the latitude/longitude lines on, the triangles appeared to be coming directly from them - the lines and the intersections were pretty much the entire source of these mysterious little triangles. The triangles look and behave exactly the same with or without the grid being visible, but there seems to be some sort of connection between them even when the grid is turned off.

Some of the settings I'd played with in my efforts to make it work were:

- Shut off the "show terrain" mode - this completely grayed out the screen;
- Used "show terrain" but with very low res - could see the entire planet at once, but as soon as the planet touched the edges of the screen on zoom, the triangles came in and almost immediately blotted everything out. I've found I can minimize the triangles to a degree by using a high-level of detail on the terrain, and even further by increasing the elevation exaggeration the full way to 3.

None of the other settings seemed to have much of an effect on it.

Okay, there are my issues. Can anyone help? Even just a little bit of help on just one or two aspects of these problems would be very appreciated.

Thanks for your time, and peace to you all. :-)

---

### Post by Zorael on 2011-01-14
I'm searching and googling for hints about the audio issue, but seeing as I don't have such a soundcard the nomenclature is foreign to me.

Is [this guide](http://alsa.opensrc.org/index.php/.asoundrc) the one you seek? On how to set up an **.asoundrc** file to join channels, etc.

If it turns out to be a driver bug, which it doesn't really sound like, then [Realtek](http://www.realtek.com.tw/) has some fresh drivers from late November. Click HD Audio Codecs down in the Quick Links section, accept the terms, then scroll way down for it. I'm really not sure if this solves anything, but it shouldn't make things worse to have newer drivers. Also see [this thread](http://ubuntuforums.org/showthread.php?t=1100552&highlight=alc658) for installation notes.

As for the video thing, are you sure that's not a hardware error? It sounds like what you get when one of the videocard's memory chip is busted. It starts out just as an annoyance, some minor polygon errors here and there, then as the chip gets warm it becomes more prevalent, and after a while the 3D content on the screen is just full of jagged edges. Could you take a screenshot of it?

Further, does it happen in other graphically intensive programs? Do you have any OpenGL screensavers or 3D games with which to stress it some?

---

