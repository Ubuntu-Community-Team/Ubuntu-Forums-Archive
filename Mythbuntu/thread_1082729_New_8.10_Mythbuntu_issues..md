---
title: "New 8.10 Mythbuntu issues."
date: 2009-02-28
forum: Mythbuntu
---

### Post by woosey on 2009-02-28
Hi guys,

I set up mythbuntu on an AMD dual core with 1GB ram, 250gb hard drive, using a TD-500 which worked out of the box, however i have a couple of problems which i can't seem to cure, has anyone got any ideas?

1.The IR receiver isn't seen by the system
2.The reception when scanning goes from 60% to 20% and so it only picks up around 5 channels, which all have bad frame loss on them, making them unwatchable :( When the aerial is connected to the TV, it picks up all the channels and have excellent signal strength for all channels.

I've turned on the internal amp on the card, so not sure what else i can do?

Thanks

Chris

---

### Post by ian dobson on 2009-02-28
Hi,

With regards to the ir have a look here [http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Remote_Control](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Remote_Control)

Regards
Ian Dobson

---

### Post by woosey on 2009-02-28
> **ian dobson said:**
> Hi,

With regards to the ir have a look here [http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Remote_Control](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI#Remote_Control)

Regards
Ian Dobson

Hi,

Thanks for that, but its not seen by the system -

```
root@mythbuntu:~# cat /proc/bus/input/devices | grep IR
root@mythbuntu:~#

```

Has anyone seen this before?

Full devices list is -

```
root@mythbuntu:~# cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c313 Version=0110
N: Name="LITEON Technology USB Multimedia Keyboard"
P: Phys=usb-0000:00:0b.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input1
U: Uniq=
H: Handlers=kbd event1
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c313 Version=0110
N: Name="LITEON Technology USB Multimedia Keyboard"
P: Phys=usb-0000:00:0b.0-4/input1
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.1/input/input2
U: Uniq=
H: Handlers=kbd event2
B: EV=13
B: KEY=1810 8001000 e0000 0 0 0
B: MSC=10

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input3
U: Uniq=
H: Handlers=kbd event3
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
U: Uniq=
H: Handlers=kbd event4
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
U: Uniq=
H: Handlers=kbd event5
B: EV=3
B: KEY=100000 0 0 0

root@mythbuntu:~#

```

---

### Post by woosey on 2009-02-28
Incase anyone comes across this thread, i fixed this by adding the 1.2FW,

```

root@mythbuntu:~# dmesg | grep dvb
[   12.628781] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[   12.628785] firmware: requesting dvb-usb-dib0700-1.20.fw
[   13.774531] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   14.484033] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   14.485136] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   14.896362] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.264336] dvb-usb: schedule remote query interval to 50 msecs.
[   15.264342] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   15.264553] usbcore: registered new interface driver dvb_usb_dib0700

```

Now inputs shows -

```
I: Bus=0003 Vendor=2040 Product=8400 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:04:09.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:10.0/0000:04:09.2/usb3/3-1/input/input6
U: Uniq=
H: Handlers=kbd event6
B: EV=3
B: KEY=14afc336 284284d 0 0 0 4 80058000 2190 40000801 9e96c0 0 900200 ffd


```

---

### Post by woosey on 2009-03-01
Fixed the poor video performance by installing the 177 nvidia driver.

---

