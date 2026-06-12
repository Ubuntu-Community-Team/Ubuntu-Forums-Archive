---
title: "Cisco Valet Connector AM10 in Ubuntu 11.04 - DRIVER"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by ohmysql on 2011-09-08
In this thread:

[http://ubuntuforums.org/showthread.php?t=1808690](http://ubuntuforums.org/showthread.php?t=1808690)

I was trying to get the AM10 to switch into the kind of device I need. That is now working.

But now, I can't get the driver working.

When I do ndiswrapper with the XP driver that comes with the AM10 my computer freezes.

And when I use the rt3572sta I've been getting messages like this in the syslog:

> 
RTUSB_VendorRequest failed(-32),TxFlags=0x0, ReqType=OUT, Req=0x2, Idx=0x3834,pAd->Flags=0x0
[  333.491070]     Request Value=0x2060!
Any ideas?

---

### Post by lkjoel on 2011-09-08
Could you run the Network Info script (in my signature), and attach the generated file?

Also, try this:
```
sudo modprobe -r ndiswrapper
sudo modprobe -r rt3572sta
sudo modprobe rt2800usb

```

---

### Post by ohmysql on 2011-09-08
> **lkjoel said:**
> Could you run the Network Info script (in my signature), and attach the generated file?

Also, try this:
```
sudo modprobe -r ndiswrapper
sudo modprobe -r rt3572sta
sudo modprobe rt2800usb

```

I might be a bit of a n00b. I'm getting the hang of this but it's not automatic for me.

I ran the code you suggested and the USB device didn't work. With ndiswrapper a wireless network appeared right away (and then the computer froze repeatedly).

I've PMed you a link to the Network Info you requested. Please let me know when you get it.

OMS!!

---

### Post by lkjoel on 2011-09-09
I saw the Network Info. It shows that you have the wrong driver activated.

I have attached the correct driver for your USB stick.
Download the attached file to your home directory (not to Downloads).
Type in a Terminal window:
```
cd ~
bunzip2 DRIVER.tar.lzma.bz2; unlzma DRIVER.tar.lzma; tar -xf DRIVER.tar
cd 2010_0709_RT2870_Linux_STA_v2.4.0.1
sudo make
sudo make install
echo 'blacklist rt3572sta' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo sed -i 's:rt3572sta::g' /etc/modules
sudo sed -i 's:ndiswrapper::g' /etc/modules
sudo modprobe -r rt3572sta
sudo modprobe -r ndiswrapper
sudo modprobe rt2870sta
echo 'rt2870sta' | sudo tee -a /etc/modules

```
If you can't connect right away, reboot.

---

### Post by ohmysql on 2011-09-09
> **lkjoel said:**
> I saw the Network Info. It shows that you have the wrong driver activated.

I have attached the correct driver for your USB stick.
Download the attached file to your home directory (not to Downloads).
Type in a Terminal window:
```
cd ~
bunzip2 DRIVER.tar.lzma.bz2; unlzma DRIVER.tar.lzma; tar -xf DRIVER.tar
cd 2010_0709_RT2870_Linux_STA_v2.4.0.1
sudo make
sudo make install
echo 'blacklist rt3572sta' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo sed -i 's:rt3572sta::g' /etc/modules
sudo sed -i 's:ndiswrapper::g' /etc/modules
sudo modprobe -r rt3572sta
sudo modprobe -r ndiswrapper
sudo modprobe rt2870sta
echo 'rt2870sta' | sudo tee -a /etc/modules

```If you can't connect right away, reboot.

Ok I did all that. I also blacklisted ndiswrapper - I hope that is correct. I assume it was.

I'm not sure those commands for /etc/modules did anything. I didn't see anything in there.

When I do lsmod | grep rt2870sta it comes up. That said, when I inserted the USB key nothing happened. When I restarted with the USB key plugged in ubuntu wouldn't load past the GRUB loader. That is VERY strange! (I'm going to try with another key in a minute, but I don't think I've ever had that problem).

So I loaded without any key plugged in. Then when I plug in the AM10, nothing happened. I just PMed you the latest network-info with the AM10 plugged in. (Right now I'm using an ethernet connection).

Please do let me know if you see any next steps. I am in way over my head!

OMS!

PS I downloaded the driver from the Ralink site, I hope that's ok.

---

### Post by lkjoel on 2011-09-09
Which driver did you download from the Ralink site?
Also, try this:
```
sudo mv /etc/network/interfaces /etc/network/int.er.face.es.BA.CK.UP
cat << EOF | sudo tee /etc/network/interfaces
[FONT=monospace]auto lo
iface lo inet loopback

EOF

```
And reboot
[/FONT]

---

### Post by ohmysql on 2011-09-10
> **lkjoel said:**
> Which driver did you download from the Ralink site?
Also, try this:
```
sudo mv /etc/network/interfaces /etc/network/int.er.face.es.BA.CK.UP
cat << EOF | sudo tee /etc/network/interfaces
[FONT=monospace]auto lo
iface lo inet loopback

EOF
[/FONT]
```[FONT=monospace]
And reboot
[/FONT]

I downloaded this driver:

[URL="http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpBNUwyUnZkMjVzYjJGa05ETTVOalU0TXpVeU5pNWllakk5UFQweU1ERXdYekEzTURsZlVsUXlPRGN3WDB4cGJuVjRYMU5VUVY5Mk1pNDBMakF1TVM1MFlYST1D"]http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpBNUwyUnZkMjVzYjJGa05ETTVOalU0TXpVeU5pNWllakk5UFQweU1ERXdYekEzTURsZlVsUXlPRGN3WDB4cGJuVjRYMU5VUVY5Mk1pNDBMakF1TVM1MFlYST1D
[/URL]
Should be the exact same one.

I just tried the modifications to network/interfaces you gave me. I rebooted but it didn't detect the wireless device automatically when I plugged it in.

Tell me: when I do the things you're trying, then reboot and plug in the device, is there something I should be trying? (As a reminder I reboot and THEN plug-in because if I leave the AM10 in my computer freezes and doesn't start after GRUB).

I just updated network-info in the directory I gave you.

OMS

---

### Post by lkjoel on 2011-09-11
OK, you used an outdated driver that doesn't even compile. Please follow this post exactly as it says: [http://ubuntuforums.org/showpost.php?p=11234959&postcount=4](http://ubuntuforums.org/showpost.php?p=11234959&postcount=4)

---

### Post by ohmysql on 2011-09-11
> **lkjoel said:**
> OK, you used an outdated driver that doesn't even compile. Please follow this post exactly as it says: [http://ubuntuforums.org/showpost.php?p=11234959&postcount=4](http://ubuntuforums.org/showpost.php?p=11234959&postcount=4)

Ok, I've done this. Where did you get that driver then if not off the Ralink website. It has the same version number and everything.

Well, I've done that and then I just added the network-info to the same folder. My system now recognizes the driver but doesn't see any wireless networks. If you have ideas I'm all ears. I even entered my wireless network's information by hand and tried to connect but it kept asking for the password over and over and not connecting.

I also tried:

[code}sudo restart network-manager[/code]

And when it restarts it just says the AM10 is not ready.

OMS

---

### Post by lkjoel on 2011-09-11
It's the same driver, except that it has a few patches that make it work with the new kernel headers.

Could you give me the output of this Terminal command?
```
sudo rfkill list all

```

---

### Post by ohmysql on 2011-09-12
> **lkjoel said:**
> It's the same driver, except that it has a few patches that make it work with the new kernel headers.

Could you give me the output of this Terminal command?
```
sudo rfkill list all

```

Sure, when I do sudo rfkill list all I get no result.

I saw other people suggesting I do that. How strange that I get no result.

OMS!

---

### Post by lkjoel on 2011-09-12
Oh right, you don't have the driver.
Is it a card or a usb stick?

---

### Post by ohmysql on 2011-09-12
> **lkjoel said:**
> Oh right, you don't have the driver.
Is it a card or a usb stick?

It's a USB stick, henceforth referred to as this !@#$ing thing:

[http://homesupport.cisco.com/en-us/wireless/valet/AM10](http://homesupport.cisco.com/en-us/wireless/valet/AM10)

I'm not sure what you mean I "don't have the driver."

When I do:

```
lsmod | grep rt2
```I get "rt2870sta             630019  0"

But I'm standing by for further instructions!

OMS!

---

### Post by ohmysql on 2011-09-19
Any ideas of things to try?

---

### Post by lkjoel on 2011-09-19
I'm sorry for the late reply!
Could you give me the output of this Terminal command?
```
uname -a
```

---

### Post by ohmysql on 2011-09-19
Sure, and I really appreciate your help.

Linux xxx-ubuntu 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by praseodym on 2011-09-19
Can you show the outputs of:

```
lsusb
usb-devices
lsmod
```

---

### Post by ohmysql on 2011-09-19
```

xxx@xxx-ubuntu:~$ lsusb
Bus 002 Device 003: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 002 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 018: ID 13b1:0031 Linksys AM10 v1 802.11n [Ralink RT2870]
Bus 001 Device 017: ID 1307:1169 Transcend Information, Inc. TS2GJF210 JetFlash 210 2GB
Bus 001 Device 016: ID 1307:0169 Transcend Information, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
xxx@xxx-ubuntu:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=10
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-11-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:02.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#= 16 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1307 ProdID=0169 Rev=01.00
S:  Manufacturer=Cisco Systems, Inc.
S:  Product=Cisco AM10 USB Hub
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=16 Port=00 Cnt=01 Dev#= 17 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1307 ProdID=1169 Rev=01.00
S:  Manufacturer=Cisco Systems, Inc.
S:  Product=Cisco AM10 AM10
S:  SerialNumber=000000000000D9
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)

T:  Bus=01 Lev=02 Prnt=16 Port=01 Cnt=02 Dev#= 18 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=13b1 ProdID=0031 Rev=01.01
S:  Manufacturer=Cisco
S:  Product=Cisco AM10
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=450mA
I:  If#= 0 Alt= 0 #EPs= 7 Cls=ff(vend.) Sub=ff Prot=ff Driver=rt2870

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh=10
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-11-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=045e ProdID=00db Rev=01.73
S:  Manufacturer=Microsoft
S:  Product=Natural® Ergonomic Keyboard 4000
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=045e ProdID=007d Rev=00.00
S:  Manufacturer=Microsoft
S:  Product=Microsoft 3-Button Mouse with IntelliEye™
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
xxx@xxx-ubuntu:~$ lsmod
Module                  Size  Used by
rt2870sta             630019  1 
usb_storage            53538  0 
uas                    17996  0 
sha256_generic         21031  2 
cryptd                 20510  0 
aes_x86_64             17208  906 
aes_generic            38279  1 aes_x86_64
dm_crypt               22993  1 
vesafb                 13761  1 
snd_hda_codec_hdmi     28167  4 
snd_hda_codec_realtek   336771  1 
binfmt_misc            17565  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
serio_raw              13166  0 
i2c_nforce2            13058  0 
nvidia              10709116  40 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
joydev                 17606  0 
ppdev                  17113  0 
parport_pc             36959  1 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
k10temp                13119  0 
edac_core              53845  0 
edac_mce_amd           23464  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
hid_microsoft          12865  0 
usbhid                 46956  0 
hid                    91020  2 hid_microsoft,usbhid
forcedeth              63555  0 
sata_nv                32054  2 

```

---

### Post by praseodym on 2011-09-19
Check with

```
modinfo rt2870sta | grep 0031
```
if the device ID is present.

---

### Post by ohmysql on 2011-09-19
> **praseodym said:**
> Check with

```
modinfo rt2870sta | grep 0031
```if the device ID is present.

Yes, it is present. I even added 1307x0169 to rt2870sta just in case.

Right now when I plug in the device it says "Wireless Device Disconnected" but network manager does create a listing for wireless devices every time I plug it in.

But it's not finding any wireless networks in the area. Let me know if you have additional things to check for.

OMS

---

### Post by praseodym on 2011-09-19
Is the package "linux-firmware" installed?

---

### Post by ohmysql on 2011-09-19
Yes, it is version 1.52.

Here's something I was looking at, wondering if this might be related.

When I do gksudo gedit /etc/network/interfaces

I get:

```
auto lo
iface lo inet loopback

```

But I get this when I do iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I've been reading about how I'm supposed to change that interfaces file but I'm still not quite sure. When I do commands like ifup ra0 it tells me no ra0 thing is installed. I'll be curious if you have ideas. I'm pretty new to this stuff.

OMS

---

### Post by praseodym on 2011-09-19
Did you uninstall ndiswrapper completely?

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo modprobe -rf rt2870sta
sudo modprobe -v rt2870sta
```
Replug the stick.

If it doesnt work: Checkbox all user rights in "Users&Groups", login again, remove your current wireless profile and create a new on in "Infrastructure" modus. Do you use Wicd and networkmanager in parallel?

---

### Post by ohmysql on 2011-09-19
> **praseodym said:**
> Did you uninstall ndiswrapper completely?

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo modprobe -rf rt2870sta
sudo modprobe -v rt2870sta
```Replug the stick.

If it doesnt work: Checkbox all user rights in "Users&Groups", login again, remove your current wireless profile and create a new on in "Infrastructure" modus. Do you use Wicd and networkmanager in parallel?

I just completely uninstalled ndiswrapper as you said. It doesn't seem to have helped. The system still seems to recognize the device (the networks manager list changes and includes wireless devices, but under Wireless Devices it still says "disconnected."

I hadn't checked a user right to wireless networks so I did that for myself then rebooted. 

I also did as you said, deleting my old wireless connection and writing a new one, under infrastructure. I tried to load it under "Hidden Networks" (because I'm not getting a list of available networks), but to no luck.

to answer your question I do not have Wicd installed.

Any thoughts on the next step? I'm going to look into udev stuff - but I'm still wondering if ra0 might be involved.

Let me know if you want my IM so we can do this a little faster and then post our results.

OMS

---

### Post by ohmysql on 2011-09-19
This is my udev:

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:e5:49:6a:d2:1d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x13B1:0x0031 (ndiswrapper)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="68:7F:74:E3:F6:4B", ATTR{dev_id}=="0x0", ATTR{type}=="1", #KERNEL=="wlan*", NAME="wlan0"

# USB device 0x13b1:0x0031 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="68:7f:74:e3:f6:4b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# USB device 0x13b1:0x0031 (usb)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="68:7f:74:e3:f6:4b", ATTR{dev_id}=="0x0", ATTR{type}=="1", #KERNEL=="wlan*", NAME="wlan0"
```

And this is a section of my dmesg:

```
[  221.342614] <==== rt28xx_init, Status=0
[  221.344068] 0x1300 = 00064300
[  222.180861] -->RTUSBVenderReset
[  222.180982] <--RTUSBVenderReset
[  222.458444] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[  222.458462] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[  222.459026] Key1Str is Invalid key length(0) or Type(0)
[  222.459070] Key2Str is Invalid key length(0) or Type(0)
[  222.459113] Key3Str is Invalid key length(0) or Type(0)
[  222.459157] Key4Str is Invalid key length(0) or Type(0)
[  222.459917] 1. Phy Mode = 5
[  222.459921] 2. Phy Mode = 5
[  222.486800] phy mode> Error! The chip does not support 5G band 8!
[  222.487012] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  222.506274] 3. Phy Mode = 9
[  222.514279] MCS Set = ff ff 00 00 01
[  222.524961] <==== rt28xx_init, Status=0
[  222.526408] 0x1300 = 00064300
[  233.270059] ra0: no IPv6 routers present
```

---

### Post by praseodym on 2011-09-19
This is strange:
> # USB device 0x13B1:0x0031 ([COLOR="Red"]ndiswrapper[/COLOR])
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="68:7F:74:E3:F6:4B", ATTR{dev_id}=="0x0", ATTR{type}=="1", #KERNEL=="wlan*", NAME="[COLOR="Red"]wlan0[/COLOR]"

...

# USB device 0x13b1:0x0031 ([COLOR="Red"]usb[/COLOR])
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="68:7f:74:e3:f6:4b", ATTR{dev_id}=="0x0", ATTR{type}=="1", #KERNEL=="wlan*", NAME="[COLOR="Red"]wlan0[/COLOR]"
Rename the file and create a new one:

```
sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
```
Replug the stick or reboot and check again:

```
iwconfig
lsmod
cat /etc/udev/rules.d/70-persistent-net.rules
dmesg | grep rt2
sudo iwlist scan
rfkill list
```

---

### Post by ohmysql on 2011-09-19
> **praseodym said:**
> This is strange:

Rename the file and create a new one:

```
sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
```Replug the stick or reboot and check again:

```
iwconfig
lsmod
cat /etc/udev/rules.d/70-persistent-net.rules
dmesg | grep rt2
sudo iwlist scan
rfkill list
```

Ok, here's the latest code. I hope this helps.

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

xxx@xxx-ubuntu:~$ lsmod
Module                  Size  Used by
usb_storage            53538  0 
uas                    17996  0 
sha256_generic         21031  2 
cryptd                 20510  0 
aes_x86_64             17208  398 
aes_generic            38279  1 aes_x86_64
dm_crypt               22993  1 
vesafb                 13761  1 
snd_hda_codec_hdmi     28167  4 
snd_hda_codec_realtek   336771  1 
binfmt_misc            17565  1 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
serio_raw              13166  0 
snd_hda_intel          33176  2 
nvidia              10709116  40 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_hwdep              13604  1 snd_hda_codec
joydev                 17606  0 
ppdev                  17113  0 
parport_pc             36959  1 
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_timer              29602  2 snd_seq,snd_pcm
i2c_nforce2            13058  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
k10temp                13119  0 
edac_core              53845  0 
edac_mce_amd           23464  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_seq,snd_hwdep,snd_pcm,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
rt2870sta             630019  1 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
hid_microsoft          12865  0 
usbhid                 46956  0 
hid                    91020  2 hid_microsoft,usbhid
forcedeth              63555  0 
sata_nv                32054  2 
xxx@xxx-ubuntu:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:e5:49:6a:d2:1d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
xxx@xxx-ubuntu:~$ dmesg | grep rt2
[   12.272351] usbcore: registered new interface driver rt2870
[   58.601182] <==== rt28xx_init, Status=0
[   59.908559] <==== rt28xx_init, Status=0
xxx@xxx-ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results

xxx@xxx-ubuntu:~$ rfkill list
xxx@xxx-ubuntu:~$ 
```Here's dmesg around when the rt2870 loads up (I don't plug in the device at bootup because it doesn't get past grub):

```
[  221.342614] <==== rt28xx_init, Status=0
[  221.344068] 0x1300 = 00064300
[  222.180861] -->RTUSBVenderReset
[  222.180982] <--RTUSBVenderReset
[  222.458444] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[  222.458462] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[  222.459026] Key1Str is Invalid key length(0) or Type(0)
[  222.459070] Key2Str is Invalid key length(0) or Type(0)
[  222.459113] Key3Str is Invalid key length(0) or Type(0)
[  222.459157] Key4Str is Invalid key length(0) or Type(0)
[  222.459917] 1. Phy Mode = 5
[  222.459921] 2. Phy Mode = 5
[  222.486800] phy mode> Error! The chip does not support 5G band 8!
[  222.487012] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  222.506274] 3. Phy Mode = 9
[  222.514279] MCS Set = ff ff 00 00 01
[  222.524961] <==== rt28xx_init, Status=0
[  222.526408] 0x1300 = 00064300
[  233.270059] ra0: no IPv6 routers present
[  417.480124] -->RTUSBVenderReset
[  417.480224] <--RTUSBVenderReset
[  417.754919] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[  417.754938] CfgSetCountryRegion():CountryRegion in eeprom was programmed
[  417.755503] Key1Str is Invalid key length(0) or Type(0)
[  417.755547] Key2Str is Invalid key length(0) or Type(0)
[  417.755590] Key3Str is Invalid key length(0) or Type(0)
[  417.755634] Key4Str is Invalid key length(0) or Type(0)
[  417.756395] 1. Phy Mode = 5
[  417.756399] 2. Phy Mode = 5
[  417.783025] phy mode> Error! The chip does not support 5G band 8!
[  417.783242] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  417.802375] 3. Phy Mode = 9
[  417.810381] MCS Set = ff ff 00 00 01
[  417.821055] <==== rt28xx_init, Status=0
[  417.822505] 0x1300 = 00064300
[  421.186737] usb 1-4: USB disconnect, address 7
[  421.186745] usb 1-4.1: USB disconnect, address 8
[  421.187109] usb 1-4.2: USB disconnect, address 9
[  421.187445] Bulk In Failed. Status=-108, BIIdx=0x0, BIRIdx=0x0, actual_length= 0x0
[  421.190140] rtusb_disconnect: unregister usbnet usb-0000:00:02.1-4.2

```

Also, I note that udev didn't create a rule for this device. I wonder why. OMS!

---

### Post by praseodym on 2011-09-19
> Also, I note that udev didn't create a rule for this device. I wonder why. OMS! 
Should be no problem, please show:

```
ifconfig -a
```
Which channel do you use (GHz!)? This indicates, that you are using (want to use?) the 5 GHz band:

> [  222.486800] phy mode> Error! The chip does not support 5G band 8!
...
[  417.783242] RTMPSetPhyMode: channel is out of range, use first channel=1 

How many letters/numbers/etc. does your key have? 64 is one too long:

> [  222.459026] Key1Str is Invalid key length(0) or Type(0)
[  222.459070] Key2Str is Invalid key length(0) or Type(0)
[  222.459113] Key3Str is Invalid key length(0) or Type(0)
[  222.459157] Key4Str is Invalid key length(0) or Type(0)

---

### Post by ohmysql on 2011-09-19
> **praseodym said:**
> Should be no problem, please show:

```
ifconfig -a
```

Ok, here you go.

```
eth0      Link encap:Ethernet  HWaddr 50:e5:49:6a:d2:1d  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fe6a:d21d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5928614 (5.9 MB)  TX bytes:2111087 (2.1 MB)
          Interrupt:41 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:255105 (255.1 KB)  TX bytes:255105 (255.1 KB)

```

> Which channel do you use (GHz!)? This indicates, that you are using (want to use?) the 5 GHz band:[/quote[I'm sorry, I'm not sure how to tell. I have another machine that connects using wireless - how would I check this?

[quote]How many letters/numbers/etc. does your key have? 64 is one too long:To answer your question, our wifi password is 40 characters long.

I'm all ears if you have other things to check. This card has NEVER worked in Linux before, so if we get this, it will be quite the victory.

OMS

---

### Post by praseodym on 2011-09-19
Ok,

```
gksudo gedit /etc/udev/rules.d/70-persistent-net.rules
```

add a space line and the following:

```
# USB device 0x13b1:0x0031 (usb)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="68:7f:74:e3:f6:4b", ATTR{dev_id}=="0x0", ATTR{type}=="1", #KERNEL=="[COLOR="Red"]ra[/COLOR]*", NAME="[COLOR="Red"]ra0[/COLOR]"
```
save, close and

```
sudo service udev reload
sudo modprove -rf rt2870sta
sudo modprobe -v rt2870sta
```
Replug the stick and restart the network.

Check:

```
ifconfig -a
iwconfig
sudo iwlist scan
dmesg | egrep 'ra0|rt2'
```

---

### Post by ohmysql on 2011-09-19
> **praseodym said:**
> Ok,

```
gksudo gedit /etc/udev/rules.d/70-persistent-net.rules
```add a space line and the following:

```
# USB device 0x13b1:0x0031 (usb)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="68:7f:74:e3:f6:4b", ATTR{dev_id}=="0x0", ATTR{type}=="1", #KERNEL=="[COLOR=Red]ra[/COLOR]*", NAME="[COLOR=Red]ra0[/COLOR]"
```

Are you sure you didn't mean:

```
# USB device 0x13b1:0x0031 (usb - Cisco AM10)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="68:7f:74:e3:f6:4b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="ra*", NAME="ra0"
```? It looks to me like you're commenting out the best parts. Well, I did what you said. 

> save, close and Replug the stick and restart the network.

```
sudo service udev reload
sudo modprove -rf rt2870sta
sudo modprobe -v rt2870sta
```Replug the stick and restart the network.Assuming you meant modprobe in the second line. Anyway, this is done and the last command gave:

```
insmod /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rt2870sta.ko
```Going to restart now. Back in a moment. (How should I normally restart the network? Sorry) More comments soon.

> Check:

```
ifconfig -a
iwconfig
sudo iwlist scan
dmesg | egrep 'ra0|rt2'
```

Here are the results from these last checks:

```
   	 	 	 	 	 	  xxx@xxx-ubuntu:~$ ifconfig -a 
 eth0      Link encap:Ethernet  HWaddr 50:e5:49:6a:d2:1d   
           inet6 addr: fe80::52e5:49ff:fe6a:d21d/64 Scope:Link 
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:267 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:306 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:202120 (202.1 KB)  TX bytes:63418 (63.4 KB) 
           Interrupt:41 Base address:0xc000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:1617 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:1617 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:123692 (123.6 KB)  TX bytes:123692 (123.6 KB) 
  
 ra0       Link encap:Ethernet  HWaddr 68:7f:74:e3:f6:4b   
           inet6 addr: fe80::6a7f:74ff:fee3:f64b/64 Scope:Link 
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:26 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:2032 (2.0 KB) 
  
 xxx@xxx-ubuntu:~$ iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA" 
           Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated    
           Bit Rate:1 Mb/s    
           RTS thr:off   Fragment thr:off 
           Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm 
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
  
 xxx@xxx-ubuntu:~$ sudo iwlist scan 
 lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
  
 ra0       No scan results 
  
 xxx@xxx-ubuntu:~$ dmesg | egrep 'ra0|rt2' 
 [   12.489211] usbcore: registered new interface driver rt2870 
 [   67.779855] <==== rt28xx_init, Status=0 
 [   69.017484] <==== rt28xx_init, Status=0 
 [   79.630063] ra0: no IPv6 routers present
```

---

### Post by praseodym on 2011-09-19
Looks better, check:

```
route -n
cat /etc/resolv.conf
iwlist chan
lsmod
```
Sorry for the typo.

Network restart via:

```
sudo service network-manager restart
```

---

### Post by ohmysql on 2011-09-19
> **praseodym said:**
> Looks better, check:

```
route -n
cat /etc/resolv.conf
iwlist chan
lsmod
```Sorry for the typo.

Network restart via:

```
sudo service network-manager restart
```

Thanks for the network restart code. That will be helpful. Here is the output:

```

  	 	 	 	 	 	  xxx@xxx-ubuntu:~$ route -n 
 Kernel IP routing table 
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
 xxx@xxx-ubuntu:~$ cat /etc/resolv.conf 
 # Generated by NetworkManager 
 xxx@xxx-ubuntu:~$ iwlist chan 
 lo        no frequency information. 
  
 eth0      no frequency information. 
  
 ra0       13 channels in total; available frequencies : 
           Channel 01 : 2.412 GHz 
           Channel 02 : 2.417 GHz 
           Channel 03 : 2.422 GHz 
           Channel 04 : 2.427 GHz 
           Channel 05 : 2.432 GHz 
           Channel 06 : 2.437 GHz 
           Channel 07 : 2.442 GHz 
           Channel 08 : 2.447 GHz 
           Channel 09 : 2.452 GHz 
           Channel 10 : 2.457 GHz 
           Channel 11 : 2.462 GHz 
           Channel 12 : 2.467 GHz 
           Channel 13 : 2.472 GHz 
           Current Frequency:2.412 GHz (Channel 1) 
  
 xxx@xxx-ubuntu:~$ lsmod 
 Module                  Size  Used by 
 btrfs                 550457  0  
 zlib_deflate           27074  1 btrfs 
 libcrc32c              12644  1 btrfs 
 ufs                    75815  0  
 qnx4                   17685  0  
 hfsplus                84797  0  
 hfs                    54731  0  
 minix                  36367  0  
 ntfs                  101769  0  
 vfat                   21708  0  
 msdos                  17333  0  
 fat                    61374  2 vfat,msdos 
 jfs                   182186  0  
 xfs                   823190  0  
 exportfs               12998  1 xfs 
 reiserfs              248223  0  
 usb_storage            53538  0  
 uas                    17996  0  
 sha256_generic         21031  2  
 cryptd                 20510  0  
 aes_x86_64             17208  548  
 aes_generic            38279  1 aes_x86_64 
 dm_crypt               22993  1  
 vesafb                 13761  1  
 snd_hda_codec_hdmi     28167  4  
 snd_hda_codec_realtek   336771  1  
 binfmt_misc            17565  1  
 snd_seq_midi           13324  0  
 snd_hda_intel          33176  2  
 snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
 snd_rawmidi            30486  1 snd_seq_midi 
 snd_hwdep              13604  1 snd_hda_codec 
 snd_seq_midi_event     14899  1 snd_seq_midi 
 snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event 
 joydev                 17606  0  
 serio_raw              13166  0  
 snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
 ppdev                  17113  0  
 nvidia              10709116  40  
 snd_timer              29602  2 snd_seq,snd_pcm 
 parport_pc             36959  1  
 snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq 
 snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_pcm,snd_timer,snd_seq_device 
 i2c_nforce2            13058  0  
 soundcore              12680  1 snd 
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
 edac_core              53845  0  
 k10temp                13119  0  
 edac_mce_amd           23464  0  
 rt2870sta             630019  1  
 lp                     17825  0  
 parport                46458  3 ppdev,parport_pc,lp 
 hid_microsoft          12865  0  
 usbhid                 46956  0  
 hid                    91020  2 hid_microsoft,usbhid 
 sata_nv                32054  2  
 forcedeth              63555  0
```


Would you confirm that you gave me the right udev code? It looked like it was all commented out. I should probably take out everything but the first hash mark, right?


OMS

---

### Post by ohmysql on 2011-09-19
Just so you're aware, you may want to check out the thread here (last reply)

[http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-%28ubuntu%29/new/?topicseen#new](http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-%28ubuntu%29/new/?topicseen#new)

---

### Post by ohmysql on 2011-09-22
I wanted to give an update on this issue.

I've been trying the rt3572sta driver and having more luck.

In fact, I'm almost there, I just need the wpa-supplicant to play well with this driver. Here's what I did:

In the driver folder I went to the common folder and altered rtusb_dev_id.c

I added this line:

```
    {USB_DEVICE(0x13B1,0x0031)}, /*Cisco Linksys AM10*/
```

Then I went to os/linux/config.mk and set both wpa supplicant settings to y rather than n.

Under the rt35xx line. Adding it under rt2870 didn't seem to do much. To me, that indicates that the rt3070 driver may be the right one.

So now.... some good news. The command sudo iwlist scan finally bears results!!!

```
          Cell 03 - Address: 00:16:B6:B3:A0:10
                    Protocol:802.11b/g
                    ESSID:"2325"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/100  Signal level=-77 dBm  Noise level=-83 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```

That is a very good sign! Ubuntu now mode_switches, recognizes the wireless device, successfully scans. We're really close! But how do I get the wpa to play well with this driver?

Here is from syslog:

```
Sep 22 11:40:46 cool1-ubuntu NetworkManager[3222]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Sep 22 11:40:46 cool1-ubuntu NetworkManager[3222]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Sep 22 11:40:46 cool1-ubuntu kernel: [12657.990100] ---> RTMPFreeTxRxRingMemory
Sep 22 11:40:46 cool1-ubuntu kernel: [12657.990122] <--- RTMPFreeTxRxRingMemory
Sep 22 11:40:46 cool1-ubuntu kernel: [12657.990170]  RTUSB disconnect successfully
Sep 22 11:40:46 cool1-ubuntu dhclient: can't create /var/lib/dhcp3/dhclient.ra0.leases: No such file or directory
Sep 22 11:40:46 cool1-ubuntu dhclient: Bind socket to interface: No such device
Sep 22 11:40:46 cool1-ubuntu wpa_supplicant[815]: Could not read interface ra0 flags: No such device
Sep 22 11:40:46 cool1-ubuntu wpa_supplicant[3022]: Failed to initiate AP scan.
Sep 22 11:40:57 cool1-ubuntu wpa_supplicant[3022]: last message repeated 10 times
Sep 22 11:40:57 cool1-ubuntu kernel: [12669.220091] usb 1-4: new high speed USB device using ehci_hcd and address 10
Sep 22 11:40:57 cool1-ubuntu kernel: [12669.372188] hub 1-4:1.0: USB hub found
Sep 22 11:40:57 cool1-ubuntu kernel: [12669.372366] hub 1-4:1.0: 3 ports detected
Sep 22 11:40:57 cool1-ubuntu kernel: [12669.650258] usb 1-4.1: new high speed USB device using ehci_hcd and address 11
Sep 22 11:40:57 cool1-ubuntu kernel: [12669.762600] scsi6 : usb-storage 1-4.1:1.0
Sep 22 11:40:57 cool1-ubuntu usb_modeswitch: switching 1307:1169 (Cisco Systems, Inc.: Cisco AM10 AM10)
Sep 22 11:40:58 cool1-ubuntu wpa_supplicant[3022]: Failed to initiate AP scan.
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.510283] usb 1-4.2: new high speed USB device using ehci_hcd and address 12
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.642650] 
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.642652] 
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.642654] === pAd = ffffc9000e0fd000, size = 550752 ===
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.642657] 
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.642994] <-- RTMPAllocTxRxRingMemory, Status=0
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.643179] <-- RTMPAllocAdapterBlock, Status=0
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.645742] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
Sep 22 11:40:58 cool1-ubuntu NetworkManager[3222]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4.2/net/ra0, iface: ra0)
Sep 22 11:40:58 cool1-ubuntu NetworkManager[3222]:    SCPluginIfupdown: locking wireless connection setting
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.908040] RTMP_TimerListAdd: add timer obj ffffc9000e146638!
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.908043] RTMP_TimerListAdd: add timer obj ffffc9000e1466b0!
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.908045] RTMP_TimerListAdd: add timer obj ffffc9000e146728!
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.908047] RTMP_TimerListAdd: add timer obj ffffc9000e1465c0!
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.908049] RTMP_TimerListAdd: add timer obj ffffc9000e146458!
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.908051] RTMP_TimerListAdd: add timer obj ffffc9000e1464d0!
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.908052] RTMP_TimerListAdd: add timer obj ffffc9000e110940!
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.908054] RTMP_TimerListAdd: add timer obj ffffc9000e0ff5f8!
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.908055] RTMP_TimerListAdd: add timer obj ffffc9000e0ff678!
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.908057] RTMP_TimerListAdd: add timer obj ffffc9000e110ad0!
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.908060] RTMP_TimerListAdd: add timer obj ffffc9000e110850!
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.908062] RTMP_TimerListAdd: add timer obj ffffc9000e110a50!
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.909484] -->RTUSBVenderReset
Sep 22 11:40:58 cool1-ubuntu kernel: [12670.909608] <--RTUSBVenderReset
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000120] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000128] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000133] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000137] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000141] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000144] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000148] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000151] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000154] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000157] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000160] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000164] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000167] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000170] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000173] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000176] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000180] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000183] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000186] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000189] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000192] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000196] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000199] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000202] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000205] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000209] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000212] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000215] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000218] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000234] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.000238] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100118] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100126] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100131] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100135] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100138] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100142] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100145] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100148] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100152] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100155] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100158] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100161] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100165] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100168] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100171] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100174] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100178] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100181] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100184] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100188] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100191] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100194] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100197] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100201] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100204] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100207] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100210] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100214] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100217] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100233] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.100236] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.180896] Key1Str is Invalid key length(0) or Type(0)
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.180941] Key2Str is Invalid key length(0) or Type(0)
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.180985] Key3Str is Invalid key length(0) or Type(0)
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.181030] Key4Str is Invalid key length(0) or Type(0)
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.181822] 1. Phy Mode = 5
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.181826] 2. Phy Mode = 5
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.181831] NVM is Efuse and its size =2d[2d0-2fc] 
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200119] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200125] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200130] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200137] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200142] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200148] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200153] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200159] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200164] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200170] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200175] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200181] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200186] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200192] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200198] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200203] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200209] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200214] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200232] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.200238] UsbVendorReq_semaphore get failed
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.228987] phy mode> Error! The chip does not support 5G band 8!
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.229206] RTMPSetPhyMode: channel is out of range, use first channel=1 
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.232992] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.251737] 3. Phy Mode = 9
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.272865] MCS Set = ff ff 00 00 01
Sep 22 11:40:59 cool1-ubuntu NetworkManager[3222]: <error> [1316706059.364212] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Sep 22 11:40:59 cool1-ubuntu NetworkManager[3222]: <info> (ra0): driver does not support SSID scans (scan_capa 0x00).
Sep 22 11:40:59 cool1-ubuntu NetworkManager[3222]: <info> (ra0): new 802.11 WiFi device (driver: 'usb' ifindex: 5)
Sep 22 11:40:59 cool1-ubuntu NetworkManager[3222]: <info> (ra0): exported as /org/freedesktop/NetworkManager/Devices/2
Sep 22 11:40:59 cool1-ubuntu NetworkManager[3222]: <info> (ra0): now managed
Sep 22 11:40:59 cool1-ubuntu NetworkManager[3222]: <info> (ra0): device state change: 1 -> 2 (reason 2)
Sep 22 11:40:59 cool1-ubuntu NetworkManager[3222]: <info> (ra0): preparing device.
Sep 22 11:40:59 cool1-ubuntu NetworkManager[3222]: <info> (ra0): deactivating device (reason: 2).
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.283550] <==== rt28xx_init, Status=0
Sep 22 11:40:59 cool1-ubuntu kernel: [12671.285111] 0x1300 = 00064300
Sep 22 11:40:59 cool1-ubuntu usb_modeswitch: switched to 13b1:0031 (Cisco: Cisco AM10)
Sep 22 11:40:59 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant interface state:  starting -> ready
Sep 22 11:40:59 cool1-ubuntu NetworkManager[3222]: <info> (ra0): device state change: 2 -> 3 (reason 42)
Sep 22 11:40:59 cool1-ubuntu wpa_supplicant[3574]: ctrl_iface exists and seems to be in use - cannot override it
Sep 22 11:40:59 cool1-ubuntu wpa_supplicant[3574]: Delete '/var/run/wpa_supplicant/ra0' manually if it is not used anymore
Sep 22 11:40:59 cool1-ubuntu wpa_supplicant[3574]: Failed to initialize control interface '/var/run/wpa_supplicant'.#012You may have another wpa_supplicant process already running or the file was#012left by an unclean termination of wpa_supplicant in which case you will need#012to manually remove this file before starting wpa_supplicant again.
Sep 22 11:40:59 cool1-ubuntu wpa_supplicant[3022]: CTRL-EVENT-TERMINATING - signal 15 received
Sep 22 11:41:00 cool1-ubuntu wpa_supplicant[815]: Failed to initiate AP scan.
Sep 22 11:41:00 cool1-ubuntu dhclient: can't create /var/lib/dhcp3/dhclient.ra0.leases: No such file or directory
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.258360] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.526808] RTMP_TimerListAdd: add timer obj ffffc9000e146638!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.526817] RTMP_TimerListAdd: add timer obj ffffc9000e1466b0!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.526824] RTMP_TimerListAdd: add timer obj ffffc9000e146728!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.526830] RTMP_TimerListAdd: add timer obj ffffc9000e1465c0!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.526837] RTMP_TimerListAdd: add timer obj ffffc9000e146458!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.526842] RTMP_TimerListAdd: add timer obj ffffc9000e1464d0!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.526847] RTMP_TimerListAdd: add timer obj ffffc9000e110940!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.526852] RTMP_TimerListAdd: add timer obj ffffc9000e0ff5f8!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.526856] RTMP_TimerListAdd: add timer obj ffffc9000e0ff678!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.526861] RTMP_TimerListAdd: add timer obj ffffc9000e110ad0!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.526867] RTMP_TimerListAdd: add timer obj ffffc9000e110850!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.526873] RTMP_TimerListAdd: add timer obj ffffc9000e110a50!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.528230] -->RTUSBVenderReset
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.528356] <--RTUSBVenderReset
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.807381] CfgSetCountryRegion():CountryRegion in eeprom was programmed
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.807386] CfgSetCountryRegion():CountryRegion in eeprom was programmed
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.807526] Key1Str is Invalid key length(0) or Type(0)
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.807536] Key2Str is Invalid key length(0) or Type(0)
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.807547] Key3Str is Invalid key length(0) or Type(0)
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.807558] Key4Str is Invalid key length(0) or Type(0)
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.807756] 1. Phy Mode = 5
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.807757] 2. Phy Mode = 5
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.807758] NVM is Efuse and its size =2d[2d0-2fc] 
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.863729] phy mode> Error! The chip does not support 5G band 8!
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.863807] RTMPSetPhyMode: channel is out of range, use first channel=1 
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.867612] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.886363] 3. Phy Mode = 9
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.907364] MCS Set = ff ff 00 00 01
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.918036] <==== rt28xx_init, Status=0
Sep 22 11:41:00 cool1-ubuntu kernel: [12672.919482] 0x1300 = 00064300
Sep 22 11:41:01 cool1-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
Sep 22 11:41:02 cool1-ubuntu kernel: [12674.882362] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:41:02 cool1-ubuntu kernel: [12674.883235] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:41:04 cool1-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
Sep 22 11:41:08 cool1-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) starting connection 'New 2325'
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> (ra0): device state change: 3 -> 4 (reason 0)
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> (ra0): device state change: 4 -> 5 (reason 0)
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0/wireless): access point 'New 2325' has security, but secrets are required.
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> (ra0): device state change: 5 -> 6 (reason 0)
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> (ra0): device state change: 6 -> 4 (reason 0)
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> (ra0): device state change: 4 -> 5 (reason 0)
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0/wireless): connection 'New 2325' has security, and secrets exist.  No new secrets needed.
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Config: added 'ssid' value '2325'
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Config: added 'scan_ssid' value '1'
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Config: added 'psk' value '<omitted>'
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> Config: set interface ap_scan to 1
Sep 22 11:41:10 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  inactive -> scanning
Sep 22 11:41:11 cool1-ubuntu kernel: [12682.950021] ra0: no IPv6 routers present
Sep 22 11:41:12 cool1-ubuntu wpa_supplicant[815]: Trying to associate with 00:16:b6:b3:a0:10 (SSID='2325' freq=2462 MHz)
Sep 22 11:41:12 cool1-ubuntu wpa_supplicant[815]: Association request to the driver failed
Sep 22 11:41:12 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  scanning -> associating
Sep 22 11:41:12 cool1-ubuntu kernel: [12684.742702] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:41:12 cool1-ubuntu kernel: [12684.744426] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Sep 22 11:41:12 cool1-ubuntu kernel: [12684.744542] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:41:17 cool1-ubuntu wpa_supplicant[815]: Authentication with 00:16:b6:b3:a0:10 timed out.
Sep 22 11:41:17 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  associating -> disconnected
Sep 22 11:41:17 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Sep 22 11:41:18 cool1-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
Sep 22 11:41:19 cool1-ubuntu wpa_supplicant[815]: Trying to associate with 00:16:b6:b3:a0:10 (SSID='2325' freq=2462 MHz)
Sep 22 11:41:19 cool1-ubuntu wpa_supplicant[815]: Association request to the driver failed
Sep 22 11:41:19 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  scanning -> associating
Sep 22 11:41:19 cool1-ubuntu kernel: [12691.702455] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 625
Sep 22 11:41:19 cool1-ubuntu kernel: [12691.703165] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Sep 22 11:41:19 cool1-ubuntu kernel: [12691.703263] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 625
Sep 22 11:41:24 cool1-ubuntu wpa_supplicant[815]: Authentication with 00:16:b6:b3:a0:10 timed out.
Sep 22 11:41:24 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  associating -> disconnected
Sep 22 11:41:24 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Sep 22 11:41:26 cool1-ubuntu wpa_supplicant[815]: Trying to associate with 00:16:b6:b3:a0:10 (SSID='2325' freq=2462 MHz)
Sep 22 11:41:26 cool1-ubuntu wpa_supplicant[815]: Association request to the driver failed
Sep 22 11:41:26 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  scanning -> associating
Sep 22 11:41:26 cool1-ubuntu kernel: [12698.662453] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 625
Sep 22 11:41:26 cool1-ubuntu kernel: [12698.662842] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Sep 22 11:41:26 cool1-ubuntu kernel: [12698.662949] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 625
Sep 22 11:41:31 cool1-ubuntu wpa_supplicant[815]: Authentication with 00:16:b6:b3:a0:10 timed out.
Sep 22 11:41:31 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  associating -> disconnected
Sep 22 11:41:31 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Sep 22 11:41:33 cool1-ubuntu wpa_supplicant[815]: Trying to associate with 00:16:b6:b3:a0:10 (SSID='2325' freq=2462 MHz)
Sep 22 11:41:33 cool1-ubuntu wpa_supplicant[815]: Association request to the driver failed
Sep 22 11:41:33 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  scanning -> associating
Sep 22 11:41:33 cool1-ubuntu kernel: [12705.622459] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 625
Sep 22 11:41:33 cool1-ubuntu kernel: [12705.622841] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Sep 22 11:41:33 cool1-ubuntu kernel: [12705.622949] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 625
Sep 22 11:41:36 cool1-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 20
Sep 22 11:41:38 cool1-ubuntu wpa_supplicant[815]: Authentication with 00:16:b6:b3:a0:10 timed out.
Sep 22 11:41:38 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  associating -> disconnected
Sep 22 11:41:38 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Sep 22 11:41:40 cool1-ubuntu wpa_supplicant[815]: Trying to associate with 00:16:b6:b3:a0:10 (SSID='2325' freq=2462 MHz)
Sep 22 11:41:40 cool1-ubuntu wpa_supplicant[815]: Association request to the driver failed
Sep 22 11:41:40 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  scanning -> associating
Sep 22 11:41:40 cool1-ubuntu kernel: [12712.592466] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 625
Sep 22 11:41:40 cool1-ubuntu kernel: [12712.592834] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Sep 22 11:41:40 cool1-ubuntu kernel: [12712.592936] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 625
Sep 22 11:41:45 cool1-ubuntu wpa_supplicant[815]: Authentication with 00:16:b6:b3:a0:10 timed out.
Sep 22 11:41:45 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  associating -> disconnected
Sep 22 11:41:45 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Sep 22 11:41:47 cool1-ubuntu wpa_supplicant[815]: Trying to associate with 00:16:b6:b3:a0:10 (SSID='2325' freq=2462 MHz)
Sep 22 11:41:47 cool1-ubuntu wpa_supplicant[815]: Association request to the driver failed
Sep 22 11:41:47 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  scanning -> associating
Sep 22 11:41:47 cool1-ubuntu kernel: [12719.572461] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 625
Sep 22 11:41:47 cool1-ubuntu kernel: [12719.572836] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Sep 22 11:41:47 cool1-ubuntu kernel: [12719.573036] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:41:48 cool1-ubuntu NetworkManager[3222]: <warn> (ra0): link timed out.
Sep 22 11:41:52 cool1-ubuntu wpa_supplicant[815]: Authentication with 00:16:b6:b3:a0:10 timed out.
Sep 22 11:41:52 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  associating -> disconnected
Sep 22 11:41:52 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Sep 22 11:41:54 cool1-ubuntu wpa_supplicant[815]: Trying to associate with 00:16:b6:b3:a0:10 (SSID='2325' freq=2462 MHz)
Sep 22 11:41:54 cool1-ubuntu wpa_supplicant[815]: Association request to the driver failed
Sep 22 11:41:54 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  scanning -> associating
Sep 22 11:41:54 cool1-ubuntu kernel: [12726.542464] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:41:54 cool1-ubuntu kernel: [12726.542875] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Sep 22 11:41:54 cool1-ubuntu kernel: [12726.542974] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:41:56 cool1-ubuntu dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
Sep 22 11:41:59 cool1-ubuntu wpa_supplicant[815]: Authentication with 00:16:b6:b3:a0:10 timed out.
Sep 22 11:41:59 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  associating -> disconnected
Sep 22 11:41:59 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Sep 22 11:42:01 cool1-ubuntu wpa_supplicant[815]: Trying to associate with 00:16:b6:b3:a0:10 (SSID='2325' freq=2462 MHz)
Sep 22 11:42:01 cool1-ubuntu wpa_supplicant[815]: Association request to the driver failed
Sep 22 11:42:01 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  scanning -> associating
Sep 22 11:42:01 cool1-ubuntu kernel: [12733.512582] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:42:01 cool1-ubuntu kernel: [12733.512965] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Sep 22 11:42:01 cool1-ubuntu kernel: [12733.513154] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:42:02 cool1-ubuntu dhclient: No DHCPOFFERS received.
Sep 22 11:42:02 cool1-ubuntu dhclient: No working leases in persistent database - sleeping.
Sep 22 11:42:02 cool1-ubuntu avahi-autoipd(ra0)[3606]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 108).
Sep 22 11:42:02 cool1-ubuntu avahi-autoipd(ra0)[3606]: Successfully called chroot().
Sep 22 11:42:02 cool1-ubuntu avahi-autoipd(ra0)[3606]: Successfully dropped root privileges.
Sep 22 11:42:02 cool1-ubuntu avahi-autoipd(ra0)[3606]: Starting with address 169.254.10.96
Sep 22 11:42:06 cool1-ubuntu wpa_supplicant[815]: Authentication with 00:16:b6:b3:a0:10 timed out.
Sep 22 11:42:06 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  associating -> disconnected
Sep 22 11:42:06 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Sep 22 11:42:07 cool1-ubuntu avahi-autoipd(ra0)[3606]: Callout BIND, address 169.254.10.96 on interface ra0
Sep 22 11:42:08 cool1-ubuntu wpa_supplicant[815]: Trying to associate with 00:16:b6:b3:a0:10 (SSID='2325' freq=2462 MHz)
Sep 22 11:42:08 cool1-ubuntu wpa_supplicant[815]: Association request to the driver failed
Sep 22 11:42:08 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  scanning -> associating
Sep 22 11:42:08 cool1-ubuntu kernel: [12740.472509] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:42:08 cool1-ubuntu kernel: [12740.472923] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Sep 22 11:42:08 cool1-ubuntu kernel: [12740.473023] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:42:11 cool1-ubuntu NetworkManager[3222]: <warn> Activation (ra0/wireless): association took too long.
Sep 22 11:42:11 cool1-ubuntu NetworkManager[3222]: <info> (ra0): device state change: 5 -> 6 (reason 0)
Sep 22 11:42:11 cool1-ubuntu NetworkManager[3222]: <warn> Activation (ra0/wireless): asking for new secrets
Sep 22 11:42:11 cool1-ubuntu NetworkManager[3222]: <info> (ra0): supplicant connection state:  associating -> disconnected
Sep 22 11:42:11 cool1-ubuntu avahi-autoipd(ra0)[3606]: Successfully claimed IP address 169.254.10.96
Sep 22 11:42:11 cool1-ubuntu ntpdate[3629]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Sep 22 11:42:11 cool1-ubuntu ntpdate[3629]: no servers can be used, exiting
Sep 22 11:42:13 cool1-ubuntu NetworkManager[3222]: <info> (ra0): device state change: 6 -> 9 (reason 7)
Sep 22 11:42:13 cool1-ubuntu NetworkManager[3222]: <warn> Activation (ra0) failed for access point (2325)
Sep 22 11:42:13 cool1-ubuntu NetworkManager[3222]: <info> Marking connection 'New 2325' invalid.
Sep 22 11:42:13 cool1-ubuntu NetworkManager[3222]: <warn> Activation (ra0) failed.
Sep 22 11:42:13 cool1-ubuntu NetworkManager[3222]: <info> (ra0): device state change: 9 -> 3 (reason 0)
Sep 22 11:42:13 cool1-ubuntu NetworkManager[3222]: <info> (ra0): deactivating device (reason: 0).
Sep 22 11:42:22 cool1-ubuntu kernel: [12753.962482] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:42:22 cool1-ubuntu kernel: [12753.962784] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:42:52 cool1-ubuntu kernel: [12783.962886] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
Sep 22 11:42:52 cool1-ubuntu kernel: [12783.963295] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 447
```

Whoa, wtf?

OMS

---

### Post by ohmysql on 2011-09-22
Question: Do you know why ubuntu is seeing my ethernet connection as a wireless network? That's super weird.

---

### Post by ohmysql on 2011-10-12
I'm going to mark this as solved. I never did get the wpa_supplicant to work. That's too bad!

And I may have to recompile this driver every time I upgrade, but that's fine.

Overall, rt3572sta seems to work. I'm going to mark this thread as solved. :)

OMS

---

### Post by praseodym on 2011-10-12
> **ohmysql said:**
> Question: Do you know why ubuntu is seeing my ethernet connection as a wireless network? That's super weird.

Check:

```
ifconfig -a
cat /etc/udev/rules.d/70-persistent-net.rules
iwconfig
dmesg | egrep 'eth0|ra0|interface'
```

---

### Post by ohmysql on 2011-10-15
> **praseodym said:**
> Check:

```
ifconfig -a
cat /etc/udev/rules.d/70-persistent-net.rules
iwconfig
dmesg | egrep 'eth0|ra0|interface'
```

Thank you. Because I'm not using network manager anymore, the problem seems to have gone away. But if I use it again, I'll follow your advice and report back. Thanks again.

OMS

PS It's good to have the internet on my wireless now :)

---

