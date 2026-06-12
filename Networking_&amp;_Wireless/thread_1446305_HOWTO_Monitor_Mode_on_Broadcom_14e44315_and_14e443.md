---
title: "HOWTO: Monitor Mode on Broadcom 14e4:4315 and 14e4:432* Wireless Cards"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by chenxiaolong on 2010-04-03
First of all, this tutorial will use NDISWRAPPER, not b43, not wl (Broadcom STA). So, hooray for new method (actually, the only method :D). Now, I don't want anyone to get scared because of bad experiences with Ndiswrapper or whatever, it's actually quite easy. I did not come up with any of this info. I'm just putting this guide together from Kacper Szczesniak's info (who came up with this method), WifiDocsDriverbcm43xxFeisty_No-Fluff from the Ubuntu Wiki, and my experience.

The Broadcom STA (wl) driver has references to monitor mode in it's code, but does not have that functionality in reality. The Broadcom Windows driver on the other hand does have this capability. So, for monitor mode to work, you will need a patched version of ndiswrapper.

[COLOR="Red"][SIZE="4"]Pre-everything stuff[/SIZE][/COLOR]
----------------------

1) Install the Linux kernel headers:

```
sudo apt-get install linux-headers-$(uname -r)
```

2) Install the tools required to compile Ndiswrapper:

```
sudo apt-get install checkinstall dh-make fakeroot gcc build-essential
```

3) Unload current Ndiswrapper module, if running:

```
sudo rmmod ndiswrapper
```

4) Ummm...continue on:D!

[COLOR="Red"][SIZE="4"]Download and Patch Ndiswrapper[/SIZE][/COLOR]
-------------------------------

1) Download the Latest Ndiswrapper tarball by click the green download button at [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/) to a folder called "ndiswrapper" in your home directory. So, download to ~/ndiswrapper.

2) Change to ~/ndiswrapper in the Terminal:

```
cd ~/ndiswrapper
```

3) Extract the tarball:

```
tar zxvf ndiswrapper-1.*.tar.gz
```

4) Download "bcmmon.diff.zip" (attached to this post) to ~/ndiswrapper and unzip it to make "bcmmon.diff":

```
unzip bcmmon.diff.zip
```

5) This is the annoying part (for some people). If you the latest version of Ndiswrapper, when you downloaded, was 1.56, then continue to the next step. Otherwise, keep reading. If you downloaded a later version, you will need to open the "bcmmon.diff" in a text editor (Gedit -- Gnome, Kwrite -- KDE). DON'T LET ALL THAT TEXT SCARE YOU :D. Now, press <Ctrl> + F and find "1.56". Every time you find 1.56, change it to the version you downloaded.

6) Patch the sources:

```
patch -p1 < bcmmon.diff
```

7) Now, change to the ndiswrapper-1.* directory:

```
cd ndiswrapper-1.*
```

8) Now, run "make" to compile Ndiswrapper:

```
make
```

9) Remove existing Ndiswrapper, if installed:

```
sudo apt-get remove ndiswrapper-common
```

If you are running Linux Mint, the packages: [mint-meta-gnome mint-meta-x64 mintwifi] will be removed. This is okay. We will reinstall them later.

10) After compiling, run checkinstall to make a DEB package:

```
sudo checkinstall
```

For the description, I put:

> Patched ndiswrapper build to make monitor mode work on Broadcom cards.
For kernel: <your kernel>

I definitely suggest that you put your kernel version in the description because you will need to make a new DEB package every time your kernel gets upgraded (I.e. run "sudo apt-get remove ndiswrapper-common && sudo checkinstall" again).

For the name, use: "ndiswrapper-common2"

For "Provides: ," also use: "ndiswrapper-common"

11) Press Enter. Your new ndiswrapper package will be installed automatically.

If you are running Linux Mint, you can reinstall the packages: [mint-meta-gnome mint-meta-x64 mintwifi] now.

[COLOR="Red"][SIZE="4"]Download and Install Windows Driver[/SIZE][/COLOR]
-------------------------------------

1) Change back to "~/ndiswrapper" and create "~/ndiswrapper/windriver". Then change to "~/ndiswrapper/windriver":

```
cd ~/ndiswrapper
mkdir ~/ndiswrapper/windriver
cd ~/ndiswrapper/windriver
```

2) Download this file using a web browser (wget gives wierd file name) to "~/ndiswrapper/windriver":

> [http://myspamb8.googlepages.com/R174291-pruned.zip](http://myspamb8.googlepages.com/R174291-pruned.zip)

3) Unzip "R174291-pruned.zip":

```
unzip R174291-pruned.zip
```

4) Check if there were previous Windows WLAN drivers installed:

```
sudo /usr/sbin/ndiswrapper -l
```

If there are, remove it with:

```
sudo /usr/sbin/ndiswrapper -r <the driver>
```

5) Install the downloaded Dell Windows driver in Ndiswrapper:

```
sudo /usr/sbin/ndiswrapper -i bcmwl5.inf
```

6) Now, when you run "[COLOR="Blue"]sudo /usr/sbin/ndiswrapper -l[/COLOR]," you should get something similar to this:

> bcmwl5 : driver installed
        device (14E4:4315) present (alternate driver: wl)

7) Umm...continue on.

[COLOR="Red"][SIZE="4"]Ndiswrapper module stuff[/SIZE][/COLOR]
--------------------------

1) Refresh the list of modules to make sure that the ndiswrapper module is found:

```
sudo depmod
sudo depmod -a
```

2) To ensure that there are no conflicting drivers loaded on boot, add the following lines to "[COLOR="Blue"]/etc/modprobe.d/broadcom.conf[/COLOR]":

```
sudo < gedit OR kwrite > /etc/modprobe.d/broadcom.conf
```

Add:

> blacklist b43
blacklist b43legacy
blacklist bcm43xx
blacklist ssb
blacklist wl

3) Open "[COLOR="Blue"]/etc/modules[/COLOR]" and check to make sure that b43 / b43legacy / bcm43xx / ssb / wl aren't mentioned. Then, add "ndiswrapper" on a new line.

```
sudo < gedit OR kwrite > /etc/modules
```

4) REBOOT!!! OR to use ndiswrapper without rebooting, run:

```
sudo rmmod b43 b43legacy bcm43xx ssb wl
sudo modprobe ndiswrapper
```

5) Enjoy cracking your neighbor's wireless...I mean...I didn't say...anything :D.

-----------

Again, thanks to Kacper Szczesniak for his experience and his info at [http://seclists.org/fulldisclosure/2008/Nov/506](http://seclists.org/fulldisclosure/2008/Nov/506) and also to the Ubuntu Wiki for the Dell Windows XP Broadcom driver: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202e:%20R174291%20Driver%20Download/Extraction](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202e:%20R174291%20Driver%20Download/Extraction).

---

### Post by Alaric on 2010-04-03
Hey,

Sorry, I was pretty excited by this post.  Especially considering the amazing timing of the google search.  The patch isn't working for me though.  Running 10.04 beta btw, but that shouldn't affect the patch process.  Also, I'm using gcc4.4 instead of 3.4, which I could see making a difference.  

```

alaric@alaric-laptop:~/.opt/ndiswrapper-1.56$ patch -p1 < bcmmon.diff
patching file ndiswrapper-1.56_bcmmon/driver/iw_ndis.c
Hunk #1 FAILED at 29.
Hunk #2 FAILED at 176.
Hunk #3 FAILED at 205.
Hunk #4 FAILED at 302.
Hunk #5 FAILED at 316.
Hunk #6 FAILED at 1832.
Hunk #7 FAILED at 1935.
Hunk #8 FAILED at 1948.
8 out of 8 hunks FAILED -- saving rejects to file ndiswrapper-1.56_bcmmon/driver/iw_ndis.c.rej
patching file ndiswrapper-1.56_bcmmon/driver/iw_ndis.h
Hunk #1 FAILED at 194.
1 out of 1 hunk FAILED -- saving rejects to file ndiswrapper-1.56_bcmmon/driver/iw_ndis.h.rej
patching file ndiswrapper-1.56_bcmmon/driver/ndis.c
Hunk #1 FAILED at 30.
Hunk #2 FAILED at 56.
Hunk #3 FAILED at 89.
Hunk #4 FAILED at 102.
Hunk #5 FAILED at 154.
Hunk #6 FAILED at 201.
Hunk #7 FAILED at 2244.
Hunk #8 FAILED at 2259.
Hunk #9 FAILED at 2266.
9 out of 9 hunks FAILED -- saving rejects to file ndiswrapper-1.56_bcmmon/driver/ndis.c.rej

```

---

### Post by Alaric on 2010-04-03
Fail, Be sure to be in the directory outside of ndiswrapper-1.56, not inside of ndiswrapper-1.56.

---

### Post by Teratoma on 2010-05-04
Thanks for this guide. I did everything EXACTLY as you posted and it all worked, except...

The only problem I have now is that wlan0 had disappeared when I check ifconfig  :confused:

Any ideas?

---

### Post by chenxiaolong on 2010-05-04
Does wlan0 show up in "iwconfig"? If it does, then all you need to do, is to run "sudo ifconfig wlan0 up."

---

### Post by Teratoma on 2010-05-04
> **chenxiaolong said:**
> Does wlan0 show up in "iwconfig"? If it does, then all you need to do, is to run "sudo ifconfig wlan0 up."

Nope, not there. "no such device"

---

### Post by Teratoma on 2010-05-04
I did a reinstall of Ubuntu 10.04, followed the directions, and still no wlan0. Not even in iwconfig

---

### Post by chenxiaolong on 2010-05-04
Well, that's frustrating. My card shows up just fine.

EDIT: Oh yeah, does "sudo ndiswrapper -l" say "Hardware Present" (or something of the sort)? If not, you will need a new WinXP driver for ndiswrapper.

---

### Post by Teratoma on 2010-05-04
Yeah the card shows up there. Weirdest thing ever.

---

### Post by chenxiaolong on 2010-05-05
Hmmmm....mmmm....GAH!!!

The only thing I can suggest now is the most basic thing:

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
dmesg | grep "ndiswrapper" #<--Check for errors in dmesg

---

### Post by WildWillie on 2010-06-07
All I'm getting from any attempt to put the card (bcm4328) into monitor mode with any tool is either an explicit 

Ndiswrapper does not support monitor mode

message, or from iwconfig
```

$sudo iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
```

I followed the tut exactly and received no errors. No conflicting modules are running, all are blacklisted. What could it be?

---

### Post by The Low End Theory on 2010-06-11
im having the exact same problem, does anyone know how to fix this?

---

### Post by chenxiaolong on 2010-06-11
WildWillie: I'm pretty sure the "Ndiswrapper does not support monitor mode" error only happens when you run aircrack-ng. I'll take a look at the source code soon. Does it work for Kismet?

WildWillie, Mr. Popo: About this error: 

```
$sudo iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
```

Try running:

```
sudo ifconfig wlan0 down
```

first, then run:

```
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up
```

---

### Post by The Low End Theory on 2010-06-12
ive been doing that, it dosent help

---

### Post by elkanji on 2010-06-15
> **chenxiaolong said:**
> WildWillie: I'm pretty sure the "Ndiswrapper does not support monitor mode" error only happens when you run aircrack-ng. I'll take a look at the source code soon. Does it work for Kismet?

WildWillie, Mr. Popo: About this error: 

```
$sudo iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
```Try running:

```
sudo ifconfig wlan0 down
```first, then run:

```
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up
```

I have the exact same thing, 8B06. Can't use Monitor Mode for some reason.

My card is :4315, dude thanks for this tutorial, very interesting info!!! 

So yeah I wanna get aircrack going but can't at the moment ... 

anyway as soon as i run airodump-ng wlan0 it tells me Ndiswrapper doesn't support monitor mode. 

xD

---

### Post by The Low End Theory on 2010-06-15
yea im getting ```
Ndiswrapper doesn't support monitor mode.

```

---

### Post by jmasterx on 2010-10-03
I'm getting the same issue as Mr. Popo and WildWilllie . Has anyone figured this out? I have a 432B and managed mode runs fune but can't get into monitoring mode.

---

### Post by yatagarasu on 2010-10-11
Have the asme problem.

Only ndiswrapper reports that my card alternative driver is ssb

Have tested broadcom drivers from this post and lenovo broadcom drivers.
Have network card installed in lenovo s10-s. maybe there is something wrong with hardware revision.

---

### Post by jiballs on 2010-10-14
have tried all that was said in the tut and still having ndiswrapper not supporting monitor mode.
i guess i'm going to uninstall and return to as it was before except if someone has a solution to it

---

### Post by jiballs on 2010-10-14
hey how do i revert all of this (ndiswrapper installation) back to where i was with the eth1 interface

---

### Post by Lupius on 2010-10-17
Hi there,

I'm using the 14e4:4727 chipset on Lenovo V460. If I were to follow your tutorial, all I have to do is to find the windows driver for this chipset, right? Would you know where I can download it?

Thanks

---

### Post by BooleanLife on 2012-02-03
Hello Chenxiaolong,

Thank you very much for your tutorial, but i'm stuck at compiling ndiswrapper 1.56 after having patched bcmmon.diff.

```
root@amnesia:/home/amnesia/ndiswrapper/ndiswrapper-1.56# make
make -C driver
make[1]: entrant dans le répertoire « /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver »
make -C /usr/src/linux-headers-3.2.0-1-486 M=/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver
make[2]: entrant dans le répertoire « /usr/src/linux-headers-3.2.0-1-486 »
  LD      /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/built-in.o
  MKEXPORT /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/crt_exports.h
  MKEXPORT /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/hal_exports.h
  MKEXPORT /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/ndis_exports.h
  MKEXPORT /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/ntoskernel_exports.h
  MKEXPORT /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/ntoskernel_io_exports.h
  MKEXPORT /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/rtl_exports.h
  MKEXPORT /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/usb_exports.h
  CC [M]  /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/crt.o
  CC [M]  /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/hal.o
  CC [M]  /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.o
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_essid’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:87: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_essid’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:121: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_infra_mode’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:181: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_infra_mode’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:242: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_network_type’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:297: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_freq’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:317: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_freq’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:351: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_tx_power’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:397: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_tx_power’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:416: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_bitrate’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:453: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_bitrate’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:471: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_rts_threshold’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:516: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_rts_threshold’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:534: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_frag_threshold’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:554: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_frag_threshold’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:572: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_ap_address’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:605: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_ap_address’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:619: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_encr’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:806: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_wep’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:971: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_nick’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1057: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_nick’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1069: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_scan’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1261: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_scan’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1268: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_power_mode’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1330: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_power_mode’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1353: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_sensitivity’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1385: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_sensitivity’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1404: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_ndis_stats’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1426: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_range’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1437: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_mlme’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1602: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_auth’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1636: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_auth’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1677: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_encodeext’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1708: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_pmksa’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1814: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘priv_reset’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1893: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘priv_deauthenticate’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1907: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘priv_power_profile’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1930: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘priv_network_type’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1955: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘priv_media_stream_mode’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1987: error: ‘struct net_device’ has no member named ‘priv’
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘priv_reload_defaults’:
/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:2008: error: ‘struct net_device’ has no member named ‘priv’
make[5]: *** [/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.o] Erreur 1
make[4]: *** [_module_/home/amnesia/ndiswrapper/ndiswrapper-1.56/driver] Erreur 2
make[3]: *** [sub-make] Erreur 2
make[2]: *** [all] Erreur 2
make[2]: quittant le répertoire « /usr/src/linux-headers-3.2.0-1-486 »
make[1]: *** [modules] Erreur 2
make[1]: quittant le répertoire « /home/amnesia/ndiswrapper/ndiswrapper-1.56/driver »
make: *** [all] Erreur 2
root@amnesia:/home/amnesia/ndiswrapper/ndiswrapper-1.56# 
```

I don't understand...

Could someone help me ? :idea:

Thanks

---

### Post by phlegathetic on 2012-12-07
I have tried this step by step first with ndiswrapper-1.57 and would change the file bcmmod.diff from 1.56 to 1.57 and would get a constant error trying to patch, then i figured i would just download ndiswrapper-1.56 and revert the bcmmon.diff file to its original state 1.56 the patch seemed to have been successful as everything return like that and  


:~/ndiswrapper$ patch -p1 < bcmmon.diff
patching file ndiswrapper-1.56/driver/iw_ndis.c
Hunk #2 succeeded at 180 (offset -7 lines).
Hunk #3 succeeded at 242 (offset -7 lines).
Hunk #4 succeeded at 351 (offset -7 lines).
Hunk #5 succeeded at 367 (offset -7 lines).
Hunk #6 succeeded at 1908 (offset 11 lines).
Hunk #7 succeeded at 2026 (offset 11 lines).
Hunk #8 succeeded at 2040 (offset 11 lines).
patching file ndiswrapper-1.56/driver/iw_ndis.h
patching file ndiswrapper-1.56/driver/ndis.c
Hunk #7 succeeded at 2261 (offset -14 lines).
Hunk #8 succeeded at 2277 (offset -14 lines).
Hunk #9 succeeded at 2289 (offset -14 lines).


so i proceed to cd the ndiswrapper-1.56 and run the make command and get an error.


:~/ndiswrapper/ndiswrapper-1.56$ make
make -C driver
make[1]: Entering directory `/home/jesus/ndiswrapper/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-3.2.0-34-generic-pae M=/home/jesus/ndiswrapper/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-34-generic-pae'
  LD      /home/jesus/ndiswrapper/ndiswrapper-1.56/driver/built-in.o
  MKEXPORT /home/jesus/ndiswrapper/ndiswrapper-1.56/driver/crt_exports.h
  MKEXPORT /home/jesus/ndiswrapper/ndiswrapper-1.56/driver/hal_exports.h
  MKEXPORT /home/jesus/ndiswrapper/ndiswrapper-1.56/driver/ndis_exports.h
  MKEXPORT /home/jesus/ndiswrapper/ndiswrapper-1.56/driver/ntoskernel_exports.h
  MKEXPORT /home/jesus/ndiswrapper/ndiswrapper-1.56/driver/ntoskernel_io_exports.h
  MKEXPORT /home/jesus/ndiswrapper/ndiswrapper-1.56/driver/rtl_exports.h
  MKEXPORT /home/jesus/ndiswrapper/ndiswrapper-1.56/driver/usb_exports.h
  CC [M]  /home/jesus/ndiswrapper/ndiswrapper-1.56/driver/crt.o
  CC [M]  /home/jesus/ndiswrapper/ndiswrapper-1.56/driver/hal.o
  CC [M]  /home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.o
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_essid’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:87:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_essid’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:121:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_infra_mode’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:181:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_infra_mode’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:242:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_network_type’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:297:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_freq’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:317:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_freq’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:351:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_tx_power’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:397:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_tx_power’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:416:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_bitrate’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:453:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_bitrate’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:471:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_rts_threshold’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:516:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_rts_threshold’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:534:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_frag_threshold’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:554:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_frag_threshold’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:572:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_ap_address’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:605:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_ap_address’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:619:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_encr’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:806:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_wep’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:971:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_nick’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1057:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_nick’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1069:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_scan’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1261:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_scan’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1268:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_power_mode’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1330:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_power_mode’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1353:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_sensitivity’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1385:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_sensitivity’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1404:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_ndis_stats’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1426:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_range’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1437:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_mlme’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1602:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_auth’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1636:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_get_auth’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1677:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_encodeext’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1708:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘iw_set_pmksa’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1814:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘priv_reset’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1893:17: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘priv_deauthenticate’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1907:23: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘priv_power_profile’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1930:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘priv_network_type’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1955:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘priv_media_stream_mode’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:1987:28: error: ‘struct net_device’ has no member named ‘priv’
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c: In function ‘priv_reload_defaults’:
/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.c:2008:28: error: ‘struct net_device’ has no member named ‘priv’
make[3]: *** [/home/jesus/ndiswrapper/ndiswrapper-1.56/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/jesus/ndiswrapper/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-34-generic-pae'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/jesus/ndiswrapper/ndiswrapper-1.56/driver'
make: *** [all] Error 2

im stuck at this point ...
any help would be greatly appreciated...

---

