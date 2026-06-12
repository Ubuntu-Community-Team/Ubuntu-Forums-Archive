---
title: "Driver for KWorld PC160 tuner"
date: 2011-11-14
forum: Mythbuntu
---

### Post by MickSulley on 2011-11-14
Hi,

I have a KWorld PC160 PCI tuner.  I installed it in 11.04 and it was working, but I have just done a fresh install of 11.10 (Ubuntu and added the myth bits) and now I cannot see it is the backend Capture Cards setup screen.  I have a TBS6981 as well and I can see that.


In dmesg I see
```
[   15.578540] dvb-usb: found a 'KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T)' in cold state, will try to load a firmware
[   15.583470] dvb-usb: did not find the firmware file. (dvb-usb-af9015.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[   15.583490] dvb_usb_af9015: probe of 3-1:1.0 failed with error -2
[   15.583528] usbcore: registered new interface driver dvb_usb_af9015
[   15.630190] fbcon: inteldrmfb (fb0) is primary device

```

lspci shows
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82578DM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
01:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
04:01.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
04:01.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```

I found a hit that looked promising [http://doc.ubuntu-fr.org/af9015](http://doc.ubuntu-fr.org/af9015) but it is in French, which I don't speak, and either it doesn't work or something was lost in the Google translation.

Several hits say that the driver is built into the kernel but a couple say that it is not working in 11.10 and needs to be loaded.

Can anyone point me to some instructions to download and install the driver?

Thanks
Mick

---

### Post by nickrout on 2011-11-14
```
sudo apt-get install linux-firmware-nonfree
```

That firmware seems to be there:

[http://packages.ubuntu.com/oneiric/all/linux-firmware-nonfree/filelist](http://packages.ubuntu.com/oneiric/all/linux-firmware-nonfree/filelist)

---

### Post by MickSulley on 2011-11-15
That seems to be it!

Thanks for your help
Mick

---

