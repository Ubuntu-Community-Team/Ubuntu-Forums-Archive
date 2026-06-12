---
title: "First time wireless setup"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by gordon071 on 2010-08-10
Very new to Ubuntu.  I installed Ubuntu on two machines--one desktop one laptop.
Dual boot with Vista and Windows 7.
I can bring up Ubuntu.
I can not connect via wireless 
I understand I may need drivers, etc., but threads talk of 'installing' things. 
I can't see how to install anything if the internet is not available. 
How do I get wireless to work?
Thanks

---

### Post by embolalia1187 on 2010-08-10
Ah, the classic catch-22. Can you connect to the network with a wire at all? What kind of wireless card are you using? (If you don't know, type lspci and look for anything that says "wireless", "network" or "802.11")

---

### Post by gordon071 on 2010-08-10
Ok. 
I just know this is going to sound dumb, but type it where?

---

### Post by gordon071 on 2010-08-10
To your question though, I have the following:**[SIZE=3]D-Link DWA-125 Wireless 150 USB Adapter[/SIZE] **

---

### Post by embolalia1187 on 2010-08-10
> **gordon071 said:**
> Ok. 
I just know this is going to sound dumb, but type it where?

Sorry. My fault. You would type it in the terminal. (Applications -> Accessories -> Terminal) Although, if it's USB, I don't know if lspci will show it...

Before I go on, I just want to make sure I'm right about where you are here. If you click on your network applet (top right, near the clock and such. Should be a pair of arrows or a wireless symbol), do you see anything about wireless? If you do, say what. If not, go ahead with the below.

I think, and it's been a while since I've had a wireless card that didn't work, that we need to know more than the brand name. We need to know the kind of chip that it uses. So if you go to the terminal and type in "lsusb", without the quotes, you should see something that says wireless or network. If you don't, paste it all here, as well as the output from typing "lspci", also without the quotes.

---

### Post by gordon071 on 2010-08-10
> **embolalia1187 said:**
> Sorry. My fault. You would type it in the terminal. (Applications -> Accessories -> Terminal) Although, if it's USB, I don't know if lspci will show it...
 
Before I go on, I just want to make sure I'm right about where you are here. If you click on your network applet (top right, near the clock and such. Should be a pair of arrows or a wireless symbol), do you see anything about wireless? If you do, say what. If not, go ahead with the below.
 
I think, and it's been a while since I've had a wireless card that didn't work, that we need to know more than the brand name. We need to know the kind of chip that it uses. So if you go to the terminal and type in "lsusb", without the quotes, you should see something that says wireless or network. If you don't, paste it all here, as well as the output from typing "lspci", also without the quotes.
 
------------------------------------------------------------------
First of all, thanks so much for your patience.
I ran the two commands and got:
 
[FONT=Liberation Serif]administrator@ubuntu:~$ isusb[/FONT]
 
[FONT=Liberation Serif]No command 'isusb' found, did you mean:[/FONT]
 
[FONT=Liberation Serif]Command 'lsusb' from package 'usbutils' (main)[/FONT]
 
[FONT=Liberation Serif]isusb: command not found[/FONT]
 
[FONT=Liberation Serif]administrator@ubuntu:~$ lsusb[/FONT]
 
[FONT=Liberation Serif]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
 
[FONT=Liberation Serif]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
 
[FONT=Liberation Serif]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
 
[FONT=Liberation Serif]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
 
[FONT=Liberation Serif]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
 
[FONT=Liberation Serif]Bus 002 Device 010: ID 03f0:4207 Hewlett-Packard [/FONT]
 
[FONT=Liberation Serif]Bus 002 Device 009: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD[/FONT]
 
[FONT=Liberation Serif]Bus 002 Device 008: ID 045e:0761 Microsoft Corp. [/FONT]
 
[FONT=Liberation Serif]Bus 002 Device 007: ID 04fc:05d8 Sunplus Technology Co., Ltd [/FONT]
 
[FONT=Liberation Serif]Bus 002 Device 006: ID 0409:0050 NEC Corp. [/FONT]
 
[FONT=Liberation Serif]Bus 002 Device 005: ID 04b8:0005 Seiko Epson Corp. Stylus D88+[/FONT]
 
[FONT=Liberation Serif]Bus 002 Device 004: ID 04a9:2213 Canon, Inc. CanoScan LiDE 50/LiDE 35/LiDE 40[/FONT]
 
[FONT=Liberation Serif]Bus 002 Device 003: ID 03f0:2e17 Hewlett-Packard Printing Support[/FONT]
 
[FONT=Liberation Serif]Bus 002 Device 002: ID 0409:0050 NEC Corp. [/FONT]
 
[FONT=Liberation Serif]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
 
[FONT=Liberation Serif]Bus 001 Device 002: ID 07d1:3c0d D-Link System [/FONT]
 
[FONT=Liberation Serif]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
 
[FONT=Liberation Serif]administrator@ubuntu:~$ lspci[/FONT]
 
[FONT=Liberation Serif]00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:03.0 Communication controller: Intel Corporation 82Q963/Q965 HECI Controller (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:03.2 IDE interface: Intel Corporation 82Q963/Q965 PT IDER Controller (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:03.3 Serial controller: Intel Corporation 82Q963/Q965 KT Controller (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)[/FONT]
 
[FONT=Liberation Serif]00:1f.0 ISA bridge: Intel Corporation 82801HO (ICH8DO) LPC Interface Controller (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)[/FONT]
 
[FONT=Liberation Serif]00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)[/FONT]
 
[FONT=Liberation Serif]02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)[/FONT]
 
[FONT=Liberation Serif]06:00.0 Multimedia controller: ATI Technologies Inc Theater 550 PRO PCI [ATI TV Wonder 550][/FONT]
 
[FONT=Liberation Serif]06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)[/FONT]
 
[FONT=Liberation Serif]administrator@ubuntu:~$ [/FONT]
 
 
[FONT=Arial]When I attempt to connect to hidden wireless network it asks for the password. I use the same one used with my other wireless Windows machines. But it does not connect.[/FONT]
I got a message that the wireless keyring did not get logged in when I started computer and it gave me the chance to enter the admin password which I did
 
The network icon shows the name of the network I try to connect to and keeps asking for the wireless encryption key. (Connect to Hidden Wireless Network)
 
Any assistance is greatly appreciated

---

### Post by grahammechanical on 2010-08-11
On the base or side of your wireless router/modem you should find the wireless key, also called WPA-PSK (the type of encryption). This combination of letters and numbers is what you are being asked to enter. It prevents other from accessing your wireless router. The system should remember it automatically. Another thing, if you are set for automatic logon when booting, then you will be asked for a password when you use a program that needs to connect to the router/modem. I can not find a way to stop this except to log in at boot up. It is a security feature, I think.

regards.

---

### Post by gordon071 on 2010-08-23
Thank you again for all the assistance.  I am still trying to get one PC to connect, but did get my laptop working.  I think you have supplied all I need.

---

