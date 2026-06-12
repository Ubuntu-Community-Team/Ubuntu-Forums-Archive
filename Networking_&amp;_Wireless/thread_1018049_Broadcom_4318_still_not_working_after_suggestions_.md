---
title: "Broadcom 4318 still not working after suggestions posted..."
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by thorin81 on 2008-12-21
'sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh'


I just tried the above solution, but it did not work for me... I am running an Acer 5000 with the Broadcom 4318.

lspci gives:

nick@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

iwconfig gives:

lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=27 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I cannot seem to get it to run at all... I am relatively new to the Linux thing. Any help would be great!
	
dmesg also gives:

6103.444577] b43-phy1: Broadcom 4318 WLAN found
[ 6103.517319] phy1: Selected rate control algorithm 'pid'
[ 6107.630213] input: b43-phy1 as /devices/virtual/input/input9
[ 6107.712046] firmware: requesting b43/ucode5.fw
[ 6107.717900] firmware: requesting b43/pcm5.fw
[ 6107.725109] firmware: requesting b43/b0g0initvals5.fw
[ 6107.745786] firmware: requesting b43/b0g0bsinitvals5.fw
[ 6107.889698] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 6108.007692] Registered led device: b43-phy1::tx
[ 6108.008220] Registered led device: b43-phy1::rx
[ 6108.008642] Registered led device: b43-phy1::radio
[ 6108.044616] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6545.824166] b43-pci-bridge 0000:00:0b.0: PCI INT A disabled
[ 6567.838660] ieee80211_crypt: registered algorithm 'NULL'
[ 7025.576874] ieee80211_crypt: unregistered algorithm 'NULL'
[ 7037.035527] b43-pci-bridge 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 7037.092118] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0b.0
[ 7037.155678] b43-phy0: Broadcom 4318 WLAN found
[ 7037.222769] phy0: Selected rate control algorithm 'pid'
[ 7037.226013] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[ 7041.397943] input: b43-phy0 as /devices/virtual/input/input10
[ 7041.480054] firmware: requesting b43/ucode5.fw
[ 7041.485797] firmware: requesting b43/pcm5.fw
[ 7041.492852] firmware: requesting b43/b0g0initvals5.fw
[ 7041.511309] firmware: requesting b43/b0g0bsinitvals5.fw
[ 7041.656215] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 7041.783403] Registered led device: b43-phy0::tx
[ 7041.783899] Registered led device: b43-phy0::rx
[ 7041.784360] Registered led device: b43-phy0::radio
[ 7041.820643] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7042.408038] b43-phy0: Radio hardware status changed to DISABLED
[ 7042.464032] b43-phy0: Radio turned on by software
[ 7042.464048] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 7261.118968] ieee80211_crypt: registered algorithm 'NULL'
[ 7261.372323] ieee80211_crypt: registered algorithm 'TKIP'

Still not sure what to do next...

---

### Post by Ayuthia on 2008-12-21
> [ 7042.464048] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
Do you have a button or a switch that will turn on your card?  You might check that and see if you can connect.

---

### Post by acimmarusti on 2009-01-24
Hey there,

Go here, download the deb package under b43-firmware

[http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/)

(I know you are going to say this package is for hardy ubuntu 8.04, but trust me...I've tried the package meant for intrepid and it doesn't work!)

Once you do that, double click on the package to "execute" it. It will probably ask you for your administrator password. When you are done, restart your computer. Your wireless light should turn on after you log back in ubuntu and you should be able to detect wireless connections close to you.

I hope this works for ya. It has worked for me. If it complains saying that you have newer firmware installed, then force the installation.

---

### Post by acimmarusti on 2009-01-24
The new drivers don't work well in ubuntu 8.10. In fact this is a common problem for many distros. If you can't install the package at all, try reinstalling ubuntu and then install the package.

---

### Post by sampbar on 2009-01-25
Hello,

You could try my guide which uses ndiswrapper:
[http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html](http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html)

Any problems email: samuelbarrett {@} sampbar.com or just reply to this thread.

Samuel

---

