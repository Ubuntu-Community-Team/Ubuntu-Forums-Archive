---
title: "Alsamixer &quot;Master&quot; volume control slider +/- has no effect on speakers volume"
date: 2018-07-10
forum: Multimedia Software
---

### Post by bijan2 on 2018-07-10
New installation of Ubuntu 18.04 on ASUS laptop results on NO control of speakers loudness using System Volume Control or Alsamixer "Master".
Has anyone experienced this? 
TIA

---

### Post by wildmanne39 on 2018-07-10
*Thread moved to **Multimedia Software for a more appropriate fit**.*

---

### Post by irisheart on 2018-07-11
Laptop Model and hardinfo would be helpful to start

---

### Post by bijan2 on 2018-07-12
Thank you, Model is ASUS ZenBook 3 Delux UX490UAR with Analog Surround 4.0 Output speakers.

UX490UAR:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 08)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d13 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Network controller: Intel Corporation Wireless 8265 / 8275 (rev 78)

---

### Post by TheFu on 2018-07-12
No idea how to handle a slider, but with vol+ / vol- buttons you can use xdotool to tie the keys to normal commands to increase/decrease  volume.

Here's the vol- button command for my laptop: pactl set-sink-volume 1 -10%
If you are using openbox,  I can provide more details. Otherwise, those details are useless.  Every window-manager handles these things differently.

---

### Post by bijan2 on 2018-07-12
Thank you for the command but that did not work for me. The keyboard fn+f11 / f12 does not work either. Applications volume like YouTube,etc indiviually works fine when I use them. The problem is Master Volume at the top right corner of the Ubuntu screen is the one has no effect to speakers volume.

---

### Post by TheFu on 2018-07-13
> **bijan2 said:**
> Thank you for the command but that did not work for me. The keyboard fn+f11 / f12 does not work either. Applications volume like YouTube,etc indiviually works fine when I use them. The problem is Master Volume at the top right corner of the Ubuntu screen is the one has no effect to speakers volume.

The "sink" number 1 in my case may not be the correct sink for you.  I'm assuming the DE you run uses pulse audio, which most do, except LXDE.

I have no idea how to control the volume though a panel widget. Don't use those myself, since I don't run any DE.

You can also try **pavucontrol** which is the main PulseAudio control application. It is too complicated for connecting to vol+/vol- buttons, but if it works, then pulse audio is definitely being used.  Pulse is more complex than it really needs to be  for most uses, but it does bring some impressive audio routing capabilities, provided it is working.

---

### Post by bijan2 on 2018-07-13
There are some modifications that I can make to this file  ==>> **sudo nano /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common** as recommended by few users which it gets the Volume Control to work but the sound becomes scratchy and I also loose Headphones Volume. 
As far as **pavucontrol** goes, it is installed and I can only control the volumes of indiviual applications like VLC, YouTube, etc. It has no effect what so ever on Ubuntu Master Volume slider, the only thing I can do is mute and unmute.
FYI, all is fine when I use Windows 10 but when I boot to Ubuntu 18.04 the volume slider which I believe is a function of alsa-mixer does not work...

---

### Post by TheFu on 2018-07-13
Only Lubuntu users should still be using alsamixer.  With 16.04 the most popular Ubuntu flavors all switched to PulseAudio.
I've been helped by some sound experts here previously. Hopefully they will correct any mistakes I've made and be helpful.

In my mind, if there is scratchy audio, that would say it is a loose connection somewhere, but you said everything works as expected under Windows?

---

### Post by bijan2 on 2018-07-13
Thank you, I agree with you. I did a new ground up installation of Ubuntu 18.04 and not upgrading from 16.04 / 17.10. Even that did not help and for whatever the reson is I get some Alsamixer config files under PulseAudio directory.
I am not sure of that. Like you said, hope some sound expert can help here. I'll report soon... Thanks

---

### Post by bijan2 on 2018-07-14
It seems to be a problem with Pulseaudio not starting normally after each reboot. Here is the results for:

pulseaudio -v
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 11.1
I: [pulseaudio] main.c: Page size is 4096 bytes
I: [pulseaudio] main.c: Machine ID is f6ca47e9f5604b6c8493d4d16bdd4a40.
I: [pulseaudio] main.c: Session ID is 2.
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/bijan/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-11.1/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

I have also attached the image of Alsamixer. The up / down of Master and Speakers columns has no effects on Speakers Volume. The only thing works there is PCM.

---

### Post by bijan2 on 2018-07-16
The latest updates of software solved the problem... Thanks to the developers.

---

