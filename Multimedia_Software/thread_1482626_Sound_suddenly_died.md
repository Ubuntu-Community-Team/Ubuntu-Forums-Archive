---
title: "Sound suddenly died"
date: 2010-05-13
forum: Multimedia Software
---

### Post by Rawrhunter on 2010-05-13
I have a Dell Studio XPS 16 laptop with Ubuntu 10.4. It *did* have sound working perfectly. Today I decided to plug in a pair of headphones, and now the sound is not working. I did not change anything else.
What I've done:
-Checked all my volume levels/mutes
-Restarted a few times
-Followed "Comprehensive Sound Problem Solutions Guide" sticky
-Booted to windows 7, and sound works fine, through headphones and speakers

Any suggestions would be appreciated!

Byron

---

### Post by Rawrhunter on 2010-05-14
Bump!

---

### Post by SpaceBison on 2010-05-14
Have you tried opening the terminal and typing in "alsamixer" and seeing if anything was muted?

---

### Post by Rawrhunter on 2010-05-14
Yes I did. Everything was fine.

---

### Post by Rawrhunter on 2010-05-14
Bump!

---

### Post by Rawrhunter on 2010-05-14
Bump!

---

### Post by Rawrhunter on 2010-05-14
Bump :(

---

### Post by Rawrhunter on 2010-05-15
My sound card is recognized and selected, all volumes are up in alsamixer and the gnome-volume-control, but I am still not getting any sound. Everything still works fine in windows 7.

---

### Post by Rawrhunter on 2010-05-15
I installed Pulseaudio volume control and the output display shows bars moving up and down when audio is played. So sound is being output and ubuntu thinks it is playing it. Everything is turned on in gnome-alsamixer (there's no external amp option), and I'm tring to check all the options at the bottom, but 'IEC958 Playback Source' and 'Line Jack Mode' uncheck themselves as soon a I exit the volume control. The speakers and headphones definitely do work as they make sound as soon as I boot to Windows 7.

Where could the sound be distrupted between the Pulse audio output and the speakers?

---

### Post by Rawrhunter on 2010-05-15
Bump!

---

### Post by Rawrhunter on 2010-05-15
I completely removed then reinstalled alsa and pulseaudio. I think this would have restored all volume levels/mutes to their defaults. The defaults were working when I first install 10.04, so there seems to be nothing stopping this from working.

Any other suggestions would be greatly appeciated!

---

### Post by Rawrhunter on 2010-05-15
Buumpp!

---

### Post by Rawrhunter on 2010-05-15
Bump!

---

### Post by Rawrhunter on 2010-05-16
Bump.

---

### Post by gnik1 on 2010-05-16
I had a sound problem last week. Didn't see any problems. Then realized I had it muted. Just didn't stick out enough for me to realize that it was. Don't know how my sound got muted either, but unmuted and sound was back. Just in case your oversight is the same as mine was.

---

### Post by lidex on 2010-05-16
Probably jack-sense problem. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. *_Also helpful is the make/model of your PC/Laptop._*

---

### Post by Rawrhunter on 2010-05-16
uname -a
```
Linux byronUbuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

head -n 1 /proc/asound/card*/codec#*
```
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD73C1X5

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
```

The computer is a Dell Studio XPS 16 with the default onboard sound card. As mentioned, the sound was working fine, then seems to have suddenly stopped working. Sound works on my dual-booted windows, so it's not a hardware issue.

---

### Post by lidex on 2010-05-16
Oops, sorry. Mixing up my threads. Hold on I'll be right back.

OK, try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-eq
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by Rawrhunter on 2010-05-16
That did it!
Added that to the file, rebooted and turned up the volume in alsamixer and had sound once again.
Thanks for your time lidex!

---

### Post by lidex on 2010-05-16
You're welcome. When you confirm the fix, please mark the thread as solved using 'Thread Tools' up top.

---

