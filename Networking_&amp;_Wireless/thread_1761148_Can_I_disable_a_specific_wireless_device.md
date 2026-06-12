---
title: "Can I disable a specific wireless device?"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by residualbit on 2011-05-17
11.04 64 bit

Hey guys,

I just picked up a new high-gain usb wireless adapter that I would like to use for a while in place of the built in wireless adapter in my desktop. It is detected and works just fine. My question is this: Is there any way I can disable just the built in adapter and leave the new one active (or visa versa?) I don't want to remove the built-in one as there will be occasions that I will want to use both. Ideas?

Thanks.

---

### Post by residualbit on 2011-05-20
nothing?

they are both detected and working properly.

wlan0 and wlan1

I just need the ability to disable one or the other.

---

### Post by residualbit on 2011-05-28
still nothing?

---

### Post by dhave-dhave on 2011-05-28
Is this thread helpful?

[http://ubuntuforums.org/showthread.php?t=1663711](http://ubuntuforums.org/showthread.php?t=1663711)

When I started using an external USB wifi adapter, I just went into BIOS settings and turned off the built-in wifi adapter. But it sounds as if there are several ways to skin this cat.

---

### Post by residualbit on 2011-05-29
There are some solutions in that thread, but not really what i was looking for.

I will need to occasionally use both, or switch back and forth on the fly while is session, so physically unplugging the built-in device or disabling in in the bios wouldn't be the most effective solutions. Also, the if config down option only works temporarily and not at all if you have connections setup to auto connect (it just ends the session and immediately starts a new one)

I hate being this guy, but in Windows, enable/disabling is as simple as right clicking the device and selecting enable/disable.

---

### Post by dhave-dhave on 2011-05-29
> **nkirk1 said:**
> 
I hate being this guy, but in Windows, enable/disabling is as simple as right clicking the device and selecting enable/disable.

Yeah, I hear you. I'm not sure, but I think this might be one shortcoming of Linux's shared ancestry with Unix, and the principle that, in Unix, [_[COLOR="Blue"]everything is a file[/COLOR]_](http://ph7spot.com/musings/in-unix-everything-is-a-file).

Still, I'd be surprised if there's not a way in Ubuntu at least to approximate the Windows "enable/disable device" function.

---

### Post by residualbit on 2011-05-29
I've done some more digging on this with no luck. I've seen some threads stating to blacklist the driver, which I can't do because both adapters use the same one.

I know I won't find any sort of check box option, but I'd be content with changing a few lines in a file somewhere. Like, commenting out the built-in card when I don't want to use it.

There has to be something (I'm still optimistic at this point at least.) any other ideas anyone?

---

