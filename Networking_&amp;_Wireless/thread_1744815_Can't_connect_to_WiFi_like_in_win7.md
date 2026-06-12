---
title: "Can't connect to WiFi like in win7"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by mastermind01 on 2011-04-30
Hi there all. 

I'm new to linux ... and i have a big problem. I have installed both win7 and ubuntu, and with win7 i can easily connect to wifi in my arrea. Why i cannot i connect with this? I've installed the system with wired internet, and i'm trying to connect to a unsecured wifi. Please help me ... because in win7 i have no problems with this.

Thanks.

---

### Post by 6677 on 2011-04-30
Have you installed the drivers for your wifi card. If not i cant guide you through that as I am also new to linux but googling the wifi card model should show yield some results. Using your win7 you should be able to find the card model. Once again google will show you how as I havent used windows 7 outside of college computers where we have limited access

---

### Post by mastermind01 on 2011-04-30
it is strange that it shows the available wifi connections, i try to connect to one and it prompts "connecting" and after a while times out ... that means that i have my wireless card instaled, right?

---

### Post by majorawesome on 2011-04-30
An easier thing to do is just go to additional drives under administration in system. if that doesn't work type ```
lspci
``` in terminal and post it here (and if your running 64 or 32 bit)

---

### Post by mastermind01 on 2011-04-30
mastermind@mastermind-F6E:~$ lspci
    00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
    00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
    00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
    00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
    00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
    00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
    00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
    00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
    00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
    00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
    00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
    00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
    00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)


as i sed, i see wireless networks, trying to connect, but timeout ....

---

### Post by Blasphemist on 2011-04-30
Your ethernet and wifi aren't shown. See mine here.


> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation WiFi Link 5100


I don't know how to force it but try this. Run Additional Drivers and see if there is anything listed.

---

### Post by TBABill on 2011-04-30
If the wireless is a USB device (or internal USB device....yes, they exist) then do a ```
lsusb
``` so the system will report USB devices.

---

### Post by abisdad on 2011-04-30
Hi, while not an expert, if 
> it is strange that it shows the available wifi connections, i try to connect to one and it prompts "connecting" and after a while times out ... that means that i have my wireless card installed

then it might be a simple case of the wireless device that you are trying to connect to is looking for a password which you can add under the network connections wireless tab, then edit your connection, under the Wireless Security tab.

Good luck, Rob.

---

### Post by mastermind01 on 2011-05-01
> **TBABill said:**
> If the wireless is a USB device (or internal USB device....yes, they exist) then do a ```
lsusb
``` so the system will report USB devices.

 mastermind@mastermind-F6E:~$ lsusb
    Bus 007 Device 003: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
    Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 006 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
    Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 005 Device 002: ID 04f3:0232 Elan Microelectronics Corp. 
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 006: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
    Bus 002 Device 003: ID 04f2:b029 Chicony Electronics Co., Ltd 1.3M UVC Webcam
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    mastermind@mastermind-F6E:~$ 
    

and i must say that i see the wireless access points, and try to conect and nothing. The wifi network i try to connect is unsecured and has 2/5 lines of signal. Any help would be apreciated, thanks.

---

### Post by Blasphemist on 2011-05-01
With wireless only, what happens when you try to connect to the router using 192.168.1.1?

---

### Post by abisdad on 2011-05-02
Blas,

I'm guessing that you mean MM01 should open a terminal and type:

ping 192.168.1.1

or maybe

ping 192.168.0.1

to see if there is a connection.

Rob.

---

### Post by lz1dsb on 2011-05-02
> **mastermind01 said:**
>  The wifi network i try to connect is unsecured and has 2/5 lines of signal. Any help would be apreciated, thanks.

It could be that the signal level isn't high enough. Even though it shows 2/5 the signal level is always fluctuating. So this could be just the case with a poor coverage. 
Did you try to connect to an AP which has higher signal level?

---

### Post by Blasphemist on 2011-05-02
> **abisdad said:**
> Blas,

I'm guessing that you mean MM01 should open a terminal and type:

ping 192.168.1.1

or maybe

ping 192.168.0.1

to see if there is a connection.

Rob.

That would work but so would entering that IP into the address bar of the browser.

---

