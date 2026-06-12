---
title: "missing sound in kubuntu"
date: 2011-09-14
forum: Multimedia Software
---

### Post by mobruu on 2011-09-14
Having problems with getting any sound at all on my Asus X71ja (X77ja -eu version)..

Tried changing from Redwood HDMI to the "internal" speaker with no luck.
I've tried the alsamixer "trick" but it doesn't help.
I've checked that I'm not muted..

morten@arcturus:~/Dokumenter$ uname -r
 2.6.38-11-generic-pae

 morten@arcturus:~/Dokumenter$ lspci | grep Audio
 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
 01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]

morten@arcturus:~/Dokumenter$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



Running Kubuntu..


Can anyone please give me some help with getting sound on my laptop?


Thanks in advance..

---

### Post by mobruu on 2011-09-14
Umm..I just found out that my system is playing "notifications" ..

Now, I have no clue at all of what's wrong... o_O

Edit: I've tried Banshee and Amarok. Tried VLC.. No sound at all..

---

### Post by SeijiSensei on 2011-09-15
> **mobruu said:**
> Umm..I just found out that my system is playing "notifications" ..

Now, I have no clue at all of what's wrong... o_O

Edit: I've tried Banshee and Amarok. Tried VLC.. No sound at all..

Go to System Settings > Multimedia > Phonon.  Browse through the audio output options and make sure the device you want to use is at the top of the list in each case.

---

### Post by mobruu on 2011-09-15
The phonon is the only one there..

I had, a couple of days ago both the redwood and another card in that list, but they both disappeared and was replaced by "phonon"..

But, as I said.. The system is playing notificatons. Not playing the startup theme and not playing any mp3's..

---

### Post by SeijiSensei on 2011-09-15
> **mobruu said:**
> The phonon is the only one there.

Phonon isn't a device, it's a system for managing devices.

After choosing Phonon, go down the list of device preferences in the left-hand tree.  Do they all point to the same device, e.g, "Internal Audio Analog Stereo," or do other devices appear?  If you can hear the Notifications, which device do they use?  Do music and video use the same device?

If KMix isn't running in the system tray (you'll see a little speaker icon if it is), open a Konsole and type "kmix &" at the prompt to activate it.  Go to the Mixer and make sure the output isn't muted.  (It shouldn't be if you can hear the Notifications.)

---

### Post by mobruu on 2011-09-22
Hey!

Sorry for the late reply. Been busy.

Notifications are using the same device as music and videos.

I'm actually having the same problem with my Asus eeePC. Hearing the notificatons, but I cannot hear any mp3's.
Downloaded the codecs available (as prompted when you first start up Banshee) but to no avail. 

Checked the kmixer and there is no mute. I have the "speaker" in the systray, and it's not muted :-(

---

