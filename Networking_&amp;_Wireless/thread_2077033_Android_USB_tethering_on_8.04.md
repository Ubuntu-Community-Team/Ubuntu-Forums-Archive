---
title: "Android USB tethering on 8.04?"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2012-10-27
Yes, 8.04 Hardy Heron.  I received an older laptop  which has ATI X1250 graphics, and the last version of Ubuntu that supports it is Hardy.  So don't ask me why I'm running an old version of Ubuntu.

I would like to be able to use the native USB tethering on my Android phone, an LG Optimus T running CyanogenMod 7.  USB tethering works pretty much out of the box on pretty much every version of Ubuntu from 10.04 on up, so I'm assuming this is probably a kernel issue (lack of drivers)

So here is what I've discovered so far.  I can ADB shell into my phone.  When I engage the USB tethering, my ADB shell session ends.
no activity is shown in the Gnome Network Manager applet.  If I execute the command

```
ifconfig usb0 up
```
in return I get
```
usb0: ERROR while getting interface flags: No such device
```

Is this just a matter of the drivers for Android USB tethering not being present in Linux kernel 2.6.24?  If so, would it be possible to build the specific .ko files for this kernel and where would I find the source files?  I've done this in the past for unsupported devices like web cams and Bamboo drawing pads, so in theory it's just a matter of missing drivers in my particular kernel.  The ADB itself has generic drivers for Android devices but they are Windows specific.

As I mentioned, the last official ATI Catalyst drivers for my graphics card are for kernel 2.6.24, so I'm kind of locked in.  This graphics card isn't very powerful to begin with and performance using the open source drivers on later kernels is terrible, bordering on unusable, so upgrading is not really an option.

I'm also going to look into methods like Easy Tether (which requires 9.10+ I believe) but perhaps can be coaxed into functioning on 8.04, or Azilink tunneling which I've had success with in the past, but doesn't register on the Gnome Network Manager as an interface.

---

### Post by N00b-un-2 on 2012-10-28
looks like trying to enable usb tethering in the kernel is a dead end, but Azilink does work just fine following this tutorial

[http://www.humans-enabled.com/2011_08_01_archive.html]("http://www.humans-enabled.com/2011_08_01_archive.html")

---

