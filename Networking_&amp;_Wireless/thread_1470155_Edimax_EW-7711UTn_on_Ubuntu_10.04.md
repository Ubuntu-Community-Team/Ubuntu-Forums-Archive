---
title: "Edimax EW-7711UTn on Ubuntu 10.04"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by combinekidd on 2010-05-02
I recently installed Ubuntu 10.04 on my computer (I was previously using XP). I used an Edimax EW-7711UTn Wireless USB adapter on XP and it worked flawlessly. Now when using Ubuntu it says I'm connected (see photos below) and says I have a 100% connection, but I can't go online. However, it does work when I go an unprotected network (mines encrypted using WPA2). Does anyone else have a similar problem? Thanks.
[IMG]http://img405.imageshack.us/img405/351/screenshotue.png[/IMG]
[IMG]http://img405.imageshack.us/img405/4770/screenshot1wb.png[/IMG][IMG]http://img232.imageshack.us/img232/8026/screenshot2zo.png[/IMG]

---

### Post by riphil on 2010-08-03
Yes, I have the exact same problem with 10.04 clean install.  Ultimately it was resolved based on the information in this thread: [http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)

These guidance notes are based on memory!

1. Take the driver as supplied on the CD with the adapter
2. Uncompress the archive:
```

shell> tar jxvf 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2

```3. To avoid compiler kernel errors in the 10.04 release kernel version apply the patch listed in the thread above:
```

shell> gunzip rt3070-2.6.31-compile.patch.gz
shell> patch -p0 < rt3070-2.6.31-compile.patch
shell> cd 2009_0525_RT3070_Linux_STA_v2.1.1.0/

```4. As I was using WPA2 the following needs to be enabled
```

shell> vi os/linux/config.mk
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```5. To avoid some un-necessary logging output edit one of the files:
```

shell> vi common/rtusb_io.c
replace:
DBGPRINT(RT_DEBUG_OFF, ("#\n"));
with:
//DBGPRINT(RT_DEBUG_OFF, ("#\n"));

```
See the note in the other thread about the security issue (I have not tested this yet)
**Security Update**:
For those using this driver with wpasupplicant you should know about this bug which could affect your system:

[http://bugzilla.kernel.org/show_bug.cgi?id=14591](http://bugzilla.kernel.org/show_bug.cgi?id=14591)

A quick fix for it is to: 

 ```

shell> cd os/linux
shell> vi sta_ioctl.c
replace:
struct iw_mlme *pMlme = (struct iw_mlme *)wrqu->data.pointer;
with
struct iw_mlme *pMlme;
and
struct iw_pmksa *pPmksa = (struct iw_pmksa *)wrqu->data.pointer;
with
struct iw_pmksa *pPmksa;

```5. Because the make appears to want to write to /tftpboot you have to make as root
```

shell> sudo make
shell> sudo make install

```6. Copy the files into all the right places
```

shell> sudo mkdir -p /etc/Wireless/RT2870STA
shell> sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
shell> sudo chmod +x /etc/Wireless/RT2870STA/RT2870STA.dat
shell> sudo cp common/rt2870.bin /lib/firmware/

```I think mine installed to /etc/Wireless/RT3070/RT3070STA.dat.  Either way I ended up linking the directories /etc/Wireless/RT2870STA and /etc/Wireless/RT3070SAT together.
```

shell> sudo ln -s /etc/Wireless/RT2870 /etc/Wireless/RT3070STASTA

```7. blacklist and remove possible conflicting modules from the kernel
```

shell> sudo vi /etc/modprobe.d/blacklist.conf

add the following lines:
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
blacklist rt2070sta
save and close

shell> sudo rmmod rt2x00usb (just in case)
shell> sudo rmmod rt2x00lib (just in case)
shell> sudo rmmod rt2800usb (just in case)
shell> sudo rmmod rt2070sta (just in case)

```You might have to do this:
```

shell> cd os/linux
shell> sudo cp ./rtk3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/
shell> sudo rmmod rt3070sta
shell> sudo modprobe rt3070sta

```...and this:
```

shell> sudo vi /etc/modules.conf
add the following line:
alias ra0 rt3070sta

```..to get the module to load at boot

This is all from memory and provide this only as a possible assistance to anyone with this error, I am NOT a GNU/Linux - Ubuntu expert, unfortunately I can offer no further assistance with problems you may encounter.  See the linked thread from lesnoland [http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828) on which all this information is based.

---

### Post by VH2011 on 2011-01-16
This is a very useful post. I am new to Linux & wireless networking. I  have now got my wireless connection working. :D

Thanks

---

