---
title: "Wireless Dongle! (So close)"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by tp-owner on 2009-04-08
I have installed ndiswrapper and the driver for me dongle. Its a zoom wireless 4410B and I am using a thinkpad 600e on ubuntu.

[B]Here are some results of test:
[/B]
Entered:
```
sudo lshw -C network
```
Result:
```
 *-network DISABLED      
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:25:85:98:2a:40
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

Entered:
```
lspci -nn
```
Result:
```
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:02.0 CardBus bridge [0607]: Texas Instruments PCI1251A [104c:ac1d]
00:02.1 CardBus bridge [0607]: Texas Instruments PCI1251A [104c:ac1d]
00:06.0 Multimedia audio controller [0401]: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] [1013:6001] (rev 01)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 02)
01:00.0 VGA compatible controller [0300]: Neomagic Corporation NM2200 [MagicGraph 256AV] [10c8:0005] (rev 12)
06:00.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
06:00.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
06:00.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 02)


```

Enetered:
```
iwconfig
```
Result:
```

lo        no wireless extensions.

pan0      no wireless extensions.



```

**I wasn't sure about the lspci bit because its a usb dongle...**

---

### Post by Kevbert on 2009-04-08
To list USB devices use
```
lsusb
```
(list usb devices, lspci is list pci devices).
According to
```
sudo lshw -C network
```
you have no firmware (drivers) installed. It may be worth running ndisgtk which you can find on the install CD in the /pool/main/n/ndisgtk directory.
To install it just double click on the .deb file. This will then give you the System-Administration-Windows Wireless Drivers menu option.
Make sure the USB adapter is connected and then run Windows Wireless Drivers and point it to your .inf and .sys windows files. You should then be able to set up a wireless connection.
If this fails try using
```
ifconfig pan0 up
```
to power up the dongle.

---

### Post by tp-owner on 2009-04-08
> **Kevbert said:**
> 
you have no firmware (drivers) installed. It may be worth running ndisgtk which you can find on the install CD in the /pool/main/n/ndisgtk directory.
To install it just double click on the .deb file. This will then give you the System-Administration-Windows Wireless Drivers menu option.
Make sure the USB adapter is connected and then run Windows Wireless Drivers and point it to your .inf and .sys windows files. You should then be able to set up a wireless connection.

I have done the above so I will try:
> 
If this fails try using
```
ifconfig pan0 up
```
to power up the dongle.

i WILL post again in a few mins...

---

### Post by tp-owner on 2009-04-08
I tried ```
ifconfig pan0 up
```

It said permission denied, this is confusing as I am on the admin coount... (the only one from installation!)

---

### Post by tp-owner on 2009-04-08
I eneterd the following and got the following result:

> sudo ifconfig pan0
pan0      Link encap:Ethernet  HWaddr 96:25:85:98:2a:40  
          inet6 addr: fe80::9425:85ff:fe98:2a40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)



---

### Post by 3rdalbum on 2009-04-08
Can you please give us the output of 'lsusb' as this will help us identify what chipset the dongle uses. I'd rather you use a native Linux driver if possible, before investigating running Windows drivers especially as Ndiswrapper doesn't work for all wireless devices.

---

### Post by tp-owner on 2009-04-08
```
bus 004 Device 002: ID 0803:4410 Zoom telephonics, Inc.
bus 004 Device 001: ID 1d6b:0002 Linux foundation 2.0 root hub
bus 004 Device 001: ID 1d6b:0001 Linux foundation 1.1 root hub
bus 004 Device 001: ID 1d6b:0001 Linux foundation 1.1 root hub
bus 004 Device 001: ID 1d6b:0001 Linux foundation 1.1 root hub
```

---

### Post by Kevbert on 2009-04-09
> **tp-owner said:**
> I tried ```
ifconfig pan0 up
```

It said permission denied, this is confusing as I am on the admin coount... (the only one from installation!)

Please use 'sudo' for permissions.
```
sudo ifconfig pan0 up
```

---

### Post by tp-owner on 2009-04-09
# sudo ifconfig pan0 up

this just asked for password and returned nothing... it just told me my username/computer name etc...

so i tried:
```
sudo ifconfig pan0
```

and i got:
```
pan0      Link encap:Ethernet  HWaddr fa:f0:b5:c1:b8:f6  
          inet6 addr: fe80::f8f0:b5ff:fec1:b8f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)


```

---

### Post by Kevbert on 2009-04-09
What does 
```
iwconfig
```
return ?
Also what do you now get with
```
iwlist scanning
```
?
If  you still get problems it still suggests the firmware drivers are not installed or recognised.
Edit...Seems that no-one has had any luck with this USB dongle in Linux yet...

---

### Post by tp-owner on 2009-04-09
#iwconfig:
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1104 (1.1 KB)  TX bytes:1104 (1.1 KB)

pan0      Link encap:Ethernet  HWaddr fa:f0:b5:c1:b8:f6  
          inet6 addr: fe80::f8f0:b5ff:fec1:b8f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

```

#iwlist scanning... Interface doesn't support scanning!

---

### Post by Kevbert on 2009-04-10
Do you have the .inf and .sys (XP) files for your modem ?  If not, you have two choices:

1) Contact [[COLOR="Red"]Zoom[/COLOR]]("http://www.zoom.com/techsupport/wireless_g/wireless4410b.shtml") and get them to send you the two files, explaining that you are trying to install their USB modem in Linux via ndiswrapper and need the two files. Install via the ndisgtk method mentioned earlier.

2) Download the [[COLOR="Red"]drivers[/COLOR]]("http://www.zoom.com/techsupport/wireless_g/wireless4410b.shtml") and get someone who has Windows to extract the files from the .exe file for you. You'll end up with a directory called Zoom4410B_Setup. Within this directory you want to go to /Driver/Ndis6 and try to copy and install the WlanUZGVxx.inf file where xx is either the 32 or 64 bit version. Install it via the ndisgtk method mentioned earlier. If this does not work you may need to try the drivers in the /Driver/Ndis5x directory.  Unfortunately I am unable to try this out as I don't have a Zoom modem.

There seems to be quite a few posts on the web regarding problems with this USB modem.

Good Luck.

---

### Post by tp-owner on 2009-04-10
I have installed the 32bit at the moment and it says that the hardware is present... If you seem to think the rest if fine then maybe I should try connecting to a network... Which I also lack the ability LOL...

---

### Post by Kevbert on 2009-04-10
To connect to a wireless network right-click on the icon that looks like two monitors in the top right-hand corner of your desktop. Check that both 'Enable Networking' and 'Enable wireless' are ticked. Now left-click on that icon and you should be able to see any available wireless networks and select one. You may be asked for a password key - enter this making sure you use the correct case for the entered characters. If your password is successful the two monitor icon will change to two dots with an arrow circling around it and then eventually this will turn into four signal strength bars. You now have a connection to the web....

---

### Post by tp-owner on 2009-04-10
> **Kevbert said:**
> To connect to a wireless network right-click on the icon that looks like two monitors in the top right-hand corner of your desktop. Check that both 'Enable Networking' and 'Enable wireless' are ticked. Now left-click on that icon and you should be able to see any available wireless networks and select one. You may be asked for a password key - enter this making sure you use the correct case for the entered characters. If your password is successful the two monitor icon will change to two dots with an arrow circling around it and then eventually this will turn into four signal strength bars. You now have a connection to the web....

Thanks that has really helped EXEPT.. I do not have the wireless check box... just the networking one :P

---

### Post by tp-owner on 2009-04-10
[B]Thanks a lot.... You telling my how to do that...

I went back into the easy install for drivers and installed two others which I had in the folder. One said invalid but the other also said that It worked, i right clicked on the thing again and WIRELESS WAS THERE! I CONNECTED TO OUR NETWORK ASAP... THANKS...[/B]

---

