---
title: "Mythbuntu 10.10 - Antec Fusion VFD + IR"
date: 2011-02-05
forum: Mythbuntu
---

### Post by ardnut on 2011-02-05
Hi,

Recently upgraded to mythbuntu 10.10 and I'm trying to get the VFD + IR working (with an mce remote).

I have the latest versions installed:
lcdproc = 0.5.3
lirc  = 0.8.7-pre3

lsusb reports the device as Bus 002 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
/etc/LCDd.conf is set to use the imon driver
/etc/modprobe.d/imon.conf has: options imon display_type=1
(i've been using this option successfully in ubuntu 10.04 and setting this to anything else instead of type 1 just gives me these errors: imon: lcd_write: invalid payload size: 32 (expecting 8))

I do get text displayed on the vfd but it's just 1 line of random letters and symbols.

On the lirc side of things I've done a sudo dpkg-reconfigure lirc, set it as a linux input layer and using /dev/input/by-path/pci-0000:00:0b.0-usb-0:7:1.0-event-mouse (i've tried all the other options as well).
Running irw and then pressing buttons on my mce remote gives me no output at all.

Is any one using an Antec Fusion VFD + IR successfully with Mythbuntu 10.10, and if so what am I doing wrong? :)

Thanks,
Ash

---

### Post by barti on 2011-02-06
Afraid I can't bring anything useful to this one - though I'm in exactly the same situation. I know the remote and receiver both work, as they're fine in the Windows installation on the same machine.

Unfortunately pretty much all the guides/how-tos etc online refer to older versions of things (such as assuming lirc is using /dev/lirc0 rather than the linux device).

If I figure anything out I'll post back!

Stephen

---

### Post by LiveBootleg on 2011-02-11
Hi,

Please let me know if you find a solution to this. Also experiencing the same problem...

Thanks

---

### Post by Neon Dusk on 2011-02-11
I've got the Antec VFD working in 10.10.

Similar to the [thread=1594799]Generic MCE Receiver[/thread] I had to disable the kernel driver and install lirc-modules-source.

It was a few months ago but I think the steps I followed are listed [here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/666493/comments/3)

(n.b. you may be using a newer kernel so some of the paths will be different)

---

