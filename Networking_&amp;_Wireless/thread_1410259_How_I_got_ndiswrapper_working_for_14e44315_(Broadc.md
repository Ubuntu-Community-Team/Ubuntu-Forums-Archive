---
title: "How I got ndiswrapper working for 14e4:4315 (Broadcom bcm4312 rev 01)"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by leorolla on 2010-02-18
I am not an expert, this topic is from my experience. I see other users who also suffer lack of wireless, so I decided to create this topic.

So....

I had STA Broadcom proprietary driver automatically installed and working fine for months.

Recently it was broken with a log message just like [http://ubuntuforums.org/showthread.php?t=1369975](http://ubuntuforums.org/showthread.php?t=1369975). It was broken without any action from me. Jockey would simply produce that error.

(A side comment: after many releases running out-of-the box with Jockey and a proprietary driver, we had the unfortunate regression that it only works for Karmic after the first update/upgrade, using wired network of course.)

I tried blacklisting this and that, I purged and reinstalled bcmwl-kernel-source, didn't work.

I tried a chip of the instructions from your famous thread to install the b43 driver and linux-backports, didn't work.

I tried madwifi following [AspireOne/Ubuntu8.04 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AspireOne/Ubuntu8.04"), didn't work.
 
Then I had the idea of just using ndiswrapper.

I believe this should last stable until Lucid release, much more probably than any other solution subject to Ubuntu-update regressions.

----------------------------

1. Install ndisgtk
 
2. Download the Windows driver from Acer at [http://global-download.acer.com/GDFiles/Driver/Wireless%20LAN/WLAN_Broadcom_4.170.75.0_XPx86.zip?acerid=633701164785992813&Step1=Netbook&Step2=Aspire%20One&Step3=AOD150&OS=X01&LC=en&BC=Acer&SC=PA_7](http://global-download.acer.com/GDFiles/Driver/Wireless%20LAN/WLAN_Broadcom_4.170.75.0_XPx86.zip?acerid=633701164785992813&Step1=Netbook&Step2=Aspire%20One&Step3=AOD150&OS=X01&LC=en&BC=Acer&SC=PA_7)[]("http://global-download.acer.com/GDFiles/Driver/Wireless%20LAN/WLAN_Intel_12.1.0.14_XPx86.zip?acerid=633701164795352753&Step1=Netbook&Step2=Aspire%20One&Step3=AOD150&OS=X01&LC=en&BC=Acer&SC=PA_6") 

3. Extract the zip file to a folder.

4. Open Windows Wireless Drivers (or run "sudo ndisgtk").

5. Click on "Install new Driver", open the folder and choose the file bcmwl5.inf (it may give an error messge, but may work anyway).

6. Check at the files inside /etc/modprobe.d that other wireless drivers are neither loaded nor blacklisted.

----------------------------

A comment about blacklisting:

It worked (very) well the first time, then I blacklisted everything else and rebooted. It wasn't working.
I thought that, even though it doen't make sense to me, the problem could be with the blacklisting, as it was the only thing I did between working and not-working. Bingo!
I removed the blacklistings, rebooted and it worked. Again and again.
I blacklisted again, rebooted, not working.
Removed the blacklisting, rebooted, and it was working. Rebooted again and again, and it was working.
Curious conclusion: it was working only when the other drivers were not blacklisted, even though they didn't seem to be loaded from lsmod.

---

### Post by northd_tech on 2010-02-18
If you'd prefer something other than Windows drivers leo,  Broadcom does offer their proprietary "STA" driver (and a support email address) here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Broadcom's website further states:

> These packages contain Broadcom's IEEE 802.11a/b/g/n hybrid Linux® device driver for use with Broadcom's BCM4311-, **BCM4312**-, BCM4313-, BCM4321-, and BCM4322-based hardware. **There are different tars for 32-bit and 64-bit x86 CPU architectures. Make sure that you download the appropriate tar because the hybrid binary file must be of the appropriate architecture type.** The hybrid **binary file is agnostic to the specific version of the Linux kernel because it is designed to perform all interactions with the operating system through operating-system-specific files and an operating system abstraction layer file**. All Linux operating-system-[COLOR=Blue]specific code is provided in source form, making it possible to retarget to different kernel versions and fix operating system related issues[/COLOR].

I have read of the STA driver working for people with 4311, 4312, 4321, 4322, and my "4328"/4321AG Broadcom wireless.

If you go with the STA driver, you want to make sure that "wl" is the only kernel module loaded, using an **lsmod** command from a terminal (as in you don't want Broadcom "b43" or "ssb" modules loaded for an STA driver installation).  Those might need to be removed and/or blacklisted if you see those conflicting with the STA's "wl" module.

I used ndiswrapper/Windoze drivers "back in the day" with my Broadcom 4321AG before the STA driver came along (since the 802.11n and 4321 weren't very well supported or compatible with the older "b43" and "fwcutter" stuff long ago).

---

### Post by leorolla on 2010-02-19
Thanks!

I went to the link and saw the README.txt

For Ubuntu, it is already pre-compiled and is available at the Ubuntu repositories.

It is called **bcmwl-kernel-source** and is what I was calling **Jockey** (the Ubuntu application that detects the hardware and suggests the appropriate driver).

However, this has also stopped working all of a sudden about a month ago... for me and some other users.

---

### Post by lilmalice on 2012-09-02
I have an Acer Aspire 5516 with a Broacom Wifi card (BCM4312).

The steps above got my Wifi working!

Thanks... I had tried everything else.

....


But the Wifi disconnected a few minutes in, and after a reboot my wireless now reads "device not ready (firmware missing)". Yikes!

---

