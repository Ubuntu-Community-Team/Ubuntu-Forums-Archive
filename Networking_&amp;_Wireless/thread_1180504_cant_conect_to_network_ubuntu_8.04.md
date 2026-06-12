---
title: "cant conect to network ubuntu 8.04"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by phildred on 2009-06-06
Hi everyone. I'm having trouble connecting to my wireless network. I'm running a dual boot win xp/ubuntu 8.04 I've got a linksys wireless g usb network adapter. I can see my network and nearby ones but when I try to connect it errors out and asks for my newtork key again. I had a wired connection a few months ago that worked fine.

I looked through the forum to try and find a similar post but I still couldn't get it working. I am also new to ubuntu and to linux so if anyone can help me and give me pre-school instructions I would appreciate it. Thanks in advance.

---

### Post by coffeeaddict22 on 2009-06-06
Hi Phil,
First up, wireless has improved out of sight in the last 12 months, and I'd strongly recommend upgrading to 9.04; many cards that needed ndiswrapper 12 months ago now have kernel drivers.  
If you want/ need to stay with 8.04, start off by opening a terminal and typing in the following.  The output will localise the problem.
```
lshw -C network
iwconfig
nm-tool
route -n
```
Post back what you get if you need more help.

---

### Post by phildred on 2009-06-07
Hello coffeeaddict, here is my output from what you asked. I don't have any idea what this all means. If I can't get this to work I might try installing 9.04.

*-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 20
       serial: 00:1c:25:e6:dd:70
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:18:39:0a:4a:6a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:[HTML][/HTML]off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/wlan0
  Type:              802.11 Wireless
  Driver:            rt2500usb
  Active:            no
  HW Address:        00:18:39:0A:4A:6A

  Capabilities:
    Supported:       yes

  Wireless Settings
    Scanning:        yes
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Networks (* = Current Network)
    eddie01:         Infrastructure Mode, Freq 2.462 MHz, Rate 62 Mb/s, Strength 48%, Encrypted (WEP)
    


- Device: eth0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/eth0
  Type:              Wired
  Driver:            sky2
  Active:            no
  HW Address:        00:1C:25:E6:[HTML][/HTML]DD:70

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes

  Wired Settings
    Hardware Link:   no


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

---

### Post by coffeeaddict22 on 2009-06-07
Hi,
The clue is in what's NOT there.  If you look at the output of lshw -C network, you'll see your ethernet card, all set up and behaving nicely.  Your wireless card is missing a few things though; the most important is the driver.  I'm not sure why it's showing up as having one in nm-tool, particularly since the network manager essentially sits on top of the drivers.
Have a look in System/Administration/Hardware Drivers and see if there's a driver in there for it.  If there is, enable it, and that should fix it.
If not, I'd recommend updating to 9.04 before you start doing the driver hunting thing, or getting into the details of ndiswrapper.

---

### Post by phildred on 2009-06-07
Well the Driver was not listed so I took your advice and installed 9.04 and it worked like a charm. Thanks for all your help!

---

### Post by coffeeaddict22 on 2009-06-07
It's always nice when the easy option works.  Enjoy!

---

