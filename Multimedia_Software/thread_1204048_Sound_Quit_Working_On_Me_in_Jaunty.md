---
title: "Sound Quit Working On Me in Jaunty"
date: 2009-07-04
forum: Multimedia Software
---

### Post by iaskedalice09 on 2009-07-04
Jaunty 9.04
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Not sure what's up. It just stopped working. I reinstalled ALSA. No luck. Thoughts?

Thanks in advance!

---

### Post by ~sHyLoCk~ on 2009-07-04
Did you try running ```
sudo alsaconf
``` ?

---

### Post by iaskedalice09 on 2009-07-04
didn't find the command. just tried it now. ran apt-get install autoconf -y and no package was found. :( What should I do?

---

### Post by iaskedalice09 on 2009-07-04
Crashing for a while. I'll respond when I get up, it's been a hard night for me.

---

### Post by ~sHyLoCk~ on 2009-07-04
Hmm seems like alsaconf do't work in ubuntu. [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by iaskedalice09 on 2009-07-04
Got something - says
autoconf - no input file

Wow. Sounds like bad juju. Interpreters, please?

---

### Post by iaskedalice09 on 2009-07-04
Added this line
```

options snd-hda-intel model=dell-m81

```

to alsa-base.conf

Restarted alsa

no luck.

I got an error when running pulseaudio -D Daemon startup failed.

Thoughts?
Thanks so much for your help!

---

### Post by iaskedalice09 on 2009-07-04
I just logged out and in to see if that would start pulseaudio. It didn't.

---

### Post by lycangrrl on 2009-07-04
this is jaunty. the original poster doesn't mention if this is a new jaunty install, but if it is, there's a known issue ( [>>bug #339164]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/339164") ) where the user doesn't get added to certain groups, one of them being 'audio'..

try:

```
sudo groups foo
```where 'foo' is your username'

if audio is not  listed, you can:

```
sudo usermod -a -G audio foo
```


you'll have to log out and back in for this to take effect.

---

### Post by lycangrrl on 2009-07-04
i verified (through an IM) that the OP's user is a member of audio, and pulse-rt, and pulseaudio is running.  the sound should be working; amixer sees the card and according to it the playback volume is all the way up.

```
$ amixer
Simple mixer control 'Master',0
 Capabilities: pvolume pswitch pswitch-joined
 Playback channels: Front Left - Front Right
 Limits: Playback 0 - 65536
 Mono:
 Front Left: Playback 65536 [100%] [on]
 Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
 Capabilities: cvolume cswitch cswitch-joined
 Capture channels: Front Left - Front Right
 Limits: Capture 0 - 65536
 Front Left: Capture 42598 [65%] [on]
 Front Right: Capture 42598 [65%] [on]
```

i'm a little new to the pulseaudio crowd (but not by any means, to *nix), and would appreciate anyone who can help my friend. :)  i've also had them confirm that yes, their speakers are on and turned up. :)

any ideas?

---

### Post by iaskedalice09 on 2009-07-04
What would happen if I removed pulseaudio? Just curious.

---

