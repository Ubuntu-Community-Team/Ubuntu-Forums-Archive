---
title: "Strange problem with laptop suddenly not waking when opened and no sound"
date: 2020-03-18
forum: Multimedia Software
---

### Post by jongudm on 2020-03-18
I'm dealing with a problem that seems to get progressively weirder as time passes. I have a Lenovo X1 Carbon laptop (new since late September), I installed 18.04 straight out of the box and was very happy with how it worked. I noticed a strange issue that I found more people had run into with the built in microphones not working, but that was a very minor issue for me. I saw bug reports that suggested this had been fixed in later releases so I expected to upgrade to 20.04 as soon as it came out and that would be that.

Then the reality hit that everyone would have to work from home if they possibly could and keep social distance. As part of that everyone at my workplace was instructed to make sure we could attend meetings via Microsoft Teams. Since screen sharing did not seem to work at all in the web version I installed the new client from Microsoft (not the one in the Ubuntu repo, I didn't know about that one until afterwards) to see if it worked there. Big mistake (or so it seemed). The next time I rebooted the machine (which happened later that day because the battery ran out) I started getting the "System problem detected" notification and my soundcard seemed to be completely gone. Opening Settings -> Sound only showed "Dummy output". This time no sound came from either speaker and the microphones did not work either. Every time I closed the laptop it turned out to be crashed when I opened it again, no matter how short the time was. Interestingly I could get sound, both input and output, by plugging my headset into the dock but not the laptop itself.

So now I had two different reasons to simply wipe the machine and do a clean install of a new version that would have the fix I expected for the microphone issue. I installed 19.10 today (re-encrypting the entire SSD drive so there should not be any remaining "ghosts") but both problems are still there! No sound in or out (except via the dock), Settings -> Sound only shows "Dummy output" and closing the laptop leads to an immediate crash.

At this point I'm not even sure this is a software problem at all, but it seems like an extremely weird coincidence that a hardware/firmware/??? problem would start to turn up immediately after I install something huge and intrusive like the Teams client (side note; avoid that thing, even if it isn't the source of my problems here, insists on starting when you boot and has no functionality that the web version doesn't have).

At this point I have not started a deep log dive (had to try to get some of my work done during this whole mess of an upgrade), when I do I'll post what I find if it seems even remotely relevant.

Thanks for reading through this, if any of you have ideas they would be greatly appreciated.

---

### Post by oldfred on 2020-03-18
Moved to Multimedia sub-forum.
And in that forum review the sticky on sound issues.
[https://ubuntuforums.org/forumdisplay.php?f=334](https://ubuntuforums.org/forumdisplay.php?f=334)

Do not know if this is related or not.
Audio issue Bionic Eoan
[https://bugs.launchpad.net/ubuntu/+source/linux-oem-osp1/+bug/1864061](https://bugs.launchpad.net/ubuntu/+source/linux-oem-osp1/+bug/1864061)

---

### Post by jongudm on 2020-03-18
This certainly seems to be the appropriate place for this thread, since these two things, sound disappearing and the laptop not suspending or waking, seem to go together more often than I thought. What little I have found by searching is that this seems related to Intel sound drivers, but how that can start to happen suddenly on one release that had worked great and then keep going like nothing happened after a clean install of a newer release is still weird.

---

### Post by jongudm on 2020-03-19
There is clearly something driver related here:

```

root@jonhg-laptop:~# lspci -vv | grep -i audio00:1f.3 Audio device: Intel Corporation Cannon Point-LP High Definition Audio Controller (rev 11) (prog-if 80)
    Subsystem: Lenovo Cannon Point-LP High Definition Audio Controller

```

```

root@jonhg-laptop:~# dmesg | grep -i audio[    0.243879] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[   10.963284] snd_soc_skl 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   10.986130] skl_hda_dsp_generic skl_hda_dsp_generic: Unsupported HDAudio/iDisp configuration found
[ 5218.363077] usb 1-5.2.4: Product: ThinkPad Dock USB Audio
[ 5218.378860] input: Generic ThinkPad Dock USB Audio Consumer Control as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.2/1-5.2.4/1-5.2.4:1.3/0003:17EF:306F.0007/input/input22
[ 5218.439054] input: Generic ThinkPad Dock USB Audio as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.2/1-5.2.4/1-5.2.4:1.3/0003:17EF:306F.0007/input/input23
[ 5218.439712] hid-generic 0003:17EF:306F.0007: input,hiddev2,hidraw6: USB HID v1.11 Device [Generic ThinkPad Dock USB Audio] on usb-0000:00:14.0-5.2.4/input3
[ 5218.694367] usbcore: registered new interface driver snd-usb-audio

```

Unsupported configuration found seems like something to follow up on...

---

### Post by jongudm on 2020-03-20
To clarify (because this might get lost in the wall of text at the top), this problem appeared using 18.04, I performed a clean install (wiping everything) of 19.10 and the same problem is present.

---

### Post by jongudm on 2020-03-24
I missed this part last time, here is the output for audio from lspci -v:

```

00:1f.3 Audio device: Intel Corporation Cannon Point-LP High Definition Audio Controller (rev 11) (prog-if 80)	Subsystem: Lenovo Cannon Point-LP High Definition Audio Controller
	Flags: bus master, fast devsel, latency 64, IRQ 16
	Memory at ea33c000 (64-bit, non-prefetchable) [size=16K]
	Memory at ea000000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 3
	Capabilities: [80] Vendor Specific Information: Len=14 <?>
	Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: snd_soc_skl
	Kernel modules: snd_hda_intel, snd_soc_skl, sof_pci_dev

```

---

### Post by jongudm on 2020-03-24
OK, so this seems to be solved in the next kernel update, as seen here: [https://bugs.launchpad.net/ubuntu/+source/linux-oem-osp1/+bug/1864061](https://bugs.launchpad.net/ubuntu/+source/linux-oem-osp1/+bug/1864061) (and as was pointed out in literally the first answer, I missed that... :O ). I guess I'll just wait for that one then. Does anyone know when it is likely to hit? I know it's in proposed but it also still has some issues so I'm not going to risk this getting worse.

Marking this as solved, since the actual solution seems to be found even if it's not here yet.

---

### Post by oldfred on 2020-03-24
Newer kernel is in Focal.
You can install newer kernel, but whether that works with everything else, is up to you. 
[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

```

fred@fred-Z170N-focal:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu Focal Fossa (development branch)"
fred@fred-Z170N-focal:~$ uname -a
Linux fred-Z170N-focal 5.4.0-18-generic #22-Ubuntu SMP Sat Mar 7 18:13:06 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

---

