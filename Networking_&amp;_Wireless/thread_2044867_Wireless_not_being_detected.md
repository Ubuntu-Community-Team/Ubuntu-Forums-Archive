---
title: "Wireless not being detected"
date: 2012-08-20
forum: Networking &amp; Wireless
---

### Post by Koolmaster on 2012-08-20
Someone gave me an old dell d610. It was running slow, so a friend suggested me Ubuntu and gave me a 10.10. which I installed right away. Its much better than the previous Xp it used to run on, except the wi-fi doesnt work. I tried for solutions on the Internet, but no avail. So I require the experts' advice.
I dont know if it worked on Xp.
From what i came to know, here's what all you need:

dmin9@admin9-Latitude-D610:~$ sudo lshw -C network
[sudo] password for admin9: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:43:4b:6a:29
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=5751-v3.29a ip=192.168.0.100 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:dfcf0000-dfcfffff
admin9@admin9-Latitude-D610:~$ sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Thanks in advance!

---

### Post by chili555 on 2012-08-20
So far, we see nothing in your readings that could be a wireless device. Please run and post:```
lspci -nn
```We are suspicious that your Dell has no wireless card or that it is defective.

---

### Post by irv on 2012-08-20
I have a Broadcom BCM4311 so if you have this card you can get it going by following these steps. Make sure you are on a wire conneted to the Internet to get your wifi going.

1.) Make sure you have dkms installed first.
```
sudo apt-get install dkms
```
2.) Uninstalled bcmwl-kernel-source package
```
sudo apt-get remove bcmwl-kernel-source
```
3.) Install firmware-b43-installer package
```
sudo apt-get install firmware-b43-installer
```
4.) Installed b43-fwcutter packager
```
sudo apt-get install b43-fwcutter
```
5.) Type into the terminal
```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```
This should be the output:
> # which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
You should be able to see any wireless connections in range at this point.

---

### Post by Koolmaster on 2012-08-20
@chili555:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M22 [Mobility Radeon X300] [1002:5460]
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
03:01.5 Communication controller [0780]: Texas Instruments PCI6515 SmartCard Controller [104c:8038]


@irv:

This is the output i got:

# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
options iwlagn 11n_disable=1
alias pci:v000014E4d00004311sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00000009sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv0000000Asd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper

---

### Post by irv on 2012-08-20
I see your card is different then mine. You have the BCM5751 Broadcom. I don't know if my instructions will work for you. Broadcom card have been a pain with Ubuntu. Hopefully someone can help you with this.

---

### Post by chili555 on 2012-08-20
We still see no wireless device at all. Your Broadcom...>  Broadcom Corporation NetXtreme BCM5751 Gigabit *Ethernet* PCI Express [14e4:1677] (rev 01)...is an ethernet device, not wireless.

I see no wireless device to enable. As I said before, we are suspicious that your Dell has no wireless card or that it is defective. I do see that ndiswrapper was attempted for several different Broadcom devices; I see none of them in your readings.

Sorry.

---

### Post by irv on 2012-08-20
My mistake I thought the Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01) was the wireless. I have this Broadcom wireless thing stuck in my brain.
I was wondering if the wireless is turn off in the BIOS if it is installed and working? I also have a switch on the side of my laptop that turns it on and off. Maybe it has one and it is turned off? Just a couple of things to check.

---

### Post by chili555 on 2012-08-20
> I also have a switch on the side of my laptop that turns it on and off. Maybe it has one and it is turned off? Even in this case, it will still show up in *lspci*. The state of the wireless switch will be provided in:```
rfkill list all
```I certainly suggest a run through the BIOS to look for wireless enabled or disabled.

---

### Post by irv on 2012-08-20
> **chili555 said:**
> Even in this case, it will still show up in *lspci*. The state of the wireless switch will be provided in:```
rfkill list all
```I certainly suggest a run through the BIOS to look for wireless enabled or disabled.

Again you are right, it should show up even with the switch off. Yes the BIOS is the place to start.

---

### Post by Koolmaster on 2012-08-20
Thanks for your responses. I had already checked the Bios before starting the thread.It was off and despite turning it on , nothing changed. Also,The card is physically present in its slot, checked it myself. This model doesn't have any physical switch. only Fn+F2.

Anymore Ideas?

---

### Post by irv on 2012-08-20
> **Koolmaster said:**
> Thanks for your responses. I had already checked the Bios before starting the thread.It was off and despite turning it on , nothing changed. Also,The card is physically present in its slot, checked it myself. This model doesn't have any physical switch. only Fn+F2.

Anymore Ideas?

If you turned it on then it should be seen. Reboot one more time and go back into the BIOS and make sure it stayed on. I seen this happen where things sometimes just seem to get turn off even after setting them. If it show that it is still on, then the only thing it could be is a bad or a card that is not seated in the slot. And if it is a integrated card then it is bad.
Were you running another OS where it was working?

---

### Post by chili555 on 2012-08-20
Unless the operating system recognizes at least its presence, there isn't anything else we can do. It may be electrically defective. Did you try to remove it and reseat it? Are the antenna leads secure?

---

### Post by Koolmaster on 2012-08-20
Thanks irv! Problem solved.!Works perfectly now. BIOS was the culprit. I dont know how it got off despite turning it on. I was struggling with it whole weekend..

---

### Post by irv on 2012-08-20
> **Koolmaster said:**
> Thanks irv! Problem solved.!Works perfectly now. BIOS was the culprit. I dont know how it got off despite turning it on. I was struggling with it whole weekend..

Sometimes we just have to backup to go forward. Best way to get out of a rut.

---

