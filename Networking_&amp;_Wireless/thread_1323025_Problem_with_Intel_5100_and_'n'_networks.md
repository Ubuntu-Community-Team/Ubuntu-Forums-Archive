---
title: "Problem with Intel 5100 and 'n' networks"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by Zyronic on 2009-11-11
Hallo All,

At my school they recently upgraded from wireless g to wireless n, before the change I could use the wireless without any problem, but since they upgraded it turned slow. 
A friend, who was sitting next to me, was downloading at 5 mb/s (windows 7) and me in my windows environment (windows 7) also download with the same speed. But under ubuntu I download with 5kb/s - 200 kb/s (mostly 5kb/s).

The problem is the wireless 'n', at home I got 'g' and I download with 500 kb/s.
I tried to locate the problem myself. Looking at the iwconfig I notice something strange: the bitrate (when connected) was 0 bit/s and the frequency was 2.5 (which is the g frequency). Currently as I'm writing this topic I'm connected to my home wireless (g) and I have an bitrate  of 1 mbit/s. When I changed the bitrate to 54 (at school) mbits/s (g) the frequency changed to the n domain (5k+). But still, it was slow.

Guys, what could be the problem?
You are probably interested in seeing some conf.

```
me@me-laptop:~$ dmesg | grep firmware
[   15.346100] iwlagn 0000:03:00.0: firmware: requesting lbm-iwlwifi-5000-2.ucode
[   15.381152] iwlagn 0000:03:00.0: lbm-iwlwifi-5000-2.ucode firmware file req failed: -2
[   15.381168] iwlagn 0000:03:00.0: firmware: requesting lbm-iwlwifi-5000-1.ucode
[   15.542997] iwlagn 0000:03:00.0: Loaded firmware lbm-iwlwifi-5000-1.ucode, which is deprecated. Please use API v2 instead.
[   15.543004] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12

``````
me@me-laptop:~$ dmesg | grep iwl
[   15.199608] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   15.199611] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   15.209599] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.209629] iwlagn 0000:03:00.0: setting latency timer to 64
[   15.209687] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   15.257940] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.258052] iwlagn 0000:03:00.0: irq 30 for MSI/MSI-X
[   15.267019] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.346100] iwlagn 0000:03:00.0: firmware: requesting lbm-iwlwifi-5000-2.ucode
[   15.381152] iwlagn 0000:03:00.0: lbm-iwlwifi-5000-2.ucode firmware file req failed: -2
[   15.381168] iwlagn 0000:03:00.0: firmware: requesting lbm-iwlwifi-5000-1.ucode
[   15.542997] iwlagn 0000:03:00.0: Loaded firmware lbm-iwlwifi-5000-1.ucode, which is deprecated. Please use API v2 instead.
[   15.543004] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   15.695245] Registered led device: iwl-phy0::radio
[   15.695290] Registered led device: iwl-phy0::assoc
[   15.695324] Registered led device: iwl-phy0::RX
[   15.695359] Registered led device: iwl-phy0::TX
me@me-laptop:~$ ls -al /lib/firmware | grep 5000
-rw-r--r--  1 root root   12401 2009-10-18 00:55 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root  345008 2009-10-18 00:55 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2009-10-18 00:55 iwlwifi-5000-2.ucode
me@me-laptop:~$ uname -r
2.6.31-14-generic

```[   15.257940] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
That is something I call weird, where is the 'n' network, while it says: iwlagn <--

I installed the backport modules generic 2.6.31-14. 

So deprate as I am, I tried To use Wireless Network Drivers (the windows wireless thingy) and downloaded the driver for 5100, (netw5x32.inf) but it says: invalid driver (downloaded it from the asus website (got a asus f6v))
I don't know what this function is (the windows driver)  and/or if that is really a fix for this. or where to get a working driver.

I think that the problem is in the firmware. What you thing about the problem?

Thanks for ready so far, hope you got an idea for a fix.
-Zyronic

edit: I can't change the bitrate higher than 54 (it changes to 0)

EDIT2: Problem solved: click [here]("http://www.uluga.ubuntuforums.org/showpost.php?p=9286373&postcount=10") for fix

---

### Post by Zyronic on 2009-11-12
Did some research: 5300 got the same problem, the only difference is that he got a bitrate set: 54 mb/s but still downloads at a rate of 20kb/s. 

It is wireless wpa2 enterprice, on a N network. 

Suggestions?

---

### Post by Zyronic on 2009-11-13
Ok, I asked the ICT staff and they said that wireless 'n' is not 100% supported for linux, for a lot of cards it is hard to use.
They won't give support for linux, but they said it would be fixed by forcing to use any other 802.11, How do I do that, setting the bitrate won't fix it.

So how can I force to use 802.11a/b/g?

---

### Post by Zyronic on 2009-11-14
140 views and no one got a suggestion?

I&#7743; trying to find out how to make me AGN card to a AG card, so that my card acts like a 802.11g card. 
How can I do this?
or knows why the 802.11n is so slow.

---

### Post by supervalino on 2009-11-18
Try this:

[http://baheyeldin.com/technology/linux/intel-wireless-wifi-link-5100-iwlagn-kubuntu-karmic-koala-910.html](http://baheyeldin.com/technology/linux/intel-wireless-wifi-link-5100-iwlagn-kubuntu-karmic-koala-910.html)

---

### Post by araysuck on 2009-12-26
> **supervalino said:**
> Try this:

[http://baheyeldin.com/technology/linux/intel-wireless-wifi-link-5100-iwlagn-kubuntu-karmic-koala-910.html](http://baheyeldin.com/technology/linux/intel-wireless-wifi-link-5100-iwlagn-kubuntu-karmic-koala-910.html)
I've tried to do that steps, but I still have an error message when I try to do "make" command. 
> /home/araysuck/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x/rtl8187_leds.c: In function ‘rtl8187_unregister_led’:
/home/araysuck/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x/rtl8187_leds.c:170: error: implicit declaration of function ‘flush_delayed_work’
make[4]: *** [/home/araysuck/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x/rtl8187_leds.o] Error 1
make[3]: *** [/home/araysuck/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x] Error 2
make[2]: *** [/home/araysuck/compat-wireless-2009-12-11/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/araysuck/compat-wireless-2009-12-11] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Error 2
And then I try to pass this error with next step (sudo make install), then I have another one like this:
> araysuck@araysuck-laptop:~/compat-wireless-2009-12-11$ sudo make install
[sudo] password for araysuck: 
WARNING: -e needs -E or -F
Your old wireless subsystem modules were left intact:

updates/cw/mac80211.ko
updates/cw/cfg80211.ko
updates/cw/lib80211.ko
updates/cw/adm8211.ko
updates/cw/ar9170usb.ko
updates/cw/at76c50x-usb.ko
updates/cw/ath.ko
updates/cw/ath5k.ko
updates/cw/ath9k.ko
updates/cw/b43.ko
updates/cw/b43legacy.ko
updates/cw/b44.ko
updates/cw/cdc_ether.ko
updates/cw/eeprom_93cx6.ko
updates/cw/ipw2100.ko
updates/cw/ipw2200.ko
updates/cw/iwl3945.ko
updates/cw/iwlagn.ko
updates/cw/iwlcore.ko
updates/cw/lib80211_crypt_ccmp.ko
updates/cw/lib80211_crypt_tkip.ko
updates/cw/lib80211_crypt_wep.ko
updates/cw/libertas.ko
updates/cw/libertas_cs.ko
updates/cw/libertas_sdio.ko
updates/cw/libertas_spi.ko
updates/cw/libertas_tf.ko
updates/cw/libertas_tf_usb.ko
updates/cw/libipw.ko
updates/cw/mac80211_hwsim.ko
updates/cw/mwl8k.ko
updates/cw/p54common.ko
updates/cw/p54pci.ko
updates/cw/p54spi.ko
updates/cw/p54usb.ko
updates/cw/rndis_host.ko
updates/cw/rndis_wlan.ko
updates/cw/rt2400pci.ko
updates/cw/rt2500pci.ko
updates/cw/rt2500usb.ko
updates/cw/rt2x00lib.ko
updates/cw/rt2x00pci.ko
updates/cw/rt2x00usb.ko
updates/cw/rt61pci.ko
updates/cw/rt73usb.ko
updates/cw/rtl8180.ko
updates/cw/rtl8187.ko
updates/cw/ssb.ko
updates/cw/usb8xxx.ko
updates/cw/usbnet.ko
updates/cw/zd1211rw.ko

make -C /lib/modules/2.6.31-14-generic/build M=/home/araysuck/compat-wireless-2009-12-11 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/araysuck/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x/rtl8187_leds.o
/home/araysuck/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x/rtl8187_leds.c: In function ‘rtl8187_unregister_led’:
/home/araysuck/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x/rtl8187_leds.c:170: error: implicit declaration of function ‘flush_delayed_work’
make[4]: *** [/home/araysuck/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x/rtl8187_leds.o] Error 1
make[3]: *** [/home/araysuck/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x] Error 2
make[2]: *** [/home/araysuck/compat-wireless-2009-12-11/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/araysuck/compat-wireless-2009-12-11] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Error 2

What must I suppose to do with those error message?
FYI, I'm using Ubuntu Karmic Koala on my Lenovo Y450.
This is my lspci:
> araysuck@araysuck-laptop:~/compat-wireless-2009-12-11$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
07:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
07:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
07:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

Thx before..

---

### Post by iamnotcoward on 2010-01-13
I'm wondering what to do with those error messages as well, even though I'm using T400 with a different kernel and the wireless card doesn't get recognised by Ubuntu.

Thx

---

### Post by Zyronic on 2010-05-11
Hoping that this problem would be fixed with ubuntu 10.04.
So this morning I installed ubuntu 10.04. Problem still excist.

I just finished building the compat drivers by doing the following
```
sudo aptitude update
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.34/compat-wireless-2.6.34-rc4.tar.bz2
sudo aptitude install module-assistant
sudo m-a prepare
sudo m-a update
tar xjf compat-wireless-2.6.34-rc4.tar.bz2 
cd compat-wireless-2.6.34-rc4
./scripts/driver-select iwlwifi
make
sudo make install
sudo make unload
sudo shutdown -r 0
```Can't confirm if this fixed the problem. I will post tomorrow if it is fixed.

---

### Post by Zyronic on 2010-05-12
Problem ain't fixed.
At least the Bit Rate is at a better rate.
Anyone got some suggestions?
```

wlan0     IEEE 802.11abgn  ESSID:"hu-eduroam-wpa"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:27:0D:0A:6D:51   
          Bit Rate=**72.2 Mb/s**   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Zyronic on 2010-05-12
Problem solved!!!

[https://bugs.launchpad.net/ubuntu/+bug/575492](https://bugs.launchpad.net/ubuntu/+bug/575492)

```
sudo nano /etc/modprobe.d/options.conf
```
This file does not excist, add this:
```
options iwlagn 11n_disable=1 11n_disable50=1
```
Reboot and it's fixed.

---

### Post by PandoraJones on 2010-11-01
> **Zyronic said:**
> Problem solved!!!

[https://bugs.launchpad.net/ubuntu/+bug/575492](https://bugs.launchpad.net/ubuntu/+bug/575492)

```
sudo nano /etc/modprobe.d/options.conf
```
This file does not excist, add this:
```
options iwlagn 11n_disable=1 11n_disable50=1
```
Reboot and it's fixed.

OOPS!  did this and now my wireless card is not detected. how do i undo it?

---

### Post by rockcrawler on 2010-11-04
> **PandoraJones said:**
> OOPS!  did this and now my wireless card is not detected. how do i undo it?

Remove the file you created, wither via command line with the "rm" command, or via nautilus, and reboot again.

---

