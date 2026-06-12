---
title: "Wireless Dell 1450 USB adapter stops working after upgrade to 10.04"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by efx456 on 2010-05-01
I upgraded from 9.10 to 10.04 and my wireless card no longer works.

The card is a Dell 1450 USB a/b/g card.

lsusb sees the card. device id is 413c:8104

dmesg says that p54usb is trying to load firmware isl3887usb but that failed (error -2)

I looked in /lib/firmware and didn't find that file

any ideas would be appreciated.

ps. god why did i upgrade??? upgrades always screw me.... i'm such an idiot... ](*,)

---

### Post by curdog on 2010-05-01
Same exact problem here, but on a fresh install.  No luck following the usual broadcom guides.

---

### Post by pdc on 2010-05-02
to efx456

[http://swiss.ubuntuforums.org/showthread.php?p=9210909](http://swiss.ubuntuforums.org/showthread.php?p=9210909)

post #3 ..... is any of this any help?

to curdog: what made you think this device was a broadcom device?

can I also suggest you both run this diagnostic script: download and run it; it is used mainly on OpenSuse wireless forum .. 

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

that will analyse your wireless setup; make recommendations; and the analysis can be posted back here for further help

---

### Post by efx456 on 2010-05-02
Thank you for your reply. I'm actually familiar with that post. But I  prefer to use Linux drivers that worked in 9.10 instead of ndiswrapper. **[COLOR=Red] Why are those drivers not working after the upgrade??[/COLOR]**

---

### Post by mykewould on 2010-05-02
Having the same problem. Worked with 9.10, will not work now.

---

### Post by efx456 on 2010-05-02
Anyone?  This seems to be a widespread problem.  Doesn't anyone know why this happened in 10.04??

---

### Post by curdog on 2010-05-02
> **pdc said:**
> 
to curdog: what made you think this device was a broadcom device?

can I also suggest you both run this diagnostic script: download and run it; it is used mainly on OpenSuse wireless forum .. 

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Uberblick-/-Overview.html#English)

Thanks, pdc.  I've posted the results from the script you suggested (very long).  Btw, I had just suspected the 1450 USB was Broadcom-based since that is the case for the pci version of the 1450.  I haven't been able to find out how to pull the exact information.

**Script results:**
Run using NetworkTopology #1: WLAN accesspoint <--> linuxclient
```
--- Which type of your network connection should be tested?
--- (2) Wireless connection (WLAN)
--- What's the type of networktopology?
--- (1) WLAN access point <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient
--- WLAN SSID to connect to: t#e#u#h#u#e

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0110E: For the selected connection type there was no active network interface found on your system
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to http://www.linux-tips-and-tricks.de/CND#English to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see http://www.linux-tips-and-tricks.de/CND_UPL#English for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
==================================================================================================================
*** uname -a
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
==================================================================================================================
*** cat /etc/*[-_]release || cat /etc/*[-_]version
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
==================================================================================================================
*** cat /etc/resolv | grep -i "nameserver"
cat: /etc/resolv.conf: No such file or directory
==================================================================================================================
*** cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	ubuntu.ubuntu-domain	ubuntu
==================================================================================================================
*** route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
==================================================================================================================
*** ifconfig
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xc000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2664 (2.6 KB)  TX bytes:2664 (2.6 KB)
==================================================================================================================
*** ping tests
connect: Network is unreachable
Ping of 195.135.220.3 failed
ping: unknown host www.suse.de
Ping of www.suse.de failed
==================================================================================================================
*** lspci
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
==================================================================================================================
*** lsusb
Bus 002 Device 003: ID 045e:0053 Microsoft Corp. Optical Mouse
Bus 002 Device 002: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1221:3234  
Bus 001 Device 005: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 001 Device 002: ID 413c:8104 Dell Computer Corp. Wireless 1450 Dual-band (802.11a/b/g) USB2.0 Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
==================================================================================================================
*** lsmod # (filtered)
| ac97_bus        | agpgart         | binfmt_misc     | bitblit         | cfg80211         |
| cx2341x         | cx25840         | drm             | drm_kms_helper  | fat              |
| fbcon           | floppy          | font            | forcedeth       | hid              |
| i2c_algo_bit    | i2c_nforce2     | ieee1394        | isofs           | ivtv             |
| k8temp          | led_class       | lirc_dev        | lirc_mceusb     | lp               |
| mac80211        | nls_cp437       | nls_iso8859_1   | nls_utf8        | ohci1394         |
| p54common       | p54usb          | pata_amd        | ppdev           | radeon           |
| sata_nv         | snd_ac97_codec  | snd_intel8x0    | snd_rawmidi     | snd_seq_device   |
| snd_seq_dummy   | snd_seq_midi    | snd_seq_oss     | softcursor      | tileblit         |
| ttm             | tuner           | tuner_simple    | tuner_types     | tveeprom         |
| usb_storage     | v4l1_compat     | v4l2_common     | vfat            | vga16fb          |
| vgastate        | wm8775          |
==================================================================================================================
*** cat /etc/network/interfaces
--- /etc/network/interfaces
auto lo
iface lo inet loopback
==================================================================================================================
*** iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
==================================================================================================================
*** Actual date for bias of following greps
20:29:29 2010-05-02
==================================================================================================================
*** grep -i radio /var/log/messages* | tail -n 5
May  1 21:58:56 ubuntu kernel: [   13.580882] tveeprom 2-0050: has no radio
May  1 22:04:57 ubuntu kernel: [   13.403323] tveeprom 2-0050: has no radio
May  1 22:33:26 ubuntu kernel: [   13.987034] tveeprom 2-0050: has no radio
May  2 06:25:55 ubuntu kernel: [   14.768744] tveeprom 4-0050: has no radio
May  2 20:23:20 ubuntu kernel: [   13.493808] tveeprom 2-0050: has no radio
==================================================================================================================
*** dmesg | grep -i radio | tail -n 5
[   13.493808] tveeprom 2-0050: has no radio
==================================================================================================================
*** tail -n 300 /var/log/messages* | /bin/grep -i firmware | tail -n 5
May  2 20:23:20 ubuntu kernel: [   14.022046] usb 1-1: firmware: requesting isl3887usb_bare
May  2 20:23:20 ubuntu kernel: [   14.329027] ivtv 0000:01:05.0: firmware: requesting v4l-cx2341x-enc.fw
May  2 20:23:20 ubuntu kernel: [   14.345369] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
May  2 20:23:20 ubuntu kernel: [   14.561691] cx25840 2-0044: firmware: requesting v4l-cx25840.fw
May  2 20:23:24 ubuntu kernel: [   18.130875] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
==================================================================================================================
*** ls /lib/firmware/*
| 2.6.32-21-generic       | 3com                    | acenic                  | adaptec                  |
| advansys                | agere_ap_fw.bin         | agere_sta_fw.bin        | aic94xx-seq.fw           |
| ar9170-1.fw             | ar9170-2.fw             | ar9170.fw               | ath3k-1.fw               |
| atmel_at76c502_3com.bin | atmel_at76c502.bin      | atmel_at76c502d.bin     | atmel_at76c502e.bin      |
| atmel_at76c504_2958.bin | atmel_at76c504a_2958.bin| atmel_at76c504.bin      | atmel_at76c506.bin       |
| atmsar11.fw             | av7110                  | bnx2                    | bnx2x-e1-4.8.53.0.fw     |
| bnx2x-e1-5.2.7.0.fw     | bnx2x-e1h-4.8.53.0.fw   | bnx2x-e1h-5.2.7.0.fw    | cis                      |
| cpia2                   | cxgb3                   | dabusb                  | dsp56k                   |
| dvb-fe-xc5000-1.6.114.fw| dvb-usb-dib0700-1.20.fw | e100                    | ea                       |
| edgeport                | emi26                   | emi62                   | ess                      |
| i2400m-fw-usb-1.3.sbcf  | i2400m-fw-usb-1.4.sbcf  | intelliport2.bin        | ipw2100-1.3.fw           |
| ipw2100-1.3-i.fw        | ipw2100-1.3-p.fw        | ipw2200-bss.fw          | ipw2200-ibss.fw          |
| ipw2200-sniffer.fw      | iwlwifi-1000-3.ucode    | iwlwifi-3945-2.ucode    | iwlwifi-4965-2.ucode     |
| iwlwifi-5000-1.ucode    | iwlwifi-5000-2.ucode    | iwlwifi-5150-2.ucode    | iwlwifi-6000-4.ucode     |
| kaweth                  | keyspan                 | keyspan_pda             | korg                     |
| libertas                | matrox                  | mts_cdma.fw             | mts_edge.fw              |
| mts_gsm.fw              | mwl8k                   | myricom                 | NPE-B                    |
| NPE-C                   | ositech                 | ql2100_fw.bin           | ql2200_fw.bin            |
| ql2300_fw.bin           | ql2322_fw.bin           | ql2400_fw.bin           | ql2500_fw.bin            |
| qlogic                  | r128                    | radeon                  | rt2561.bin               |
| rt2561s.bin             | rt2661.bin              | rt2860.bin              | rt2870.bin               |
| rt73.bin                | RTL8192SE               | sb16                    | scripts                  |
| slicoss                 | sun                     | sxg                     | tehuti                   |
| ti_3410.fw              | ti_5052.fw              | tigon                   | tr_smctr.bin             |
| ttusb-budget            | usbdux                  | usbduxfast_firmware.bin | usbdux_firmware.bin      |
| v4l-cx231xx-avcore-01.fw| v4l-cx23418-apu.fw      | v4l-cx23418-cpu.fw      | v4l-cx23418-dig.fw       |
| v4l-cx2341x-dec.fw      | v4l-cx2341x-enc.fw      | v4l-cx2341x-init.mpg    | v4l-cx23885-avcore-01.fw |
| v4l-cx23885-enc.fw      | v4l-cx25840.fw          | v4l-pvrusb2-24xxx-01.fw | v4l-pvrusb2-29xxx-01.fw  |
| vicam                   | whiteheat.fw            | whiteheat_loader.fw     | yam                      |
| yamaha                  | zd1201-ap.fw            | zd1201.fw               | zd1211                   |
==================================================================================================================
*** ndiswrapper -l
No ndiswrapper module loaded
==================================================================================================================
*** Active processes
wpa_supplicant:YES knetworkmanager:NO nm-applet:YES
==================================================================================================================
*** grep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net*
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
==================================================================================================================
*** grep -r 'eth[0-10]|ath[0-10]|wlan[0-10]|ra[0-10]' /etc/modprobe.*
==================================================================================================================
*** iwlist scanning
No WLANs found
==================================================================================================================
*** NWElizaStates
IF:eth0 IM:1 DI:1 AP:0 FALON:0 

```

---

### Post by efx456 on 2010-05-02
Thank you for posting this curdog - I couldn't because my computer is off the network (obviously).  I hope someone can point us in the right direction.

---

### Post by mykewould on 2010-05-02
Tried the ndiswrapper with dellinc.inf driver. No dice.

---

### Post by efx456 on 2010-05-02
mykewould: can you give  a brief summary of what you had to do to make it work with ndiswrapper?  And if someone knows how to make the native linux drivers work (p54usb I think) please let us know.

---

### Post by mykewould on 2010-05-02
I'm sorry efx, I meant to say "No dice" not "Nice dice", which is to say that I did not get it to work. Reviewing the 2nd check in the ndiswrapper guide, here on the forum, states that that driver architecture and your system architecture have to be matched. I'm not sure if the driver posted on the guide above is 64-bit, which is what I'm running. I had trouble just finding a single driver for this adapter so I'm not sure if I'll be able to find a 64-bit version. Finding and installing the 64-bit will be my next troubleshooting step. Hopefully someone finds another answer soon.

---

### Post by efx456 on 2010-05-02
Everyone, please go to this bug report and click "affects me" link so that they know this is affecting many people.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565613](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565613)

---

### Post by efx456 on 2010-05-02
> **mykewould said:**
> I'm sorry efx, I meant to say "No dice" not "Nice dice", which is to say that I did not get it to work. Reviewing the 2nd check in the ndiswrapper guide, here on the forum, states that that driver architecture and your system architecture have to be matched. I'm not sure if the driver posted on the guide above is 64-bit, which is what I'm running. I had trouble just finding a single driver for this adapter so I'm not sure if I'll be able to find a 64-bit version. Finding and installing the 64-bit will be my next troubleshooting step. Hopefully someone finds another answer soon.

I'm using 64 bit too. That's why I don't want to use ndiswrapper. I want to use the driver that was working well for me in 9.10.  God I hate upgrading...

---

### Post by efx456 on 2010-05-02
If one of you is connected to the internet, can you run this command to provide info to ubuntu so they can fix this bug?  

```
apport-collect 565613
```

> Thank you for taking the time to report  this bug and helping to make Ubuntu better. Please execute the following  command, as it will automatically gather debugging information, in a  terminal:
 

apport-collect 565613
 

This will help us to find and resolve the problem. Bear in mind that  you may need to install the python-launchpadlib package from the  universe repository.  Thanks in advance!

        


---

### Post by alexcuervo on 2010-05-03
This should solve it for many of you.

```
sudo apt-get install linux-firmware-nonfree

```
reboot. (or unplug and plug the usb wireless adapter)

Done

---

### Post by curdog on 2010-05-03
> **alexcuervo said:**
> This should solve it for many of you.

```
sudo apt-get install linux-firmware-nonfree

```

I don't have hardwired internet access on the 10.04 system, but even w/ all the repositories selected I don't see linux-firmware-nonfree (only linux-firware, but the reinstall option is not available).  Am I doing something wrong, or is it available from the CD?  Can I install it from a memory stick?

However, linux-wlan-ng (prism utilities) was not selected and I vaguely remember this card using prism drivers in the past.  So installed this & rebooted but got nothing.  Strangely, even when installing this package, I get the error saying bcmwl-kernel-source cannot be installed (or something like that) even though synaptic tells me it is.

---

### Post by efx456 on 2010-05-03
> **alexcuervo said:**
> This should solve it for many of you.

```
sudo apt-get install linux-firmware-nonfree

```reboot. (or unplug and plug the usb wireless adapter)

Done

Thank you very much. That worked for me.  I  had to connect the pc to the internet to download that package.

---

### Post by curdog on 2010-05-03
> **alexcuervo said:**
> This should solve it for many of you.

```
sudo apt-get install linux-firmware-nonfree

```
reboot. (or unplug and plug the usb wireless adapter)

Done

It works!  Although I couldn't do it through APT, I was able to download the linux-firmware-nonfree deb file [v. 1.8] ([https://launchpad.net/ubuntu/lucid/i386/linux-firmware-nonfree/1.8]("https://launchpad.net/ubuntu/lucid/i386/linux-firmware-nonfree/1.8")) and install.  Wireless worked right away.  Thanks!

---

### Post by mykewould on 2010-05-03
Awesome! Thank you!

---

### Post by nickmhalliday on 2010-05-07
Brilliant - Have just spend a day trying to get my 1450 working and seeing very complicated solutions - just ran yours and it worked immediately - hope others find this!

---

### Post by mankyman6 on 2010-08-01
First let me say, sorry for bumping an old thread. :(

Secondly, I followed all of these steps, including the last one that seemed to work for everybody and my adapter still won't connect to my wireless network.

It sees the networks in my area and when I tell it to connect to mine, it asks for the WEP. I put in the correct WEP and it acts like it's trying to connect but it never does.

Please help. :|

---

### Post by ubto66 on 2010-08-03
Thank you, works well.

---

### Post by nova423 on 2010-11-07
Hi,

I am running my old Dimension 8300 with Ubuntu 9.10 after trying twice with 10.10 and 10.  Neither would work with my v1 WUSB54G adapter.  Ubuntu 9.1 works fine.

I played with ndis wrapper in 10.10, was able to install the 54G driver, and the system recognized networks all around my building EXCEPT mine.  Thought that was weird.

I will not be updating until there is any easy fix :)

Also is it true that VLC has security issues with 9.1?

Thanks!

---

### Post by MM7 on 2011-12-18
> **mankyman6 said:**
> First let me say, sorry for bumping an old thread. :(

Secondly, I followed all of these steps, including the last one that seemed to work for everybody and my adapter still won't connect to my wireless network.

It sees the networks in my area and when I tell it to connect to mine, it asks for the WEP. I put in the correct WEP and it acts like it's trying to connect but it never does.

Please help. :|
I'm also sorry for bumping an old thread.  Been trying every December for 3 years to get Ubuntu working, normally at Christmas but I thought I'd have an early start.  2 days this year and can't get it to work.
I'm getting exactly the same problem as mankyman6.
Tried version 11.10, 9.04 and 9.10.  Currently on v9.10 and I get a light on my usb wireless device for 8 seconds.  This is since I've installed [linux-firmware-nonfree_1.8_all.deb]("http://launchpadlibrarian.net/44390666/linux-firmware-nonfree_1.8_all.deb")                   (2.5 MiB)

Any help would be appreciated as I just can't get away from Windows. ;)

---

