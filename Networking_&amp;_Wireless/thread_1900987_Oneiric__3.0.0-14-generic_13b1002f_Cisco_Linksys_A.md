---
title: "Oneiric  3.0.0-14-generic 13b1:002f Cisco Linksys AE1000 v1 802.11n / rt3572"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by ghat on 2011-12-27
hi

Anyone got this one running in kernel 3.X / Oneiric ?

XBMC Eden is comming soon, and I was bootstapping the new OS on my media server and the RAlink 2.4.0.2 drivers wont compile... 

G

---

### Post by ghat on 2011-12-28
What I have done until now... 

1. compiled the latest stable kernel 3.1.6, using the ubuntu upstream instructions
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)
Instead of using the git-kernel I used the latest stable tarball..
2. enabled the the experimental rt3572 support in the kernels rt28xx.ko
This is in the make menuconfig step of (1)
3. wireless works but has some problems...
basically, (/etc/init.d/networking restart) lost the connection and was throuwing errors at random..
I googled, and read on some forum that the firmware is the issue... so I searched for various versions of the firmware..
4. replaced the rt2870.bin in the /lib/firmware/ with the one found in the latest driver package 2011*v2.5.0.0* 

here is a bunch of md5sums from the various firmwares I have found... 
not sure which works/is stable.. 
```

d8a2bdd274ad86f60fe8643b4574387e  /lib/firmware/rt2870.bin
36c944c3138125605d28c0a3a1338be9  /lib/firmware/rt2870.bin-bck
2bb89af3a7d446deb4695c9a3daa7f9d  /lib/firmware/rt2870.bin-v22
4613706159f1b75b9e6c040c19e09388  /lib/firmware/rt2870.bin-v2402
d8a2bdd274ad86f60fe8643b4574387e  /lib/firmware/rt2870.bin-v2500

```Lets see how this goes, but the system seems to boot up fine with the usb-stick wifi up
at boot. 

G
> 
AND
you need this...
[http://codeghar.wordpress.com/2011/07/18/debian-running-etcinit-dnetworking-restart-is-deprecated-because-it-may-not-enable-again-some-interfaces/](http://codeghar.wordpress.com/2011/07/18/debian-running-etcinit-dnetworking-restart-is-deprecated-because-it-may-not-enable-again-some-interfaces/)

```

alias netrestart="sudo nohup sh -c 'stop networking; date; echo sleeping; sleep 2; echo waking; date; start networking'"

```

---

