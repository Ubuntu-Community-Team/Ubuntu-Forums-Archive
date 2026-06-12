---
title: "Radeon X1300, ATI 8.40.4, AMD64 and Gutsy"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by Thangalin on 2007-10-18
Hi,

After several hours of searching, reading, searching, trying, and failing, I seek your help.

Here's what I have:

$  lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (prog-if 00 [VGA])
01:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)

$ xdpyinfo | grep resolution; xdpyinfo | grep dimensions
  resolution:    96x96 dots per inch
  dimensions:    1600x1200 pixels (423x318 millimeters)

$ cat /etc/default/linux-restricted-modules-common | grep ^DISABLED
DISABLED_MODULES="fglrx"

$ lsmod | grep fglrx
fglrx                 855428  0

$ ls -laR /lib | grep fglrx
drwxr-xr-x  2 root root 152 2007-04-17 20:54 fglrx
/lib/linux-restricted-modules/2.6.20-15-generic/fglrx:
-rw-r--r--  1 root root  29216 2007-04-13 09:51 fglrx.mod.o
-rw-r--r--  1 root root 942240 2007-04-13 09:52 libfglrx_ip.a.GCC4
drwxr-xr-x  2 root root 152 2007-10-17 19:12 fglrx
/lib/linux-restricted-modules/2.6.22-14-generic/fglrx:
-rw-r--r--  1 root root   30248 2007-10-15 08:35 fglrx.mod.o
-rw-r--r--  1 root root 1111872 2007-10-15 08:36 libfglrx_ip.a.GCC4
-rw-r--r-- 1 root root 1801083 2007-10-17 20:28 fglrx.ko

Monitor: ViewSonic VX2000
CPU: AMD 64
ATI Driver: ati-driver-installer-8.40.4-x86.x86_64.run

I did install the fglrx drivers (an older version) on the same machine using Kubuntu 7.04 (32 bit). That worked fine.

Here is what I have done now:

1. Installed a fresh copy of Kubuntu 7.04 (64 bit) on a new harddrive.
2. Upgraded Kubuntu 7.04 to Kubuntu 7.10.
3. Installed the xorg-fglrx driver the Ubuntu-way.
4. Uninstalled the driver (because it did not work).
5. Installed the fglrx driver manually.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) (doesn't support X1300?)

When I reboot (or restart X) using the fglrx module, I get a blank screen.

The logs show that everything seems fine.

I have attached the kernel log, the Xorg log, and my xorg.conf file that does not work (swap "vesa" for "fglrx" and it works, but does not use fglrx, of course).

I do have this working on another harddrive using Kubuntu 7.04 32-bit. I would really like to use 64-bit Kubuntu, but it looks like it may not be possible.

I look forward to any insightful comments and help!

---

### Post by JoePits on 2007-10-18
try 

Other known bugs
Blank screen with some ATI hardware

    *

      People with ATI display adapters may get a blank screen when loading X due to the driver being unable to initialize certain hardware. Upstream is working on it, and hopefully we'll be able to release an update for 7.10 soon after the release. In the meantime, add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf. Bug #132716


this is in the 7.10 release notes

[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

---

### Post by Thangalin on 2007-10-18
Hi, Joe.

Thanks for the search tips.

I added the LVDSBiosNativeMode option to the Device section for the fglrx driver. The screen remains blank. (There is no "driver" section in my xorg.conf file?)

Perhaps I'll just have to wait for the next release.

Thanks, Joe.

---

### Post by BlackTigerIII on 2007-10-18
> **Thangalin said:**
> Hi, Joe.

Thanks for the search tips.

I added the LVDSBiosNativeMode option to the Device section for the fglrx driver. The screen remains blank. (There is no "driver" section in my xorg.conf file?)

Perhaps I'll just have to wait for the next release.

Thanks, Joe.


Ok
First i'm sorry but my english suck xPPP
Anyway
I had the same problem, so i tried this solution, and it works.
I write this option on Device section after BusID.
NOTE: This only work after I revert to the xorg driver by executing sudo dpkg-reconfigure xserver-xorg
and select fglrx driver 


I hope it works with you too

---

### Post by LinuxNewb_22 on 2007-10-18
> **Thangalin said:**
> Hi, Joe.

Thanks for the search tips.

I added the LVDSBiosNativeMode option to the Device section for the fglrx driver. The screen remains blank. (There is no "driver" section in my xorg.conf file?)

Perhaps I'll just have to wait for the next release.

Thanks, Joe.

Just a suggestion but do you think it would work if you added a driver section...?
e.g.
Section "driver"
Option "LVDSBiosNativeMode" "false"
EndSection


Also, instead of upgrading, have you tried doing a fresh install with the alternate iso?

---

### Post by Thangalin on 2007-10-18
> **LinuxNewb_22 said:**
> Just a suggestion but do you think it would work if you added a driver section...?

No ... I'm fairly certain it belongs to the "Device" section, right below the BusID.

> Also, instead of upgrading, have you tried doing a fresh install with the alternate iso?

When I installed Kubuntu 7.04 (64-bit), it was as fresh as fresh can be. New harddrive, new R/W DVD drive, straight from DVDs purchased (yes!) online from the Linux Store.

No luck. Thanks anyway. :-)

---

### Post by dragon1711 on 2007-10-19
same problem, even more : blank screen after enabling restricted drivers... I think ati m200 and x1100 - x1400 are being used in A LOT of computers  (most of notebooks and desktops within $1000, so if these problems will not be cleared in the near future, we may not see ubuntu on a distrowatch.com even ranked :(

---

### Post by amanz on 2007-10-23
I am having the same Black Screen problem. I have upgraded form 7.04 to 7.10. I have AMD Athlon 64-bit processor. First it started normally but when I installed the driver for my ATI Radeon X1300, it did not stat the X and shows the black screen. I have tried the above solution but it did not works.

---

### Post by xluryan on 2007-10-26
I have an ATI Radeon Mobility 7500. I had the "blank screen" issue after upgrading from 7.04 to 7.10. Here is what I did to fix it:

Boot up into recovery mode and type in the root password when it asks. Then add this option line in your /etc/X11/xorg.conf:

```

Section "Device"
  Identifier  "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
  Driver    "ati"
  BusID   "PCI:1:0:0"
  Option "LVDSBiosNativeMode" "false"
EndSection

```

The Identifier will be whatever your card is. I'm not sure what your Driver will be; most likely "ati", like mine. Keep the BusID the same, just add the option line at the end.

Save the file and then issue the reboot command.

---

