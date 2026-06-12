---
title: "PulseAudio cuts out after a couple minutes using Presonus Audiobox USB"
date: 2013-10-20
forum: Multimedia Software
---

### Post by lwestfall on 2013-10-20
Hello all,

I just got back into the linux world and I'm trying to get my sound to work. Right now, if I play music it will go for a few minutes and then will stop. If I go into PulseAudio Volume control and switch from analog output to digital/SPDIF output, the audio comes right back in where it left off for another couple of minutes and then stop again. If I switch back to analog output it again comes back on. There doesn't seem to be a consistent period to these cycles and it get's really annoying having to switch all the time!

Also, I've tried getting rid of pulseaudio and just using ALSA but it doesn't work at all. Alsamixer also has no controls for my USB sound device.

Any suggestions? Thanks!

---

### Post by lwestfall on 2013-10-22
Update!

I configured pulse to be verbose. Checked my syslog to see what pulseaudio was reporting at the exact time the sound cuts out. Here it is:

> 
Oct 22 23:10:36 luke-ubuntu kernel: [195576.458372] cannot submit urb (err = -18)
Oct 22 23:10:36 luke-ubuntu kernel: [195576.459283] delay: estimated 177, actual 1
Oct 22 23:10:36 luke-ubuntu kernel: [195576.459302] cannot submit urb (err = -18)


This is the only thing it reports at the time when the audio cuts out. I've confirmed that it happens consistently every time.

[I found a commit with a fix.]("https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=e1944017839d7dfbf7329fac4bdec8b4050edf5e") Apparently it's caused by underruns (not sure what that means). Can anyone point me to a guide where I can apply this fix myself? I'm running kernel 3.11.0-12 if that helps at all.

Thanks!

[B]EDIT:
[/B]
I think I've solved my issue. I ended up compiling and installing the latest kernel version (3.12.0-rc6) and it already had the above patch applied. So if anyone has the same issue as me, try updating your kernel.

---

