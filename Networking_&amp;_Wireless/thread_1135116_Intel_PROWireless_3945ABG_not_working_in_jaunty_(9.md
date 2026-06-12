---
title: "Intel PRO/Wireless 3945ABG not working in jaunty (9.04)"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by XAR on 2009-04-24
After upgrade from Intrepid wireless stopped working.
As I can see, there's no ipw3945 driver:
```
root@alex-laptop:/etc/modprobe.d# modprobe ipw3945
FATAL: Module ipw3945 not found.
```And with iwl3945 I got this:

```
root@alex-laptop:/etc/modprobe.d# lspci
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

``````
root@alex-laptop:/etc/modprobe.d# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"XAR"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````
root@alex-laptop:/etc/modprobe.d# lsmod
iwl3945                94212  0 
ndiswrapper           250624  0 
iwlcore               128896  1 iwl3945
lbm_cw_mac80211       259000  2 iwl3945,iwlcore
lbm_cw_cfg80211        85048  3 iwl3945,iwlcore,lbm_cw_mac80211
led_class              13064  2 iwl3945,iwlcore

``````
root@alex-laptop:/etc/modprobe.d# dmesg | grep ndis
[   17.108864] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   17.219458] usbcore: registered new interface driver ndiswrapper

``````
root@alex-laptop:/etc/modprobe.d# dmesg | grep iwl
[   16.223298] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   16.223316] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   16.223553] iwl3945 0000:0c:00.0: assigned PCI INT A -> IRQ 4
[   16.223583] iwl3945 0000:0c:00.0: sharing IRQ 4 with 0000:00:1f.2
[   16.223587] iwl3945 0000:0c:00.0: sharing IRQ 4 with 0000:00:1f.3
[   16.223597] iwl3945 0000:0c:00.0: sharing IRQ 4 with 0000:02:00.0
[   16.223619] iwl3945 0000:0c:00.0: setting latency timer to 64
[   16.302075] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   16.302079] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   16.302205] iwl3945 0000:0c:00.0: irq 2300 for MSI/MSI-X
[   16.302755] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   20.404914] iwl3945 0000:0c:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[   20.616748] iwl3945 0000:0c:00.0: loaded firmware version 15.28.2.8
[   22.620039] iwl3945 0000:0c:00.0: Wait for START_ALIVE timeout after 2000ms.
[ 1472.186616] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[ 1472.186620] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[ 1472.186737] iwl3945 0000:0c:00.0: assigned PCI INT A -> IRQ 4
[ 1472.186766] iwl3945 0000:0c:00.0: sharing IRQ 4 with 0000:00:1f.2
[ 1472.186770] iwl3945 0000:0c:00.0: sharing IRQ 4 with 0000:00:1f.3
[ 1472.186780] iwl3945 0000:0c:00.0: sharing IRQ 4 with 0000:02:00.0
[ 1472.186807] iwl3945 0000:0c:00.0: setting latency timer to 64
[ 1472.228611] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[ 1472.228615] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[ 1472.228742] iwl3945 0000:0c:00.0: irq 2300 for MSI/MSI-X
[ 1472.230421] phy1: Selected rate control algorithm 'iwl-3945-rs'
[ 1472.302724] iwl3945 0000:0c:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[ 1472.319117] iwl3945 0000:0c:00.0: loaded firmware version 15.28.2.8
[ 1474.320031] iwl3945 0000:0c:00.0: Wait for START_ALIVE timeout after 2000ms.
[ 1531.975108] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[ 1531.975112] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[ 1531.975231] iwl3945 0000:0c:00.0: assigned PCI INT A -> IRQ 4
[ 1531.975260] iwl3945 0000:0c:00.0: sharing IRQ 4 with 0000:00:1f.2
[ 1531.975265] iwl3945 0000:0c:00.0: sharing IRQ 4 with 0000:00:1f.3
[ 1531.975274] iwl3945 0000:0c:00.0: sharing IRQ 4 with 0000:02:00.0
[ 1531.975301] iwl3945 0000:0c:00.0: setting latency timer to 64
[ 1532.015369] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[ 1532.015372] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[ 1532.015498] iwl3945 0000:0c:00.0: irq 2300 for MSI/MSI-X
[ 1532.017135] phy2: Selected rate control algorithm 'iwl-3945-rs'
[ 1532.085949] iwl3945 0000:0c:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[ 1532.089914] iwl3945 0000:0c:00.0: loaded firmware version 15.28.2.8
[ 1534.096028] iwl3945 0000:0c:00.0: Wait for START_ALIVE timeout after 2000ms.

``````
root@alex-laptop:/etc/modprobe.d# sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:3c:64:a9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:72:a3:96
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.33 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 82:dd:32:b4:6a:ad
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

``````
root@alex-laptop:/etc/modprobe.d# iwlist scan
wlan0     Interface doesn't support scanning : Network is down

``````
root@alex-laptop:/etc/modprobe.d# uname -mr
2.6.28-11-generic x86_64

``````
root@alex-laptop:/etc/modprobe.d# sudo ifconfig wlan0 up
SIOCSIFFLAGS: Connection timed out

``````
root@alex-laptop:/etc/modprobe.d# cat /etc/modprobe.d/iwl3945.conf
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1

``````
root@alex-laptop:/etc/modprobe.d# cat /boot/grub/menu.lst
title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c15bca19-9ff9-4ab0-a2b5-089651a0f452 ro noapic nolapic irq=noacpi acpi=off quiet splash clocksource=hpet 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

```linux-restricted-modules-2.6.28-11-generic - installed


PS: After each bloody kernel update I have to do some weird voodoo magic to get my wifi working!!! Freaking me out!

---

### Post by rlzyoner on 2009-04-24
Though not directly related to your problem.
I just read this a minute ago over on ubuntugeek

Its for enabling packet injection on your wireless card.
For packet injection to work, I would assume the wireless card should work too.
Maybe try following this if all else fails

[http://www.ubuntugeek.com/how-to-enable-packet-injection-on-a-intel-prowireless-3945abg-wireless-card.html](http://www.ubuntugeek.com/how-to-enable-packet-injection-on-a-intel-prowireless-3945abg-wireless-card.html)

---

### Post by huntz on 2009-04-24
I'm with Jaunty and Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) working right now.

[http://ubuntuforums.org/showthread.php?t=1135218]("http://ubuntuforums.org/showthread.php?t=1135218")

I hope this will help.

---

### Post by xghstst0riesx on 2009-04-26
XAR - I feel for you. Seems that with every kernel update I have problems with this card. It was working fine in Intrepid for quite a while. After the upgrade to Jaunty it broke again.


I've tried a number of things and still no wireless:

[LIST]
[*]Adding "options iwl3945 disable_hw_scan=1" to /etc/modprobe.d/iwl3945.conf as suggested in [http://ubuntuforums.org/showthread.php?t=1097096&highlight=iwl3945+jaunty]("http://ubuntuforums.org/showthread.php?t=1097096&highlight=iwl3945+jaunty")
[*]Reloading the module
[*]Installing WICD
[*]Turning the killswitch on/off
[/LIST]

One thing that seems suspicious is that the wireless indicator light is no longer lit (on my Dell Inspiron E1505), even though syslog indicates the killswitch has been activated/deactivated.

---

### Post by Hero of Time on 2009-04-26
I got the same issues. In Intrepid, I installed the Jaunty development kernel and it was working just fine until they forced you install Wireless-CRDA, and that was in 2.6.28-8. It works just fine in 2.6.28-7 and before.
I see my wireless light go on, as it's a hardware switch instead of a soft-touch one, detect wireless networks but wpa_supplicant is unable to connect to any access point.
As WICD is only a tool that uses wpa_supplicant, that won't work either. I've even tried 2.6.29.1 and 2.6.30-rc3 and that didn't work either.
I really blame Ubuntu from forcing wireless-crda, which just doesn't work. And I can't install the drivers from linuxwireless.org either, make fails with error code 2. The linux-backports-modules-jaunty don't work either, as they have the same module version, that is even in 2.6.27, 1.2.26ks.

---

### Post by Hero of Time on 2009-04-26
I installed Xserver-xorg and Xfce, now I do get connected properly. How strange.

---

### Post by jsegel on 2009-05-21
is there any way to set the killswitch off with iwl3945? 

on an hp nc 6320, the hardware key doesn't have any effect in ubuntu.

---

### Post by stillious on 2009-05-21
I have a Dell D830 with this card. All worked OK in 8.10, now in 9.04 I *can* connect, but it is sooo painfully slow (with random disconnects) that it is unusable.

**XAR:**

You can download the driver from here: ```
http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.32.2.9.tgz
``` unzip it and copy the iwlwifi-3945-2.ucode file into the /lib/firmware directory.

See how that goes for you, I'm still struggling with this myself :rolleyes:

---

### Post by jsegel on 2009-05-27
i believe this is working for me... though initial reboot didn't do it, second reboot (today) and i have the little blue light and the killswitch is off, wireless is working!

---

### Post by RomanIvanov on 2009-06-28
I had the same problem - Xubuntu 9.04 on Dell Vostrol 1510 (Wireless 49454ABG) - does not work wireless. Worked fine for 8.10.

Solution:
just install new xfce 4.6.1

Source link: [http://jeromeg.blog.free.fr/index.php?post/2009/03/04/Installing-Xfce-4.6-on-Ubuntu-8.04-and-Ubuntu-8.10](http://jeromeg.blog.free.fr/index.php?post/2009/03/04/Installing-Xfce-4.6-on-Ubuntu-8.04-and-Ubuntu-8.10)


Run in terminal:
gpg --keyserver keyserver.ubuntu.com --recv 0E23917F5D9DCE6C
gpg --export --armor 0E23917F5D9DCE6C | sudo apt-key add - 

Add in Source code (Application / System /Software Sources -> tab ThirdParty  software)
deb [http://ppa.launchpad.net/jerome-guelfucci/ppa/ubuntu](http://ppa.launchpad.net/jerome-guelfucci/ppa/ubuntu) jaunty main

Restart the laptop  - work fine.

---

### Post by cristianrosa on 2009-08-05
Ok I was suffering of the same problems after each kernel upgrade, and I discovered that the two things that solved the connection problem with the iwl3945 are:

[LIST=1]
[*]Install linux-backports-modules-jaunty
[*]Install the new version of the firmware as suggested by stillious
[/LIST]

The first one is necessary because otherwise the default module will still look for the old firmware.
I hope this will help someone.

---

