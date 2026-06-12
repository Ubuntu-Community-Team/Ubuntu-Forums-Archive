---
title: "Netgear 311"
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by GQed76 on 2005-12-14
On Ubuntu install it detected my wireless card as an ATT czard, not a Netgear card.  It errored out in Red when I tried to install it so I skipped that step.

Is this a typical isssue?  it still thinks its an ATT card.  I havent done ANYthing to it yet. (im at work).

I just thought Netgear was supported out of box.  What should I do when I get home?

---

### Post by GQed76 on 2005-12-14
Well I enabled it, and it enabled.  I got the SSID in there, no WEP...the green light is on in the back, but i cant hit the internet..am I missing a step or 12?

---

### Post by Lambert on 2005-12-14
1. Check to make sure you're associated with the router

```
iwconfig
``` 
should see access point xx:xx:xx:xx:xx under the wireless device and they should not be all zeros

2. Check to see if you have an ip address assigned to the device

```
ifconfig
``` 
second line should say inet address xxx.xxx.x.x but with numbers in place of the x

3. Check to make sure you have a route to the router in your routing table

```
route
``` 
should see something like this

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.0.0     U     0      0        0 ath0
default         192.168.0.1     0.0.0.0         UG    0      0        0 ath0

If you don't have this look in the man page for route

4. If all this checks out try to ping your router, then try to ping google via ip address (ping 63.233.167.147) then try to ping using common name (ping [www.google.com]("http://www.google.com"))

If you can ping with ip address but not common name then you don't have a nameserver set up in /etc/resolv.conf

If you have problems post back with what looks bad from this list.

---

### Post by GQed76 on 2005-12-14
as i suspected its all 0s and route was empty.

All i did was cliock enable on the card.  never got any errors but Im wondering if i need to install a different driver?

---

### Post by Lambert on 2005-12-14
possible.

try this command from the command line.

sudo iwconfig wlan0 essid ____ channel _ ap __:__:__:__:__ commit

this is for no wep setting (I believe you said you're not using wep)

replace wlan0 with your interfaces logical name if it's not wlan0
channel = the channel of your router
ap = the mac address of your router. sudo iwlist wlan0 scan should be able to see your router and give you that if you don't know it. (of course change wlan0 if needed to whatever the interface name is)

After this run iwconfig again to see if you are associated with the router.

---

### Post by drummer on 2005-12-14
I have the Netgear WG311v2 and use ndiswrapper with the XP drivers so that I can use WEP. Also, in Device Manager, the card comes up as Texas Instruments which is the chipset, Netgear is mentioned elsewhere as the 'OEM Vendor' (see screenshots below)

Check here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) for a list of cards and configs tested with ndiswrapper. Make sure you know which version of the card you have, there are 3 versions i think with varying chipsets. The version should be printed somewhere small on the box or on the card.

---

### Post by GQed76 on 2005-12-15
hrrm im using the 64 bit OS...netgear has no 64 bit drivers...
grrr

---

### Post by GQed76 on 2005-12-15
when i do this udo iwconfig wlan0 essid ____ channel _ ap __:__:__:__:__ commit
none of the changes are showing when i redo iwconfig

---

### Post by Lambert on 2005-12-15
First, to make sure, you did fill in the ___ with actual data? Sometimes what I write isn't clearly understood. So the command should have looked more like this.

sudo iwconfig wlan0 essid !@#$%^ channel 6 ap 02:08:al:3d:6t commit

when you run sudo iwlist wlan0 scan does your card see your ap?

Do you have any settings on your router such as mac filtering that would prevent you from associating with the ap?

And last, post the output of these commands here.

sudo lshw -C network
lspci -v

---

### Post by GQed76 on 2005-12-15
does it matter if the card is enabled or not when i do this
?

---

### Post by Lambert on 2005-12-15
It has to be enabled only for the iwlist command. All other commands I gave it doesn't matter if interface is enabled or not.

---

### Post by GQed76 on 2005-12-15
Lambert thanks for your help.

I went ahead and got the 32 bit version of Ubuntu.  The set up didnt error out on the card, but the rest is the same.

I am typing just like you said, but the mac address of the AP never changes.

I was going to use ndiswrapper but it isnt included in the 32 bit editon

I have to reboot and go into Ubuntu every time i try something so i cant really cut and paste information with ease

---

### Post by GQed76 on 2005-12-15
haha! stole my roomies laptop

OK when i type sudo iwcofig + all that information, it sets the ssid, but for some reason its refusing to set the access point.

i tried ndiswrapper (i got it installed all by myself hehe)
not sure if im doing THAT right, but no change.

side bar...on boot what is ALSA card?
sidebar 2 is it bad when it says BIOS handoff failed 104,101001

---

### Post by GQed76 on 2005-12-15
getting annoyed here.  I cant tell you how tired i am of rebooting into windows to post here....lol

basically i cant set the access point..not sure why..its the only think i cant set.

I used the winxpdrivers with ndwiswrapper, but noticed no change whatsoever

---

### Post by GQed76 on 2005-12-15
[HTML]gqed76@gqubuntu:~$ sudo iwconfig wlan0 mode managed essid linksys channel 9 ap 00:13:10:44:A0:C5 commit
gqed76@gqubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"linksys"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.452 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:47:E4:84
          inet6 addr: fe80::20f:b5ff:fe47:e484/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18
[/HTML]


[HTML]gqed76@gqubuntu:~$ lspci -v
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0282
        Subsystem: Asustek Computer, Inc.: Unknown device 80a3
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <available only to root>

0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1282
        Flags: bus master, medium devsel, latency 0

0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2282
        Flags: bus master, medium devsel, latency 0

0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3282
        Flags: bus master, medium devsel, latency 0

0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4282
        Flags: bus master, medium devsel, latency 0

0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7282
        Flags: bus master, medium devsel, latency 0

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]  (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: f9f00000-fbffffff
        Prefetchable memory behind bridge: e0000000-f8ffffff
        Capabilities: <available only to root>

0000:00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev 80) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 808a
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at f9800000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at a800 [size=128]
        Capabilities: <available only to root>

0000:00:0a.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Et hernet 10/100/1000Base-T Adapter (rev 13)
        Subsystem: Asustek Computer, Inc.: Unknown device 811a
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at f9a00000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at b000 [size=256]
        Expansion ROM at f9900000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:00:0d.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Inter face
        Subsystem: Netgear: Unknown device 4c00
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at f9c00000 (32-bit, non-prefetchable) [size=8K]
        Memory at f9b00000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <available only to root>

0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Co ntroller (rev 80)
        Subsystem: Asustek Computer, Inc. A7V600 motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at d000 [size=8]
        I/O ports at c800 [size=4]
        I/O ports at c400 [size=8]
        I/O ports at c000 [size=4]
        I/O ports at b800 [size=16]
        I/O ports at b400 [size=256]
        Capabilities: <available only to root>

0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Asustek Computer, Inc. A7V600 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at fc00 [size=16]
        Capabilities: <available only to root>

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Asustek Computer, Inc. A7V600 motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at d400 [size=32]
        Capabilities: <available only to root>

0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Asustek Computer, Inc. A7V600 motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at d800 [size=32]
        Capabilities: <available only to root>

0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Asustek Computer, Inc. A7V600 motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at e000 [size=32]
        Capabilities: <available only to root>

0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Asustek Computer, Inc. A7V600 motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at e400 [size=32]
        Capabilities: <available only to root>

0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20  [EHCI])
        Subsystem: Asustek Computer, Inc. A7V600 motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at f9e00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]
        Subsystem: Asustek Computer, Inc. A7V600 motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 60)
        Subsystem: Asustek Computer, Inc.: Unknown device 812a
        Flags: medium devsel, IRQ 22
        I/O ports at e800 [size=256]
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0045 (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at f9f00000 [disabled] [size=128K]
        Capabilities: <available only to root>

gqed76@gqubuntu:~$[/HTML]

---

### Post by GQed76 on 2005-12-15
when i do ndiswrapper -l  it lists the correct driver and hardware detected

---

### Post by Lambert on 2005-12-15
I know how you feel. installed probably 20 different distros when I first came to linux and settled with ubuntu simply because my card worked out of the box.

With your situation I'm stumped. You're using an open signal and you can't associate with the ap.

The last thought on my mind is in the folder where you put the .inf file. Did you also copy any other files from the xp driver file to the folder on your drive? .sys or .bin files? Some drivers are written where they rely on each file to function properly. 

Currently it looks like you have a semi-functional driver where it's communicating with the os but it's not fully functional.

---

### Post by GQed76 on 2005-12-15
i have the sys file but not the bin files...ill move all of them.  I also found im not using the latest nwisdwrapper..ill let ya know

---

### Post by GQed76 on 2005-12-16
well that didnt work.

lol...so frustrated because i know i wont give up, loose sleep,ect maybe ill try a few different drivers

---

### Post by GQed76 on 2005-12-16
well im about to give up

People report it works, but I can;'t get mine to work

After a Ubuntu install is there ANYTHING i need to enable and or install before I get the network card running

Am i missing a protocol or something?

---

### Post by greenwom on 2005-12-16
Check the wiki and see if you find anything that helps here, I noticed a few how-tos on the netgear entries.


[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28Netgear%29%7C%28311%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28Netgear%29%7C%28311%29)

I've only useed linksys and dlink cards

---

### Post by GQed76 on 2005-12-16
well its supposed to work out of box..i shouldnt even have to use ndiswrapper.

Could this be an issue with BIOS settings?

---

### Post by drummer on 2005-12-16
Another idea.. if you're using ndiswrapper, make sure that kernel modules for any other drivers aren't loaded as well. Do "lsmod" to see what modules are loaded and remove ones with "sudo rmmod foo".

ie. the card is the same as mine, so do "lsmod | grep acx" and that'll list the modules with 'acx' in the name.. i think i removed acx_pci and one other after I installed ndiswrapper. then on subsequent boots, the default driver and it's modules aren't loaded because ndiswrapper is loaded explicitly from /etc/modules (it's added by "ndiswrapper -m").

Also, when I first got my card it was a right pain but i got it working after persevering for many hours. Hopefully it will sort itself out.

Another also, you can try editing /etc/network/interfaces by hand to set the AP and anything else. And I don't think there should be *2* entries for wlan0 in iwconfig.. I'll check on my computer a bit later (I'm not at it atm).

---

### Post by drummer on 2005-12-16
here's my iwconfig:```
owen@ubuntubox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:6E:4E:F2
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:2347 B   Fragment thr:2312 B
          Power Management:off
          Link Quality:100/100  Signal level:-50 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

---

### Post by GQed76 on 2005-12-17
Thanks, ill try this when I get home.

I want to use Ubuntu so bad lol

---

### Post by GQed76 on 2005-12-18
ok when i lsmod, I see the acx driver and a firmware thing.  How do i remove them  exactly?

i triedsudo rmmod foo and it didnt work and i tried rrmod ACX_PCI and it said it wasnt in /modules

---

### Post by Lambert on 2005-12-18
acx_pci should be in lower case letters

and you'll want to use modprobe instead

sudo modprobe -r acx_pci

this is a "smarter" method of removing modules (as in how the modules are handled by the os). If there are any dependencies to this driver that are not needed, it will also remove them.

To prevent acx_pci from loading at boot you'll need to add acx_pci to a file /etc/hotplug/blacklist (I believe that's correct but you'll want to double check this)

line should look like this

blacklist acx_pci

---

### Post by GQed76 on 2005-12-18
ok i took out the native driver and am rebooting now

---

### Post by GQed76 on 2005-12-18
ell that changed the iwconfig somewhat...still cant get out .now i think i need to find the right driver version

---

### Post by GQed76 on 2005-12-18
All i did was reboot and HELLO FROM UBUNTU.

Thank you guys SO much, removing the default driver by blacklisting it did the trick!

---

### Post by Lambert on 2005-12-18
Glad to see you hung in there and resolv this. Takes a lot of patience sometimes.

Good luck with the rest of your ubuntu experience.

---

### Post by drummer on 2005-12-19
Glad it worked out.. it's so satisfying when it does.

---

