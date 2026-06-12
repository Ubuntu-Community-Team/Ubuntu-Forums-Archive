---
title: "Do graphical effects work on netbooks?"
date: 2011-05-07
forum: Multimedia Software
---

### Post by palzhanov on 2011-05-07
HI
I have Samsung NP145 with intel atom n450
And this is what terminal says:
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller

Do graphical effects work on my netbook?

---

### Post by BicyclerBoy on 2011-05-07
This is my take on the situation...

Your system has integrated CPU-GPU (atom n450)
The GPU core is GMA3150, this is same as GMA3000 & same family as GMA950/945...all disappointing.
The i915 driver is required for all these.

My netbook uses atom 330 & GMA950 945GME (power hungry) .. this manages unity 3d okay but only after updating the video driver (i915) ppa.

With 10.10 netbook & natty 11.04, I needed to use xorg-edgers ppa to get any graphics performance.
The std 10.10 netbook i915 & natty i915/x-server did not work. 

The desktop usability/performance (Unity 3d) on an atom netbook is really good...YMMV

Run in a terminal (<ctrl>+<alt>+<t>)
lsmod
search for i915

lsmod | grep i915

---

### Post by palzhanov on 2011-05-08
Thanks

This is what terminal says
@Samsung:~$ lsmod | grep i915
i915                  290938  3 
drm_kms_helper         30200  1 i915
drm                   168054  4 i915,drm_kms_helper
intel_agp              26360  2 i915
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
@Samsung:~$ 

It seem there is i915 isn`t it?

"I new to Ubuntu It is being hard but interesting"

---

### Post by BicyclerBoy on 2011-05-08
Yes but...the i915 driver (whole xorg intel driver packages) that installed with natty did not work for my netbook..

If you add the xorg-edgers ppa & update the xorg drivers your netbook may come to live & allow unity 3d desktop.

 The way to determine the X server that is running your GUI X is by looking into the file:
/var/log/Xorg.0.log
or the std output from
dmesg

Prepare to be scrolling thru' a lot of 'stuff'

---

### Post by palzhanov on 2011-05-08
HI again
I have installed Compiz now there are effects
like 3d box, wombly window

Sth what is unity 3d desktop??(stupidly...)

---

### Post by BicyclerBoy on 2011-05-08
Maybe you can try out the other desktops to see if you are using Unity..
I did not install compiz..
AFAIK Unity uses parts of compiz..

When you login to ubuntu (if you have login screen set ON) you get to choose 
ubuntu
failsafe
netbook2d
something-else-i-can't-remember
ditto

(You can log out of your desktop to get the login screen...)
Select the user & then can choose the desktop...

You might not be using "Ubuntu" ...this is the unity 3d default desktop for natty desktop & netbook combined..

Maybe the latest natty xorg-intel-i915 drivers work now ??

---

