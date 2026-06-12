---
title: "Need Help with Installation - no video"
date: 2007-12-01
forum: Mythbuntu
---

### Post by ahood on 2007-12-01
Hi All,

I need some help badly...

I am installing Mythbuntu on a system with the following specs...

System Specifications
> 
Motherboard: Foxconn 6100K8M. 
CPU: AMD Athlon 3200 (socket 754)
RAM: 1 Gb
Video: nvidia GeForce 6100 (onboard)
Hard Drive: 500 Gb (Samsung)
Networking: Netgear 311GT (wireless)
TV Tuners: PVR-350 and PVR-500


We are able to launch the Mythbuntu Live CD and go through the configuration steps. The installation from the live CD seems to go well. We don't configure MythTV during the initial installation. Then, it comes to reboot.

We reboot and there is a black screen. Nothing else and no activity from the hard disk.

We have tried using a Nvidia 8600GS PCIx16e video, but the system hangs on that one too.

We think there must be a compatibility problem somewhere, but we have no clue.

Could the problem be with the TV Tuner cards?
We have them in PCI slots right next to each other.

Could the problem be with the three hard drives?
We have two connected as master and slave. The third is a slave to the DVD ROM (master).

The above also happens with KnoppMyth.

What else could be the problem?

The only other symptom I have is that when we boot up, a WinFast logo is supposed to appear; however, all we see are thick red lines down the screen and no WinFast text. What would this indicate?

Any help or suggestion will be greatly appreciated.

Al

---

### Post by ahood on 2007-12-02
Could this be a BIOS problem?

Al

---

### Post by ntetreau on 2007-12-02
> **ahood said:**
> Could this be a BIOS problem?

Al

When you say you get a blank screen or the computer hangs, is this right from the start or do you see lot's of disk activity as if the computer was booting up but you don't see an image?

Do you get any error message?

Well, you could try first to boot up using the "vesa" universal video drivers which have a good chance of booting up fine,  

To do this, press ESC when the bootloader, grub, shows up.  Then choose to boot the "recovery mode kernel".  If you get dumped at a terminal, that's fine.  Now let's try to change the video driver to vesa.

```
 sudo nano /etc/X11/xorg.conf

```

go down to the Section "Device" and change the driver to "vesa" with the quotes.  Use Ctrl-x to save, then to start X:

```
exit 
```

If the systems then shows up, you definitely have a video problem, which shouldn't be too hard to fix!

---

### Post by ahood on 2007-12-06
Thanks, I will try this...

---

### Post by ahood on 2007-12-12
This issue was solved...See [http://ubuntuforums.org/showthread.php?t=635943](http://ubuntuforums.org/showthread.php?t=635943)

---

