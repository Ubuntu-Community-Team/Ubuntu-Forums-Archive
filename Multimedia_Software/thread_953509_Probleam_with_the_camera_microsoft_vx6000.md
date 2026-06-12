---
title: "Probleam with the camera microsoft vx6000"
date: 2008-10-20
forum: Multimedia Software
---

### Post by Turge on 2008-10-20
Hello.
I bought a Microsoft Vx6000 camera and i have probleams with the camera.
I can use the microphone that in the camera but not the camera.
It's says no device.

So someone told me to write in the terminal "sudo lsusb" and "sudo lspci" and to say what it's says.

so that's what it's says when I write:

**_sudo lsusb :_**

Bus 007 Device 002: ID 045e:00f4 Microsoft Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 045e:009d Microsoft Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000 

**_sudo lspci :_**

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro]
01:00.1 Display controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (secondary)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

And then he says that there is no even 1 hint that said I have a camera.
Here is a picture of the camera:
[http://http://www.microsoft.com/hardware/digitalcommunication/images/lifecam/ic_productfeatures_vx6000.jpg]("http://http://www.microsoft.com/hardware/digitalcommunication/images/lifecam/ic_productfeatures_vx6000.jpg")

And then I go into System ---->Administration--->Hardware Drivers and it's says Microsft usb 2.0 camera in use and there is a green V.

But I told him in the skype it's says no devices how can I check it?
then he told me to write "sudo ls -al | grep /dev/video" and to see if it's give me "video 0" if it's tell me "video 0" so it's worked.

And it's says to me "ls: cannot access .gvfs: Permission denied ".


He said that there is a specific bag with this camera but there is a way to fix it.

Somebody know maybe?

Thank you anyway.

---

### Post by Turge on 2008-10-22
Somebody?

---

### Post by Turge on 2008-10-24
no one?

---

### Post by Turge on 2008-10-25
> **Turge said:**
> no one?

Someone?

---

### Post by thirstyghost on 2008-10-25
I don't think the ms-lifecams are supported in Linux yet.  I might've read somewhere that the vx-3000 worked partially, but I would recommend getting a logitech for using with Ubuntu.   I got a Logitech Quickcam STX which works out of the box, and the Pro-5000 which works sometimes.   The STX is about $50 new, but can be found for half that on Ebay or Craigslist.

---

### Post by Turge on 2008-10-27
So what are u saying to me?
That microsoft vx6000 lifecam cannot work in ubuntu?

Thank you.

---

### Post by Turge on 2008-10-28
> **Turge said:**
> So what are u saying to me?
That microsoft vx6000 lifecam cannot work in ubuntu?

Thank you.

???????????

---

### Post by skubler on 2008-10-31
I believe the previous responder is correct. I don't think your webcam is currently supported and hence may not work.

The following is a link to supported (and not so supported) webcams in the Ubuntu Wiki.

Hope this helps...


[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

