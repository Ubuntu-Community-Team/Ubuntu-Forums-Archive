---
title: "No sound HP Touchsmart"
date: 2011-01-23
forum: Multimedia Software
---

### Post by bryan6376 on 2011-01-23
Hey all:

I'm sure I sound like a broken record, but I've had Maverick installed for a few days and haven't had any sound output to go along with it.  I've been working my way through the forums trying to solve my sound issues.  Care to suggest anything?  I've uninstalled and reinstalled pulse and alsa a few times over, with no success.  Here are my aplay and lspci outputs:

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


sudo lspci -v

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
	Subsystem: Hewlett-Packard Company Device 2a74
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at f9bf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

Any suggestions?  I'll post back on here if I manage to solve anything :)

SOLVED:  Via terminal:  sudo gedit /etc/modprobe.d/alsa-base.conf
At the very end, add a line which says:  options snd-hda-intel model=touchsmart

It seems like depending on your type of computer, all you need to do to fix many of the sound issues is change "touchsmart" to whatever you are using (laptop, toshiba, etc.).  Good luck!

---

### Post by ptate on 2011-08-12
Just installed Ubuntu on an old HP Touchsmart I acquired from my extended family.   Sound did not work upon initial install, but found this post, applied the one line change to alsa-base.conf as you described and now sound is working like a charm.   Thanks!

-ptate

---

### Post by RockOut on 2011-12-31
I too found this solution to be an excellent one! Thank you!!!

---

### Post by parminides on 2012-05-26
I run Ubuntu 12.04 on an HP TouchSmart. For a long time I couldn't get sound out of the internal speakers, although the headphones (either usb or in the headphone jack) worked.

This morning I came across this thread and added 

> 
options snd-hda-intel model=touchsmart


to the end of /etc/modprobe.d/alsa-base.conf.

After reboot, I get sound out of the internal speakers for the first time ever in Ubuntu, and the usb headphones still work, but now there's no sound out of the headphone jack.

Does anyone know how to get all three outputs to work?

---

