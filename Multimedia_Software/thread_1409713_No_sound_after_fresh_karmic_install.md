---
title: "No sound after fresh karmic install"
date: 2010-02-17
forum: Multimedia Software
---

### Post by kylegalloway on 2010-02-17
I just installed karmic on my media server.  With Jaunty, everything worked fine.  I tried an upgrade, and go no sound.  After poking around in the forms and trying some solutions still no sound.

So I decided to try a fresh install, again, no sound.  I have cheched the obvious, mixer volumes, mute, output device, etc.  But I can't seem to get it to work.  I poked around in the forms and I've tried many of the solutions, but still no luck.

If I'm just stupid and someone has a good solution, hopefully they will kindly point me in that direction and I apologise for the repeat but this is maddening.

Here is my lspci output for my sound device...

00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 8345
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fcf78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

And aplay -l
pseudorandom@thecaptain:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I am ruinning 64-bit Karmic, and I use the analog output for sound on this box.

Any help would be greatly appreciated.

---

### Post by Galtz91 on 2010-02-18
I have a similar problem: I had karmic and everything was fine, but I screwed something up with the packages and couldn't install anything anymore, so I reinstalled kubuntu 9.10, but now I don't have any sound except for the sound when I log in.

I'm using an ASUS X5DIJ series. It uses a HDA Intel audio-device. Under Jaunty, this model lacked any kind of audio, but as I said, when I first installed karmic koala, everything worked just fine.

update: by installing some recommended packages, I've now got sound when I listen to music from amarok. vlc media player as well as any kind of online-audio (youtube, myvideo, etc) ain't making a sound.

update2: internet-audio suddenly started working, now only the vlc media player stays mute.

---

### Post by VertexPusher on 2010-02-18
```
speaker-test -D plughw:NVidia
```
When you run this command in a terminal window, do you hear sound? If not, do you see an error message?

If there is neither sound nor an error, open a second terminal window/tab, enter
```
alsamixer -D hw:NVidia
```
and check all the volume settings while speaker-test is running.

---

### Post by garvinrick4 on 2010-02-18
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Do not forget to reboot after.

---

