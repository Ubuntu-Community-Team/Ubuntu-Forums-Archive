---
title: "Problems Installing drivers for USB Wireless Card"
date: 2011-12-05
forum: Networking &amp; Wireless
---

### Post by KirkS on 2011-12-05
Hello,

I've been all over the Internet looking for, and trying out ways to get this USB network adapter to work, and I just can't get it right.  I'm not exactly fluent with Terminal, though I have used it several times for finding, and installing other apps.  The system is a Dell Latitude C600 laptop, with Ubuntu 10.10 operating system.  The USB card is a Realtek 150Mbps 802.11b|g|n, that came with the drivers RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715 on a mini-CD.  I have tried installing the drivers, but I must not be doing it correctly, because I'm always given the "Not Allowed" warning.  Does anyone no how to install this software, and get the computer to see, and use the USB card?  Thanks.

---

### Post by bogan on 2011-12-05
> **KirkS said:**
> Hello,

I've been all over the Internet looking for, and trying out ways to get this USB network adapter to work, and I just can't get it right.  I'm not exactly fluent with Terminal, though I have used it several times for finding, and installing other apps.  The system is a Dell Latitude C600 laptop, with Ubuntu 10.10 operating system.  The USB card is a Realtek 150Mbps 802.11b|g|n, that came with the drivers RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715 on a mini-CD.  I have tried installing the drivers, but I must not be doing it correctly, because I'm always given the "Not Allowed" warning.  Does anyone no how to install this software, and get the computer to see, and use the USB card?  Thanks.
HI! **KirkS**

I am not the expert you want, but perhaps I can steer you.
In a terminal enter 'sudo lsusb'
You should get a line starting "RealTek...." please post it.
It is listing the full title of your adapter. If it is "...RTL8188xx... I may be able to help from my own experience
with a RealTek 8188SU dongle'. Is yours a card or a dongle?
Good Luck. Chao! , **boga**n.

---

### Post by KirkS on 2011-12-05
> **bogan said:**
> HI! **KirkS**

I am not the expert you want, but perhaps I can steer you.
In a terminal enter 'sudo lsusb'
You should get a line starting "RealTek...." please post it.
It is listing the full title of your adapter. If it is "...RTL8188xx... I may be able to help from my own experience
with a RealTek 8188SU dongle'. Is yours a card or a dongle?
Good Luck. Chao! , **boga**n.

Man, I am really mixed up now.  I thought I at least had the driver installed.  Here is what I got with the Terminal entry you gave,

Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15d9:0a4f Trust International B.V. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I don't see a thing about RealTek there. :confused:

Oh, and yes, it the packaging lists it as a dongle.  I looks like a large USB card to me, with a little green light when it works.

---

### Post by bogan on 2011-12-06
Hi! , KirkS,
 On my setup 'lsusb' includes the line:> Bus 002 Device 006: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter You should get something like that, even if no driver is found.
The fact you do not get anything like that is a bit beyond me; and suggests that Linux is not recognizing the plugged in device, even though it is flashing. 
Have you tried it in a different USB port?
Another simple thing you could try that has worked for me in the past, is to plug the dongle in, **after** you have fully booted up. If it is recognized, you should get an Authorization Requester, even if it does not work and connect.
Edit3: Also the WiFi Icon in the top bar, on the right, should appear, and, hopefully, show that scanning is in progress.
There are other things I could suggest , first some queries:
What system are you running & is it joint with Windows using a Grub Menu?
  To check the Ubuntu version run:```
 sudo uname -r
```If joint, does Windows recognise and use it OK?
Do you have another direct Internet connection with your Lap-top, or do you have to copy stuff over?

I would not expect them to be fruitful, but try the following:```
sudo iwconfig 
``````
sudo iwlist scan
```Edit:  Also:```
 sudo nm-tool
```Chao! , bogan,

---

### Post by KirkS on 2011-12-06
bogan,

I think I misinformed you.  The light on the card came on when I had Ubuntu 11.10 installed.  I hated 11.10, so I wiped my system, and installed 10.10, which is what I have on my Inspiron, and the one I like best.

Next, when I run the scan for wireless settings, I get this:

mandoman@ubuntuLatitude:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

That is a puzzle to me, as I have been using a wireless card on this Latitude for about six years.  But that was with Win. XP.  Why can't Ubuntu detect the same device I used with Windows?

Also, here is what I have for Internet usage at the moment:

lspci -nnk | grep -iA2 net
00:10.0 Ethernet controller [0200]: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] [10b7:6055] (rev 10)
    Subsystem: 3Com Corporation Device [10b7:6456]
    Kernel driver in use: 3c59x

Network manager can detect my network through the direct LAN line, but it doesn't see wireless capabilities.

NetworkManager Tool

State: connected

- Device: eth0  [NETGEAR] -----------------------------------------------
  Type:              Wired
  Driver:            3c59x
  State:             connected
  Default:           yes
  HW Address:        00:01:03:8D:C1:1F

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

This gets weirder all the time.

---

### Post by bogan on 2011-12-07
Hi! **KirkS**,
When you post data please highlight the Prompt, the Command and the output, and click the '#' symbol Icon at the top of the edit box. Preferably each command separately.
This will enclose it all in a Code box, with, if needed, its own Scroll bars, making it much easier to interpret .
You posted, K >> P#5:> Why can't Ubuntu detect the same device I used with Windows?I take this to be a 'yes' answer to my question if the dongle works with Windows on the same machine, and that the same dongle has worked there for years. - or is there a card installed in laptop.?
If that is correct, either way, please post what Windows Device Manager says about the Network adapter, and the driver version it uses. { Right click on the Adapter entry, and select Properties.} At least then we will know what you have got plugged in.
An indirect answer to your {rhetorical??} question, is this: Would you criticize an auto with a manual gearbox, for not changing gear on its own, when it comes to a steep hill.??
 Manual gears are chosen either because they are more efficient but cheaper, or to give the driver more control and flexibility.
This is a case where Linux has a manual and Windows has a automatic.

I know where you are coming from, I have been there myself; as you will see if you look up two of my threads:  "Linux Won't Recognize Realtek Wlan ( 1&2)"
Before you tried to install the drivers, did you download the 'building essentials'?
And: If you do not know the exact name of the device, how did you decide which driver to install?

---

### Post by bogan on 2011-12-07
Hi! **KirkS**, I got your message,
When you post data, please highlight the Prompt, the command and the output, and Click the '#' symbol Icon at the top of the edit box. That makes it much easier to interpret, especially for long data streams.
You Posted, K >> P#5> That is a puzzle to me, as I have been using a **wireless card** on this  Latitude for about six years.  But that was with Win. XP.  Why can't  Ubuntu detect **the same device **I used with Windows?I take that to be a 'Yes' answer to my question if Windows recognizes and uses the dongle on the same machine; and that it has worked there for several years, ie it is not a new device. - or is there a card installed in  the laptop.??
If that is correct, either way,please post what Windows Device Manager says for the Network Adapter [all entries] and the driver used. {Right-Click on the Adapter entry and select Properties.} 
Then, at least, you will know what you have got plugged in.
An indirect answer to your { rhetorical?? } question is this:
Would you criticize an auto with a manual gearbox for not changing gear on its own when it comes to a steep hill.?
Manual gears are chosen because they are more efficient but cheaper, and to give the driver more control and flexibility.
This is a case where Linux has a manual and Windows has an automatic.
Chao! , **bogan**.
Edit: PS I thought I had lost the first entry and had  re-written it and posted before I realised it had been sent, even though Forum told me I could not and deleted it.

---

### Post by KirkS on 2011-12-07
> **bogan said:**
> Hi! **KirkS**, I got your message,
When you post data, please highlight the Prompt, the command and the output, and Click the '#' symbol Icon at the top of the edit box. That makes it much easier to interpret, especially for long data streams.
You Posted, K >> P#5I take that to be a 'Yes' answer to my question if Windows recognizes and uses the dongle on the same machine; and that it has worked there for several years, ie it is not a new device. - or is there a card installed in  the laptop.??
If that is correct, either way,please post what Windows Device Manager says for the Network Adapter [all entries] and the driver used. {Right-Click on the Adapter entry and select Properties.} 
Then, at least, you will know what you have got plugged in.
An indirect answer to your { rhetorical?? } question is this:
Would you criticize an auto with a manual gearbox for not changing gear on its own when it comes to a steep hill.?
Manual gears are chosen because they are more efficient but cheaper, and to give the driver more control and flexibility.
This is a case where Linux has a manual and Windows has an automatic.
Chao! , **bogan**.
Edit: PS I thought I had lost the first entry and had  re-written it and posted before I realised it had been sent, even though Forum told me I could not and deleted it.

OK, it seems we are on completely different pages on this.  I never intended to mislead you, or give you false information, but you seem to want to take my every response as a deliberate insult.  What I meant by my computer has used a wireless network device was exactly that, it HAS used a wireless network card for years while using Windows XP, but that was a NETGEAR  card that I already found is not supported by Ubuntu, not even using ndiswrapper.  The card I am trying to use instead came with drivers for the RealTek USB wireless devise I thought we were discussing.

Look, if all I'm doing is making you upset, then why don't we just call it quits.  All I want to do is get this USB adapter to work on my Latitude, which no longer can use the PCMCIA NETGEAR card I used with Windows, because it didn't work when I tried it, and when I looked it up it did not appear as supported on the Ubuntu "WiFi Docs Wireless cards Supported" list.  So no, I did NOT try this USB device with Windows.  I thought I was giving you the info you asked for, because I DID type those commands into Terminal,  and listed the responses I got in return.  I'm sorry I didn't notice the request to  highlight the Prompt, the command and the output, and Click the '#' symbol Icon at the top of the edit box.  I am not an expert on this stuff, and I'm certainly not perfect, so I miss things, like the mentioned request.

You know something, I'm tired of this conversation, so why don't we just go our separate ways.  I apologize for taking up your valuable time with my ignorance.

---

### Post by bogan on 2011-12-07
Hi! **KirkS**

From my point of view it is you who appears to be upset. I am not. IOTTHU.
For anyone to help you, they need to know exactly what device is in use and what history there is of its operation under what conditions, and what has been tried and the results.
 That is what I was trying to establish so that I could recommend an expert.
If you have chosen to end our interaction, OK, it is up to you; all you need to do is not send the info I asked for; that will end it right here.

If you search the Networking & Wireless Forum with the Key words: "Trouble With Wireless" you will get no less than 187 results. I recommend you do that and post to the one with the most answers that is currently active.
 If you can find one where **'praseodym**' is operating; better yet. He is the expert in the type of USB dongle I think you have, and getting the right driver for the various different varieties that exist.

One word of advice: Do not refer to the dongle as a 'card'; that will confuse him as much as it confused me. Cards plug into slots on the Motherboard or are installed internally in a laptop.

Good Luck, CHAO!! , **bogan**.
                                                :lolflag:

---

### Post by KirkS on 2011-12-07
I'm an idiot with this stuff, and nothing has proven that to me more than when I loaded Ubuntu onto my Latitude.  It ran so smooth on my Inspiron that I just figured it would be the same on a Latitude.  Wrong again.  What I think I'm going to do is find all the literature I can on using Terminal, and about Grub, Debian, and Python.  Ignorance is a terrible thing.  I was pretty good with Windows, though I hated it, but this is a whole different thing.  Thanks for your help, and I will look for posts by [B]praseodym, as you suggest. As you say,

CHAO!
[/B]

---

### Post by KirkS on 2011-12-07
After some study, and messing around, here are some of the results I got.  None of this helped me get the USB DONGLE working.

Command:

>  sudo cat /var/log/syslog | grep etwork | tail -n20

Answer:

> Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> dhclient started with pid 1461
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info>   address 192.168.1.3
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info>   prefix 24 (255.255.255.0)
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info>   gateway 192.168.1.1
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info>   nameserver '192.168.1.1'
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> Policy set 'stimsonNETGEAR' (eth0) as default for IPv4 routing and DNS.
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) successful, device activated.
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.

Command:

> sudo iwconfig wlan0 mode managed

Answer:

> Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.

Command:

> sudo lsusb

Answer:

> Bus 004 Device 005: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15d9:0a4f Trust International B.V. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Command:

> sudo cat /etc/udev/rules.d/70-persistent-net.rules

Answer:

> # This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10b7:0x6055 (3c59x)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:01:03:8d:c1:1f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

Command:

> sudo cat /etc/network/interfaces

Answer:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

Command:

> sudo modprobe rtl8192se

Answer:

> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module rtl8192se not found.

Command:

> dmesg | grep -e wlan -e 819

Answer:

> [    0.000000]   #5 [00009a5000 - 00009a8198]             BRK
[    0.360892] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.361480] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.361692] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.361892] TCP: Hash tables configured (established 8192 bind 8192)
[    1.819018]  sda1 sda2 <
[    1.819225] sr 1:0:0:0: Attached scsi generic sg1 type 5

Command:

> sudo ls /lib/firmware/RTL8192SU

Answer:

> rtl8192sfw492.bin  rtl8192sfw74.bin  rtl8192sfw.bin

Command:

> cat /etc/resolv.conf

Answer:

> # Generated by NetworkManager
nameserver 192.168.1.1

Command:

> sudo cat /var/log/syslog | grep etwork | tail -n20

Answer:

> Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> dhclient started with pid 1461
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info>   address 192.168.1.3
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info>   prefix 24 (255.255.255.0)
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info>   gateway 192.168.1.1
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info>   nameserver '192.168.1.1'
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> Policy set 'stimsonNETGEAR' (eth0) as default for IPv4 routing and DNS.
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) successful, device activated.
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.

Command:

> lspci -nn

Answer:

> 00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:03.0 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
00:03.1 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:08.0 Multimedia audio controller [0401]: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator [125d:1998] (rev 10)
00:10.0 Ethernet controller [0200]: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] [10b7:6055] (rev 10)
00:10.1 Communication controller [0780]: 3Com Corporation Mini PCI 56k Winmodem [10b7:1007] (rev 10)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility M3 AGP 2x [1002:4c46] (rev 02)
02:00.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
02:00.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
02:00.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)

Command:

> sudo lshw -C network

Answer:

> PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 3c556 Hurricane CardBus [Cyclone]
       vendor: 3Com Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 10
       serial: 00:01:03:8d:c1:1f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.3 latency=32 link=yes maxlatency=5 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:d400(size=256) memory:f3ffdc00-f3ffdc7f memory:f3ffd800-f3ffd87f memory:fc000000-fc01ffff

Command:

> lsusb

Answer:

> Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15d9:0a4f Trust International B.V. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Notice in the above that it is different than the results of the same command earlier.  Is that because I used sudo in the first one?

Command:

> sudo cat /var/log/syslog | grep -e etwork -e 819 | tail -n25

Answer:

> Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> dhclient started with pid 1461
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec  7 19:49:50 ubuntuLatitude NetworkManager[656]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info>   address 192.168.1.3
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info>   prefix 24 (255.255.255.0)
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info>   gateway 192.168.1.1
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info>   nameserver '192.168.1.1'
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec  7 19:49:51 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> Policy set 'stimsonNETGEAR' (eth0) as default for IPv4 routing and DNS.
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) successful, device activated.
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.

Command:

> ~/Desktop$ lsusb

I had the file that held the drivers for my USB network adapter dongle on the Deshtop.

Answer:

> Bus 004 Device 006: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15d9:0a4f Trust International B.V. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I got all of that by searching through, and reading a lot of threads on this forum.  It's confusing, to say the least.  It seems to be saying that their IS no Wireless Network device installed, but then when asked about the drivers to the device that is "no such device", it lists them right out.  What I need is to get a Wireless Network configured on this Ubuntu 10.10 Latitude, but I can't seem to find the way to accomplish this.

If anyone is looking at this at all.......HELP, PLEASE!!!!!!!!!!!! ](*,)

KirkS

---

### Post by bogan on 2011-12-08
Hi!** KirkS**, onceagain.
Hopefully a person more expert than I will respond to Your Post: K >>P#11> If anyone is looking at this at all.......HELP, PLEASE!!!!!!!!!!!! ](*,)

KirkS 'Anyone' includes me, and "CHAO!" means: "until next time", so, somewhat warily, I am responding.
Two points of interest, to me:
 First: your 'lsusb' output twice includes```
Bus 004 Device 005: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``` and once it omits the first line. suggesting that a RealTek device was recognized intermittently, or was not present in one case. 
AS your Ethernet network works OK, and uses```
:*-network               
       description: Ethernet interface
       product: 3c556 Hurricane CardBus [Cyclone]
       vendor: 3Com Corporation
``` not a RealTek device, this is not for Eth0.
You posted:> Notice in the above that it is different than the results of the same  command earlier.  Is that because I used sudo in the first one? I do not think 'Sudo' would be needed or affect lsusb, nor would the CD to Desktop.
I would have expected the ID to be "0bda:8171" but that may be that your dongle is an RTL8188CU and not an RTL8188SU.
What does surprise me is that it shows two devices on the same bus, which could mean some conflict, but I do not know enough to  say more.
Second: your Syslogs confirm that the Realtek device is not being recognised, but it also, twice, showed:```
Dec  7 19:49:52 ubuntuLatitude NetworkManager[656]: <info> Policy  set 'stimson**NETGEAR**' (eth0) as default for IPv4 routing and DNS.
```. Again,  I do not know enough to  say more, but in view of your remark that you previously used a NetGear on your Latitude, that suggests to me that there may be some remnants of that installation that are in conflict with the Realtek, preventing its recognition.
 Probably you would need to make a blacklist entry. 
You also Posted:>   It seems to be saying that their IS no Wireless Network device  installed, but then when asked about the drivers to the device that is  "no such device", it lists them right out.   What it listed, as far as I could tell, was the Firmware files and folder. The fact they are present does not mean they are installed; nor used, as they would not be, if the device for which they are there is not recognized.
All your current data suggests the 8192 driver is not being used.

All the best kuck.
CHAO! **,bogan**.

---

### Post by KirkS on 2011-12-08
Bogan,

I hold no animosity towards you, I just didn't think we were getting anywhere.  Did you?  I did as you recommended, in fact, and traced down all the posts I could find concerning this issue, especailly by praseodym.  I even sent a PM to him requesting assistance.  He gave me the following list of commands to run and post;

> Code:
---------
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
rfkill list
sudo iwlist scan


Then he told me to start a new thread with the results.  I have done so.  Incidentally,  I noticed several of your posts looked quite similar to our exchanges, except you about gave that Chili dude a breakdown, LOL!!!!  :biggrin:

---

### Post by bogan on 2011-12-08
Hi! **KirkS**.

Good Oh!   I guess you can mark this as 'Solved'.

Interestingly, from my point of view, What I finally suggested was what I had had in mind from the start; I was just trying to be certain it was the right way to go.

I'll follow your post with interest but will not intervene, unless you direct a post to my attention, using  "@bogan".

All Best Wishes,

CHAO! ,**boga**n.

---

