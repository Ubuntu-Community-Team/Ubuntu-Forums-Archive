---
title: "Disable DVB card IR receiver"
date: 2009-12-01
forum: Multimedia Software
---

### Post by avoa on 2009-12-01
Hi,

I have Antec Fusion 430 Black media server running Ubuntu 9.10. I'm using Hauppage Nova-T 500 DVB-T card. Antec have built-in Soundgraph iMON IR receiver and Hauppauge have also IR receiver. My problem is that LIRC connects wrong IR receiver. 
I want to use iMON and during LIRC installation I told to use Soundgraph iMON PAD. When Ubuntu starts, it seems that LIRC connects Hauppauge IR receiver. Devices are listed:
I: Bus=0003 Vendor=15c2 Product=ffdc Version=0000
N: Name="**iMON PAD IR Mouse **(15c2:ffdc)"
P: Phys=usb-0000:00:02.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb4/4-4/4-4:1.0/input/input6
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=7
B: KEY=1f0000 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=2040 Product=8400 Version=0100
N: Name="**IR-receiver inside an USB DVB receiver**"
P: Phys=usb-0000:01:08.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/0000:01:08.2/usb3/3-1/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=14afc336 284284d00000000 0 480058000 219040000801 9e96c000000000 90020000000ffd

dmesg shows:
avo@MediaU:~$ **dmesg **|grep lirc
[    6.784900] lirc_dev: IR Remote Control driver registered, major 61 
[    8.325793] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
[    8.325833] lirc_dev: lirc_register_driver: sample_rate: 0
[    8.325890] lirc_imon: Registered iMON driver (lirc minor: 0)
[    8.345052] lirc_imon: iMON device (15c2:ffdc, intf0) on usb<4:2> initialized
[    8.345101] usbcore: registered new interface driver lirc_imon

avo@MediaU:~$ **lsusb**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 004 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 2040:8400 Hauppauge 


[    8.325793] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
[    8.325833] lirc_dev: lirc_register_driver: sample_rate: 0
[    8.325890] lirc_imon: Registered iMON driver (lirc minor: 0)
[    8.325937] input: iMON PAD IR Mouse (15c2:ffdc) as /devices/pci0000:00/0000:00:02.0/usb4/4-4/4-4:1.0/input/input6
[    8.345052] lirc_imon: iMON device (15c2:ffdc, intf0) on usb<4:2> initialized
[    8.345101] usbcore: registered new interface driver lirc_imon
/.../
[   10.382524] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   10.382590] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.382886] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   10.628097] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   10.814613] DiB0070: successfully identified
[   10.814619] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.814907] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   10.965638] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[   11.164659] DiB0070: successfully identified
[   11.164762] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:08.2/usb3/3-1/input/input7
[   11.164818] dvb-usb: schedule remote query interval to 50 msecs.
[   11.164822] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   11.165065] usbcore: registered new interface driver dvb_usb_dib0700

I have tried with Logitech Harmony 515 remote, but irw doesn't show any signals. Instead Hauppauge remote generates codes to irw.
How I can disable Hauppauge IR receiver, so that LIRC will connect iMON IR receiver?
I'm not very familiar with Linux, may-be somebody can help me to get iMON receive IR signals.

Avo Aasma

---

### Post by steefjeqv on 2009-12-01
Hi,

You can try blacklisting the hauppauge ir driver module.

In terminal : 

sudo lsmod

This command will show all drivers used. Look for the haupauge ir module and add this driver to /etc/modprobe.d/blacklist.

Greetings,
Steven

---

