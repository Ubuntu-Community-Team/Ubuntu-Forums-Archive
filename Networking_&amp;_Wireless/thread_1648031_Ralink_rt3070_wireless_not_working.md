---
title: "Ralink rt3070 wireless not working"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by clarett on 2010-12-18
I just bought a novatech x10-TP netbook which has a Ralink rt3070 wireless card.
I just cannot get it to work.
The wireless network is enabled but it is grey and says "Disconnected".  There are at least 4 wireless networks (1 my own!!) 'visible' in my house so it should be picking up something!

I've tried all the fixes mentioned in these threads:
[https://answers.launchpad.net/ubuntu/+question/128344](https://answers.launchpad.net/ubuntu/+question/128344)
[http://ohioloco.ubuntuforums.org/showthread.php?p=9831137](http://ohioloco.ubuntuforums.org/showthread.php?p=9831137)

but none of them work.  The only change was when I blacklisted rt2870 - then the wireless card 'disappeared' - it wasn't registered at all.

Feeling very frustrated!!
I'm a newbie to linux so need fairly basic instructions.  I did try and install the linux drivers for rt3070 from Ralink website but couldn't.  Unpacked it ok but couldn't get into os/linux/config to make the necessary changes there.  Right now I can't remember the exact error messages but something about not having a target.

Any help would be really appreciated.  I bought a novatech especially cos it didn't have an operating system and didn't want to line MS's pocket but am banging my head against the wall a little.

Thanks

---

### Post by chili555 on 2010-12-18
Before we proceed further, let's see exactly what device you have. Please post:```
lspci -nn
sudo modprobe rt2870sta
dmesg | grep -i rt2
```Thanks.

---

### Post by clarett on 2010-12-18
following lspci -nn I got this:

00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

---

### Post by clarett on 2010-12-18
Then...

clare@clare-laptop:~$ sudo modprobe rt2870sta
clare@clare-laptop:~$ dmesg | grep -i rt2
[   12.674392] Registered led device: rt2800usb-phy0::radio
[   12.674450] Registered led device: rt2800usb-phy0::assoc
[   12.674509] Registered led device: rt2800usb-phy0::quality
[   12.674812] usbcore: registered new interface driver rt2800usb
[   13.326429] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   13.344994] usbcore: registered new interface driver rt2870
[   19.692219] rt2800usb 1-6:1.0: firmware: requesting rt2870.bin

---

### Post by clarett on 2010-12-18
I also did this as I'm aware that the wireless is usb rather than pci (not that I really know what that means!!)

clare@clare-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 002: ID 0ac8:3343 Z-Star Microelectronics Corp. Sirius USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2010-12-18
This device is supposed to work with the module rt2800usb and not rt2870sta. Please make sure that the file /etc/modprobe.d/blacklist.conf shows this line:```
blacklist rt2870sta
```Now reboot.

Run and post:```
lsmod | grep rt2
iwconfig
```Thanks.

---

### Post by clarett on 2010-12-18
thanks for getting back to me.
Blacklisted as you said - no change still showing the wireless network as disconnected.

Then ran the code you gave me:

clare@clare-laptop:~$ lsmod | grep rt2
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126528  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
clare@clare-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by clarett on 2010-12-18
Though it didn't have any smileys when I pasted it in!!

---

### Post by chili555 on 2010-12-18
It all looks pretty healthy, actually. What does this tell us?```
sudo iwlist wlan0 scan
```What happens when you click the Network Manager icon? Do you see networks? Does it try to connect? Is your ethernet disconnected at the time?

---

### Post by clarett on 2010-12-18
glad it's making sense to you!!

ok from the last bit

clare@clare-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for clare: 
wlan0     Interface doesn't support scanning : Network is down

I always check the wireless with the ethernet disconnected.  There's been no change in what Network   Manager says:  In grey:   "Wireless network" and underneath "disconnected"
Which I understand to mean that it's not seeing any networks when I know for a fact that there's at least 4

Thanks

---

### Post by chili555 on 2010-12-18
I am studying this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/602213](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/602213)

I am disappointed that there doesn't seem to be a definitive fix, however, I suggest you try the technique in post #29. You might add to the bug report if your laptop also works as listed.

May I see:```
lsmod | grep -e acpi -e wmi
```Thanks.

---

### Post by clarett on 2010-12-19
Hi

I tried installing the package mentioned in that thread but it didn't work - still no change.
Someone suggested blacklisting rt2800usb instead of rt2870sta which I tried but had no effect.
So that's where it stands at the moment.

The output that you asked for:

clare@clare-laptop:~$ lsmod | grep -e acpi -e wmi
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Thanks for your time

---

### Post by chili555 on 2010-12-19
Is this any help?> This issue still effects me running 10.10 after an upgrade. Wireless does work if I activate the wireless hotkey during the bootsplash.What does this tell us?```
rfkill list all
sudo rfkill unblock all
```Thanks.

---

### Post by clarett on 2010-12-19
Hi
I tried using the hotkey while it was booting but it didn't make any difference.

This is what I got with the code:

clare@clare-laptop:~$ rfkill list all
clare@clare-laptop:~$ sudo rfkill unblock all
[sudo] password for clare: 
clare@clare-laptop:~$

which doesn't seem like it would be much help??
Assuming that it was meant to output something that is!!

---

### Post by clarett on 2011-01-04
Anyone got any other ideas?

---

### Post by fhd on 2011-01-10
I had the exact same issue and figured out that it works if you activate WLAN (it's disabled per default on the x10, press Fn+F2 to change that) and then restart network-manager. See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/602213").

---

