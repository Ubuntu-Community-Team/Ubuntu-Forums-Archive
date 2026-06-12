---
title: "AD198x playback problem"
date: 2011-08-09
forum: Multimedia Software
---

### Post by nmxdaven on 2011-08-09
Hey guys.  First off, i know very little about trouble shooting sound cards so bear with me please!  I have a hp touchsmart 300 running a  AD198x audio device on 11.04. Using VLC, all my media files have a VERY slight sync problem with the audio. Using VLC's sync to track tool its about -0.100 out of sync. I dont have this problem when I open with totem. Any ideas on whats happening?  Thanks!

---

### Post by BicyclerBoy on 2011-08-09
Soundcard h/w is basically AC97 or HDA-intel compatible because they are the PC audio standards.

The difference in the audio sync can be adjusted in the player & it should save in the preferences somewhere.
IME VLC is a bit slack in saving this type of stuff.

The audio sync delay can be effected by using different codecs & video post decode filters.
i.e. de-interlacing yadifx2 needs to buffer frames for post processing so diff delay.

The players that use h/w decode like VDPAU (MythTV XMBC) internally correct the audio sync based on the decoder/post processing filters..

So in your case maybe Totem (gstreamer)  has it sorted..

---

### Post by nmxdaven on 2011-08-09
Thanks for the reply!  Ok I think I understand it a little better now.  My problems would be solved if VNC were to save my sync settings. Im guessing there should be some way to play around with the video settings to trick it into syncing for me? Like finding a de-interlacing setting that would reduce video speed enough to sync it up?

---

### Post by BicyclerBoy on 2011-08-10
No run yadifx2 if your h/w can.
Better still use VA-API if your video h/w can support
Or better still use MythTV XBMC mplayer smplayer with VDPAU if you have nVidia video h/w support.

In VLC
preferences
select "Show Settings All"  (hiding at the bottom)
select audio group
find audio desynchronization compensation
set & save..
obvious isn't it ..

---

### Post by nmxdaven on 2011-08-10
Thanks so much, works just fine now!

---

