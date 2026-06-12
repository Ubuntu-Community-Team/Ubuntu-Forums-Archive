---
title: "KWorld USB2800R TV Tuner Box"
date: 2008-11-03
forum: Multimedia Software
---

### Post by billstei on 2008-11-03
Finally got my KWorld USB2800R TV Tuner box working (in Intrepid) and since there does not seem to be a lot of info in the Ubuntu forums about this particular model, here is what I did... the device is not recognized directly by the em28xx driver so in the /etc/modprobe.d/options file I added the following line:

options em28xx card=3 tuner=61


Hope that helps someone.

Bill

---

### Post by billstei on 2010-06-09
Not sure why:

options em28xx card=3 tuner=61

was not working in Lucid up until now (6-9-2010), but it's working (again).  Also not sure why the driver disk that came with this TV box says "KWorld PVR-TV 2800", which should be card=12, but 12 does not work, and results in the TV video input source being not available (audio works).

---

### Post by billstei on 2010-07-12
Now I know why it suddenly started working...

In the process of trying to get it working I tried card=12, and that (for whatever reason) got sound working.  Then when I tried card=3 tuner=61, the sound was still working from the card=12 trial.  As long as the external tuner box is kept powered via USB, audio will continue to work.  If audio does stop, the following worked from a terminal to restore it (and assumes that card=3 tuner=61 was already used at boot-up):

sudo rmmod em28xx
sudo modprobe em28xx card=12
sudo rmmod em28xx
sudo modprobe em28xx card=3


P.S. Also renamed /etc/modprode.d/options to options.conf per the modprobe complaining that all these config files must have a .conf extension.

---

