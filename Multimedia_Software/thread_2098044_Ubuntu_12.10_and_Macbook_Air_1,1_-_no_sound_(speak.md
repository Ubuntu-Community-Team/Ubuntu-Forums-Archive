---
title: "Ubuntu 12.10 and Macbook Air 1,1 - no sound (speakers + microphone) - headphones OK"
date: 2012-12-25
forum: Multimedia Software
---

### Post by kaiyer on 2012-12-25
I ran lspci | grep Audio and got:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
I've searched the forums and added the following line to alsa.conf

# macbook air sound
options snd-hda-intel model=mbp3
I rebooted and there was still no sound.

So I ran alsamixer. It shows that the speakers and master are not muted. The speakers and microphone are still not working. What can I do to get them to work? I'm running a single-boot Ubuntu 12.10 system with a 64-bit kernel, on a Macbook Air 1.1.

I also ran the command hwinfo and got the following results

'hwinfo --sound

hal.1: read hal dataprocess 2630: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282. This is normally a bug in some application using the D-Bus library. libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files 13: PCI 1b.0: 0403 Audio device
[Created at pci.318] Unique ID: u1Nb.4u0CAOk3K5C SysFS ID: /devices/pci0000:00/0000:00:1b.0 SysFS BusID: 0000:00:1b.0 Hardware Class: sound Model: "Intel 82801H (ICH8 Family) HD Audio Controller" Vendor: pci 0x8086 "Intel Corporation" Device: pci 0x284b "82801H (ICH8 Family) HD Audio Controller" SubVendor: pci 0x106b "Apple Computer Inc." SubDevice: pci 0x00a2 Revision: 0x03 Driver: "snd_hda_intel" Driver Modules: "snd_hda_intel" Memory Range: 0x90500000-0x90503fff (rw,non-prefetchable) IRQ: 43 (338 events) Module Alias: "pci:v00008086d0000284Bsv0000106Bsd000000A2bc04sc03i00" Driver Info #0: Driver Status: snd_hda_intel is active Driver Activation Cmd: "modprobe snd_hda_intel" Config Status: cfg=new, avail=yes, need=no, active=unknown'

---

### Post by mercutio on 2012-12-26
I have the same issue.  Under earlier ubuntu versions I was able to get the sound working by adding that line to /etc/modprobe.d/alsa-base.conf:

options snd_hda_intel model=mbp3
also have tried with dashes as above
options snd-hda-intel model=mbp3

I have never gotten the isight microphone working on older versions of ubuntu, but it seems with the loss of speakers, hardware support on this machine is going in reverse.

A crazy note is that the sound card works... if you use headphones in the jack.  Of course, so do other sound cards like bluetooth etc...  It really seems like there is a problem with the speakers specifically, or about the headphones plug detection reading incorrectly.

---

### Post by JSmith1234 on 2013-01-26
I have exactly the same problem. Macbook Air (first generation), Ubuntu 12.10 (recently installed), sound working on headphones but not speakers.

Tried to configure alsa-base.conf with options snd_hda_intel model=*

where * E {mbp3, mba, mba1, mba11}

tried all, none works

any solutions, ideas out there?

---

### Post by twinturbotom on 2013-03-05
Same issue here, 12.10 1st gen macbook air.

---

### Post by E27 on 2013-06-10
Hi, I just installed raring ringtail on my MBA 1,1 and have the same sound issue as described here.  Is this a reported bug in Ubuntu?  Should we report it (have never actually done that before!) ?

---

### Post by nicolo.p on 2013-11-19
Hello,
same problem for me, though speakers and HP have always worked (I'm with 12.04 now)
I filled bugs in many places, but up to now it is not clear how to proceed: it seems difficult to reproduce some specific settings Apple has at EFI level or elsewhere, regarding vendor-specific verbs

[http://superuser.com/questions/646470/microphones-not-working-on-apple-macbook-air-1-1-early-2008-under-linux/670849#670849](http://superuser.com/questions/646470/microphones-not-working-on-apple-macbook-air-1-1-early-2008-under-linux/670849#670849)
[https://bugzilla.kernel.org/show_bug.cgi?id=52221](https://bugzilla.kernel.org/show_bug.cgi?id=52221)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/268301](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/268301)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1170837](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1170837)

---

