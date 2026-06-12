---
title: "xine/vlc occasionally freezes system (audio repeatedly loops)"
date: 2009-04-12
forum: Multimedia Software
---

### Post by blastus on 2009-04-12
I have a HTPC with an NVIDIA video card and built-in audio. I don't recall this being an issue prior to Ubuntu 8.10. Usually once or twice during the playback of an unencrypted DVD movie with MythTV and xine (or vlc) over the network, my system will freeze completely. When the system freezes nothing is responsive anymore and the audio repeatedly loops around 1/2 second or so at the moment the system locked up.

For Video:
xine: I've tried xv, opengl, and xshm video drivers and the problem persists. 
vlc: I tried the default video settings and the problem occurred. 

For Audio:
I am using a digital optical connection to my receiver.
xine: I use ALSA and "Pass Through" for speaker arrangement
vlc: I use the audio device "A/52 over S/PDIF"

I'm beginning to think this is an audio issue as it has never locked up during playback with mplayer of other video that is connected via analog RCA cables to my receiver. And what's up with the audio endlessly looping around half a second? Because this occurs once or sometimes twice at any time (it's completely random) during a movie I can't exactly reproduce the problem.

Has anyone encountered a problem like this before? Here's the output of "sudo lspci"...

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```

---

### Post by blastus on 2009-04-29
I am posting this for the benefit of anyone else that may have a similar issue. I believe the problem had to do with the NVIDIA driver. Since the rolling out of the NVIDIA driver 180.xx (on Intrepid and now on Jaunty) I haven't encountered any system freezes anymore.

---

