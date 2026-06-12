---
title: "Totem and surround sound"
date: 2009-05-12
forum: Multimedia Software
---

### Post by chrroessner on 2009-05-12
Hi,

I just would like to watch DVDs in 5.1 surround sound on my PC, but I only get stereo.

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

I have installed totem-gstreamer as well as totem-xine. The latter set as default with update-alternatives.

But still not surround.

Even tried xine-ui, mplayer, vlc, ...

So maybe I need some asoundrc or so, but I am not an expert on things like sound under Linux :-)

So is there someone, who can help me with this.

My onboard sound system is connect with 6-channel analog _and_ SPDIF (coaxial) to a Kenwood receiver.

I really, really would thank you getting this working, because I always have to boot into Windows Vista to use PowerDVD. And I would love it, not to switch the system just for watching DVDs.

Thanks alot in advance

Christian

N.B.: Sound settings in totem are curently set to AC3-passtrough, which should do the job ;-) But doesn´t

---

### Post by chrroessner on 2009-05-12
Ok, just found one thing out: It is playing 6 channel sourround over analog.

Unfortunately pulseaudio does not show a HD S/PDIF output device, just the analog one. Is there some way to workaround this?

---

### Post by chrroessner on 2009-05-12
I also have an open bug report @

[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/319281](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/319281)

Maybe this belongs together?

---

### Post by djbushido on 2009-05-12
Also, just to check, make sure that you are using the surround audio channel in the dvd. Most come with a stereo channel as well. Probably not the case, but it's worth a check.

---

### Post by chrroessner on 2009-05-12
I have double checked this, but this is not the reason.

---

### Post by djbushido on 2009-05-12
Sorry, I can't help much beyond that. Check to see if you can bypass Pulse (send straight to Alsa).

---

### Post by chrroessner on 2009-05-14
I have checked aplay -l. Seems pulseaudio does not recognize the digital output?

aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: AD198x Analog [AD198x Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: AD198x Digital [AD198x Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

---

