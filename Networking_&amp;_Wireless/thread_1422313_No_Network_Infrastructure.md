---
title: "No Network Infrastructure"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by vchapman on 2010-03-05
Yesterday I did the upgrade from 8.04 to 8.10 to 9.04. Somewhere along the way I lost my ability to manage the network interface. So when I boot the machine I have no network access.

In reading another thread, I found if I do this:

sudo ifup eth0
[sudo] password for jean: 
pam_mount(pam_mount.c:100): unknown pam_mount option "use_first_pass"
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:b9:6c:28:ef
Sending on   LPF/eth0/00:1b:b9:6c:28:ef
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.194 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.194 from 192.168.0.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 192.168.0.194 -- renewal in 34757 seconds.
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts

I get connected.

I think the network manager is missing, but I don't know how to verify this.

I have the wireless symbol at the top of my monitor with a red x stop sign!

I went through the upgrade process in the first place to get the wireless adapter to work. Now I am having trouble with the ethernet connection.

Some gentle help will be appreciated.

TIA

---

### Post by chili555 on 2010-03-05
> I have the wireless symbol at the top of my monitor with a red x stop sign!That is the Network Manager applet, so it seems you do have it.

Generally, you can use NM or manual configuration; that is, with /etc/network/interfaces, but not both. Yours seems to work, despite the usual behavior.

If you'd like to work on the wireless and fix up Network Manager as we go, please post:```
lspci -nn
iwconfig
```Thanks.

---

### Post by vchapman on 2010-03-05
Thanks for this. I am running the upgrade to 9.10. This will take a couple of hours. Then I will reply.

---

### Post by vchapman on 2010-03-05
> **chili555 said:**
> That is the Network Manager applet, so it seems you do have it.

post:```
lspci -nn
iwconfig
```Thanks.

 lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:0314]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:1314]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:2314]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. PT890 Host Bridge [1106:3208]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:4314]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:7314]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] [1106:3344] (rev 01)

=====================================

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

===============================


Previously I had another wireless adapter. I think that I had followed a bunch of instructions and done some kind of a custom low level install of that device. I suspect that some of that suff is still hanging around.

---

### Post by chili555 on 2010-03-05
I see nothing in your *lspci* that resembles a wireless device. Is it a USB device? If so, please insert it and post:```
lsusb
```Or, is it a PCMCIA device?```
lspcmcia
```We'll find it!

---

### Post by vchapman on 2010-03-05
> **chili555 said:**
> I see nothing in your *lspci* that resembles a wireless device. Is it a USB device? If so, please insert it and post:```
lsusb
```Or, is it a PCMCIA device?```
lspcmcia
```We'll find it!
Its there!

lsusb
Bus 001 Device 003: ID 0bda:8192 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2010-03-05
Now we're getting somewhere!> [COLOR="Blue"]0bda:8192[/COLOR] Realtek Semiconductor Corp. This is supported by a driver module *r8192s_usb* that is happily already in your kernel! Please try:```
sudo modprobe r8192s_usb
iwconfig
```Now do you have a wireless interface, wlan0, perhaps? Can you click the Network Manager icon and connect?

---

### Post by vchapman on 2010-03-05
> **chili555 said:**
> Now we're getting somewhere!This is supported by a driver module *r8192s_usb* that is happily already in your kernel! Please try:```
sudo modprobe r8192s_usb
iwconfig
```Now do you have a wireless interface, wlan0, perhaps? Can you click the Network Manager icon and connect?
Here is what I got:

 sudo modprobe r8192s_usb
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
jean@jean-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The network manager still has its white x on a red stop sign. If I rt click on the NM and select connection information, I get an error that says "no valid active connections found." I am running eth0 to send this message. The enable wireless is there and checked in the NM.

---

### Post by vchapman on 2010-03-05
> **vchapman said:**
> Here is what I got:

 sudo modprobe r8192s_usb
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
jean@jean-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The network manager still has its white x on a red stop sign. If I rt click on the NM and select connection information, I get an error that says "no valid active connections found." I am running eth0 to send this message. The enable wireless is there and checked in the NM.
If I left click on the NM under Wired Network I get "device not managed."

Under Wireless Networks I get "device not ready."

---

### Post by chili555 on 2010-03-05
Please let me see:```
ndiswrapper -l
dmesg | grep wlan
rfkill list
```Thanks.

---

### Post by vchapman on 2010-03-05
> **chili555 said:**
> Please let me see:```
ndiswrapper -l
dmesg | grep wlan
rfkill list
```Thanks.
Not much happening here

 ndiswrapper -l
root@jean-desktop:/home/jean# dmesg | grep wlan
[ 1133.035777] udev: renamed network interface wlan0 to wlan2
root@jean-desktop:/home/jean# rfkill list

---

### Post by vchapman on 2010-03-05
> **vchapman said:**
> Not much happening here

 ndiswrapper -l
root@jean-desktop:/home/jean# dmesg | grep wlan
[ 1133.035777] udev: renamed network interface wlan0 to wlan2
root@jean-desktop:/home/jean# rfkill list
I think at some pint in the past I followed these instructions. Hence, I am wondering if they are now getting in the way of where I want to be.

[http://ubuntuforums.org/showthread.php?t=571188&highlight=wpa+drops+connection](http://ubuntuforums.org/showthread.php?t=571188&highlight=wpa+drops+connection)

---

### Post by chili555 on 2010-03-05
It could very well be. The post is intended to allow you to configure networking without Network Manager. I have not read each and every line, but I am not sure, due to its age, it was written in the modern age in which NM is so tightly wound around our systems that manual configuration is almost impossible. In order to accomplish manual configuration effectively, NM must be removed. If you have second thoughts, it's not easy to get back!

One way to test whether NM will allow you to connect is to comment out the details in /etc/network/interfaces (which you can quickly and easily undo at any time) like this:> auto lo
iface lo inet loopback

#auto wlan0
#iface wlan0 inet dhcp
#wireless-essid mylilrouter
#wireless-key 096onlyforwepAFE 

#auto eth0
#iface eth0 inet dhcpReboot and see if NM manages your interfaces effectively.

Of course, you can simply remove NM through Synaptic and cross your fingers. You do have another computer available is we have to trouble-shoot, eh?

I am a bit confused as to whether your wireless card is using ndiswrapper or the native driver, r8192s_usb. However, you have a working interface, wlan2, so let's not fix what ain't broken.

---

### Post by vchapman on 2010-03-06
Yes, I have another computer.

Here is what my interfaces file looks like before I start to fiddle.

auto lo
iface lo inet loopback


iface eth0 inet dhcp




iface wlan0 inet dhcp
wireless-key 5CE2FE0CF2605CAF5C19F05B08
wireless-essid hawks





auto wlan0


It looks like I have been in here before!

---

### Post by chili555 on 2010-03-06
And did you comment out the wlan0 parts and reboot to see if NM takes over?> auto lo
iface lo inet loopback

[COLOR="Red"]#auto eth0 [/COLOR]
[COLOR="Red"]#[/COLOR]iface eth0 inet dhcp




[COLOR="Red"]#[/COLOR]iface wlan0 inet dhcp
[COLOR="Red"]#[/COLOR]wireless-key 5CE2FE0CF2605CAF5C19F05B08
[COLOR="Red"]#[/COLOR]wireless-essid hawks





[COLOR="Red"]#[/COLOR]auto wlan0
NM and manual configuration never work and play well together.

---

### Post by vchapman on 2010-03-06
Success, I think. I commented out all of those lines and restarted the computer. The NM started immediately and connected to eth0. So the ethernet connection appears to work normally.

The NM does not see the wireless connection.

---

### Post by chili555 on 2010-03-06
> The NM does not see the wireless connection.Please see: [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

Especially see:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themNM will, therefor, not probably show the wireless until the wire is detached. Please try and let us know.

---

### Post by vchapman on 2010-03-06
Something happened to my last reply. This from another computer. I removed the Ethernet cable. The NW threw up the white x with red stop sign. The NW does not see the wireless adapter. It only sees the wired network.

---

### Post by chili555 on 2010-03-06
Does *iwconfig* show an active wireless interface, wlan0 perhaps?

---

### Post by vchapman on 2010-03-06
> **chili555 said:**
> Does *iwconfig* show an active wireless interface, wlan0 perhaps?
it shows
lo 
eth0

I think that we need to hook up the wire (maybe) and reload the driver.

How did we get the driver from the kernel?

---

### Post by chili555 on 2010-03-06
```
sudo modprobe r8192s_usb
iwconfig
```If that works as expected, do:```
sudo su
echo r8192s_usb >> /etc/modules
exit
```It should load at boot hereafter.

---

### Post by vchapman on 2010-03-07
Something happened to my last post so I am sending it again. I have plugged the Ethernet cable back in.

The wireless still doesn't work although I think it is closer. See below:

 lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:1b:b9:6c:28:ef
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.0.194 latency=64 maxlatency=8 mingnt=3 multicast=yes
       resources: irq:23 ioport:ee00(size=256) memory:fdffe000-fdffe0ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan2
       serial: 00:e0:4c:81:92:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

---

### Post by chili555 on 2010-03-07
May we have a peek at:```
dmesg | grep r8192
```Thanks.

---

### Post by vchapman on 2010-03-07
ean@jean-desktop:~$ dmesg | grep r8192
[   19.052638] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.

---

### Post by vchapman on 2010-03-07
I think that I am ready for the sledge hammer approach. I think there are too many residual thing floating around from previous attempts to get the wireless network running. 

So what I am thinking is that I should backup my data and do a reformat and reinstall of Ubuntu 9.10.

Do you think that this may have a better outcome?

---

### Post by chili555 on 2010-03-07
It might. We certainly also could try to clean out the old stuff. What do you remember trying?

---

### Post by vchapman on 2010-03-07
For most of the life of the computer, it was running an old Linksys usb adapter. As I recall I had taken the Windows drivers and installed it using the ndiswrapper. It was an 802.11b adapter. I purchased a new router that is capable of supporting two wireless networks. So I left the b adapter running but was trying to get the r8192s adapter running on the n side of the network. The b side only supports wep whereas I wanted to get the wpa encryption going. I have a notebook with an 'n' adapter and that works really well.

At some point I had installed the Windows net8192 driver. There is a piece of software called Windows Wireless Adapter that facilitates this. I think it a front end for the ndiswrapper process. I had some limited success with this, but I couldn't get a sustainable connection. 

During the last day, I noticed that the system was starting up and shutting down something called (I think) WI-FI Radar daemon. I have no idea how that has come into play. I also notice that I have menu item called WI-FI Radar.

So the wireless network side is a mess. Do you think that it is worth trying to clean out all of the junk. Or, should I back up the data and reinstall the OS.

---

### Post by chili555 on 2010-03-07
I think it's at least worth a try to clean up what we have before we give up. When you run:```
lsmod | grep -e r819 -e ndis
```Which is running your device? You might also learn from:```
dmesg | grep -e r819 -e ndis
```If ndiswrapper is doing nothing for us, we can start by removing it in Synaptic. What does this tell us?```
ls /etc/modprobe.d | grep black
```If some modules were blacklisted, we might have to reverse it.

If you are not sure, don't remove anything until we agree.

---

### Post by vchapman on 2010-03-08
Do we need to see if the drivers for the old network adapter are still hanging around (I think that they are).

---

### Post by chili555 on 2010-03-08
That's where I am heading. If we can verify that your 8192 device is actually using r8192s_usb, and not by any chance, ndiswrapper, then we can remove and purge ndiswrapper. We may remove a level of confusion.

With the device inserted, let's do:```
sudo modprobe r8192s_usb
sudo modprobe ndiswrapper
sudo lsusb -v
```Let's see which device grabs your device. Thanks.

---

### Post by vchapman on 2010-03-08
> **chili555 said:**
> That's where I am heading. If we can verify that your 8192 device is actually using r8192s_usb, and not by any chance, ndiswrapper, then we can remove and purge ndiswrapper. We may remove a level of confusion.

With the device inserted, let's do:```
sudo modprobe r8192s_usb
sudo modprobe ndiswrapper
sudo lsusb -v
```Let's see which device grabs your device. Thanks.

 sudo modprobe r8192s_usb
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

The next command outputs an awful lot ... I am not sure tha I have it all


  bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints          11
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0a  EP 10 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0b  EP 11 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0c  EP 12 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0d  EP 13 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:10.4
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0503 highspeed power enable connect
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:10.3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:10.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x045e Microsoft Corp.
  idProduct          0x008c Wireless Intellimouse Explorer 2.0
  bcdDevice            0.56
  iManufacturer           1 Microsoft
  iProduct                2 Microsoft Wireless Optical Mouse&#65533; 1.0A
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
      ** UNRECOGNIZED:  09 21 11 01 00 01 22 d1 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:10.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0303 lowspeed power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:10.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0300 lowspeed power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

---

### Post by vchapman on 2010-03-08
I think that some of this is what is missing from the last post

 lsusb -s 2 -v

Bus 001 Device 002: ID 0bda:8192 Realtek Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x8192 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           95
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints          11
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0a  EP 10 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0b  EP 11 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0c  EP 12 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0d  EP 13 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x045e Microsoft Corp.
  idProduct          0x008c Wireless Intellimouse Explorer 2.0
  bcdDevice            0.56
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
      ** UNRECOGNIZED:  09 21 11 01 00 01 22 d1 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1

---

### Post by vchapman on 2010-03-08
More stuff that you asked for:

 lsmod | grep -e r819 -e ndis
r8192s_usb            222424  0 
ieee80211_rsl         126448  1 r8192s_usb
ndiswrapper           185532  0 
jean@jean-desktop:~$ dmesg | grep -e r819 -e ndis
[   18.122214] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   18.440045] usbcore: registered new interface driver ndiswrapper
[   19.564573] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
jean@jean-desktop:~$ ls /etc/modprobe.d | grep black
blacklist-ath_pci.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
jean@jean-desktop:~$

---

### Post by chili555 on 2010-03-08
I am starting to feel like ndiswrapper is going to heaven today. Please let me see:```
cat /etc/modprobe.d/ndiwrapper.conf
cat /etc/modprobe.d/blacklist.conf
```I am pretty sure it will do no harm, and may help to remove it, but let's just see those files first.

---

### Post by vchapman on 2010-03-08
> **chili555 said:**
> I am starting to feel like ndiswrapper is going to heaven today. Please let me see:```
cat /etc/modprobe.d/ndiwrapper.conf
cat /etc/modprobe.d/blacklist.conf
```I am pretty sure it will do no harm, and may help to remove it, but let's just see those files first.
cat /etc/modprobe.d/ndiwrapper.conf
cat: /etc/modprobe.d/ndiwrapper.conf: No such file or directory
jean@jean-desktop:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by chili555 on 2010-03-08
Your blacklist file looks fine; we don't need any changes there.

Sorry, I made a typo.```
cat /etc/modprobe.d/ndi[COLOR="Red"]s[/COLOR]wrapper.conf
```Before we get out the hatchet, may we take a look?

---

### Post by vchapman on 2010-03-08
There is no ndiswrapper.conf file

Howevver

root@jean-desktop:/etc# cd modprobe.d
root@jean-desktop:/etc/modprobe.d# ls
alsa-base.conf           blacklist-framebuffer.conf  libpisock9.conf
blacklist-ath_pci.conf   blacklist-modem.conf        ndiswrapper
blacklist.conf           blacklist-oss.conf          nvidia-kernel-nkc.conf
blacklist-firewire.conf  blacklist-watchdog.conf
root@jean-desktop:/etc/modprobe.d# cat ndiswrapper
alias usb:v050Dp805Ed*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v07AAp0043d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0BDAp8192d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0DF6p0031d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v1740p9201d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3301d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v5A57p0290d*dc*dsc*dp*ic*isc*ip* ndiswrapper
root@jean-desktop:/etc/modprobe.d#

---

### Post by chili555 on 2010-03-08
> cat ndiswrapper
alias usb:v050Dp805Ed*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v07AAp0043d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v[COLOR="Blue"]0BDAp8192[/COLOR]d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0DF6p0031d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v1740p9201d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v2001p3301d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v5A57p0290d*dc*dsc*dp*ic*isc*ip* ndiswrapper> lsusb
Bus 001 Device 003: ID [COLOR="Blue"]0bda:8192[/COLOR] Realtek Semiconductor Corp. Now I fear that ndiswrapper is driving your device. However, if it's not connecting at all, it's obviously not driving it well. We can experiment:```
sudo rmmod -f r8192s_usb
sudo modprobe ndiswrapper
```Now does the device work as expected? If not, let's reverse it:```
sudo rmmod -f ndiswrapper
sudo modprobe r8192s_usb
```How about now?

---

### Post by vchapman on 2010-03-08
> **chili555 said:**
> Now I fear that ndiswrapper is driving your device. However, if it's not connecting at all, it's obviously not driving it well. We can experiment:```
sudo rmmod -f r8192s_usb
sudo modprobe ndiswrapper
```Now does the device work as expected? If not, let's reverse it:```
sudo rmmod -f ndiswrapper
sudo modprobe r8192s_usb
```How about now?


jean@jean-desktop:~$ sudo rmmod -f r8192s_usb
[sudo] password for jean: 
jean@jean-desktop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

The NM does not see any wireless network, only a wired network.



 sudo rmmod -f ndiswrapper
jean@jean-desktop:~$ sudo modprobe r8192s_usb
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

The NM now sees a wireless network. In grayed out text it says 'devicenot ready,

---

### Post by chili555 on 2010-03-10
> sudo rmmod -f ndiswrapper
jean@jean-desktop:~$ sudo modprobe r8192s_usb
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

The NM now sees a wireless network. In grayed out text it says 'devicenot ready,When this condition exists, may I see:```
iwconfig
``` Also, please try:```
sudo iwconfig wlan0 power on
sudo iwconfig wlan0 mode auto
```Now does NM say 'device not ready?'

---

### Post by vchapman on 2010-03-10
> **chili555 said:**
> When this condition exists, may I see:```
iwconfig
``` [/CODE]

it finds 
lo

eth0 (both with no wireless extensions)

and

wlan2 

This looks like the adapter. Should I try the the other commands with wlan2 instead of wlan0?

---

### Post by vchapman on 2010-03-10
One more point. 

In NM with the Ethernet cable disconnected I get

Wired Network
Disconnected (grayed out)

---Available-----
Auto eth0
Wireless Networks
device not ready (grayed out)

---

### Post by chili555 on 2010-03-10
> Should I try the the other commands with wlan2 instead of wlan0?Please!

---

### Post by vchapman on 2010-03-10
Latest go around

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 sudo iwconfig wlan2 power on
[sudo] password for jean: 
jean@jean-desktop:~$ sudo iwconfig wlan2 mode auto
jean@jean-desktop:~$

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan2     802.11b/g  Mode:Auto  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I think that wlan0 is still hiding in the bushes. Its probably owned by the old wireless adapter.

---

### Post by vchapman on 2010-03-10
> **chili555 said:**
> Now does NM say 'device not ready?'

Sorry I didn't answer this. Yes it still says device not ready.

At the risk of further complicating things, would there be anything to be gained from a trouble shooting point of view if I were to plug in the old adapter. Would it provide any clues as to what things need to be deleted or modified to make the 8192 adapter work?

Another thought! Several steps back it appeared that the ndiswrapper was not being used. It looks like that it is using some called 8192_usb. So what happens if I throw away the ndiswrapper file. Or at least comment out the 8192 line. Do you know what all of the other stuff is in the ndiswrapper file?

---

### Post by vchapman on 2010-03-11
Well I have backed up all of the data. So now I am going to start over. This probably not the elegant solution, but I hope that it will work.

---

### Post by vchapman on 2010-03-13
> **vchapman said:**
> Well I have backed up all of the data. So now I am going to start over. This probably not the elegant solution, but I hope that it will work.

Well I have reloaded ubuntu 9.10 (twice in fact). I have discovered elsewhere

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101#USB)

that my usb adapter (AWLL6077) requires the ndiswrapper.

This has led to another new and maybe not so interesting problem.

Before I go on, I would like to thank you for your superb support in trying to get my network to run. 

So now briefly here is my new problem. The network adapter does see and connects to my router. This is a WPA enabled connection. However, I cannot ping my machine nor can I get firefox to see any servers. --- do you want me to continue here or start a new thread with this problem

---

### Post by chili555 on 2010-03-13
> The network adapter does see and connects to my router. This is a WPA enabled connection. However, I cannot ping my machine nor can I get firefox to see any servers.Please let us see:```
ifconfig
cat/etc/resolv.conf
```Thanks.

---

### Post by vchapman on 2010-03-13
> **chili555 said:**
> Please let us see:```
ifconfig
cat/etc/resolv.conf
```Thanks.
  
OK, here is what you asked for plus some other stuff. At the moment I am connect to an open network (no encryption) with same result.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:6c:28:ef  
          inet6 addr: fe80::21b:b9ff:fe6c:28ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:21:2f:2e:00:45  
          inet addr:192.168.0.189  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:2fff:fe2e:45/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16835 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16454 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3021915 (3.0 MB)  TX bytes:1232587 (1.2 MB)

 cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1


Other stuff


 ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8192u : driver installed
    device (0BDA:8192) present (alternate driver: r8192s_usb)


 dmesg | grep -e ndis -e wlan
[   14.381230] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   15.020904] ndiswrapper: driver net8192u (Airlink101,09/11/2008,5.1350.0911.2008) loaded
[   19.029735] wlan0: ethernet device 00:21:2f:2e:00:45 using NDIS driver: net8192u, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192 Wireless LAN USB NIC                                     ', 0BDA:8192.F.conf
[   19.029813] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   19.029940] usbcore: registered new interface driver ndiswrapper
[   19.058462] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   19.058577] udev: renamed network interface wlan0 to wlan1
[   19.073077] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   79.732617] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   80.301773] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   90.896014] wlan1: no IPv6 routers present
[  170.154035] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  210.187623] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  998.996620] ndiswrapper (iw_set_auth:1602): invalid cmd 12

---

### Post by chili555 on 2010-03-14
> (alternate driver: r8192s_usb)You might blacklist r8192s_usb, if it isn't already done. ```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line:```
blacklist r8192s_usb
```Can you ping the router?```
ping -c3 102.168.0.1
```> wlan1 Link encap:Ethernet HWaddr 00:21:2f:2e:00:45
inet addr:192.168.0.189 Bcast:192.168.0.255 Mask:255.255.255.0Was this IP address assigned by the router, or manually by you?> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.Please do:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```

---

### Post by vchapman on 2010-03-14
> **chili555 said:**
> You might blacklist r8192s_usb, if it isn't already done. ```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line:```
blacklist r8192s_usb
```

I have done this .... not sure that it has worked

---

### Post by vchapman on 2010-03-14
> **chili555 said:**
> Can you ping the router?```
ping -c3 102.168.0.1
```

I haven't tried this particular command, but I cannot ping the router.

---

### Post by vchapman on 2010-03-14
> **chili555 said:**
> Was this IP address assigned by the router, or manually by you?


The DHCP server in the router has a reservation for the MAC address in the network adapter card in the computer. The same address is assigned each time. There are no fixed addresses on the computer side.

---

### Post by vchapman on 2010-03-14
> **chili555 said:**
> You might blacklist r8192s_usb, if it isn't already done. ```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line:```
blacklist r8192s_usb
```Can you ping the router?```
ping -c3 102.168.0.1
```Was this IP address assigned by the router, or manually by you?Please do:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```


Here is the ping again (you have the incorrect address)

 ping -c 5 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=1.94 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=2.16 ms

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 2 received, 60% packet loss, time 4023ms
rtt min/avg/max/mdev = 1.945/2.056/2.168/0.120 ms


Here is some other stuff

 nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             disconnected
  Default:           no
  HW Address:        00:1B:B9:6C:28:EF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan1  [Auto ravens] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        00:21:2F:2E:00:45

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    airportthru:     Ad-Hoc, 02:E0:DF:62:68:B3, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    *ravens:         Infra, 00:24:01:72:D3:B3, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    DPCnet:          Infra, 00:23:12:FA:DC:DF, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    The Marshalsea:  Infra, 00:26:BB:76:F4:83, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA2
    canuck:          Infra, 00:13:46:CD:72:42, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA
    hawks:           Infra, 06:24:01:72:D3:B3, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.189
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

---

### Post by vchapman on 2010-03-14
The blacklist of the driver provided by the kernel doesn't seem to work.

 cat blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# get rid of competing wireless card driver r8192s_usb
blacklist r8192s_usb

-----------------
and
-----------------

 ndiswrapper -l
net8192u : driver installed
    device (0BDA:8192) present (alternate driver: r8192s_usb)

Two thoughts

Maybe r8192_usb is an alias and not the real driver. I checked to see if this was true but turned up nothing.

Maybe I should throw away the ndiswrapper and try r8192_usb. I think I know how to eliminate the nndiswrapper version of the driver. I do not know how to invoke the kernel version. 

In any event, I think that there is a conflict between the two.

---

### Post by chili555 on 2010-03-14
It seems apparent that some packets are getting through, all though 60% (!!) are lost. I have to suspect that the process of the router checking the MAC address is faulty, either in its implementation at the router or in the driver correctly transmitting the MAC with each and every packet.

If you are using WPA, do you feel you also need MAC address filtering? Have you tried, even temporarily, without filtering?> Maybe I should throw away the ndiswrapper and try r8192_usb. I think I know how to eliminate the nndiswrapper version of the driver. I do not know how to invoke the kernel version.Temporarily, you can do:```
sudo rmmod -f ndiswrapper
sudo modprobe r8192s_usb
```I will be interested in the result. The way to see if r8192s_usb is actually loading, and not just giving an informative message is:```
lsmod | grep r8192
```

---

### Post by vchapman on 2010-03-14
sudo rmmod -f ndiswrapper
[sudo] password for jean: 
jean@jean-desktop:~$ sudo modprobe r8192s_usb
jean@jean-desktop:~$ lsmod | grep r8192
r8192s_usb            222424  0 
ieee80211_rsl         126448  1 r8192s_usb
jean@jean-desktop:~$ dmesg | grep -e ndis -e wlan
[   14.455513] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   14.557369] usbcore: registered new interface driver ndiswrapper
[  277.609481] usbcore: deregistering interface driver ndiswrapper
jean@jean-desktop:~$

---

### Post by vchapman on 2010-03-14
Here is more stuff. I guess my question now is how do I turn it on?

 nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             disconnected
  Default:           no
  HW Address:        00:1B:B9:6C:28:EF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xU
  State:             unavailable
  Default:           no
  HW Address:        00:E0:4C:81:92:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

### Post by vchapman on 2010-03-14
I have turned off the reservations in the DHCP server.

---

### Post by chili555 on 2010-03-14
> Type: 802.11 WiFi
Driver: rtl819xU
State: unavailableHow to start it...?

What does this tell us?```
iwconfig
dmesg | grep firmware
```Thanks.

---

### Post by vchapman on 2010-03-14
> **chili555 said:**
> How to start it...?

What does this tell us?```
iwconfig
dmesg | grep firmware
```Thanks.


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jean@jean-desktop:~$ dmesg | grep firmware
[  236.142927] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  236.193150] rtl819xU:request firmware fail!
[  236.216849] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  236.227497] rtl819xU:request firmware fail!
[  236.268880] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  236.279707] rtl819xU:request firmware fail!
[  236.303901] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  236.321230] rtl819xU:request firmware fail!

---

### Post by chili555 on 2010-03-15
> rtl819xU:request firmware fail!Ah, ha!

On my system, and yours, too, I expect, I have the firmware:> /lib/firmware/2.6.31-20-generic/RTL8192SE
/lib/firmware/2.6.31-20-generic/RTL8192SE/[COLOR="Blue"]rtl8192sfw.bin[/COLOR]It is not, however, where the driver expects it to be. > usb 1-2: firmware: requesting [COLOR="Blue"]RTL8192SU[/COLOR]/rtl8192sfw.binRemove the device. Open a terminal and do:```
cd /lib/firmware/`uname -r` 
```The `uname -r` will use whatever kernel you are running at the moment, not just x-20 as I am and you may not be.```
sudo mkdir RTL8192SU
sudo cp /lib/firmware/`uname -r`/RTL8192SE/*  RTL8192SU
```This copies all the firmware files to a new RTL8192[COLOR="Blue"]SU[/COLOR] directory from the RTL8192SE directory where they currently exist.

Plug in the device and please connect! If you have rebooted since our last experiment, you will again have to rmmod ndiswrapper and modprobe r8192s_usb as above.

This is a genuine bug and the fix will need to be repeated when you update to a newer kernel version, also known as linux-image.

---

### Post by vchapman on 2010-03-15
Its never straight forward!

jean@jean-desktop:/lib/firmware/2.6.31-20-generic$ sudo cp /lib/firmware/`uname -r`/RTL8192SE/*  RTL8192SU
cp: cannot stat `/lib/firmware/2.6.31-20-generic/RTL8192SE/*': No such file or directory

At one point the driver r8192s_usb was in my blacklist file. Would that remove the directory? Or, is the directory somewhere else?

---

### Post by chili555 on 2010-03-15
Maybe it's hiding or even non-existent. Please do```
cd /lib/firmware/2.6.31-20-generic/ && ls
```Is there an RTL something file in there? You can also do:```
sudo updatedb
locate rtl8192sfw.bin
```If it is there, the idea is to simply copy (cp) it over from wherever it is, to where the driver expects it to be, namely, */lib/firmware/2.6.31-20-generic/RTL8192S[COLOR="Blue"]U[/COLOR]/rtl8192sfw.bin*

If you don't have it at all, that's a new hurdle!> r8192s_usb was in my blacklist file. Would that remove the directory?Nope.

---

### Post by vchapman on 2010-03-15
It doesn't appear to exist!!!

 sudo updatedb
[sudo] password for jean: 
jean@jean-desktop:/lib/firmware/2.6.31-20-generic$ locate rtl8192sfw.bin
jean@jean-desktop:/lib/firmware/2.6.31-20-generic$

does this provide a clue about where to look?

jean@jean-desktop:/lib/firmware/2.6.31-20-generic$ modprobe -l r8192s_usb
kernel/drivers/staging/rtl8192su/r8192s_usb.ko

---

### Post by chili555 on 2010-03-15
Here ya go!

Right click, select Extract here and drop it into the folder you created and do:```
sudo chown root:root /lib/firmware/2.6.31-20-generic/RTL8192SU/rtl8192sfw.bin
sudo chmod +x /lib/firmware/2.6.31-20-generic/RTL8192SU/rtl8192sfw.bin
```Then do:```
ls -al /lib/firmware/2.6.31-20-generic/RTL8192SU/rtl8192sfw.bin
```It should look like this:> -rwxr-xr-x 1 root root 75984 2010-03-05 07:46 /lib/firmware/2.6.31-20-generic/RTL8192SU/rtl8192sfw.binRe-insert the device and let's connect!

---

### Post by vchapman on 2010-03-15
> **chili555 said:**
> Here ya go!

Right click, select Extract here and drop it into the folder you created and

I think that I missed something here. What am I rt clicking on?

---

### Post by chili555 on 2010-03-15
You are downloading my attachment above, a zipped copy of the firmware. Extract it, put it in the SU directory and proceed as outlined.

---

### Post by vchapman on 2010-03-15
There is no joy in Mudville

jean@jean-desktop:~$ dmesg | grep firmware
[  154.698903] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
jean@jean-desktop:~$ lsmod | grep r8192
r8192s_usb            222424  0 
ieee80211_rsl         126448  1 r8192s_usb
jean@jean-desktop:~$ lsusb
Bus 001 Device 002: ID 0bda:8192 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jean@jean-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:6c:28:ef  
          inet6 addr: fe80::21b:b9ff:fe6c:28ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

jean@jean-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jean@jean-desktop:~$

---

### Post by chili555 on 2010-03-15
You have an interface *wlan0*. Does *nm-tool* show any improvement? Is the state still "Unavailable?" Does Network Manager show networks? What does this say:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by vchapman on 2010-03-15
> **chili555 said:**
> You have an interface *wlan0*. Does *nm-tool* show any improvement? Is the state still "Unavailable?" Does Network Manager show networks? What does this say:```
sudo iwlist wlan0 scan
```Thanks.


iwlist wlan0 scan
[sudo] password for jean: 
wlan0     Interface doesn't support scanning : Network is down

jean@jean-desktop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        00:1B:B9:6C:28:EF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.195
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xU
  State:             unavailable
  Default:           no
  HW Address:        00:E0:4C:81:92:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

### Post by chili555 on 2010-03-15
> - Device: eth0 [Auto eth0] ----------------------------------------------------
Type: Wired
State: [COLOR="Blue"]connected[/COLOR]
Carrier Detect: yes
Address: 192.168.0.195

- Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: rtl819xU
State: [COLOR="Blue"]unavailable[/COLOR]That's how Network Manager is designed to work, disconnect the wireless if the wired is available. Please detach the ethernet cable, give NM a few moments to recognize the change of state and try again.

---

### Post by vchapman on 2010-03-15
It doesn't connect. Here is my latest attack on the problem

r8192s_usb
[sudo] password for jean: 
jean@jean-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:6c:28:ef  
          inet6 addr: fe80::21b:b9ff:fe6c:28ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

jean@jean-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jean@jean-desktop:~$ nm-tools
No command 'nm-tools' found, did you mean:
 Command 'nm-tool' from package 'network-manager' (main)
nm-tools: command not found
jean@jean-desktop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             disconnected
  Default:           no
  HW Address:        00:1B:B9:6C:28:EF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xU
  State:             unavailable
  Default:           no
  HW Address:        00:E0:4C:81:92:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


jean@jean-desktop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

jean@jean-desktop:~$ dmesg | grep firmware
[  141.720045] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
jean@jean-desktop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

jean@jean-desktop:~$ dmesg | grep firmware
[  141.720045] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
jean@jean-desktop:~$ sudo modprobe r8192s_usb
jean@jean-desktop:~$ lsmod | grep -e 8192
r8192s_usb            222424  0 
ieee80211_rsl         126448  1 r8192s_usb
jean@jean-desktop:~$ dmesg | grep -e ndis -e wlan
[   14.507220] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   14.648417] usbcore: registered new interface driver ndiswrapper
jean@jean-desktop:~$ dmesg | grep -e ndis -e wlan
[   14.507220] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   14.648417] usbcore: registered new interface driver ndiswrapper


Looks like I have done something to cause the ndiswrapper to show up again. I have actually uninstalled the windows driver.

At this point, subject to your suggestions, I think that I might try the ndiswrapper again. As you pointed out it was very close previously. I have noticed something in the last day that makes me wonder if I had a bad setting on the router side when I was trying the ndiswrapper previously. 

Failing all of the this, I may just go and purchase a different wireless network adapter.

---

### Post by vchapman on 2010-03-16
Here is my uneasiness about my first ndiswrapper attempt.

Here is an earlier post

- Device: wlan1  [Auto ravens]  -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        00:21:2F:2E:00:45

Here is some stuff from today:

- Device: wlan0  ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xU
  State:             unavailable
  Default:           no
  HW Address:        00:E0:4C:81:92:00

-------------------------

Why do these two results have a different hardware address for my network adapter. I think you picked up on this, but not exactly two or three days ago. When I was trying this with the ndiswrapper, I had a reservation in the DHCP server for this. What happens if the HW address in the DHCP server reservation was wrong? It certainly was different than the one displayed above. So let's say it connects to the server based on the computer name. Once there things become confused because network adapter actually has a different address than the one stored in the DHCP server. I don't think I ever tried the ndiswrapper after I removed the reservation from the DHCP server.

Or maybe I am grasping at straws............

---

### Post by chili555 on 2010-03-16
> At this point, subject to your suggestions, I think that I might try the ndiswrapper again.I must reluctantly agree. I am predisposed to champion the native Linux drivers and to do whatever it takes to get it going correctly. However, the simple truth in this case is that the r8192s_usb isn't being started correctly by Network Manager or otherwise. There are a few other examples of Realtek cards with the same issue on this forum.

But isn't our real objective to get you on line, download all the updates, start emailing the grandkids* and enjoy? Ndiswrapper seems like it has the greatest chance of success if we disable or figure out MAC filtering, so I agree.> Why do these two results have a different hardware address for my network adapter.I do not know. There is surely a software glitch somewhere and perhaps it's even in ndiswrapper. Obviously, if you are using MAC filtering and the device mis-identifies itself, access to the WAN, at least, is not going to work.

I am almost afraid to ask if there is a MAC sticker on the device itself and how it compares with the two numbers that have been reported in *nm-tool*. 

I suggest you blacklist r8192s_usb. Reload ndiswrapper and turn off MAC filtering in the router. Do you connect reliably? Add MAC filtering for the address reported in *nm-tool*. Do you connect reliably?

I would love to know the make and model of your device so I can buy one and hammer it into submission.


*I have three myself and will soon have a great-grandchild. I bet you thought I was a 17-year-old hacker geek!

---

### Post by vchapman on 2010-03-16
I will respond to your latest post, later. Here is my latest ndiswrapper experience.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:6c:28:ef  
          inet6 addr: fe80::21b:b9ff:fe6c:28ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2520 (2.5 KB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:21:2f:2e:00:45  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:2fff:fe2e:45/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2443 (2.4 KB)  TX bytes:6427 (6.4 KB)

jean@jean-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"ravens"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:01:723:B3   
          Bit Rate=130 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thrff   Fragment thrff
          Power Managementff
          Link Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jean@jean-desktop:~$ dmesg | grep -e ndis -e wlan
[   14.673883] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   15.234123] ndiswrapper: driver net8192u (Airlink101,09/11/2008,5.1350.0911.200 loaded
[   19.093686] wlan0: ethernet device 00:21:2f:2e:00:45 using NDIS driver: net8192u, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192 Wireless LAN USB NIC                                     ', 0BDA:8192.F.conf
[   19.093762] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   19.093885] usbcore: registered new interface driver ndiswrapper
[   19.122779] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   19.122900] udev: renamed network interface wlan0 to wlan1
[   19.143870] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1729.728717] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1730.014256] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1740.528014] wlan1: no IPv6 routers present
jean@jean-desktop:~$ nw-tool
No command 'nw-tool' found, did you mean:
 Command 'nm-tool' from package 'network-manager' (main)
nw-tool: command not found
jean@jean-desktop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             disconnected
  Default:           no
  HW Address:        00:1B:B9:6C:28:EF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan1  [Auto ravens] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        00:21:2F:2E:00:45

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    The Marshalsea:  Infra, 00:26:BB:76:F4:83, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA2
    *ravens:         Infra, 00:24:01:72:D3:B3, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2
    Home:            Infra, 00:18:F8:C04:FC, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA
    canuck:          Infra, 00:13:46:CD:72:42, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA
    DPCnet:          Infra, 00:23:12:FACF, Freq 2417 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    hawks:           Infra, 06:24:01:723:B3, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.197
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


jean@jean-desktop:~$ ping -c 5 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:6c:28:ef  
          inet6 addr: fe80::21b:b9ff:fe6c:28ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2520 (2.5 KB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:21:2f:2e:00:45  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:2fff:fe2e:45/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2443 (2.4 KB)  TX bytes:6427 (6.4 KB)

jean@jean-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"ravens"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:01:72:D3:B3   
          Bit Rate=130 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thrff   Fragment thr:off
          Power Managementff
          Link Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jean@jean-desktop:~$ dmesg | grep -e ndis -e wlan
[   14.673883] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   15.234123] ndiswrapper: driver net8192u (Airlink101,09/11/2008,5.1350.0911.2008) loaded
[   19.093686] wlan0: ethernet device 00:21:2f:2e:00:45 using NDIS driver: net8192u, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192 Wireless LAN USB NIC                                     ', 0BDA:8192.F.conf
[   19.093762] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   19.093885] usbcore: registered new interface driver ndiswrapper
[   19.122779] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   19.122900] udev: renamed network interface wlan0 to wlan1
[   19.143870] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1729.728717] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 1730.014256] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1740.528014] wlan1: no IPv6 routers present
jean@jean-desktop:~$ nw-tool
No command 'nw-tool' found, did you mean:
 Command 'nm-tool' from package 'network-manager' (main)
nw-tool: command not found
jean@jean-desktop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             disconnected
  Default:           no
  HW Address:        00:1B:B9:6C:28:EF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan1  [Auto ravens] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        00:21:2F:2E:00:45

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    The Marshalsea:  Infra, 00:26:BB:76:F4:83, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA2
    *ravens:         Infra, 00:24:01:72:D3:B3, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2
    Home:            Infra, 00:18:F8:C0:D4:FC, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA
    canuck:          Infra, 00:13:46:CD:72:42, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA
    DPCnet:          Infra, 00:23:12:FAF, Freq 2417 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    hawks:           Infra, 06:24:01:723:B3, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.197
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


jean@jean-desktop:~$ ping -c 5 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

---

### Post by vchapman on 2010-03-16
> But isn't our real objective to get you on line, download all the updates, start emailing the grandkids* and enjoy? Ndiswrapper seems like it has the greatest chance of success if we disable or figure out MAC filtering, so I agree.I do not know.Well it turns out that the MAC address that I had on the DHCP server is the correct one. This is printed on the outside of the usb dongle.

 > There is surely a software glitch somewhere and perhaps it's even in ndiswrapper. Obviously, if you are using MAC filtering and the device mis-identifies itself, access to the WAN, at least, is not going to work.So the HW address that was being displayed when we tried the other approach is not correct. Maybe this was part of the problem with Linux supplied driver.


> I suggest you blacklist r8192s_usb. Reload ndiswrapper and turn off MAC filtering in the router. Do you connect reliably?Yes, but it almost appears that there is a problem in resolving the DNS. I should tell you that I have 3 other things that connect to the wireless side of the router and none of them have any problem.


 > Add MAC filtering for the address reported in *nm-tool*. Do you connect reliably?I am beginning to think that this is not the issue.

> I would love to know the make and model of your device so I can buy one and hammer it into submission.Its called an AirLink 101. The model is AWLL6077. It is self rated as a "Wireless N Adapter."


> *I have three myself and will soon have a great-grandchild. I bet you thought I was a 17-year-old hacker geek!You were betrayed by your kindness and patience. So I had my suspicions.

I have 3 soon to be 4 grandchildren. Two are here in the city, the other 1 + is a five hour plane ride away.

---

### Post by vchapman on 2010-03-16
dmesg | grep -e ndis -e wlan
[   14.646270] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   15.258602] ndiswrapper: driver net8192u (Airlink101,09/11/2008,5.1350.0911.2008) loaded
[   19.589737] wlan0: ethernet device 00:21:2f:2e:00:45 using NDIS driver: net8192u, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192 Wireless LAN USB NIC                                     ', 0BDA:8192.F.conf
[   19.589818] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   19.591588] usbcore: registered new interface driver ndiswrapper
[   19.619219] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   19.619333] udev: renamed network interface wlan0 to wlan1
[   19.635748] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   53.108681] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   53.442006] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   63.912019] wlan1: no IPv6 routers present
[   98.860602] ndiswrapper (iw_set_auth:1602): invalid cmd 12



Three questions / points:

1. Why does the interface get renamed from WLAN0 to WLAN1

2. The ndiswrapper is putting out an errror, invalid cmd 12. Does this need to be addressed?

3. Do I need to do something abut the "no IPv6 routers present statement.

---

### Post by chili555 on 2010-03-16
> Why does the interface get renamed from WLAN0 to WLAN1The process udev looks at, among other things, MAC addresses and if a different device is attached, the next higher wlan number is assigned. You can see more in:```
cat /etc/udev/rules.d/70-persistent-net.rules
```> The ndiswrapper is putting out an errror, invalid cmd 12. Does this need to be addressed?Yes. I am Googling and suggest you do the same. I have not found a solution yet.> Do I need to do something abut the "no IPv6 routers present statement. Nope. That just means, approximately, we were all ready to start speaking IPv6, but nobody at this address speaks it so we'll just continue with IPv4.

I don't think you have a DNS problem. The IP address of the router, in your case 192.168.0.1, is perfectly valid.

Your readings look like you connected perfectly well, except, of course, the cmd 12 error, whatever that signifies.

Was your ping test with or without MAC filtering?

---

### Post by vchapman on 2010-03-16
I have sanitized the DHCP server. There are no reservations. I have sanitized the things that connect to the DHCP server so it assigns the IP address ... no reservations. 

The problem persists. Every once and awhile I do get connected to a web site through firefox. However, it takes several minutes to connect. So nothing appears to have changed.

You have tried your best, and it is greatly appreciated. Now I need to get to the next step.

I think I could purchase another network card or usb adapter. However, what are the guarantees that I won't have this problem again. What network card would you recommend?

My other alternative would be to go and buy a copy of Windows, preferably XP if I can still get one.

The computer has a bit of an interesting history. I bought it 6 or 7 years ago. (My wife wanted her own computer). I went to the local computer store and asked for the cheapest box they had. It was $200 and came with an operating system known as GoS. I think the g stands for google. It turned out that GoS was really a front end for Ubuntu 8.04 (I think). I plugged in a wireless adapter and it worked! Some time in the last year or so I bought a new router and that's when things started going down hill. I wanted Linux to work because I hate making Bill Gates a richer man.

I have played around with open SUSE for about 10 years or so. I like it, but I have had the same problem with wireless adapters. I got really good at compiling ndiswrappers.

I have a notebook that is about 6 months old. When time permits I will load maybe ubuntu and see if can get any joy out of the built in wireless card. Does ubundu provide a good dual boot mechanism?

So do you know of a wireless card that is ***guaranteed*** to work out of the box. Or, should I cave in and buy Windows.

---

### Post by chili555 on 2010-03-16
> I have a notebook that is about 6 months old. When time permits I will load maybe ubuntu and see if can get any joy out of the built in wireless card.Why not try the live CD and see what happens. I have been running the Lucid (version 10.4) live CD for several days and everything works. In fact Network Manager seems smoother and faster!

Run *lspci -nn* and learn what kind of wireless card is built in, then search here.

My suggestion is to check here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Some of the cards listed are older and may not be sold at new retail today, but the document must also serve those who have older hardware and are trying to find out if and how their equipment is supported. When you find a candidate, you can also search this forum for others experiences. Take careful note if a user refers to model XYZ, version 2. Manufacturers change versions generally because they change chipsets. Version 2 may be a Broadcom and version 3 may be a Ralink.

I looked up your card on Amazon for users reviews and was disappointed; one out of one reviews was negative.

Sometimes a $50 card is better than an $18 card.

---

### Post by vchapman on 2010-03-17
> **chili555 said:**
> Why not try the live CD and see what happens. I have been running the Lucid (version 10.4) live CD for several days and everything works. In fact Network Manager seems smoother and faster!


Wow, that was painless. This from my notebook with the Ubuntu 9.10 live CD. After the OS loaded, it detected my wireless card and offered to install the drivers.

I haven't solved the other problem yet. However, I am encouraged by the result here.

---

### Post by vchapman on 2010-03-17
Well I went out this afternoon and purchased a new network card. a D-Link DWA-552. When I returned, I took the skin off the computer and installed it. Put everything back together and turned on the computer. Without any intervention by me, it immediately connedted to the network. And so all is now working. You were right, of course, I spent $63 not $18. 

Once again I would like to thank you for all of your prodding and assistance.

---

### Post by chili555 on 2010-03-17
Vic-

I am very happy that you are working properly now. I hope you will enjoy your Ubuntu experience. 

Great news!

---

### Post by luisfm on 2010-03-17
Hello Chili555: I've been following your threads for a while. You seem quite the expert on Wireless troubleshooting. I had Ubuntu 8.10 running fine (my wireless card is Linksys WPC54GS) and as a matter of fact I downloaded all the upgrades using it. However when I rebooted, I lost the wireless connection. When I click on Wireless network Drivers it shows the lsbcmnds and says: Hardware Present: Yes but when I click on the Configure Network button, I get "Could Not Find Network Configuration Tool". What I am missing here?. THe network Icon shows my home wireless network, but it won't connect to it. My wireless network uses WPA-PSK Security. Thanks in advance for the input

---

### Post by chili555 on 2010-03-17
> **luisfm said:**
> Hello Chili555: I've been following your threads for a while. You seem quite the expert on Wireless troubleshooting. I had Ubuntu 8.10 running fine (my wireless card is Linksys WPC54GS) and as a matter of fact I downloaded all the upgrades using it. However when I rebooted, I lost the wireless connection. When I click on Wireless network Drivers it shows the lsbcmnds and says: Hardware Present: Yes but when I click on the Configure Network button, I get "Could Not Find Network Configuration Tool". What I am missing here?. THe network Icon shows my home wireless network, but it won't connect to it. My wireless network uses WPA-PSK Security. Thanks in advance for the inputPlease start a new thread and I will be glad to help.

---

### Post by luisfm on 2010-03-17
I did under "WIreless Network gone after upgrade to ver 9.10"

Thanks

---

