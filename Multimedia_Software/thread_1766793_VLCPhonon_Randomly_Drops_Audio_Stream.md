---
title: "VLC/Phonon Randomly Drops Audio Stream"
date: 2011-05-24
forum: Multimedia Software
---

### Post by BrantlyMedders on 2011-05-24
Here's my situation:

I have an Asus EEPC that I use in my classroom whenever I want to show a movie.  I normally keep all of my educational videos as ISOs, and then simply move one over to the netbook when needed.  I normally use VLC for playback.

With the latest upgrade, however, I'm having a few difficulties.

No matter what DVD I choose to show with VLC, the audio stream will randomly drop every 10 minutes or so whenever I am using KDE as my desktop environment.  In order to re-enable the audio stream, I have to either completely stop playback OR reconfigure the audio output in VLC (it does not matter if I change it right back to what it was, I will get audio for another 10 minutes or so).  I've also noticed that if I pause playback, sometimes the audio will not re-enable when unpaused.

Strangely, however, I do not have this behavior at all when I'm using Gnome as the desktop environment.  I get seamless audiovisual playback and never have to fiddle with the audio.

Is this a documented problem in Phonon somewhere?  Anyone have any pointers as to how I might better backtrace what's going on?

---

### Post by Zorael on 2011-05-30
Unless I'm sorely mistaken VLC doesn't use Phonon for sound; Phonon doesn't seem to have been widely adopted so far, its merits notwithstanding.

I think the default setting in VLC's preferences (Audio -> Output) is to use ALSA, and while there is a PulseAudio option I'm not sure if it's a proper plugin or a hack. Have you tried both? I'm inclined to think the Pulse one would work better, but really both should work.

As a small mention and possibly completely unrelated, I always have issues with Pulse and VLC after a new installation until I set Pulse to output in 48kHz instead of the default 44.1kHz. This is on a laptop with Intel sound. At the end of **/etc/pulse/daemon.conf**;
```
; default-sample-format = s16le
**[COLOR="Green"]default-sample-rate = 48000[/COLOR]**
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

```
Note that the hightlighted line is uncommented. Also don't mind it if the fragment lines have different values - that's just me testing stuff out.

Lastly, if it's *really* critical for this to work and all attempts at troubleshooting fail, do consider removing PulseAudio altogether. Most stuff works nicely with Pulse nowadays, but every now and then issues pop up, like with any piece of software.

---

