---
title: "Wireless Problem"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by l3ecl on 2010-04-23
I've never used this OS before but it has become a requirement for my computer science class. Now I have a freshly installed ubuntu 9.10 but I can't connect wirelessly.

When I click on the network icon, there are no wireless networks available. (Disabled?)

And I've tried maybe activating it, but my Hardware Drivers come up empty. 

When i type lpsci in the terminal it returns:
D-Link System Inc RTL8139

what do?

---

### Post by chili555 on 2010-04-23
> RTL8139That is a wired ethernet device, not wireless. Do you have any other candidates in lspci? Is it a USB device? Check:```
lsusb
```

---

### Post by rosanbio on 2010-04-23
Ubuntu didn't recognized your wireless device, what is the wireless adapter you use?

---

### Post by The Thunder Chimp on 2010-04-23
Two thing for you to try out:

First, try going to System>Administration>Hardware Drivers, and see if there's any uninstalled material for you to install. That might as well work, as it's how I solved the same problem. My wireless driver was B43 by the way.

If the preceding tip failed, copy paste what the "lspci" prints in the terminal. We'll see what we can do from there.

Welcome to the Community by the way! ):P

---

### Post by l3ecl on 2010-04-24
My System>Administration>Hardware Drivers comes up empty.

owel@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

owel@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:03.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:0a.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:0c.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)

---

### Post by l3ecl on 2010-04-24
My wireless adapter looks something like this [IMG]http://www.pcarenahungary.com/pricelist/oriaskep/pci-wireless-adapter-380.jpg[/IMG]

but it's made by D-Link

---

### Post by chili555 on 2010-04-24
> 02:0a.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)I believe this is your wireless card and I doubt it is made by D-Link. This device is often claimed by two drivers which conflict and fight. Let's check; please post:```
lsmod | grep -e orinoco -e host
```Thanks.

---

### Post by l3ecl on 2010-04-24
oh man glad to see you respond

```
lsmod | grep -e orinoco -e host
```
hostap_pci             48652  0 
hostap                103360  1 hostap_pci
lib80211                6432  2 hostap_pci,hostap
orinoco_pci             4700  0 
orinoco                63600  1 orinoco_pci

---

### Post by chili555 on 2010-04-24
As I suspected, two drivers are fighting. Let's kick one out of school for not playing well with others. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```A file will open and we will add a few lines at the bottom:```
blacklist hostap
blacklist hostap_pci
```Proofread carefully; spelling and spacing and everything your teachers drilled into you are very important. Save and close gedit. Reboot and tell us how your wireless is working.

---

### Post by l3ecl on 2010-04-24
done and done. still not working. 

it just says "Wired Netowrk disconnected" and there are no available networks to choose from.

---

### Post by mark bower on 2010-04-24
@l3ecl - the good news is that if Chili555 does not get you up and running, you can get a D-link WPN311 which will work "out of the box".  this is because its driver is included in the linux kernel.  from E-Bay you can get the WPN311 for $12 (refurbished) including shipping!  i bot 3 of them and retired my hawking pci wireless cards which required additional software set-up (ndiswrapper).

@chili555 or anyone else who can - the "Supported wireless cards list . . ." page has been corrupted for D-Link, PCI cards.  there were at least two posts there for the WPN311, now they are gone with possibly some others.  if you know who to contact re this situation, please contact them or let me know here and i will attempt to do so.  the following is the link to the page.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

mark

---

### Post by l3ecl on 2010-04-25
does any1 have anymore ideas? and i looked through the wiki.ubuntu list for tried NIC. mine wasn't listed.

---

### Post by chili555 on 2010-04-25
Please let us see:```
dmesg | grep orinoco
iwconfig
```Thanks.

---

### Post by l3ecl on 2010-04-25
> **chili555 said:**
> Please let us see:```
dmesg | grep orinoco
iwconfig
```Thanks.

```
dmesg | grep orinoco
```
[   24.609862] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   24.639413] orinoco_pci 0.15 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[   24.639490] orinoco_pci 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   25.998824] orinoco_pci: Cannot register network device
[   25.998868] orinoco_pci 0000:02:0a.0: PCI INT A disabled
[   26.003951] orinoco_pci: probe of 0000:02:0a.0 failed with error -110
```
iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11-DS  Mode:Managed  
          
wlan0     IEEE 802.11-DS  Mode:Managed  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2010-04-25
Please run:```
lspci -nn | grep Network
```I'd like to find out more about your device. Is this a laptop? May I see:```
rfkill list
```Thanks.

---

### Post by l3ecl on 2010-04-25
> **chili555 said:**
> Please run:```
lspci -nn | grep Network
```I'd like to find out more about your device. Is this a laptop? May I see:```
rfkill list
```Thanks.

im running a custom built desktop from  5-10 yrs ago. 
rfkill list didn't do anything but lspci did. 

```
lspci -nn | grep Network
```
02:0a.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)

```
lsmod | grep -i hostap
```
hostap_pci             48652  0 
hostap                103360  1 hostap_pci
lib80211                6432  2 hostap_pci,hostap

---

### Post by l3ecl on 2010-04-26
chili, i found a relevant thread: [http://ubuntuforums.org/showthread.php?t=968797](http://ubuntuforums.org/showthread.php?t=968797)

i tried what they mentioned but i might be doing it wrong since it still doesn't work

---

### Post by chili555 on 2010-04-26
Evidently, you did not blacklist hostap and hostap_pci correctly if they are still loading. Please retrace your steps from my post above. If you think it is correct, please post:```
cat /etc/modprobe.d/blacklist.conf
```After you tweak the blacklist file, please reboot and do:```
iwconfig
```Thanks.

---

### Post by l3ecl on 2010-04-26
```
cat /etc/modprobe.d/blacklist.conf
```
.......

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
blacklist hostap
blacklist hostap_pci

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

when i click on the 'internet icon' before the blacklist command, there's a section for 'wireless network' AND 'wired network'. but after the reboot, the 'wireless network' is missing and only 'wired network' remains.

---

### Post by chili555 on 2010-04-26
> --- snip ---
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist hostap
blacklist hostap_pciLooks perfect. After a reboot, does hostap still load?```
lsmod | grep -e orinoco -e host
```Does the wireless interface appear if you explicitly load orinoco?```
sudo modprobe orinoco_pci
iwconfig
```If hostap is still loading, first make sure it is ***not ***in /etc/modules:```
cat /etc/modules
```If it is, edit the file to remove them. Next do:```
sudo gedit /etc/rc.local
```Add two lines above 'exit 0':```
rmmod -f hostap
rmmod -f hostap_pci
```Proofread carefully, save and close gedit. After a reboot, do things work better?

---

### Post by l3ecl on 2010-04-26
```
lsmod | grep -e orinoco -e host
```
orinoco_pci             4700  0 
orinoco                63600  1 orinoco_pci

it is my understanding hostap did not load?

```
k@ubuntu:~$ sudo modprobe orinoco_pci
[sudo] password for k: 
k@ubuntu:~$ iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```
cat /etc/modules
```
...
#This file contains the names of kernel modules that should be #loaded at boot time, one per line. Lines beginning with "#" are #ignored.

lp

```
rmmod -f hostap
rmmod -f hostap_pci
```
ERROR: Removing 'hostap': Operation not permitted
ERROR: Removing 'hostap_pci': Operation not permitted

---

### Post by l3ecl on 2010-04-26
is linux being congruent with windows? (DUAL BOOT)

```
linux
```
02:0a.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:0c.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)

```
windows
```
[IMG]http://img152.imageshack.us/img152/4750/windows1.png[/IMG]
[IMG]http://img199.imageshack.us/img199/3413/windows2.png[/IMG]

---

### Post by v1ad on 2010-04-26
> **l3ecl said:**
> 
```
rmmod -f hostap
rmmod -f hostap_pci
```
ERROR: Removing 'hostap': Operation not permitted
ERROR: Removing 'hostap_pci': Operation not permitted

If you are going to do rmmod u will need to sudo.
Example : sudo rmmod -f hostap

---

### Post by chili555 on 2010-04-26
> **v1ad said:**
> If you are going to do rmmod u will need to sudo.
Example : sudo rmmod -f hostapNot in /etc/rc.local, which is where the lines were to be added. My post was mis-read.

---

### Post by chili555 on 2010-04-26
> is linux being congruent with windows? (DUAL BOOT)Yes it is. Please check here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI)

You will see that the D-link DWL-520 uses a Prism 2.5 Wavelan chipset.> it is my understanding hostap did not load?Yes, you are correct. Let's see if the kernel has any messages to report:```
dmesg | grep orinoco
```

---

### Post by l3ecl on 2010-04-26
```
dmesg | grep orinoco
```
[    9.469282] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[    9.650686] orinoco_pci 0.15 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[    9.650762] orinoco_pci 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.992260] orinoco_pci: Cannot register network device
[   10.992303] orinoco_pci 0000:02:0a.0: PCI INT A disabled
[   10.993444] orinoco_pci: probe of 0000:02:0a.0 failed with error -110

---

### Post by chili555 on 2010-04-26
> orinoco_pci: Cannot register network device
orinoco_pci 0000:02:0a.0: PCI INT A disabled
orinoco_pci: probe of 0000:02:0a.0 failed with error -110Googling. I will post back tomorrow.

---

### Post by chili555 on 2010-04-27
Let's try to use the hostap drivers instead of the orinoco. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Change these lines:```
blacklist hostap
blacklist hostap_pci 
```To read like this:```
blacklist orinoco
blacklist orinoco_pci 
```Proofread carefully, save and close gedit.

Reboot and let us know.

---

### Post by l3ecl on 2010-04-27
still not working

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11-DS  Mode:Managed  
          
wlan0     IEEE 802.11-DS  Mode:Managed  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2010-04-27
What does this tell us?```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Thanks.

---

### Post by l3ecl on 2010-04-27
```
sudo ifconfig wlan0 up
```
SIOCSIFFLAGS: Cannot assign requested address

```
sudo iwlist wlan0 scan
```
wlan0     Interface doesn't support scanning : Network is down

---

### Post by chili555 on 2010-04-27
That is one stubborn card you have there! How about:```
dmesg | grep -e wlan -e host
```Thanks.

---

### Post by l3ecl on 2010-04-27
i know what you mean! i'd be sweet to break this card in. 
```
dmesg | grep -e wlan -e host
```
[    9.681974] hostap_pci 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.683437] hostap_pci: Registered netdevice wifi0
[   10.184052] hostap_pci: assuming no Primary image in flash - card initialization not completed
[   10.286490] wifi0: registered netdevice wlan0
[   24.953731] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
[   26.155495] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[   26.189859] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[   26.189963] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[   26.193455] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[   27.328886] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[  208.996941] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[  208.996956] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[  208.996972] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[  208.996987] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[  208.996998] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[  208.997007] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[  208.997015] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[  208.997028] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[  208.997039] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[  208.997049] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[  208.997058] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[  208.997066] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[ 7660.263156] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w

---

### Post by chili555 on 2010-04-28
> wlan0: cannot get RID fdc6 (len=12) - no PRI f/wWow!

Please see post #9 here: [http://ubuntuforums.org/showthread.php?t=1463876](http://ubuntuforums.org/showthread.php?t=1463876)

---

### Post by l3ecl on 2010-04-28
i have the original disk that came with the driver. what should i do w/ it?

---

### Post by chili555 on 2010-04-28
I think the needed firmware is going to be a HEX file. Look on the disk and see what is there. If in doubt, list the contents here.

---

### Post by l3ecl on 2010-04-28
i dont see a hex file, only
.inf
.sys
.cat

and .exe's

---

### Post by l3ecl on 2010-04-28
i looked it up on the net and maybe found the .hex file
[https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1](https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1)

should i just follow the steps under "Firmware"?

> Prepare The Firmware
The D-Link DWL-520 E1 requires 2 firmware files to be loaded. Without the firmware the card is not useable.

Download the firmware into a temporary directory
    cd /tmp
    wget [http://www.red-bean.com/~proski/firmware/1.8.4.tar.bz2](http://www.red-bean.com/~proski/firmware/1.8.4.tar.bz2)
    wget [http://www.red-bean.com/~proski/firmware/primary.tar.bz2](http://www.red-bean.com/~proski/firmware/primary.tar.bz2) 
"The above links are dead. I found the firmware here:
[http://www.netgate.com/support/prism_firmware/](http://www.netgate.com/support/prism_firmware/) May 15, 2008 ~Malangaman" Note that these were the latest files at the time this document was written. Later firmware files may be available.
........

---

### Post by chili555 on 2010-04-28
> should i just follow the steps under "Firmware"?Yes! The only place I might diverge is to try to load the firmware with prism2_srec.```
prism2_srec
Firmware image downloader for Host AP driver
  (for Intersil Prism2/2.5/3 cards)
Copyright (c) 2002-2004, Jouni Malinen <jkmaline@cc.hut.fi>

Usage:
  prism2_srec [-vvrgfdpisD] [-P <PDA file>] [-O <PDA binary>] <interface> \
              <srec file name> [srec file name]
```Evidently, prism2_srec will tell you if the file is incorrect.

I might start with:```
sudo rmmod -f hostap hostap_pci
sudo prism2_srec -r <file.hex> wlan0
sudo prism2_srec -r <file2.hex> wlan0
```Substitute the file names as outlined in the document. If both load without complaint, do:```
sudo modprobe hostap_pci
```If it works, we can make the firmware load automatic and permanent.

I have my fingers crossed.

---

### Post by l3ecl on 2010-04-28
by the time i saw your post, i already did the walk through from the website. and....... its still not working. when i click the desktop icon, under Wireless Networks, it says "device not managed"

 ```
gedit /etc/network/interfaces
``` 
> auto lo
iface lo inet loopback

iface wlan0 inet dhcp
	hostname your.hostname.com
	fw_primary /etc/firmware/pm010102.hex
	fw_secondary /etc/firmware/rf010804.hex
	wireless_mode_managed

does this look correct?

in the walk through his looks like

> iface wlan0 inet dhcp
        hostname your.hostname.com
        fw_primary /etc/firmware/pm010102.hex
        fw_secondary /etc/firmware/rf010804.hex
        wireless_mode managed 

---

### Post by l3ecl on 2010-04-28
```
iwconfig
```
> lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11-DS  Mode:Managed  
          
wlan0     IEEE 802.11-DS  Mode:Managed  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
ifconfig
```
> eth0      Link encap:Ethernet  HWaddr 00:50:ba:ad:c9:3c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


---

### Post by chili555 on 2010-04-28
In order to get /etc/network/interfaces to work, you would need to disable or possibly remove Network Manager. In System > Preferences > Startup Applications, you can stop it from loading on boot.

The interference from NM is why I suggested loading the firmware manually.

My suggestion is this:> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
fw_primary /etc/firmware/pm010102.hex
fw_secondary /etc/firmware/rf010804.hex
wireless-essid Your_network
wireless-key 0123456789 Then restart networking:```
sudo /etc/init.d/networking restart
```The wireless-key part is appropriate for WEP, WPA is only a bit more complex.

---

### Post by l3ecl on 2010-04-28
i restarted and theres no more wireless icon tab on my desktop.
but i dont think the results below are good.
```
sudo /etc/init.d/networking restart
```

 > * Reconfiguring network interfaces...                                          Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
wifi0: unknown hardware address type 801
Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
grep: /etc/resolv.conf: No such file or directory
                                                                         [ OK ]

---

### Post by chili555 on 2010-04-28
I think that tells us the firmware didn't load correctly. Did you try loading with prism2_srec to see if the system likes pm010102.hex and rf010804.hex?

---

### Post by l3ecl on 2010-04-28
btw just for clarification 

> wireless-essid Your_network
wireless-key 0123456789

[IMG]http://img144.imageshack.us/img144/6198/13982474.png[/IMG]

> wireless-essid 2WIRE868
wireless-key "mykey"

---

### Post by chili555 on 2010-04-28
Connected??

---

### Post by l3ecl on 2010-04-28
it connects with windows but still not ubuntu

i tried the command ```
sudo prism2_srec /etc/firmware/pm010102.hex wlan0
```

but result was:

```
sudo: prism2_srec: command not found
```

---

### Post by chili555 on 2010-04-28
It's in the package hostap-utils. Can you install it?

I wonder if the proper hex files are in your Windows partition.

---

### Post by l3ecl on 2010-04-28
i have a download link for hostaps
[http://packages.debian.org/lenny/hostap-utils](http://packages.debian.org/lenny/hostap-utils)

but i don't know under which "architecture" to get. 

i did the code:
```
cp 1.8.4/rf010804.hex /etc/firmware
    cp primary/pm010102.hex /etc/firmware
    chown root:root /etc/firmware/*
    chmod 644 /etc/firmware/* 

```

wouldn't that put it in my ubuntu partition?
besides that screenshot was from my laptop. i was just wondering if i put in the right network name. "wireless-essid 2WIRE868"

---

### Post by l3ecl on 2010-04-28
.

---

### Post by l3ecl on 2010-04-28
```
sudo prism2_srec /etc/firmware/pm010102.hex wlan0
```

> 'wlan0 not readable: No such file or directory.
Parsing 'wlan0' failed.

---

### Post by chili555 on 2010-04-29
> i was just wondering if i put in the right network name. "wireless-essid 2WIRE868"It looks correct.

You are better off to get the Ubuntu package: [http://packages.ubuntu.com/karmic/hostap-utils](http://packages.ubuntu.com/karmic/hostap-utils)

This assumes you are using Karmic (9.10). Select i386 at the lower left unless you know you are using 64-bit. Learn with:```
lsb_release -r
uname -r
```You need i386 unless you see *x86_64*.

Download the .deb and install with:```
sudo dpkg -i hostap-utils*.deb
```

---

### Post by chili555 on 2010-04-29
I might have reversed it. Please try:```
sudo prism2_srec -r wlan0 /etc/firmware/pm010102.hex
```

---

### Post by l3ecl on 2010-04-29
```
sudo prism2_srec -r wlan0 /etc/firmware/pm010102.hex
```

> srec summary for pm010102.hex
Included file name: PM010102.HEX
Component: 0x0015 1.1.2 (primary firmware)

ioctl[PRISM2_IOCTL_HOSTAPD]: Inappropriate ioctl for device
Missing wlan component info
Could not read wlan RIDs

should i still reinstall hostaps from the ubuntu package? the command seems to be working fine now.

---

### Post by chili555 on 2010-04-29
I think hostap_utils is working fine. I think the message tells us that pm010102.hex is not correct for your device. Are there other primary hex files here? [https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1](https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1)

We could also try ndiswrapper; I think the .inf and .sys files include the needed firmware.

---

### Post by l3ecl on 2010-04-29
i think he only mentioned 2:
  > cp 1.8.4/rf010804.hex /etc/firmware
   cp primary/pm010102.hex /etc/firmware

ugh i can't believe its not right for my hardware. they have the same name dwl-520. edit: i just checked the versions, his is E1 mine is just E. 

we can try ndiswrapper.

---

### Post by chili555 on 2010-04-29
I am confused. The 1.8.4.tar.gz I just downloaded contains:```
rf010804.hex  sf010804.hex  su010804.hex
```

---

### Post by l3ecl on 2010-04-29
i didin't notice that! should i try the other .hex?

---

### Post by chili555 on 2010-04-29
> **l3ecl said:**
> i didin't notice that! should i try the other .hex?Sure, until prism2_srec seems to be happy.

---

### Post by l3ecl on 2010-04-30
i did the code:

```
cp 1.8.4/sf010804.hex /etc/firmware
cp 1.8.4/su010804.hex /etc/firmware	
```

but its still the same result

```
sudo prism2_srec -r wlan0 /etc/firmware/pm010102.hex
```

> srec summary for pm010102.hex
Included file name: PM010102.HEX
Component: 0x0015 1.1.2 (primary firmware)

ioctl[PRISM2_IOCTL_HOSTAPD]: Inappropriate ioctl for device
Missing wlan component info
Could not read wlan RIDs

---

### Post by chili555 on 2010-04-30
> but its still the same result

Code:

sudo prism2_srec -r wlan0 /etc/firmware/pm010102.hex

What is the result with:```
sudo prism2_srec -r wlan0 /etc/firmware/[COLOR="Red"]sf[/COLOR]010804.hex
sudo prism2_srec -r wlan0 /etc/firmware/[COLOR="Red"]su[/COLOR]010804.hex
```

---

### Post by l3ecl on 2010-04-30
```
sudo prism2_srec -r wlan0 /etc/firmware/sf010804.hex
```

> srec summary for sf010804.hex
Component: 0x001f 1.8.4 (station firmware)

ioctl[PRISM2_IOCTL_HOSTAPD]: Inappropriate ioctl for device
Missing wlan component info
Could not read wlan RIDs


```
sudo prism2_srec -r wlan0 /etc/firmware/su010804.hex
```

> srec summary for su010804.hex
Component: 0x001f 1.8.4 (station firmware)

ioctl[PRISM2_IOCTL_HOSTAPD]: Inappropriate ioctl for device
Missing wlan component info
Could not read wlan RIDs

---

### Post by chili555 on 2010-04-30
Are you ready to try ndiswrapper?

---

### Post by l3ecl on 2010-04-30
haha sure! life's all about plan B. and i appreciate your help btw

---

### Post by chili555 on 2010-04-30
Do you have an ethernet connection on the machine? If so, please do:```
sudo apt-get install ndisgtk
```Next, drag and drop the files from the CD to your desktop:> i dont see a hex file, only
.inf
.sys
.cat

and .exe'sYou will just need the .inf and .sys files for Win XP. There may be two .sys files; grab them both. Then open System > Administration > Windows Wireless Drivers and install the .inf driver; the location will be Desktop. If needed, ndiswrapper will grab the .sys file(s).

You may have to blacklist the native driver, hostap and hostap_pci.

Post back if you get stuck.

---

### Post by l3ecl on 2010-05-01
im having problems installing.

i downloaded the packpage from here:
[http://packages.ubuntu.com/karmic/i386/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/karmic/i386/ndiswrapper-utils-1.9/download)

here are installation error screenshots: 

"dependency is not satisfiable:"
[IMG]http://img704.imageshack.us/i/screenshotpackageinstal.png/[/IMG]

Synaptic Package Manager can't find the downloaded file:
[IMG]http://img52.imageshack.us/i/screenshotsynapticpacka.png/[/IMG]


am i doing something wrong?

---

### Post by chili555 on 2010-05-01
If you have your install CD you can activate the CD under System > Administration > Software Sources and then do:```
sudo apt-get update
sudo apt-get install ndiswrapper*
```

---

### Post by l3ecl on 2010-05-01
i used an installation without the cd. downloaded it in windows and installed from there.

---

### Post by chili555 on 2010-05-01
> **l3ecl said:**
> i used an installation without the cd. downloaded it in windows and installed from there.I'm not sure I understand; did you get it installed successfully or are you stuck on unsatisfied dependencies?

When you got here: [http://packages.ubuntu.com/karmic/ndiswrapper-utils-1.9](http://packages.ubuntu.com/karmic/ndiswrapper-utils-1.9) did you notice that it depends on ndiswrapper-common? Did you download it and install it, too?

---

### Post by l3ecl on 2010-05-01
> **chili555 said:**
> I'm not sure I understand; did you get it installed successfully or are you stuck on unsatisfied dependencies?

When you got here: [http://packages.ubuntu.com/karmic/ndiswrapper-utils-1.9](http://packages.ubuntu.com/karmic/ndiswrapper-utils-1.9) did you notice that it depends on ndiswrapper-common? Did you download it and install it, too?

that was very clever debugging. 

i finished installing the driver and rebooted. what should i do next?

---

### Post by chili555 on 2010-05-01
Did you install the Windows .inf? What does this tell us?```
ndiswrapper -l
iwconfig
```Thanks.

---

### Post by l3ecl on 2010-05-01
```
 ndiswrapper -l
```
> WARNING: All config files need .conf: /etc/modprobe.d/hostap-utils, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netprism : driver installed
	device (1260:3873) present (alternate driver: orinoco_pci)

 ```
iwconfig
```
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  Mode:Managed  Frequency:2.457 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by chili555 on 2010-05-01
You need to blacklist orinoco and orinoco_pci. Then do:```
sudo rmmod -f orinoco orinoco_pci
```You have a wireless interface; can you connect? If not, let's have a look at:```
dmesg | grep -e ndis -e wlan
```Thanks, you are close!

---

### Post by l3ecl on 2010-05-01
i don't know how to connect perse b/c the connection tab during start up does not pop up anymore.
when i openfirefox, i still can't connect to the web

btw orinoco and orinico_pci were already blacklisted before. 
```
sudo rmmod -f orinoco orinoco_pci
```

> ERROR: Removing 'orinoco': No such file or directory
ERROR: Removing 'orinoco_pci': No such file or directory


```
dmesg | grep -e ndis -e wlan
```
> 
[    9.944551] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   11.651062] ndiswrapper: driver netprism (D-Link,07/17/2003, 3.0.8) loaded
[   11.651623] ndiswrapper 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.651891] ndiswrapper: using IRQ 22
[   12.667864] wlan0: ethernet device 00:0d:88:51:14:f8 using serialized NDIS driver: netprism, version: 0x30008, NDIS version: 0x501, vendor: 'D-Link Air DWL-520 Wireless PCI Adapter(rev.E)', 1260:3873.5.conf
[   12.793061] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C00000BB)
[   12.844207] wlan0: encryption modes supported: WEP; TKIP with WPA
[   12.899787] usbcore: registered new interface driver ndiswrapper
[   15.474127] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by chili555 on 2010-05-01
Looks solid! Any activity under Network Manager? What does this say?```
sudo iwlist wlan0 scan
```

---

### Post by l3ecl on 2010-05-01
> **chili555 said:**
> Looks solid! Any activity under Network Manager? What does this say?```
sudo iwlist wlan0 scan
```

i still dont have internet tho! haha

```
sudo iwlist wlan0 scan
```
wlan0      No Scan results

---

### Post by chili555 on 2010-05-01
I'll have to check back tomorrow.

---

### Post by l3ecl on 2010-05-01
ok sounds good

---

### Post by mark bower on 2010-05-03
@l3ecl

may i remind you of my post #11 on this thread.  also, please see success link below.  you could be a shinning star in your computer class if you purchased a WPN311 and showed other class members the ease of using a PCI card which is supported with native drivers.  of course this emulates windows like behavior "plug and play", but sometimes setting up configurations is not a practical solution timewise, when $13 and 5 days for delivery solves the problem.  

and althoh i have not seen it posted as such, maybe your insrtuctor has, IHO the more that natively supported hardware is utilized, the more the hardware maunufacturers will be inclined to continue to support linux with their hardware.  


[http://ubuntuforums.org/showthread.php?t=1464117](http://ubuntuforums.org/showthread.php?t=1464117)

---

### Post by l3ecl on 2010-05-03
> **mark bower said:**
> @l3ecl

may i remind you of my post #11 on this thread.  also, please see success link below.  you could be a shinning star in your computer class if you purchased a WPN311 and showed other class members the ease of using a PCI card which is supported with native drivers.  of course this emulates windows like behavior "plug and play", but sometimes setting up configurations is not a practical solution timewise, when $13 and 5 days for delivery solves the problem.  

and althoh i have not seen it posted as such, maybe your insrtuctor has, IHO the more that natively supported hardware is utilized, the more the hardware maunufacturers will be inclined to continue to support linux with their hardware.  


[http://ubuntuforums.org/showthread.php?t=1464117](http://ubuntuforums.org/showthread.php?t=1464117)

ill keep that in mind. fixing this is actually a good tutorial/intro for me. learn nifty stuff like sudo, blacklist.conf, downloading .tar's, intro to synaptic manager, start up applications ect ect, so i don't mind, its all good experience especially this being my first week in unix, and chili giving a damn good introductory class. if chili gives up on me, ill just buy the 13$ card haha.

---

### Post by mark bower on 2010-05-03
good for you.  i was rather satisfied when i got ndiswrapper to work for my Hawking PCI cards, but then just decided i wanted to dispense with any special setups if i could, and in particular since i have 3 Ubu boxes.  good luck - chili555 is the man.

mark

---

### Post by isaacjun16 on 2011-01-12
> **chili555 said:**
> As I suspected, two drivers are fighting. Let's kick one out of school for not playing well with others. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```A file will open and we will add a few lines at the bottom:```
blacklist hostap
blacklist hostap_pci
```Proofread carefully; spelling and spacing and everything your teachers drilled into you are very important. Save and close gedit. Reboot and tell us how your wireless is working.

I just installed Ubuntu 10.04.1 and did what you said in this post and worked like a charm. 

FYI: My network card is:

> Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)

---

