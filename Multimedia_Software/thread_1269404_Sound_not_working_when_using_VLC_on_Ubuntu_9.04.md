---
title: "Sound not working when using VLC on Ubuntu 9.04"
date: 2009-09-18
forum: Multimedia Software
---

### Post by rvec on 2009-09-18
I'm having problems getting sound to work when playing AVI's using VLC 0.9.9a.

Playing the same movie with "Movie Player" ... the sound works fine!!

I'm using a Logitech headset/mic & even have my computer speakers.
Can't get either (headset/speakers) to work with VLC but don't have a problem when using "Movie Maker"

I've already tried:
>"type= ALSA audio output" is enabled under [Audio]-[Output].
> "Use S/PDIF when available" is also enabled under [General Audio].

Please help
Newbie

---

### Post by bsmith1051 on 2009-09-18
Ubuntu 9.04 uses 'PulseAudio' (not Alsa) as it's primary sound system.  But I think Alsa is also installed, so it should still work.

If you have 'Use SPDIF' enabled, and your sound card has an SPDIF connector, then that's going to interfere with using regular stereo output.  Try disabling that option.

P.S.  There's also an additional module you can install for VLC -- go into Synaptic and install 'vlc-plugin-pulseaudio'.  I'm not sure it's necessary, though, as my VLC 0.9.9 has always worked on my Ubuntu 9.04.

---

### Post by rvec on 2009-09-19
Thanks for your reply.
Pulseaudio is installed on my system
I've installed the VLC pulseaudio plugin.
My Logitech headphone is USB.
I've disabled [use s/pdif when available]
But don't think it made a difference.
I've got all my volume on LOUD and all I can hear is the sound of my CPU fan!!

Going to Ubuntu-[Sound Preferences] I've currently got [Logitech USB Headset USB Audio (OSS)] set and that works for my USB headset in Movie Player but not VLC.

I've tried all the other option in VLC but nothing works!!! not even [Pulseaudio audio output].

I'm fresh out of ideas....:-(

---

### Post by bsmith1051 on 2009-09-21
ah, I didn't realize you had a USB-based sound 'card'.  That's surely the problem here (I don't think there's a standard for them).  Can you directly select the output device in VLC, not just the sound 'system' ?

---

### Post by rvec on 2009-09-23
Choices in VLC are limited:
Audio Track either Disable or Track1
Audio Device is greyscaled? Don't remember seeing it disabled last time.
Audio Channels: Dobly Sound, Left, Right or Reverse Stereo.

Then under preferences is the standard settings....not as detailed as [Sound Preferences] on the Ubuntu toolbar.

Just wish VLC could use the same setting as under [Sound Preferences]

Guess I'll have to play around when I've got some time.

Thanks 4 ur help

---

