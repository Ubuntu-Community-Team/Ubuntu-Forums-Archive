---
title: "Wireless (Wifi) stoped running from one day to another"
date: 2012-07-13
forum: Networking &amp; Wireless
---

### Post by DK-one on 2012-07-13
Dear Ubuntu friends,

I'm running 10.04 LTS - Lucid Lynx on a Lenovo T400 since quite a while. Unfortunately since a couple of days my wifi does not work any more. My WIFI router works for sure because  my other PC from work works fine. Unfortunately I'm stuck with the regular checks. The option "Wifi Network activate" in the dropdown (rigth click on the wifi-sign) is faded out and can not be clicked.
Can I some how check if my wifi card works in general? I would appreciate any help.

Thank you

DK-one

---

### Post by Kirk Schnable on 2012-07-13
Could you please post the output of the following commands, to give us more information to work with?

```
uname -r
```

```
lspci
```

```
iwconfig
```

Thanks,
Kirk

---

### Post by DK-one on 2012-07-13
Hi thanks for the fast reply. Please find below the asked comand line messages:
```
dominique@dominique-laptop:~$ uname -r
2.6.32-41-generic

```
```
dominique@dominique-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
```

```
dominique@dominique-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by Kirk Schnable on 2012-07-13
Unless this is your post, it looks like someone else is having issues with your chipset here:
[http://askubuntu.com/questions/158653/performance-problem-with-an-intel-wireless-5100](http://askubuntu.com/questions/158653/performance-problem-with-an-intel-wireless-5100)

I will continue researching and see if anything else of interest comes up.

Kirk

---

### Post by Kirk Schnable on 2012-07-13
Here's some more information I found for you.  It sounds like the issue may be related to the Wireless N of your card.  The solution may be to disable the N and connect with G.

Here are some places other people are discussing similar issues with your chipset:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575492](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575492)
[http://ubuntuforums.org/showthread.php?p=12084325](http://ubuntuforums.org/showthread.php?p=12084325)

This looks like it might be the workaround you need:
[http://hardc0l2e.wordpress.com/2010/05/19/intel-5100-agn-on-ubuntu-10-04/](http://hardc0l2e.wordpress.com/2010/05/19/intel-5100-agn-on-ubuntu-10-04/)

It might also be worthwhile to try a 12.04 Live CD and see if the driver issue is fixed in the new distro.  If that's the case, compiling newer drivers for your older kernel might be a solution worth exploring as well.

Kirk

---

