---
title: "infamous x lockup"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by RAKninja on 2007-10-31
been some time since my last post (yes i finally found out how to blacklist my intel gfx chip)

but i seem to have fallen victim to the infamous  "X locks up on GLX applications, but mouse still moves (momentarily)

i've tried all the common fixes (adding the noapic option to grub, adding NVagp "0" option to xorg, among others)

but still the problem remains.  it's a little different for each application also-
  -Alien Arena will suffer the same way Planetside does through wine, 10-30 second hang with sound continuing to play for about 3-5 seconds.  resumes with no problem.
  -certain screensavers (from the default installation) will lock the system up (hypertorus for one)  requires a hard reboot
  -globulation2 in glx mode will have strange things happen to every onscreen element in addition to the freeze/hang

I am getting log messages such as -
 kernel: [ 1444.763108] NVRM: Xid (0001:04): 8, Channel 00000000
 kernel: [ 1444.764321] NVRM: Xid (0001:04): 30,  L0 -> L0

I'm running a P4 2.0GHz with a Nvidia 6200 (pci)  my mobo is an intel 845 series (g model i think)  2GB RAM

to seperate myself from the other sufferers of this - i have no AGP port (there is a slot where you'd expect one, but the OEM neglected to put it on there)

any more info is available by request.

---

### Post by RAKninja on 2007-10-31
no ideas yet?

---

### Post by RAKninja on 2007-10-31
oh well, you guys coulent help me with the intel blacklisting thing (a simple fix) i wonder why i even bothered trying to get help with something as complex as this.

---

### Post by taurustiger23 on 2007-11-01
Same exact issue here.  Switching from nvidia-glx-new to nvidia-glx makes the crashes happen less frequently, but it's still happening at least once or twice a day.  

I'm going to try out the new nvidia-kernel-100.14.19 later today, and if that doesn't work, I'm going to install Fedora 8 to see if it is affected.

This problem is driving me crazy!  I've never had a Linux system that was unstable, an it is simply unacceptable.:confused:

---

### Post by RAKninja on 2007-11-19
too early to tell, but doing a fresh install of gutsy with the card removed, and then installing the card seems to have either cured the problem, or made it so that it happens very infrequently.

---

