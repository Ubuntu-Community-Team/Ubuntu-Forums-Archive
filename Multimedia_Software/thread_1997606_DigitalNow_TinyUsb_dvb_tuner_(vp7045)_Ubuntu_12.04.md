---
title: "DigitalNow TinyUsb dvb tuner (vp7045) Ubuntu 12.04"
date: 2012-06-05
forum: Multimedia Software
---

### Post by michaelAust on 2012-06-05
I have a tinyusb (from lsusb, Bus 002 Device 004: ID 13d3:3206 IMC Networks DNTV Live! Tiny USB2 BDA (No Remote). dmesg output follows 
```
[   99.748978] usb 2-1: new high-speed USB device number 3 using ehci_hcd
[   99.881261] dvb-usb: found a 'DigitalNow TinyUSB 2 DVB-t Receiver' in cold state, will try to load a firmware
[   99.906937] dvb-usb: downloading firmware from file 'dvb-usb-vp7045-01.fw'
[   99.971786] usb 2-1: USB disconnect, device number 3
[   99.971817] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[  101.721792] usb 2-1: new high-speed USB device number 4 using ehci_hcd
[  101.855290] dvb-usb: found a 'Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II)' in warm state.
[  102.009032] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  102.009283] DVB: registering new adapter (Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II))
[  102.080810] dvb-usb: MAC address: 08:ca:1a:c7:b7:ff
[  102.092720] DVB: registering adapter 0 frontend 0 (Twinhan VP7045/46 USB DVB-T)...
[  102.092956] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/input/input16
[  102.093045] dvb-usb: schedule remote query interval to 400 msecs.
[  102.248157] dvb-usb: Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II) successfully initialized and connected.

```
The tinyusb is a very sensitive tuner and it works well, and is supported in most distros. However.when the tuner is receiving a tv signal it keeps on sending tab keystrokes to the computer (it has an ir receiver in it which emulates a keyboard, I found out what keystroke it was sending with xev). This makes other apps behave strangely. This happens using gnome-dvb-client, as well as kaffeine, and does not happen with either of these programs in Ubuntu 10.04 or Linux Mint 10. It also happens in Lubuntu 12.04, Solus OS 1 (debian squeeze based, 3.0 kernel), and Linux Mint 13. This tuner is recognized properly when plugged in and tunes tv as expected. I have googled all over the place with no luck.

Edit: I compared the firmware from Mint 10 (which works properly) and Ubuntu 12.04 (which does not) as follows:
```
michael@VgBoxSda6Ubuntu12:/media/sda9/Docs$ cmp Ubuntu1204_dvb-usb-vp7045-01.fw Mint10_dvb-usb-vp7045-01.fw 
michael@VgBoxSda6Ubuntu12:/media/sda9/Docs$

```

Both firmwares are the same, so the OS is presumably getting the same output from the usb port. but it must handle it differently now.

---

### Post by BrimboriuM on 2012-06-24
I have exactly the same problem. I am using a Fujitsu-Siemens DVB-T Mobile TV Tuner stick with the same chip inside (TwinhanDTV Alpha/MagicBox II) on Ubuntu 12.04.
Firmware file is dvb-usb-vp7045-01.fw.
I use kaffeine as client, but it keeps on sending tab keys even when scanning channels with w-scan.

It worked perfectly on 10.04.

---

### Post by michaelAust on 2012-06-24
Thanks BrimboriuM,

There is a bug on launchpad for this, I have added my input. if you add yours maybe it will help get something done. The bug is at

[https://bugs.launchpad.net/ubuntu/+source/linuxtv-dvb-apps/+bug/871927?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linuxtv-dvb-apps/+bug/871927?comments=all")

I would say it is worth your while to sign up for a launchpad account so you can add to this bug. There is probably some place further upstream ie. the Linux kernel itself rather than the Ubuntu kernel guys, where we can raise a bug but I have not investigated this yet.

Michael.

---

### Post by BrimboriuM on 2012-06-24
I just added a reply there. :roll:

---

### Post by BrimboriuM on 2012-07-11
The only solution I found is to disable the ir controller:

/etc/modprobe.d/dvbt.conf:[FONT=monospace]
[/FONT]options dvb-usb disable_rc_polling=1

---

### Post by michaelAust on 2012-07-29
> **BrimboriuM said:**
> The only solution I found is to disable the ir controller:

/etc/modprobe.d/dvbt.conf:[FONT=monospace]
[/FONT]options dvb-usb disable_rc_polling=1

Thanks for that, it works well.

---

### Post by wildpig953 on 2012-08-24
Hi guys
I have a pair of these tuners and am experiencing the same problem.

I am also on a steep learning curve, first linux box, been using Windows MCE since xpMCE.


sorry to ask but i dont know what to do with this information
"/etc/modprobe.d/dvbt.conf:
options dvb-usb disable_rc_polling=1".

I do understand that this bit "options dvb-usb disable_rc_polling=1" needs to be in a file called "dvbt.conf" in the location "/etc/modprobe.d/"
I just dont know the terminal commands to make it happen.

will this command "options dvb-usb disable_rc_polling=1" disable the IR for all dvb-usb tuners?
I ask because i think the DVB-IR receivers are interfering with the dedicated USB IR reciever for my windows MCE remote.

Thanks in advance
 
My system is the Mythbuntu 12.04 with all the updates.

---

### Post by michaelAust on 2012-08-26
> **wildpig953 said:**
> Hi guys
sorry to ask but i dont know what to do with this information
"/etc/modprobe.d/dvbt.conf:
options dvb-usb disable_rc_polling=1".

I do understand that this bit "options dvb-usb disable_rc_polling=1" needs to be in a file called "dvbt.conf" in the location "/etc/modprobe.d/"
I just dont know the terminal commands to make it happen.


You would do
sudo gedit  /etc/modprobe.d/dvbt.conf

and add the line
options dvb-usb disable_rc_polling=1

> **wildpig953 said:**
> Hi guys
will this command "options dvb-usb disable_rc_polling=1" disable the IR for all dvb-usb tuners?


I only have one of these tuners so I don't know, it works for mine.
It would be good if you could add your voice to the bug as I suggested above.

---

