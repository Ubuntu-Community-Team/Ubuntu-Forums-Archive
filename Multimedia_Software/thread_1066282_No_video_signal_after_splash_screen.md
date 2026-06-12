---
title: "No video signal after splash screen"
date: 2009-02-10
forum: Multimedia Software
---

### Post by JamesFMC on 2009-02-10
I don't know if this is a unique problem or not, but I am experiencing it with Ubuntu, Xubuntu and Ubuntu for eeePC with Remix.

I have the installs on different CF cards and am using a daughter board with an Atom processor (this has the 945GSE Chipset). When run on a vendors motherboard, any distro of Ubuntu boots up fine. When I transfer it to a production board for testing, I get as far as the splash screen and status bar before the screen goes blank.

We tested the video signal (LVDS) and it loses its signal completely, so it's not sending a black color to the monitor.

I should mention that on the vendor boards, we are displaying in VGA.

I've tried downloading and installing the xf86-video-intel-2.6.0.tar, but either I didn't do it correctly or some of the dependencies were not stable because now I can only access one of my builds via command line. I lost all GUI on it.

Any ideas or suggestions would be very helpful.

---

### Post by redroad55 on 2009-02-10
first look at this :[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")
my thoughts are that the graphics that are used when booting are different than what you end up with after booting .. There is a hand off to the user account (user profile defaults etc.)..Take a look at this .. run :
```
man xorg.conf
``` 

this will show you the inner workings I'm talking about as well as commands to get the result your seeking ..Hope this helps ..Post back with any results and or questions  .. Best to you

In other words the hand off can't be made because the profile no longer exists on the other hardware

---

### Post by redroad55 on 2009-02-10
Another thought you might be able to trick it by running live cd (no install) choose appropriate resolution then install..Just a thought..best to you

---

### Post by JamesFMC on 2009-02-11
I've tried running from Live CD before with no luck. I can get PCLinux and Fedora to run, just not Ubuntu.

---

### Post by redroad55 on 2009-02-11
yes the point I'm making is in Ubuntu  KDM(kde desktop) and GDM (Gnome desktop) in there startup scripts they are different than the operating systems you mentioned, uniquely ubuntu that's the problem ..Sorry I couldn't be more help..Best to you

---

### Post by JamesFMC on 2009-02-11
I was able to get this resolved and it ended up being more of hardware issue than a Ubuntu issue, although it Ubuntu did affect it...somewhat.

Two embbeded modules we received have Chrontel chip that the 945 Chipset passes the video signal to. The Chrontel chip is supposed to then send signal to LVDS, but it doesn't. We were able to get a board with a Chrontel chip and Ubuntu booted up just fine.

I then downloaded and installed Jaunty Alpha 4, since this release is supposed to force the OS to prode for SDVO. I tried to run this from a board with Chrontel chip and was able to boot in to just fine.

Hopefully if someone else runs into this issue, you can pass along this information.

Thanks for your help.

---

