---
title: "Sony VAIO nvidia 310m HDMI fails"
date: 2010-12-29
forum: Multimedia Software
---

### Post by belfasttim on 2010-12-29
Hi-- I have a Sony VAIO VPCF11PFX/H with an Nvidia 310m onboard.
It's set up to dual boot into Windows7 and Ubuntu 10.04. I prefer to use Ubuntu for all work stuff since it's just faster. However, I need to use an external montitor to be effective-- and the laptop has only a single video out, an HDMI.

The HDMI works flawlessly on the Windows side-- but I can't get any monitor to detect any HDMI signal coming out of the machine under Ubuntu-- not when I use an HDMI to DVI adapter, or straight from HDMI to several different HDMI enabled monitors and tvs.

The Nvidia setup utility doesn't seem to have any idea that the HDMI exists either.

Can anyone help? I had quite a bit of trouble getting this setup to work under Ubuntu at all, so I'd hate to abandon the Ubuntu side and do my work on windows just because of the HDMI issue.

Thanks

---

### Post by belfasttim on 2010-12-31
bump?

I've found dozens of threads detailing sound not working over HDMI-- I just need video, I'm not worried about the sound, and I can't get the video to work. Any hints?

Thanks

---

### Post by lidex on 2010-12-31
What driver are you using? Can you post this output please:
```
sudo lshw -C display
```

---

### Post by belfasttim on 2011-01-01
hi lidex-- thanks for the help. Here's the output:

```

  *-display               
       description: VGA compatible controller
       product: GT218 [GeForce 310M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:e2000000-e2ffffff memory:d0000000-dfffffff(prefetchable) memory:e0000000-e1ffffff(prefetchable) ioport:d000(size=128) memory:e3000000-e307ffff(prefetchable)

```

---

### Post by lidex on 2011-01-04
Which version of the nvidia driver are you using? Go to 'Applications>Administration>Additional Drivers'. You'll probably want the latest, probably 256.xx and you may need to boot up with the monitor attached and turned on. A good thread for you: [http://ubuntuforums.org/showthread.php?t=1392766](http://ubuntuforums.org/showthread.php?t=1392766)

---

### Post by belfasttim on 2011-01-04
Thanks for the link lidex-- I am currently running Nvidia driver version 256.53-- however, there's a new 260.xx version on their website. I guess I'll give it a shot.

Thanks again for you help.

---

### Post by belfasttim on 2011-01-28
I'm up to the latest versions of the Nvidia driver and Ubuntu 10.10. . . still nothing from the HDMI output on this Sony.

Unfortunately I've had to switch to the Win7 partition so I can be more productive. . .

If anyone has any clues on how to get this HDMI out working, please let me know-- it's ridiculous to be working on a Ubuntu VM within a Win7 partition simply so I can enjoy a decent monitor!

Thanks

---

### Post by belfasttim on 2011-09-29
Still no love from this HDMI port!

I am now running Ubuntu 11.04 64bit, latest kernel updates.

NVIDIA driver version is NVIDIA-Linux-x86_64-280.13

Laptop is a Sony VAIO VPC F11

External monitor is Samsung SyncMaster P2770

No signal, and disper and the nvidia utility both fail to detect the connected monitor-- even though windows finds it with no problem.

You can get some stackoverflow karma if you help here-- [http://askubuntu.com/questions/29557/hdmi-port-not-recognized-on-sony-vaio](http://askubuntu.com/questions/29557/hdmi-port-not-recognized-on-sony-vaio)

---

### Post by xmastree on 2012-10-14
Did you get anywhere with this?
I have a Vaio vpcej3t1e_b and am running 12.04. Neither the vga port or the hdmi port seem to be enabled. I just had to reboot to Win 7 to use one of them.

---

