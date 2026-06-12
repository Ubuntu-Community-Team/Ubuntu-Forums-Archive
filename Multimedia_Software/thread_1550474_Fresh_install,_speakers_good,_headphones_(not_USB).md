---
title: "Fresh install, speakers good, headphones (not USB) won't work"
date: 2010-08-11
forum: Multimedia Software
---

### Post by JacquiOh on 2010-08-11
I got my new Toshiba R700 yesterday and I'm on a nice, shiny fresh install of 10.04

Went to watch the Rachel Maddow podcast :popcorn: this morning and ... no sound! It works through my speakers but the missus is sleeping, so no good. ;)

I've tried 3 different headphones just to make sure. I searched and couldn't find similar problems.

Help?

---

### Post by lidex on 2010-08-11
Have you checked your 'Sound Preferences'? How about alsamixer?
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by JacquiOh on 2010-08-11
Thanks for replying!

When I bring those things up, there's no option at all for headphones. No headphone slider or an unticked box...

---

### Post by lidex on 2010-08-11
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by JacquiOh on 2010-08-12
It's a Toshiba R700-15U Portégé

```
jacq@ubu-jacq:~$ uname -a
Linux ubu-jacq 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

```

```
jacq@ubu-jacq:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
jacq@ubu-jacq:~$ dpkg -l | grep "alsa"
ii  alsa-base                                                1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                               1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                               4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                          0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                       0.10.28-1                                       GStreamer plugin for ALSA

```

```
jacq@ubu-jacq:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

```

---

### Post by odinfromvalhalla on 2010-08-12
it is possible that the jacks of your laptop are not mapped correctly.

try adding the following at the end of /etc/modprobe.d/alsa-base:

options snd-hda-intel model=3stack
options snd-hda-intel model=toshiba

save the file and then reboot. Note that you might just need one of the lines at a time.

---

### Post by JacquiOh on 2010-08-12
Thanks for the suggestion... didn't work :(

One thing I didn't mention -- when I plug in the head phones, the external speakers go silent, so it knows the headphones are plugged in.... there's just no sound coming from them. 

The first set I tried, I actually chucked in the bin, thinking they were faulty! lol

---

### Post by cajunaggie on 2010-08-21
I'm having the same issue. None of the configuration options I've tried seem to work. Any ideas?

---

### Post by lidex on 2010-08-22
> **cajunaggie said:**
> I'm having the same issue. None of the configuration options I've tried seem to work. Any ideas?

Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

