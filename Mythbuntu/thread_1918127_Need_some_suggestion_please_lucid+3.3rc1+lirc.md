---
title: "Need some suggestion please lucid+3.3rc1+lirc"
date: 2012-01-31
forum: Mythbuntu
---

### Post by rodercot on 2012-01-31
Hey All,

 I have a test machine with a fresh lucid installed and I upgraded the kernel to 3.3rc1 to try and get the suspend/resume issues fixed but it made lirc stop working. 

 So I know with the new kernel that my imon (ffdc) using the ir in the lcd from an mce remote get loaded into the kernel. So I rmmod the lirc_imon driver and change lirc setup to /dev/input 7 I believe. but I get nothing on irw. lirc is the std version that ships with lucid so it may need 0.9 to work with the new kernel. 

 I have tried getting the ir-keytable and setting that up as well still no luck ir-keytable -t does not register any keypresses on the remote. 

 Finally I have to use /dev/input with lirc as the .86 version does not see /dev/input/by-id for my device when using dpkg-reconfigure.

 Is there any way to get 0.90 lirc onto Lucid other than compiling from source. 

 Thanks,

 Dave

---

### Post by rodercot on 2012-01-31
ok, removed the daily kernel I was testing and installed 3.3rc2 from the mainline (debs). I purged everything lirc, ir-keytable etc... did a clean install of lirc, ir-keytable. compiled and made lirc 0.9.0.

 1. ir-keytable sees the imon vfd
 2. lirc 0.8.6 is set to /dev/input and /dev/input/by-id
 3. All modules are loaded (kernel modules)
 4. mythbuntu-lirc-generator ran and removed the doubles from lircrc
 5. copied a fresh lircd.conf/devinput to /etc/lirc from the 0.9.0 source
 6. load modules "false" in hardware.conf

 No response on irw no response on ir-keytable -t
 (but the power button from the same remote will wake the machine from suspend)

 the stop lirc 0.8.6 goto the .0.9.0 build directory load up a no daemon lircd test pid - it opens /var/lirc/lircd no problems

 sudo irw in another terminal and see that lirc registers the client and initializes the device. still no response from irw. 

 so I suspend the machine and take a break come back and resume the machine  and it works on the 0.8.6 on /dev/input. 

 I am complety baffled by this and afraid to reboot the machine. I am not even sure where to look, if I reboot and it is not working but then I suspend and resume and it started working; WTF, where do I start looking for that problem.

 EDIT - Yes! that is exactly what is happening. lirc will not respond after a system reboot but does respond after the first suspend/resume.

 Regards,

 Dave

---

### Post by rodercot on 2012-02-03
All fixed it was a bug that jarod had already created a patch for and is upstream for placement into the 3.3 kernel. if you are running the 3.3rc2 kernel then I created a new imon.ko driver and you can use that it is on the link below. I created the file against the 3.3rc2 kernel modules. here is the link to the bug and and how I fixed it

[https://bugs.launchpad.net/ubuntu/+s...524/comments/7](https://bugs.launchpad.net/ubuntu/+s...524/comments/7)

rgds,

Dave

---

