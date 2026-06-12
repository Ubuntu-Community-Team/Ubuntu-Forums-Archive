---
title: "Volume has gotten lower"
date: 2008-11-12
forum: Multimedia Software
---

### Post by comunista on 2008-11-12
When I recently installed Ubuntu Intrepid my volume was fine. 100% was really loud and I usually used it on <40%. Now I have to crank my sound all the way up to the top to listen to music at a reasonable level. Below 40% I can't hear anything. Any advice?

Thanks

---

### Post by gandaran on 2008-11-12
check PCM speaker in volume control

---

### Post by comunista on 2008-11-13
PCM is all the way up by default. Its not that. Thanks though!

---

### Post by fr33k3r on 2008-11-13
Yeah, I got the same problem too...
any solution anyone...?

---

### Post by Euphorion on 2008-11-13
Hallo

I have the same problems. After having updated from Hardy to Intrepid 8.10 I have problems with the sound. They are as follows:

1. Barely audible sound despite full volume.

2. When I try to increase or decrease the volume using the Hard Keys on my laptop (Fujistu XI-2550) this leads to a system hang up.

3. When I try to eject a CD/DVD, the fist click on eject (gnome file viewer Eject arrows) the Drive (Blue Ray internal drive) just spins up. A further click causes the drive to spin down and eject. Hence to eject a disc two clicks on eject are required. 

Grip can no longer eject the disc after ripping and encoding despite aktive option.

The Hard Key eject button on the CD/DVD drive exhibits the same symptomes as above, first press - spin up no eject second press - spin down and eject.

4. When Shutting down Ubuntu, very long wait for ALSA to shut down.

I have Realtek High Definition Sound intalled in my Laptop (especially bought for Multimedia).

When I look in "Sound" I can choose the following for the diverse Output settings in the pull down lists.

HDA Intel Si3054 Modem (ALSA)
HDA Intel ALC883 Digital (ALSA)
HDA Intel ALC 883 Analgo (ALSA)
HDA ATI HDMI ATI (ALSA)
HDA Intel ALC 883 Analog (OSS)
HDA Intel ALC 883 Analog (OSS)
HDA Intel ALC 883 Analog (OSS)
ALSA Advanced Linux Sound Architectur
OSS-Open Sound System
PulseAudio Sound Server

Choosing the OSS Options yield a marginally louder output than the ALSA Options.

In SMPlayer the loudest output is achieved with the "Openal" option. VLC also yields bearly audible sound.

When I talk from loudest I mean barely audible, the only way to enjoy a film or CD is to use very sensitive headphones at full volume.

Sound in Cineralla ist totally corrupt, all I get is distorted bursts of highfrequency tones, hence film editing is currently not possible. Same applies for Open Movie Editor.

Searches in the forums seem to indicate big problems with ALSA in 8.10 I must spend time with further reading and research 

hence does anyone have a work around or knows a method to fix the above problems, would be a big help.

---

### Post by gandaran on 2008-11-13
look. I don't know if this helps, but if you have some sound the fix should be easy, some time ago I had a similar problem and on close examination I found I didn't have anymore the master volume control, somehow it was replaced by the cd volume control, what I did was remove the speaker icon from the panel the went to add to panel and added a new volume control applet, checked all volume settings, un-muted some speaker control and all was back to normal again.

Euphorion
check this  [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

---

### Post by Euphorion on 2008-11-13
Hallo Grandaran

Thank you for your tips, I have read and carried out the link that you quoted, but it has not helped substantially. I am now in a state of trial and error and have managed to get an audio at a reasonable sound level for various key applications.

In System -> Preferences -> Sound I get the best volume when I set almost everything to OSS.

In mplayer and smplayer I have also set the output to OSS and have activated the Software Volume control with an amplification factor of 250. I can now here the film sound tracks.

VLC uses OSS and plays at a decent volume

Rthymbox with full master volume can be heard in a quiet room. Grip when playing CDs cannot be heard at all - is simply dead.

The Grip Eject Problem I managed to solve by activating the "Faulty Eject Workaround" option.

The other thing that I notice in mplayer and smplayer is that when replaying mpeg videos (PAL in DVD format recorded from cable tv and cleaned using Project X) will flicker terribly if played using GL output, here I have to use X11 (slow). VLC is okay. Mplayer has problems detecting 16:9 with X11 (slow) SMPlayer and VLC are OK. I have an ATI Radeon 2700 with proprietry driver.

Ergo Intrepid has teething problems, but I will continue to research and read Forums. Hopefully some update will fix these problems especially the very sticks ALSA shutdown problem which gets on ones nerves.

Thanks again

---

### Post by Euphorion on 2008-11-13
Hallo

One Idea that I have, I have a creative USB Sound card, has anyone any experience with such USB Sound Cards on Intrepid and is there a chance that it will cure the sound problems that many of us are currently experiencing?

Further I have found a thread which recommends the removal of pulse audio

[http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)

This seems to have solved the problems for many people, but the removal of pulse audio seems to be controversial and is not so easy as claimed, the thread is very long! So at the moment I am reluctant to try it.

It would be of help if some Audio Expert from the Developers would provide a guide line and maybe say when the audio problems will be fixed as this is no good publicity for our otherwise magnificent Ubuntu.

Does anyone know if a bug report has been filed / submitted ?

---

### Post by Twilight in Zero on 2008-11-15
I am experiencing a similar problem to yours.

Below 50%, my sound is muted. But at 100%, my sound is as loud as it used to be at that level in Hardy.

I searched the forums and opened a load of tabs in Firefox. I started a thread a while back, but it didn't show up in my search.

---

