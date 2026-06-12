---
title: "tv tuner not working"
date: 2011-05-06
forum: Multimedia Software
---

### Post by konsta82 on 2011-05-06
I have compro videomate m330f tv card recognised as Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
```
konsta@konsta-MS-7592:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood PRO [Radeon HD 5500 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)

```
card list says it is number 49,but tvtime tells me NO SIGNAL every time.
To make things worse.rmmod is making me problems even after it is blacklisted.
```
konsta@konsta-MS-7592:~$ sudo rmmod saa7134_alsa
[sudo] password for konsta: 
ERROR: Module saa7134_alsa is in use
konsta@konsta-MS-7592:~$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa

```
I'm using fresh installed natty.
Any ideas what to do ???

---

### Post by satish_j on 2011-05-06
you should run foll command first
```

tvtime-scanner

```

It should scan all the channels and save them in a file,then try tvtime..

---

### Post by konsta82 on 2011-05-06
this command is searching ,but says no signal so it can't find anything

---

### Post by merkez3110 on 2011-05-20
[FONT=Lucida Console]my hardware first: saa7134 / alsa650
to run it with tvtime (with sound, etc.)

don't forget to "reboot" when you're told so.

(1)
insert [/FONT][FONT=Lucida Console]"saa7134"[/FONT][FONT=Lucida Console] at the end of file "/etc/modules"

(2)
insert [/FONT][FONT=Lucida Console]"options saa7134 i2c_scan=1 card=81 tuner=54" into [/FONT][FONT=Lucida Console]"/etc/modprobe.d/options" file

reboot

(3)
$ sudo apt-get install sox libsox-fmt-all tvtime xmltv-util

(4)
$ sudo apt-get install tvtime
tv standart > PAL
sound standart > PAL-BG
frequency table > europe

(5)
$ lspci | grep SAA
will give output like as follows:
02:03.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
"02:03.0" is the address of the sound system (select yours from your output)

(6)
$ LANG=C pactl list | grep -A2 alsa
note all output lines like "alsa_input.pciXXXXXXXXXXXXXXX"
for example:
alsa_input.pci-0000_02_03.0.analog-stereo
alsa_output.pci-0000_00_10.1.analog-stereo.monitor
alsa_input.pci-0000_00_10.1.analog-stereo
select the one with the matching numbers noted in step 5
for example, my selection would be: "alsa_input.pci-0000_02_03.0.analog-stereo"

(7)
insert the line
[/FONT][FONT=Lucida Console]"load-module module-loopback source=alsa_input.pci-0000_02_03.0.analog-stereo"
at the end of file [/FONT][FONT=Lucida Console]"/etc/pulse/default.pa"

(8)
restart pulse audio
$ pulseaudio -k

or better reboot

(9)
now correct the line
[/FONT][FONT=Lucida Console]<option name="MixerDevice" value="default/Line"/>[/FONT]
in the file  [FONT=Lucida Console]"/etc/tvtime/tvtime.xml"
like:
<option name="MixerDevice" value="hw:0/PCM"/>

reboot.

start tvtime (no need to use "sudo", use the gui menu)

search the channels and you're done.

any questions? [email]merkez3110@gmail.com[/email]

[/FONT]

---

### Post by konsta82 on 2011-06-13
working options for this card are
card=49 tuner=69 (37 or 40 also works fine)

---

