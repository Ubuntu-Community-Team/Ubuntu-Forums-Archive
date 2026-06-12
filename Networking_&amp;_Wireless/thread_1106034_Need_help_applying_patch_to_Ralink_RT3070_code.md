---
title: "Need help applying patch to Ralink RT3070 code"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by jimbob on 2009-03-25
I have found a patch on a German website that will hopefully allow me to compile the Ralink RT3070 module so my Linksys WUSB54GC wireless dongle will work under Ubuntu but I don't know how to apply the patch.

[http://74.125.45.132/translate_c?hl=en&sl=de&u=http://lobmenschen.de/index.php/RALINK_RT3070_Linux_Treiber_Installation&prev=/search%3Fq%3Drt3070%2Bon%2BDebian%26hl%3Den%26sa%3DG&usg=ALkJrhhheuYw82uF1THrQM5FmEBgn3sFIg](http://74.125.45.132/translate_c?hl=en&sl=de&u=http://lobmenschen.de/index.php/RALINK_RT3070_Linux_Treiber_Installation&prev=/search%3Fq%3Drt3070%2Bon%2BDebian%26hl%3Den%26sa%3DG&usg=ALkJrhhheuYw82uF1THrQM5FmEBgn3sFIg)

Please if anyone knows where I put this patch in the code let me know.

---

### Post by nickmcg on 2009-03-25
you need to save the text in t3070_2.0.1.0_2.6.27.patch as a text file - call it, for example, patch.diff.
Unpack the rt3070 sources into 2008_1225_RT3070_Linux_STA_v2.0.1.0.orig, then```
patch < patch.diff
```

The sources for this came from [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) & it looks like it's a patch to the latest version.

Sorry, can't test it, as I haven't got that device.

Good luck

Nick

Edit:
I have a RT2870, downloaded the sources, edited as per the readme, then ```
make
sudo make
sudo make install
```
make install creates & copies /etc/Wireless/RT2870STA/RT2870STA.dat - I needed to delete that file to get my system working again. Obviously, I don't know if the same is true for your adaptor

Nick

---

### Post by jimbob on 2009-03-26
Thanks so much for the reply but I am having a terrible time trying to apply the patch.  Here is my output:

```
root@IIBEX:/home/jaspmatt/RALINK# patch < patch.diff
can't find file to patch at input line 4
Perhaps you should have used the -p or --strip option?
The text leading up to this was:
--------------------------
|diff -urp 2008_1225_RT3070_Linux_STA_v2.0.1.0.orig/include/rt_linux.h 2008_1225_RT3070_Linux_STA_v2.0.1.0/include/rt_linux.h
|--- 2008_1225_RT3070_Linux_STA_v2.0.1.0.orig/include/rt_linux.h	2008-12-24 08:35:58.000000000 +0100
|+++ 2008_1225_RT3070_Linux_STA_v2.0.1.0/include/rt_linux.h	2009-01-29 01:07:55.728791771 +0100
--------------------------
File to patch: 

```

Don't know what I'm doing wrong but any help will be welcome.

---

### Post by chili555 on 2009-03-26
I believe it's:```
patch -p1 t3070_2.0.1.0_2.6.27.patch
```I tried this and the patch went fine.

---

### Post by jimbob on 2009-03-27
Thanks everyone.  I got through the patch operation but now I'm back to getting what appears to be errors in the C-code:

```
root@IIBEX:/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0# make
make -C tools
make[1]: Entering directory `/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/tools'
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/md5.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/mlme.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/action.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/cmm_data.o
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/cmm_data.c: In function ‘RTMP_FillTxBlkInfo’:
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/cmm_data.c:803: warning: label ‘FillTxBlkErr’ defined but not used
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/eeprom.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/dfs.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/spectrum.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../sta/assoc.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../sta/aironet.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../sta/auth.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../sta/sync.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../sta/sanity.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../sta/connect.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../sta/wpa.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/rt_linux.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/rt_main_dev.o
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/rt_main_dev.c: In function ‘rt28xx_init’:
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/rt_main_dev.c:439: warning: unused variable ‘MacValue’
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/ba_action.o
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/ba_action.c: In function ‘BAOriSessionSetUp’:
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/ba_action.c:545: warning: too many arguments for format
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/ba_action.c: In function ‘BAOriSessionSetupTimeout’:
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../common/ba_action.c:1107: warning: too many arguments for format
  CC [M]  /home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.o
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c: In function ‘MlmeThread’:
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:274: warning: assignment makes pointer from integer without a cast
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c: In function ‘RTUSBCmdThread’:
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:382: warning: assignment makes pointer from integer without a cast
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c: In function ‘TimerQThread’:
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:476: warning: assignment makes pointer from integer without a cast
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c: In function ‘RT28xxThreadTerminate’:
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:960: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘struct pid *’
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:965: error: implicit declaration of function ‘kill_proc’
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:969: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘struct pid *’
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:975: warning: assignment makes pointer from integer without a cast
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:981: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘struct pid *’
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:992: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘struct pid *’
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:998: warning: assignment makes pointer from integer without a cast
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:1005: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘struct pid *’
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:1013: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘struct pid *’
/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.c:1019: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux/../../os/linux/2870_main_dev.o] Error 1
make[1]: *** [_module_/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [LINUX] Error 2
root@IIBEX:/home/jaspmatt/RALINK/2008_1225_RT3070_Linux_STA_v2.0.1.0# 


```

Are there any C experts out there who can suggest something here?  Is there perhaps a way to make the gcc compiler less sensitive to these declaration problems?

---

### Post by jimbob on 2009-03-29
I received a patch for the compiler code from Ralink yesterday which does allow me to successfully complete the make and make install and to modeprobe the rt3070sta driver.  However I encountered a problem in the README_STA instructions which stopped me cold.  I believe this is where the device ra0 is defined to wpa_supplicant but it fails.

```
3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

```  

Here are the results:

```
root@IIBEX:/home/jaspmatt/Desktop# wpa_supplicant -Dwext -ira0 -c /etc/dbus-1/system.d/wpa_supplicant.conf -d
Initializing interface 'ra0' conf '/etc/dbus-1/system.d/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/dbus-1/system.d/wpa_supplicant.conf' -> '/etc/dbus-1/system.d/wpa_supplicant.conf'
Reading configuration file '/etc/dbus-1/system.d/wpa_supplicant.conf'
Line 1: Invalid configuration line '<!DOCTYPE busconfig PUBLIC'.
Line 2: Invalid configuration line '"-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"'.
Line 3: Invalid configuration line '"http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">'.
Line 4: Invalid configuration line '<busconfig>'.
Line 5: Invalid configuration line '<policy user="root">'.
Line 6: Invalid configuration line '<allow own="fi.epitest.hostap.WPASupplicant"/>'.
Line 8: Invalid configuration line '<allow send_destination="fi.epitest.hostap.WPASupplicant"/>'.
Line 9: Invalid configuration line '<allow send_interface="fi.epitest.hostap.WPASupplicant"/>'.
Line 10: Invalid configuration line '</policy>'.
Line 11: Invalid configuration line '<policy group="netdev">'.
Line 12: Invalid configuration line '<allow send_destination="fi.epitest.hostap.WPASupplicant"/>'.
Line 13: Invalid configuration line '<allow send_interface="fi.epitest.hostap.WPASupplicant"/>'.
Line 14: Invalid configuration line '</policy>'.
Line 15: Invalid configuration line '<policy context="default">'.
Line 16: Invalid configuration line '<deny own="fi.epitest.hostap.WPASupplicant"/>'.
Line 17: Invalid configuration line '<deny send_destination="fi.epitest.hostap.WPASupplicant"/>'.
Line 18: Invalid configuration line '<deny send_interface="fi.epitest.hostap.WPASupplicant"/>'.
Line 19: Invalid configuration line '</policy>'.
Line 20: Invalid configuration line '</busconfig>'.
Failed to read or parse configuration '/etc/dbus-1/system.d/wpa_supplicant.conf'.
Failed to add interface ra0
Cancelling scan request
Cancelling authentication timeout
root@IIBEX:/home/jaspmatt/Desktop# 


```

All suggestions are welcome.
I can supply a copy of the RT3080 driver package I received if anyone is interested but it is a 644k tarball - too large for here.

---

### Post by nickmcg on 2009-03-31
I have only used the rt2870 driver, and I set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y' as in the docs.

Once I've built & installed (sudo make install) the driver, all I do is ```
sudo modprobe rt2870sta
``` then (after a few seconds) the wireless network shows up on network manager, and I can connect.
I don't have to explicitly call wpa_supplicant.

I would guess that it should be similar for the rt3070 driver.

Good luck

Nick

---

### Post by jimbob on 2009-03-31
I can do all that and the driver rt3070sta shows up in the module list but there is no device created.  Did yours automatically generate a device named ra0 that shows up in ifconfig without your having to do anything else?
Also the light on the device never flashes like it does in ex pee.

---

### Post by nickmcg on 2009-03-31
ra0 was created for me, and the 'enable wireless' checkbox came on once the module was loaded.

I did have to remove the rt2570sta.dat file to get the wireless connection working properly (although the device was there).

Does dmesg give any clues? (rmmod then modprobe)

Is there a rt3070.bin file in /lib/firmware/ ? There seems to be one for the rt2870.

Nick

---

### Post by jimbob on 2009-03-31
Where did the rt2570sta.dat file come from? Is that a typo?

Here is output of dmesg after modprobe'ing rt3070sta in:

[ 3964.356441] rtusb init --->
[ 3964.358299] usbcore: registered new interface driver rt2870
[ 3972.404042] usb 3-2: new high speed USB device using ehci_hcd and address 2
[ 3972.588520] usb 3-2: configuration #1 chosen from 1 choice

There is no rt3070.bin file in /lib/firmware (or anywhere in the whole machine).  All I have is rt2561.bin, rt2561s.bin, rt2661.bin and rt73.bin.
rt2870.bin is in the Ralink library but never got moved in I guess.  I'm thinking of renaming it and moving it in manually.  

A lot of this problem is the way they hacked this driver together.  I don't know if you ever saw this:


Quote:
This is my candidate for the crappiest Linux driver ever created. They
basically took the rt2870 driver and modified it to support rt3070. There is
nothing wrong for them with stealing their own code. But there were a few
issues that I had to solve:

- For some reason they took an older rt2870 driver version and modified it.
Hence the driver will not compile for Fedora kernels 2.6.25 and newer. So I had
the re-introduce our iwe-stream patch.

- They did not even bother to change the filenames or variable names in the
code. The code says "rt2870" but it actually means "rt3070". Confusing. I had
to rename the RT2870STA.DAT file to RT3070STA.DAT to avoid conflicts with our
rt2870 kmod.

Other than these two things, both the common and the kmod package is identical
to our rt2870 packages in rpmfusion.


I admit that this package is crap. But still, there might be people who can
benefit from it.

(from [http://www.mail-archive.com/rpmfusio.../msg03357.html](http://www.mail-archive.com/rpmfusio.../msg03357.html))

---

### Post by nickmcg on 2009-03-31
Sorry, typo (big fingers, small brain!) - should be rt2870sta.dat

I've only had experience with the 2870, so I'm stumped, although looking at the docs on the ralink site
```
Version 2.0.1.0
	1.Finished verifying RT3071 STA support.
	2.Fix eFuse bug on big-endian platform
	3.Fix WMM problem for RT3071/72
	4.Fix bug for ATE TX power handling and ATE frequency offset bug.
	5.Fix RT307x AMPDU throughput bug after interface down/up
	6.Fix RT307x difficult to enter power save mode issue.
	7.Fix bug that is hard to connect with hidden-SSID AP.
	8.Update RT307x new firmware.


``` there should be firmware, although it only seems to ship with rt2870 firmware.

You may be able to get more information from serialmonkey - I found this thread in their forum [http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5210](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5210)

Best of luck - I'm out of ideas

Nick

---

### Post by scarfays on 2009-07-05
[FONT=Arial Black]hello  
 I buy a USB stick Zioncom with RT3070 drivers  
 but it works very well, I would like to take this usb wifi  
 you can make a little explanation tuto to install the patch Ralink RT3070  
 Please I really need your help  
 thank you friend[/FONT]

---

### Post by chili555 on 2009-07-08
If your wireless stick is working very well, why do you want to apply a patch? Are you trying to get packet injection?

It would help if you posted a link to the driver and patch you are trying to apply.

Thanks.

---

### Post by jimbob on 2009-07-08
You won't need any patches if you follow post # 2 at this link:

[http://ubuntuforums.org/showthread.php?t=1155941](http://ubuntuforums.org/showthread.php?t=1155941)

---

