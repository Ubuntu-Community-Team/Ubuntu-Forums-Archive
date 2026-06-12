---
title: "Natty 11.04: Cannot connect to Android hotspot ... other WIFI all OK"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by boblowkl on 2011-05-14
I have the weirdest problem on the newly (freshly) installed Natty on my Acer Aspire 5741G: Wifi connectivity is good out-of-the-box and can connect (at least with my office's network) but cannot connect with my phone's (HTC Legend with Froyo) configured as a portable hotspot. 

The network can be detected, but fails to connect. I have tried with WPA, without any security.... it all does not work.

Previously Lucid 10.4 connected flawlessly out-of-the-box on the same machine.

Other devices detect and connect to the phone without problems.


```
*-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:27:c4:fc:24:32
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:b5100000-b510ffff

```Not sure if this helps but syslog shows:
```

May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) starting connection 'Auto BlahHotspot'
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0/wireless): access point 'Auto BlahHotspot' has security, but secrets are required.
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0/wireless): connection 'Auto BlahHotspot' has security, and secrets exist.  No new secrets needed.
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Config: added 'ssid' value 'BlahHotspot'
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Config: added 'scan_ssid' value '1'
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Config: added 'psk' value '<omitted>'
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Config: set interface ap_scan to 1
May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> (wlan0): supplicant connection state:  inactive -> scanning
May 15 08:17:00 Blah-Aspire-5741G wpa_supplicant[884]: Trying to associate with 38:40:d8:e7:40:64 (SSID='BlahHotspot' freq=2437 MHz)
May 15 08:17:00 Blah-Aspire-5741G NetworkManager[830]: <info> (wlan0): supplicant connection state:  scanning -> associating
May 15 08:17:00 Blah-Aspire-5741G kernel: [ 6028.762076] wlan0: direct probe to 38:40:d8:e7:40:64 (try 1/3)
May 15 08:17:00 Blah-Aspire-5741G kernel: [ 6028.958173] wlan0: direct probe to 38:40:d8:e7:40:64 (try 2/3)
May 15 08:17:01 Blah-Aspire-5741G kernel: [ 6029.157866] wlan0: direct probe to 38:40:d8:e7:40:64 (try 3/3)
May 15 08:17:01 Blah-Aspire-5741G kernel: [ 6029.367494] wlan0: direct probe to 38:40:d8:e7:40:64 timed out
May 15 08:17:01 Blah-Aspire-5741G CRON[2475]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 15 08:17:10 Blah-Aspire-5741G wpa_supplicant[884]: Authentication with 38:40:d8:e7:40:64 timed out.
May 15 08:17:10 Blah-Aspire-5741G NetworkManager[830]: <info> (wlan0): supplicant connection state:  associating -> disconnected

```(MAC addresses obfuscated)

TIA.

---

### Post by boblowkl on 2011-05-16
bump

---

### Post by Martin_sensei on 2011-05-17
I have exactly the same problem on my ASUS UL30a (with the same Network card)

Android Hotspot worked on Ubuntu 10.10, and stopped working on Natty.

---

### Post by Martin_sensei on 2011-05-17
Have you tried:

```
sudo -s
echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf
```

As mentioned on: [http://askubuntu.com/questions/37409/why-is-my-internet-so-slow-with-an-atheros-wireless-card]("http://askubuntu.com/questions/37409/why-is-my-internet-so-slow-with-an-atheros-wireless-card")

---

### Post by boblowkl on 2011-05-24
Just tried... no joy.

> **Martin_sensei said:**
> Have you tried:

```
sudo -s
echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf
```As mentioned on: [http://askubuntu.com/questions/37409/why-is-my-internet-so-slow-with-an-atheros-wireless-card](http://askubuntu.com/questions/37409/why-is-my-internet-so-slow-with-an-atheros-wireless-card)

---

### Post by saberoth on 2011-05-25
Same problem here, also only timed out. It's confusing me, how could it work?

---

### Post by boblowkl on 2011-06-06
Bump....

If noone in this forum can help, could someone please direct me to the correct forum/site where I can lodge this bug and maybe get some directions on how to diagnose the problem?

I've always praised the responsiveness of the open source community in general and Ubuntu in particular.... hope in this case I will not be proven wrong.....

---

### Post by cabez0n on 2011-06-19
Yes, same thing happening to me with Ubuntu natty and a motorola milestone. 

direct probe timed out. 

I can use the hotspot feature from windows, and older ubuntu's but this bug is really annoying.

---

### Post by onaridge on 2011-09-01
I am having the same problem with my droid x. I got rid of windows which worked fine. I can't believe I will have to reinstall just to use my hotspot!!

---

### Post by fdrake on 2011-09-02
> May 15 08:16:59 Blah-Aspire-5741G NetworkManager[830]: <info> Activation (wlan0/wireless): connection 'Auto BlahHotspot' has security, and secrets exist.  No new secrets needed
that's curious :D

anyway... did you all at least get the latest updates for your kernel?

```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) linux-backports-modules-wireless-$(less /etc/lsb-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f 2)-$(uname -r | cut -d "-" -f 3)
sudo aptitude update
sudo aptitude upgrade
```
reboot

---

### Post by onaridge on 2011-09-02
Yes, I just installed it last week from the ubuntu site.

---

### Post by dashnak on 2011-09-21
Has anyone been able to fix this? I'm suffering from the exact same issue...

---

### Post by 67Mustang on 2011-10-07
Had the same problem after upgrading to 11.04. Installed kernel 3.1.0-0301rc4-generic and it's now working.  :D

---

### Post by dashnak on 2011-10-07
Installed latest version of the ath9k drivers and fixed it.
Instructions over here: [http://linuxwireless.org/en/users/Drivers/ath9k#Get_the_latest_ath9k_driver]("http://linuxwireless.org/en/users/Drivers/ath9k#Get_the_latest_ath9k_driver")

---

### Post by chrislangton on 2011-10-18
I've just installed 11.10, and my net is off so im using my wifi hotspot on my Adroid HTC Legend. Its a duel boot with Win7 and no issues on Win7.
I have an ASUS EEE 701 with ubuntu 10.04 no issues there either.

Would i also need to update the kernel even though 11.10 is less than a week old?

---

### Post by Pich78 on 2011-10-24
Same problem here ...

11.10 and Android Hero with Gingerbread 2.3.5.

Windows 7 shows no problem. Ubuntu gets the SSID of the network, but the connection fails. 

Thank you for your help.

---

### Post by cprietom on 2011-10-31
Ubuntu 11.10 with kernel 3.0.0-12-generic-pae i686 i386 trying to connect through a Motorola Defy with android 2.2.2 and... same problem.

I'll try to install the 3.1RC kernel. Is this the right way of installing it?: [http://kenhgiaiphap.vn/Detail/1260/-Install--Kernel-310-tren-Ubuntu-1104.html](http://kenhgiaiphap.vn/Detail/1260/-Install--Kernel-310-tren-Ubuntu-1104.html)

---

### Post by djabhi on 2011-11-05
i'm also facing the same problem..someone please help....

---

### Post by Sharpie1 on 2011-11-06
I can connect via Vista to my Motorola Defy without a problem, but can't connect with 11.10 Oneiric Ocelot .. like others, sees the SSID but won't connect to it at all, not just lack of connectivity but no connection made. Any help welcome ! Ath9k drivers not applicable, Im on a Broadcom Wifi I think...
tia Sharpie1

---

### Post by cjsnide on 2011-11-23
Same issue, ath9k driver, 11.10 ubuntu, Droid X 3G Hotspot

---

### Post by YAMAHAMMER_07 on 2011-11-23
Linux rookie here. But same problem ^ same version, and same device.

---

### Post by shj333 on 2011-11-28
As in post #13 above, I think the problem is in the 3.0 kernel. I installed the 3.1 generic kernel and the problem went away. 

[This page]("http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html") has instructions on how to install 3.1 kernel in Ubuntu 11.10.

---

### Post by vt4 on 2012-01-18
I have exactly the same problem with 2 fresh install of 11.10 on a netbook and a laptop when trying to connect to HTC legend and Moto MS2.  But works fine with HTC CHACHA and xperia play.
 
WIFI connected to legend and MS2 from win7 was fine.
 
Will try to update the kernel and see if that will work.

---

### Post by Jose Catre-Vandis on 2012-01-23
Upgrading the kernel to 3.1.4 fixed it for me - whoopee!

---

### Post by hans.hook on 2012-03-30
Had the same issues with 11.10 on an acer Ferrari one netbook.

Installing linux-backports-modules-cw-3.2-oneiric-generic
and linux-backports-modules-headers-oneiric-generic
resolved the porblem completely.

Regards

Hans Höök

---

