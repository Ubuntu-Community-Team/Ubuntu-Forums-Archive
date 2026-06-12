---
title: "Broadcom wireless woes...."
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by The Toxic Mite on 2009-07-23
Hey guys.
 
My desktop has a Broadcom wireless card, and I am struggling to get it to work. "lshw -c network" returns the following info about my wireless card:
 
```

description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb

```
 
I have the B43 drivers installed, but for some reason, it won't connect to my Home Hub. My mother's convinced it's a software issue rather than a hardware issue
 
Any answers would be appreciated
 
P.S. I am writing this from a windows computer by the way :p
 
P.P.S. I once managed to get it connected, but now it's refusing to connect

---

### Post by The Toxic Mite on 2009-07-23
Anyone?
 
-.-

---

### Post by Bucky Ball on 2009-07-23
Plug in an ethernet cable, get your updates. You will probably be offered restricted drivers for your card and vid card possibly too.

If not, check 'System->Admin->Hardware Drivers'

Now, go into 'System->Administration->Network and unlock

Click your wireless device and then 'Properties'.

Switch off 'Enable Roaming' in the top left and make sure the ESSID and security details match what is in your router. If not, change them.

In 'Configuration' make it 'Automatic Configuration (DHCP)' if your router is serving your IP address.

---

### Post by Ayuthia on 2009-07-23
Can you check and see if there are any error messages:
```
dmesg|grep b43
```

---

### Post by RedSingularity on 2009-07-23
Is there a revision number to your chipset?  If you dont know post the output of lspci.

---

### Post by The Toxic Mite on 2009-07-23
> **Bucky Ball said:**
> Plug in an ethernet cable, get your updates. You will probably be offered restricted drivers for your card and vid card possibly too.
 
If not, check 'System->Admin->Hardware Drivers'
 
Now, go into 'System->Administration->Network and unlock
 
Click your wireless device and then 'Properties'.
 
Switch off 'Enable Roaming' in the top left and make sure the ESSID and security details match what is in your router. If not, change them.
 
In 'Configuration' make it 'Automatic Configuration (DHCP)' if your router is serving your IP address.
 
My computer has no ethernet, and I installed the drivers using my phone as a modem.
 
I can't find "Network" in System > Administration, but I do see "Network Tools" :confused:

---

### Post by The Toxic Mite on 2009-07-23
> **Shadow121 said:**
> Is there a revision number to your chipset? If you dont know post the output of lspci.
 
```

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

---

### Post by Bucky Ball on 2009-07-23
Try 'System->Admin->Main Menu'

and see if 'Network' is unticked and therefore not appearing in your drop-down menu. It should be there.

I'm a bit confused and curious. Is there only wireless available, no router with ethernet ports?

---

### Post by The Toxic Mite on 2009-07-23
> **Ayuthia said:**
> Can you check and see if there are any error messages:
```
dmesg|grep b43
```
 
```

[    3.919320] b43-pci-bridge 0000:02:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.960255] b43-phy0: Broadcom 4306 WLAN found
[   25.689060] input: b43-phy0 as /devices/virtual/input/input7
[   25.732060] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   25.987054] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   26.075456] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   26.131505] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   26.356041] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   26.425176] Registered led device: b43-phy0::tx
[   26.425218] Registered led device: b43-phy0::rx
[   26.425260] Registered led device: b43-phy0::radio
[   26.448054] b43-phy0: Radio turned on by software

```

---

### Post by The Toxic Mite on 2009-07-23
> **Bucky Ball said:**
> Try 'System->Admin->Main Menu'
 
and see if it is unticked and therefore not appearing in your drop-down menu. It should be there.
 
I'm a bit confused and curious. If there is no internet, why do you need a wireless card? Or is there wireless available, you just can't get to it?
 
The Home Hub is showing up but it's not connecting.
 
I also notice that it changes the key when the prompt comes up.

---

### Post by The Toxic Mite on 2009-07-23
> **Bucky Ball said:**
> Try 'System->Admin->Main Menu'
 
and see if 'Network' is unticked and therefore not appearing in your drop-down menu. It should be there.
 
I'm a bit confused and curious. If there is no internet, why do you need a wireless card? Or is there wireless available, you just can't get to it?
 
No "Main Menu" either. :confused:

---

### Post by Bucky Ball on 2009-07-23
Well, the details on the router, (Home Hub, I presume, is a router) and the details on your machine need to match, especially the key. You won't get far without that if it is a secure network. Get into the router configuration and get the details and make sure it is acting as a DHCP server if it can (and most do).

---

### Post by The Toxic Mite on 2009-07-23
> **Bucky Ball said:**
> Well, the details on the router, (Home Hub, I presume, is a router) and the details on your machine need to match, especially the key. You won't get far without that if it is a secure network. Get into the router configuration and get the details and make sure it is acting as a DHCP server if it can (and most do).
 
The SSID and it's key are printed on a label stuck to the back of the router, and I type in the key that's there, but when the prompt comes up, the key is different to the one I put in.
 
EDIT: I have a couple of screenshots here; the first one shows the key I entered, and the second one shows the difference between the fist one

---

### Post by Bucky Ball on 2009-07-23
Don't quite follow. What is in there when the screen comes up?

WPA uses 16 digits I think. Change it to WEP and enter the 8 digit key you have on the back of your router.

---

### Post by The Toxic Mite on 2009-07-23
> **Bucky Ball said:**
> Don't quite follow. What is in there when the screen comes up?
 
WPA uses 16 digits I think. Change it to WEP and enter the 8 digit key you have on the back of your router.
 
The key is 10 digits long, and it's definitely WPA.

---

### Post by RedSingularity on 2009-07-23
10 digits long is WEP.  Probably hexadecimal.

---

### Post by Bucky Ball on 2009-07-23
Yep, try WEP.

---

### Post by The Toxic Mite on 2009-07-23
> **Bucky Ball said:**
> Yep, try WEP.
 
Not working on WEP. In the messagebox in the screenies above, when you click on the menu box, only WPA shows there and nothing else.

---

### Post by RedSingularity on 2009-07-23
Sounds like the manager is broken.  Even if you are not using a WEP connection it will still show in there.  Have you tried a reinstall of gnome-network-manager?

---

### Post by Ayuthia on 2009-07-23
Can you try the following from the Terminal:
```
sudo /etc/init.d/NetworkManager stop
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo iwconfig wlan0 essid BTHomeHub2-9JF3 key wep-key
sudo dhclient wlan0
```
Replace wep-key with the actual key on the back of the router.  I am pretty sure that the BT routers are still WEP unless they changed things during the past couple of years.

These commands will stop NetworkManager from running.  Then it will reload your wireless drivers and then try to connect manually.

---

### Post by The Toxic Mite on 2009-07-24
> **Ayuthia said:**
> Can you try the following from the Terminal:
```
sudo /etc/init.d/NetworkManager stop
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo iwconfig wlan0 essid BTHomeHub2-9JF3 key wep-key
sudo dhclient wlan0
```
Replace wep-key with the actual key on the back of the router. I am pretty sure that the BT routers are still WEP unless they changed things during the past couple of years.
 
These commands will stop NetworkManager from running. Then it will reload your wireless drivers and then try to connect manually.
 
Hmm, I will try that :)
 
EDIT: It hasn't worked. Here's the output from "sudo dhclient wlan0":
 
```

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:3b:13:af
Sending on   LPF/wlan0/00:11:50:3b:13:af
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by The Toxic Mite on 2009-07-24
Bump for today :P

---

### Post by Mechwizard on 2009-07-24
No need to <BUMP> for this seems to be a hot topic right now.
I will be watching this thread (as with a few others) trying to find a way to connect with WPA-PSK encryption.(I don't have a choice).
I have tried both the installed STA dvr and Ndiswrapper with the same result, no secure connect. Wired has worked from the git-go.
dell studio 1735
broadcom 4322 wl

---

### Post by Cyclingrelf on 2010-03-22
Has anyone come up with a solution to this yet? I'm an ubuntu noob, and struggling to connect to a BTHomehub2 with an Asus 802.11g wireless USB stick. I can see the connection, but when I try to connect it thinks about it for a while then acts as if it has disconnected.

---

