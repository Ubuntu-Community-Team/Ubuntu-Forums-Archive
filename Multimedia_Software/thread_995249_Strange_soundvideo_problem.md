---
title: "Strange sound/video problem"
date: 2008-11-27
forum: Multimedia Software
---

### Post by ljungkvist on 2008-11-27
Look at the bottom for my question.

Earlier this week my computer started to behave strangely.It's a two years old Compaq Presario V6103EA, which has an onboard "Intel® Graphics Media Accelerator 950", and "3D Sound Blaster Pro compatible sound 16 bit integrated". It's running Intrepid. Since I also run a virtual WinXP machine (through Virtualbox), I'm going to make some comparisons to that.

What happens is:

1) After the computer has been up some time it starts making this strange high-frequency periodic whistling sound. It is sort of like the sound coming from something spinning really fast or a capacitor charging up, but oscillating (~½ sec period). It's always hard to decide from where such a sound comes from, but as I turn the computer upside down, it becomes really clear. When I try to . It seams to be in some way related to the graphics, because when I drag a window around with the mouse, it stops, and starts over when i drop it again. If I restart the X server (ctrl alt backspace) it's back to normal (but only for a while).

2) At the same time as the noise started to appear, I also noticed that music players started to have problems. For some of them (eg Rhythmbox and Quodlibet) the problem is that once a song in the playlist has finished, it won't continue with the next one (at least not until a couple of minutes later), for others (WinAmp under virtualbox) it just won't start playing the song at all.

3) VLC player, which has always worked sweet like a charm, has started to have sound problems. Regardless of what media (video or music) I'm trying to play, it just makes this strutting hacky sound. Sometimes you can hear some resemblance to what it's supposed to be, and sometimes you don't. VLC under the virtual Windows works perfectly however.

4) So I installed MPlayer, which initially worked well. But as soon as problem 1) started, it wouldn't want to advance the picture (the sound however works perfectly). Also this is the case when I try to look at flash movies online (ie youtube).

5) I can't turn on the visual effects in Gnome anymore, (not even the Normal mode). When I try, i get an error popup showing "Desktop effects could not be enabled". This has worked well before.


So basically all of these problem started to appear simultaneously, but of course i can't be sure that they are related. For example problems 3) and 5) happen always, independently of the others. Also I can't really say if it's software or hardware related. It doesn't seem like a program-specific problem, as multiple programs seems to be effected.


I guess this was a lot of information at once. I don't expect anyone to give me a miracle solution to everything, but I'd be very happy to get some advice from someone who has experienced something similar. Some kind of classification of the problem, a place to find information or something to google search for.

---

