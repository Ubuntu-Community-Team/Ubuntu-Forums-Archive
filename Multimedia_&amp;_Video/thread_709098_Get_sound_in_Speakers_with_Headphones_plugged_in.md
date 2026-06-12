---
title: "Get sound in Speakers with Headphones plugged in"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by TE7 on 2008-02-27
Getting sound in speakers with headphones pluggd in. Anybody got any ideas? Thanks in advance for any help.

Gutsy
Dell Dimension 8400 3 GHz 1G ram
SoundBlaster Live 24 Bit


tom@Dell---JT1YM51:~$ sudo update-pciids; lspci
[sudo] password for tom:
--03:30:24--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 131,114 (128K) [text/plain]

100%[====================================>] 131,114       86.57K/s             

03:30:27 (86.25 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [131114/131114]

Done.
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
04:02.0 Multimedia audio controller: Creative Labs SB Audigy LS
tom@Dell---JT1YM51:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
tom@Dell---JT1YM51:~$

---

### Post by aimaz on 2008-02-27
I had a similar problem on my Sony Vaio. This is how I fixed it

[http://ubuntuforums.org/showpost.php?p=4198018&postcount=10](http://ubuntuforums.org/showpost.php?p=4198018&postcount=10)

Hope that helps.

---

### Post by TE7 on 2008-02-27
In the last line, i set model=auto. Rebooted, didn't work. Still get sound from speakers with headphones plugged in. Anybody with with other suggestions would be greatly appreciated.

---

