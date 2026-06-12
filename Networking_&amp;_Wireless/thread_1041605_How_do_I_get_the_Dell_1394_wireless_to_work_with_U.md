---
title: "How do I get the Dell 1394 wireless to work with Ubuntu 8.10"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by migs73 on 2009-01-16
Hi I'm new Linux and have Ubuntu 8.10 installed as a dual boot with Vista on a Dell Inspiron 1501. It has a 1394 wireless minicard installed. This is reported as DISABLED when I run lshw -C Network but the green light for WiFi is on (does not switch on and off with Fn+F2 but does with Vista).
The driver installed is the XP version running in ndiswrapper and is shown in ndisgtk GUI as being a valid driver and having recognised the hardware.
If I run ndiswrapper -l the alternative driver is listed as wl. What am I doing wrong!! Or what have I done wrong??

---

### Post by Ayuthia on 2009-01-16
It looks like you have a Broadcom card.  The card should work with the options listed in System->Administration->Hardware Drivers.  The wl driver is the Broadcom STA option.  You might need to remove ndiswrapper to make it work though.

If you want to use the ndiswrapper module, you can try the following:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
```

If it works, let us know which option you used.  If you used the ndiswrapper option, there is a workaround that needs to be added to make it permanent:
```
echo -e '#ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 ssb; modprobe --ignore-install ndiswrapper' | sudo tee -a /etc/modprobe.d/ndiswrapper
```

---

### Post by Jamco6000 on 2009-01-16
I have a similar problem, my wifi is not connected, my networks say disabled, and my fn + f2 does not work so i can enable the network. I'm pretty sure thats all thats wrong though. I appreciate any help. Thanks! 

sorry I'm new to linux but i know everyone on forums hatess reposts.

---

### Post by Ayuthia on 2009-01-17
> **Jamco6000 said:**
> I have a similar problem, my wifi is not connected, my networks say disabled, and my fn + f2 does not work so i can enable the network. I'm pretty sure thats all thats wrong though. I appreciate any help. Thanks! 

sorry I'm new to linux but i know everyone on forums hatess reposts.

Can you go into the Terminal and post the results of:
```
lspci -nn
```
It will help us see what wireless card you have.  You might also check System->Administration->Hardware Drivers and see if there is something that needs to be enabled.

---

### Post by migs73 on 2009-01-18
Thanks Ayuthia, I tried the code you recommended but it came up with errors. Tried to get rid of ndiswrapper using code I found elswhere and had other errors. Then tried to disable it using package manager but had errors on this to! Began to think I had done something terminal (no pun intended!!) as most admin type things I tried came up with errors. Re-installed Ubuntu, made sure ndiswrapper was not installed and enabled the Broadcom STA driver in hardware drivers and did a reboot. After this my wireless network was detected, but now I cannot connect to it. I put in my WEP password and the bottom left ball on the icon goes green, the top left grey and the blue band swirls round both. After a couple of minutes it returns to the original window requesting the passcode (even though it still shows being entered with the black dots).I am very confident I am using the correct password as I have other things I've connected recently. Any ideas?

---

### Post by Ayuthia on 2009-01-18
> **migs73 said:**
> Thanks Ayuthia, I tried the code you recommended but it came up with errors. Tried to get rid of ndiswrapper using code I found elswhere and had other errors. Then tried to disable it using package manager but had errors on this to! Began to think I had done something terminal (no pun intended!!) as most admin type things I tried came up with errors. Re-installed Ubuntu, made sure ndiswrapper was not installed and enabled the Broadcom STA driver in hardware drivers and did a reboot. After this my wireless network was detected, but now I cannot connect to it. I put in my WEP password and the bottom left ball on the icon goes green, the top left grey and the blue band swirls round both. After a couple of minutes it returns to the original window requesting the passcode (even though it still shows being entered with the black dots).I am very confident I am using the correct password as I have other things I've connected recently. Any ideas?

Can you go into the Terminal and post the results of lspci -nn?  I am mainly looking for the [14e4:43??] information.  I just want to confirm what options you have for wireless modules.  

I think that the issue might be with the STA module not liking the encryption.  You might first try to see if you can connect without WEP on your router.  If it works, you might then try to switch over to WPA to see if you can connect that way.

The other option could be to try the b43 module.  Of course, we need to confirm the wireless card info (the lspci -nn portion) to see which chipset you have.  If you have a valid chipset for the b43 module and you are able to connect without WEP, we could install the firmware for the b43 module and disable the STA module.  You should then be able to connect with WEP.

---

### Post by Jamco6000 on 2009-01-18
I'm on a different computer. If you can give me the information then I can look it up and type it to you. But as far as tying all of it ehh i guess i could if you need all of it. I was wondering if there was any way to turn the function f2 command. The drivers seem to be installed correctly, but its just a matter of turning it on. If you need all the info then ill get it.

---

### Post by Ayuthia on 2009-01-18
> **Jamco6000 said:**
> I'm on a different computer. If you can give me the information then I can look it up and type it to you. But as far as tying all of it ehh i guess i could if you need all of it. I was wondering if there was any way to turn the function f2 command. The drivers seem to be installed correctly, but its just a matter of turning it on. If you need all the info then ill get it.

All we need is the lspci -nn information for the wireless device.  It should be listed as a Network Controller or Ethernet Controller.  There should only be one or two entries there.  If the driver is not quite working yet, the function f2 command most likely won't work.

---

### Post by Jamco6000 on 2009-01-19
> **Ayuthia said:**
> All we need is the lspci -nn information for the wireless device.  It should be listed as a Network Controller or Ethernet Controller.  There should only be one or two entries there.  If the driver is not quite working yet, the function f2 command most likely won't work.

here is what i got for the lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 02)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

does that help?

---

### Post by Jamco6000 on 2009-01-19
here is some more info JIC

 sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:e4:be:4d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5705-v3.16 ip=192.168.1.5 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:76:34:df
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 32:aa:df:61:a2:3b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Ayuthia on 2009-01-19
> **Jamco6000 said:**
> here is some more info JIC

 sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:e4:be:4d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5705-v3.16 ip=192.168.1.5 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:76:34:df
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 32:aa:df:61:a2:3b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

You can try the following:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
```

---

### Post by Jamco6000 on 2009-01-19
> **Ayuthia said:**
> You can try the following:
[code]sudo modprobe -r b43 b43legacy ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart/[code]

now i dont even get an option for wireless network.....

do i need to restart?

---

### Post by Jamco6000 on 2009-01-19
i restarted and now my keyboard doesn't work???:confused:

---

### Post by Ayuthia on 2009-01-19
> **Jamco6000 said:**
> now i dont even get an option for wireless network.....

do i need to restart?

Sorry, I had you confused with the original poster (which was using ndiswrapper).

Can you try the following:
```
sudo modprobe -r b43 b43legacy ssb wl ndiswrapper
sudo modprobe b43legacy
sudo /etc/init.d/networking restart
dmesg|grep b43
```
You have a 4306 rev 02 card that uses the b43legacy module.  The last command will list out the messages related to the b43* modules.  Hopefully it will give you some kind of clue if firmware is missing or if something is not turned on.  With the card showing DISABLED, I am thinking that the card might not be turned on so dmesg should be able to let us know if that is the case.  If it is, then we need to figure out how to get the function f2 command working.

EDIT: Can you also let us know what computer (make and model) that you have?  It might help us see what needs to be done.

---

### Post by migs73 on 2009-01-21
Ayuthia, this is the result of the lspci -nn for my machine

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)

I was incorrect earlier saying my wireless was WEP encrypted when it was actually WPA. I took the encryption off and can connect without problems. I will try WPA but should I try WPA, WPA2 or mixed?

---

### Post by Ayuthia on 2009-01-21
> **migs73 said:**
> Ayuthia, this is the result of the lspci -nn for my machine

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)

I was incorrect earlier saying my wireless was WEP encrypted when it was actually WPA. I took the encryption off and can connect without problems. I will try WPA but should I try WPA, WPA2 or mixed?

If you were not able to connect with WPA then WPA2 will most likely not work either.  I don't really recommend switching to WEP since it is less secure.  The wl module tends to have problems with WPA/WEP.  You can either try using ndiswrapper or the b43 module.  Both should work for you.  Since you already have ndiswrapper ready to go:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
```
This should hopefully work.  The errors you encountered last time was because of your wired card.  The wired ethernet card uses the b44 module and it also needs the ssb module.  If this works, apply the following:
```
echo -e '#ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```and it should make it permanent.

---

### Post by Jamco6000 on 2009-01-27
chuck@chuck-laptop:~$ sudo modprobe -r b43 b43legacy ssb wl ndiswrapper
chuck@chuck-laptop:~$ sudo modprobe b43legacy
chuck@chuck-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
chuck@chuck-laptop:~$ dmesg|grep b43
[    7.422281] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   24.956011] b43legacy-phy0: Broadcom 4306 WLAN found
[   24.976101] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   24.976158] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   25.000111] b43legacy-phy0 debug: Radio initialized
[   39.214202] input: b43legacy-phy0 as /devices/virtual/input/input9
[   39.464105] firmware: requesting b43legacy/ucode4.fw
[   39.804448] firmware: requesting b43legacy/pcm4.fw
[   39.897927] firmware: requesting b43legacy/b0g0initvals2.fw
[   40.028118] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   40.103885] b43legacy-phy0 debug: Chip initialized
[   40.104022] b43legacy-phy0 debug: 30-bit DMA initialized
[   40.108025] Registered led device: b43legacy-phy0:tx
[   40.108025] Registered led device: b43legacy-phy0:rx
[   40.108025] Registered led device: b43legacy-phy0:radio
[   40.108025] b43legacy-phy0 ERROR: PHY transmission error
[   40.108025] b43legacy-phy0 debug: Wireless interface started
[   40.116602] b43legacy-phy0 debug: <3>b43legacy-phy0 ERROR: PHY transmission error
[  100.824529] b43legacy-phy0 ERROR: PHY transmission error
[  100.824634] b43legacy-phy0 ERROR: PHY transmission error
[  160.824611] b43legacy-phy0 ERROR: PHY transmission error
[  160.824709] b43legacy-phy0 ERROR: PHY transmission error
[  220.824720] b43legacy-phy0 ERROR: PHY transmission error
[  220.824885] b43legacy-phy0 ERROR: PHY transmission error
[  260.288012] b43legacy-phy0 debug: Removing Interface type 2
[  260.297559] b43legacy-phy0 debug: Wireless interface stopped
[  260.298995] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 1/64
[  260.299630] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 2/64
[  260.300263] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  260.305062] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  260.312083] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  260.320068] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  260.328251] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 2/128
[  260.336107] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  260.344258] b43legacy-phy0 debug: Radio initialized
[  260.344296] b43legacy-phy0 debug: Radio initialized
[  260.400441] b43-pci-bridge 0000:02:03.0: PCI INT A disabled
[  266.848011] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[  266.872015] b43legacy-phy0: Broadcom 4306 WLAN found
[  266.896190] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[  266.896281] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[  266.920302] b43legacy-phy0 debug: Radio initialized
[  271.203733] input: b43legacy-phy0 as /devices/virtual/input/input10
[  271.444085] firmware: requesting b43legacy/ucode4.fw
[  271.448746] firmware: requesting b43legacy/pcm4.fw
[  271.456023] firmware: requesting b43legacy/b0g0initvals2.fw
[  271.540165] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  271.605010] b43legacy-phy0 debug: Chip initialized
[  271.608207] b43legacy-phy0 debug: 30-bit DMA initialized
[  271.609751] Registered led device: b43legacy-phy0:tx
[  271.612969] Registered led device: b43legacy-phy0:rx
[  271.614283] Registered led device: b43legacy-phy0:radio
[  271.614441] b43legacy-phy0 ERROR: PHY transmission error
[  271.614511] b43legacy-phy0 debug: Wireless interface started
[  271.620568] b43legacy-phy0 ERROR: PHY transmission error
[  271.620666] b43legacy-phy0 ERROR: PHY transmission error
[  271.620831] b43legacy-phy0 debug: Adding Interface type 2
chuck@chuck-laptop:~$

---

### Post by Jamco6000 on 2009-01-27
I am using a Dell Latitude D600

ever since i did this code

sudo modprobe -r b43 b43legacy ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart

my keyboard doesnt work



my last post is the results of this code

sudo modprobe -r b43 b43legacy ssb wl ndiswrapper
sudo modprobe b43legacy
sudo /etc/init.d/networking restart
dmesg|grep b43

edit my keyboard works to log in, and i can hold funtion and change the brightness of the pc but when it comes to typing in things like in a seach bar they dont work.

---

### Post by Jamco6000 on 2009-01-30
keyboard works until you start writing in terminal, or type in a code, then it stops working.

---

### Post by Jamco6000 on 2009-01-31
anyone have this problem before?

---

### Post by Jamco6000 on 2009-02-01
bump....

---

### Post by Antien0222 on 2009-02-05
I'm new to Linux and I'm using a Dell inpsiron 1501 and the wireless drivers are not working for me, can anyone help me out with this issue i'm dual-booting with windows xp home edition.

---

### Post by Wolfhere on 2009-02-05
> **Ayuthia said:**
> It looks like you have a Broadcom card.  The card should work with the options listed in System->Administration->Hardware Drivers.  The wl driver is the Broadcom STA option.  You might need to remove ndiswrapper to make it work though.

If you want to use the ndiswrapper module, you can try the following:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
```

If it works, let us know which option you used.  If you used the ndiswrapper option, there is a workaround that needs to be added to make it permanent:
```
echo -e '#ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 ssb; modprobe --ignore-install ndiswrapper' | sudo tee -a /etc/modprobe.d/ndiswrapper
```

You are right! NDISWrapper is not needed. I also have the Broadcom wireless. On install without the wrapper, wireless worked great.;)

---

### Post by migs73 on 2009-06-19
I have been away a bit as I kind of gave up trying this for a while. Eventually got 8.10 to work using the wl and no ndiswrapper, but have now installed 9.04. Good news, it worked out the box once I activated the Broadcom STA driver.

---

