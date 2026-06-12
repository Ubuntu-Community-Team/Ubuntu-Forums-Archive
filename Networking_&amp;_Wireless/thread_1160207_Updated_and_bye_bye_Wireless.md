---
title: "Updated and bye bye Wireless"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by monsieurdozier on 2009-05-15
I just updated yesterday, Ubuntu 8.10, and my wireless is gone.

Normally I use ath0, but it is not on the list of iwlist

Here's lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Here's iwlist scanning:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

Then I tried to run this:

sudo ifconfig ath0 up

and got this:

ath0: ERROR while getting interface flags: No such device



ath0 is not even listed.  I'm running a Toshiba Satellite with Wicd.

Thanks much,
Monsieur Dozier

---

### Post by monsieurdozier on 2009-05-15
Here's what might be a relevant section of /var/log/syslog

May 15 10:58:06 FreeRangeChicken kernel: [   17.140244] lp: driver loaded but no devices found
May 15 10:58:06 FreeRangeChicken kernel: [   17.153873] ath_hal: module license 'Proprietary' taints kernel.
May 15 10:58:06 FreeRangeChicken kernel: [   17.156064] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
May 15 10:58:06 FreeRangeChicken kernel: [   17.205214] wlan: 0.9.4
May 15 10:58:06 FreeRangeChicken kernel: [   17.212763] ath_pci: 0.9.4
May 15 10:58:06 FreeRangeChicken kernel: [   17.212824] ath_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May 15 10:58:06 FreeRangeChicken kernel: [   17.212840] ath_pci 0000:03:00.0: setting latency timer to 64
May 15 10:58:06 FreeRangeChicken kernel: [   17.261374] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
May 15 10:58:06 FreeRangeChicken kernel: [   17.261426] ath_pci 0000:03:00.0: PCI INT A disabled

Hopefully that will help.

Monsieur Dozier

---

### Post by Sapphire Rayne on 2009-05-16
The following is what has worked for me when my wireless gets knocked out...

System>Hardware Drivers--make sure you untick anything for Atheros

Reboot.

In a terminal:
```

sudo apt-get install checkinstall
```  **if this hasn't already been installed**

```
sudo apt-get build-essential checkinstall
```

```
sudo apt-get update
```

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r4016-20090429.tar.gz
```

```
tar zxvf madwifi-hal-0.10.5.6-r4016-20090429.tar.gz
```

```
cd madwifi-hal-0.10.5.6-r4016-20090429
```

```
make
```

```
sudo checkinstall
```
```

sudo reboot
```


After rebooting, go back into System>Hardware Drivers and retick the ones you unticked for Atheros.  Reboot again.

Your wireless should be up and running properly after doing all of this.  I also made sure I saved a copy of the tar.gz file on a separate disk, just in case it had gotten deleted off my computer, that way, I don't have to redownload the package.  Good luck, and hope this helps. :)

---

### Post by monsieurdozier on 2009-05-16
Worked like a charm.  Thanks a bunch.

Monsieur Dozier

---

### Post by Sapphire Rayne on 2009-05-16
No problem...anytime!  :)

---

