---
title: "Dell mini 10 hdmi output"
date: 2011-08-06
forum: Multimedia Software
---

### Post by SharpTJ on 2011-08-06
I have a Dell mini 10 netbook that I am trying to set up as a temporary HTPC.  Using XP, I can send the video and audio over the HDMI connection, but when I attempt to do so from Ubuntu, there is not an option for a different monitor.  I am new to Ubuntu so hopefully you can point me in the right direction.

---

### Post by BicyclerBoy on 2011-08-06
I guess your video h/w is the crappy intel chipset 845 GMA900/950.

You likely need to be using the intel driver i915 to get any usable performance.
And I would suggest you would need the xorg-edgers ppa version.

The intel driver has had some major HDMI & displayport bugs recently so don't hold your breath.

What do you get from
xdpyinfo | head
xrandr -q
driconf
glxinfo

---

### Post by SharpTJ on 2011-08-09
> **BicyclerBoy said:**
> I guess your video h/w is the crappy intel chipset 845 GMA900/950.

You likely need to be using the intel driver i915 to get any usable performance.
And I would suggest you would need the xorg-edgers ppa version.

The intel driver has had some major HDMI & displayport bugs recently so don't hold your breath.

What do you get from
xdpyinfo | head
xrandr -q
driconf
glxinfo


Where can I get the i915 drive from?  I'm not sure what
> xdpyinfo | head
xrandr -q
driconf
glxinfo
means...I'm new to Linux in general

---

### Post by BicyclerBoy on 2011-08-09
Just use windows for HTPC, you probably have paid for it..
Set the machine to dual boot...XP needs to be on the primary partition.

Ubuntu 11.04 Unity is fabulous on a netbook but that is a long way from making a HTPC work well (especially with intel & HDMI)..

---

