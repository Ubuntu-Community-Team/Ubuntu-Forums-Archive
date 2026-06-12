---
title: "How to get HDTV USB DVB-T working? Can not scan frequencies"
date: 2010-06-02
forum: Multimedia Software
---

### Post by Svens on 2010-06-02
Hello everybody and have a nice day!
I have got a little problem here with my new HDTV USB DVB-T receiver.
My USB stick is this one:
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=370307620849&ssPageName=STRK:MEWNX:IT](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=370307620849&ssPageName=STRK:MEWNX:IT)
I can't get it to scan my frequencies.
PC finds the stick (lsusb):
```
Bus 002 Device 005: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick

```
When I plug it in, dmesg shows this:
```
[ 5680.696043] usb 2-2: new high speed USB device using ehci_hcd and address 7
[ 5680.834917] usb 2-2: configuration #1 chosen from 1 choice
[ 5680.849872] af9015: tuner id:179 not supported, please report!
[ 5680.852951] Afatech DVB-T 2: Fixing fullspeed to highspeed interval: 10 -> 7
[ 5680.853438] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.1/input/input14
[ 5680.853644] generic-usb 0003:15A4:9016.0005: input,hidraw1: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:1d.7-2/input1

```
I installed from Synaptic package "dvb-apps" and "linux-firmware-nonfree".
As I read on the internet, if everything is fine, then when I plug the USB in, it should create directory /dev/dvb/, but it does not. Then I found on the internet a script file named "MAKEDEV-DVB.sh", which creates the necesary directory, because if the directory is not created, then after ```
sudo scan /usr/share/dvb/dvb-t/lv-Riga

```
it shows
```
scanning /usr/share/dvb/dvb-t/lv-Riga
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

```
But if the directory is created, then after the same command I have
```
scanning /usr/share/dvb/dvb-t/lv-Riga
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 19 No such device

```
I found on the internet a firmware for my USB HDTV DVB-T stick named "dvb-usb-af9015.fw" and copied it into /lib/firmware/ but I have not seen any difference with that.

That is as far as I can get. I don't know what to do next. Could anyone please help me with this? Any help is appreciate. 
Thank you!

---

### Post by sohlinux on 2010-10-18
did you get this working? I have same problem

---

