---
title: "Hardware Detection Woes"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by Tehrasha on 2006-07-15
Dapper 'server' does not see my Avaya/Lucent 'World Card' Silver PCMCIA wireless card, nor the ISA->PCMCIA adapter card that it is sitting in.

This installer sees it just fine, in fact allows me to setup the wireless card so I can use it to download more packages.  But after the installation, the resulting OS sees nothing.

Running the CDROM as a recovery and dumping out to busybox, I can see that the installer detects the PCMCIA Lucent card and uses the 'orinoco' kernel module.

But when I boot Dapper, there is no mention of the card in  /var/log/dmesg  or /var/log/messages.

So what is the installer doing to detect the hardware that the fullblown install is not?](*,)

---

### Post by Tehrasha on 2006-07-16
As a followup to my own post with more information.
Using the CDROM in recovery mode, I salvaged the syslog from the installer with the following info.

> **ubuntu-server-installer /var/log/syslog exerpt::**

kernel: [4294788.211000] orinoco 0.15rc3
kernel: [4294788.221000] orinoco_cs 0.15rc3 
kernel: [4294788.303000] eth3: Hardware identity 0001:0001:0004:0002
kernel: [4294788.303000] eth3: Station identity  001f:0001:0006:0010
kernel: [4294788.303000] eth3: Firmware determined as Lucent/Agere 6.16
kernel: [4294788.303000] eth3: Ad-hoc demo mode supported
kernel: [4294788.303000] eth3: IEEE standard IBSS ad-hoc mode supported
kernel: [4294788.303000] eth3: WEP supported, 104-bit key
kernel: [4294788.303000] eth3: MAC address 00:02:2D:21:8B:BE
kernel: [4294788.303000] eth3: Station name "HERMES I"
kernel: [4294788.304000] eth3: ready
kernel: [4294788.305000] eth3: index 0x01: Vcc 5.0, irq 3, io 0x0100-0x013f
net/hw-detect.hotplug: Detected hotpluggable network interface eth3



However the full install of Dapper does not recognize the card at all.:confused: 

I suppose there is a slim chance it might be a kernel issue...
The installer uses 2.6.15-23-386 and I am using 2.6.15-26-386.
But I really dont want to install another kernel and headers without
knowing there is a good chance that it will fix it.

---

