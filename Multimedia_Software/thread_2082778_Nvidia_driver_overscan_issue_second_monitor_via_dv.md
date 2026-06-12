---
title: "Nvidia driver overscan issue second monitor via dvi-d cable"
date: 2012-11-10
forum: Multimedia Software
---

### Post by benmichael on 2012-11-10
Ok, I know that I have a bit of a bizarre setup, but here goes.

I have an old laptop, HP Pavilion 6000. The graphics card in there is a GeForce 7150M. The monitor connection is an old 18pin.

The external monitor I use is a Samsung SyncMaster 2333. Don't ask me why, but this monitor only has a dvi-d connection (yes, i have searched it).

So I have the monitor plugged into the laptop.

If I use any of the Nvidia propriety drivers and try to set the resolution up to 1920x1080 (the monitor's native resolution), I get a massive overscan issue.

Over the years I have tried to get this to work, tinkering with my xorg.conf to death. I have also tried this on every Ubuntu since 10.04, on all the corresponding LUbuntus, and on all the Linux Mints since Lisa. Exact same issue. I have even tried it in WinDoze and it works perfectly there (although I did get the error once, but was unable to reproduce it).

Using the Open Source drivers it works perfectly iff I switch off the laptop monitor (this makes no difference with the Nvidia drivers).

I would have happily gone on using the Open Source drivers, except that since upgrading to LUbuntu 12.10, the Open Source drivers make my monitor completely hazy and have the same overscan issue until I (through the haze, only because I know where things are) go to the monitor settings, activate the laptop's monitor, then deactivate it, and suddenly it comes right. I have to do this every time. So I have to find a way to fix one of them, so I may as well tackle the propriety drivers, hence this overlong question.

Amidst other things, I have tried the nvidia-settings, but because it is connected to an 18pin, it detects the monitor as a vga monitor and does not give me overscan correction options. I have tried custom modlines (although there are always more of those try), I have tried using xrandr, and I have tried all the FlatPanelOptions.

What I have not tried is a Gentoo build, as I don't have time any more to do that installation, but up to about three years ago when I ran Gentoo exclusively I did not have this issue.

Below is an link to an image with a red highlight around the portion of the screen visible to me, the numbers around it are the number of pixels which are cut off. This does seem to drift a few pixels every now and then.

Thanks in advance.

[Nvidia driver issue image]("http://goo.gl/d2lSO")

---

