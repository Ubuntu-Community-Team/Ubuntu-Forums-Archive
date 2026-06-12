---
title: "soyo k7vme / via 8233 audio not working on 6.06"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by dlg on 2006-12-12
Like it says in the subject, I'm trying to get the onboard audio on a Soyo K7VME motherboard to work with Ubuntu 6.06

I followed the instructions at [RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats#head-ca36a48df46a615e785bcf4ad33a94db3942a2da) to allow my fresh install of 6.06 to play MP3s, but this didn't work.  Programs can play mp3s now, but I'm not hearing any output.  I know the speakers work, I just tested them by plugging them into my iPod.  Audio-out worked Back In The Day when this computer was running Windows XP, so I don't *think* the hardware is damaged in any way.

I set out to follow the [url=http://ubuntuforums.org/showthread.php?t=205449
]Comprehensive Sound Problem Solutions Guide[/url].  It hasn't really helped.


1. Go to a shell and type: aplay -l
```
dlg@pedro:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dlg@pedro:~$ 
```


2. Type this into the shell: lspci -v
```
dlg@pedro:~$ sudo lspci -v | grep -A 5 Audio
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: Unknown device a723:10fd
        Flags: medium devsel, IRQ 185
        I/O ports at e000 [size=256]
        Capabilities: [c0] Power Management version 2

dlg@pedro:~$
```

4. Now go back to the shell and type sudo modprobe snd-...
```
dlg@pedro:~$ lsmod | grep ^snd_via
snd_via82xx            28824  1
dlg@pedro:~$
```

(note: it was detected at boot-up, i did not have to run modprobe)

I checked alsamixer, none of the outputs are muted.

I hear no output playing an mp3 in Movie Player, Rhythmbox, gxine or mpg123.

Clicking the "Test" button in gstreamer-properties for each of the audio output options produces no output.

and so, even though this is a fresh install, I re-install the audio
```
dlg@pedro:~$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
...
dlg@pedro:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils
...
dlg@pedro:~$ sudo apt-get install gdm ubuntu-desktop

```
and reboot.

and still no sound.



I'm not really prepared to rebuild kernel modules just yet, I'm coming over from the NetBSD world where everything's in one monolithic kernel.  Modules still confuse me <grin>

---

### Post by jsandys on 2006-12-13
Does sound work with the Live Distro?

Print out  /etc/modutils/alsa file.  

I had I problem getting sound out of the southbridge, and I can't remember what I changed in modutils to fix it.

---

### Post by twidget on 2007-05-28
just adding a me to. though the sound problem seems to be intermitent. ive been trying to get everything on this board to work for weeks and have installed everything from dapper to feisty using botth the live cd and alternate installs. ive gotten working sound at a realy low level 3 times but had out of like seven installs all of those were either edgy or feisty installs. if someone knows which config files i should save next time i get working sound let me know. as a side note the sy-K7VME quickstart guide lists the audio codec as being a via vt1612. my kmix says its using a via8235 so i&#7743; wondering if maybe alsa is detecting the wrong sound chip. oh another thing at least for me there is no alsa file in etc/modutils/ under my current soundless edgy install

---

### Post by twidget on 2007-05-28
I solved the problem  at least in my case. turns out that the s-video connector from my agp card was shorting out the audio1 header of the motherboard so i put a couple layes of scotch tape on the connector rebooted fired up amarok and got audio. hope this helps.

---

