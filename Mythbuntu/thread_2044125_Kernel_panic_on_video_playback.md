---
title: "Kernel panic on video playback"
date: 2012-08-18
forum: Mythbuntu
---

### Post by dpapathanasiou on 2012-08-18
I just installed Mythbuntu 12.04 to an HP AMD machine with a new 1 TB hard drive.

Everything went well, and booted with no problems, but a few hours into playing back some recorded programs, the screen went black with a "kernel panic" message.

I checked the kernel log and found this:

```
$ grep -i panic /var/log/kern.log
kernel: [    8.073624] drm: registered panic notifier
```

and here's what was just above that line in the file:

```
kernel: [    7.992582] [drm] radeon: ring at 0x0000000040001000
kernel: [    7.992603] [drm] ring test succeeded in 1 usecs
kernel: [    7.992784] [drm] radeon: ib pool ready.
kernel: [    7.992855] [drm] ib test succeeded in 0 usecs
kernel: [    7.993125] [drm:radeon_get_legacy_connector_info_from_bios] *ERROR* Unknown connector type: 8
kernel: [    7.993130] [drm] Radeon Display Connectors
kernel: [    7.993132] [drm] Connector 0:
kernel: [    7.993134] [drm]   VGA
kernel: [    7.993137] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
kernel: [    7.993139] [drm]   Encoders:
kernel: [    7.993141] [drm]     CRT1: INTERNAL_DAC2
kernel: [    7.993142] [drm] Connector 1:
kernel: [    7.993144] [drm]   DVI-D
kernel: [    7.993146] [drm]   HPD1
kernel: [    7.993148] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
kernel: [    7.993150] [drm]   Encoders:
kernel: [    7.993152] [drm]     DFP1: INTERNAL_DVO1
kernel: [    8.072441] [drm] fb mappable at 0xD0040000
kernel: [    8.072446] [drm] vram apper at 0xD0000000
kernel: [    8.072448] [drm] size 4096000
kernel: [    8.072450] [drm] fb depth is 24
kernel: [    8.072452] [drm]    pitch is 5120
kernel: [    8.072726] fbcon: radeondrmfb (fb0) is primary device
kernel: [    8.073582] Console: switching to colour frame buffer device 160x50
kernel: [    8.073622] fb0: radeondrmfb frame buffer device
kernel: [    8.073624] drm: registered panic notifier

```

I did find another thread which suggested the problem is in the Radeon driver, and that I should go to the Graphics Drivers section of the Mythbuntu Control Center and switch to a restricted driver, but none are available there.

Here's the video card I have (it's built-in to the motherboard, and I'd prefer to use it, if at all possible, as opposed to getting a new card):

```
$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS480 [Radeon Xpress 200G Series] [1002:5954]

```

Any suggestions?

---

### Post by Rotak on 2012-08-18
A friend of mine has 3 MythBoxes, all with ATI cards. There were similar problems:
* no HDMI output at all
* only HDMI audio or video working, but not both
* kernel panics in every way possible
* stuttering video playback
* desktop and myth menu fullscreen, but video playback is not

Anyway, we could solve it on 2 boxes by trying to install different driver versions. On the third box, we installed a NVidia card. There was no way to fix the on-board ATI card on that system.

I think ATI cards are great, but they should really do something about their crappy drivers. It was and is horrible in Windows, and it's a nightmare on Linux.

---

### Post by dpapathanasiou on 2012-08-19
Thanks for replying.

It's a shame because the open source ATI Radeon driver actually works pretty well most of the time, and I don't have any problems when booting, etc.

It's just that after n minutes or hours, the kernel panics and I have to reboot.

I considered adding a [adding a kernel parameter in sysctl.conf to reboot automatically]("http://askubuntu.com/questions/43555/how-to-configure-automatic-reboot-after-kernel-panic#43556") but I noticed that after panics of this kind, myth-backend wasn't usually running, so that wouldn't really solve the problem.

I tried using the closed-source binary driver from ATI [as described here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), but the particular driver installer for my card, ati-driver-installer-9-3-x86.x86_64.run, would not run under 12.04.
 
So for now, I added the [xorg-edgers ppa to my sources]("https://launchpad.net/~xorg-edgers/+archive/ppa"), and updated the xserver-xorg-video-ati package.

I won't really know if it's solved or not until I run it for a while, but I'm hoping that works, since it seems the only alternative is to buy and install a nvidia card.

---

### Post by dpapathanasiou on 2012-08-19
Update: well, that didn't take long.

The bleeding-edge ati driver didn't change a thing, and I'm still getting kernel panics.

It's weird in that I used that box for years running debian, and never had any problems with the built-in video (I know debian and ubuntu are not quite the same, but still).

---

### Post by Rotak on 2012-08-19
What you posted (logs) is only the initialization of the card. You can tell by the number in those [ and ]. It's the system/kernel uptime in seconds.

When the kernel panic actually occures, it should print some additional information to the console. But those are not logged!! Maybe you can take a "screenshot" with a camera or cell phone. That infos may help more to locate the issue.

---

### Post by dpapathanasiou on 2012-08-19
I'll do that the next time it happens, and post it here (I've shut the thing off for the time being).

BTW, is that the only way to get at the panic information? None of the other logs have it?

In the meantime, I've ordered an nvidia based video card, and I'll just use that when it arrives.

---

### Post by Rotak on 2012-08-19
You can check /var/log/kern.log.0 file. The /var/log/kern.log is from the actually running system. But from my experience, it's not always written till the end, so kern.log.0 may have all infos, except the panic. :sad:

---

### Post by dpapathanasiou on 2012-08-19
You're right, there was an earlier version of the kern.log file (it was /var/log/kern.log.1 actually), but it didn't contain any of the actually panic details, and just matched what I'd already posted originally.

---

### Post by dpapathanasiou on 2012-08-19
[Here are a couple of shots]("http://imgur.com/a/QmZIy") of the latest kernel panic: 

[http://i.imgur.com/cpghah.jpg]("http://i.imgur.com/cpghah.jpg")
[http://i.imgur.com/Ho0gth.jpg]("http://i.imgur.com/Ho0gth.jpg")

Both shots are of the same screen, just at slightly different angles.

---

### Post by Rotak on 2012-08-20
Ok, that looks different than expected. I am a software developer, but not a kernel hacker, maybe somebody else can confirm this!!!

What I can tell from the call trace is, that there seems to be an issue with an interrupt sent to your tuner card. It crashed on cx23885_video_wakeup call in the cx23885 driver (kernel module).

So your issue is not directly related to the video card. cx23885 is a DVB tuner card chipset.

The hard-to-answer question is: Is it a firmware, a driver or a kernel issue?

My first approach would be trying another kernel, like 2.6.39.x.

If I remember correctly, my cousin's HTPC is using a kernel "2.6.39.4mag" with a cx2388x chipset.  MAG is a special kernel from the guys who built the HTPC. But AFAIK the MAG part is only about a kernel patch to enable decryption of paytv with the integrated smartcard reader.

However, I don't know if there is also a "custom" firmware included in their release. "Custom", like in: Not the one that usually installs from firmware-linux package. I'd need to ask.

Maybe you can experiment with the kernel versions and check for updates on the firmware-linux package in the meanwhile.

(Did I mention that this is increasing my headache level now? :D)

---

### Post by dpapathanasiou on 2012-08-20
Thanks for spotting that (I know very little about the kernel).

The capture card I'm using is a Hauppauge 1187 WinTV-HVR-1250, and I've used it for over a year with Mythbuntu 11.04 and 11.10 on similar hardware w/o any problems.

Both this new box and the previous one are amd 64 bit cpus; the only difference is the video card: nvidia for the old box, ati for this one.

I'll try either downgrading to 11.10 and see if that makes any difference, or, if not, switching to the bleeding-edge latest kernel.

---

### Post by Rotak on 2012-08-23
I think you can downgrade the kernel without reinstalling the system. At least for a test. If it's the firmware-linux package, I am unsure whether you can dowgrade that as well.

---

### Post by dpapathanasiou on 2012-08-24
Thanks for all the replies and suggestions.

I think I'm simply going to reinstall 11.10, since I know my capture card has no problems with that kernel version.

---

### Post by jshoor on 2013-06-03
In case anyone else is struggling with this issue, I thought that I would let people know that I was able to resolve it by upgrading the motherboard BIOS.  I have a GA-73PVM-S2H. It took a little bit of fiddling around but it all works great now.

---

