---
title: "Cannot connect to WiFi"
date: 2011-10-08
forum: Networking &amp; Wireless
---

### Post by Roger Dodger on 2011-10-08
I'm fairly new to ubuntu and I just installed ubuntu 11 on a laptop. I had an old version of ubuntu 8 running on the same laptop, but decided to reinstall/upgrade to ubuntu 11. I have not been able to connect to wifi since I upgraded.

I have a Linksys wireless G Network adapter (model WPC               54G ver.2) and have a Linksys WRT54G2 v1 router. I have tried the following configurations:
-clicked on  pie shaped icon (at top right) and then 'edit connections'
-wireless tab
-highlighted the only wireless network I currently have in there
-made sure SSID is correct 
-left the following blank: BSSID, Device mac address, cloned mac address
-on the wireless security tab:
-security is set to wep 128-bit PassPhrase 
-key: correct password for wifi
-wep  index: 1(default)
-authentication: open system
-regarding the ipv4 and ipv6 setting, I did not change anything.

My last question is a general question in regard to detection of wifi networks.  Like many, I come from a Windows background and am used to a window called 'connect to a network' where I can see a listing of all available WiFi in my current location along with signal strength.  Does ubuntu have something similar?

---

### Post by roger_1960 on 2011-10-08
Hi

Normally, when you click the "pie" icon at top right, the dropdown includes the SSIDs of the available networks.  If none are visible, perhaps the wireless is turned off with a hardware switch?  Can you use another device to check that the network is actually available?

In your "edit connections", check that under IPV4, "connect automatically" and "automatic DHCP" are selected.  Set IPV6 to "ignore" for now.

---

### Post by Roger Dodger on 2011-10-08
> **roger_1960 said:**
> 
Normally, when you click the "pie" icon at top right, the dropdown includes the SSIDs of the available networks.  

I installed umbuntu 11 (not sure if this is different). When I click the pie-shaped icon, I get a dropdown consisting of:
[LIST]
[*]Wired network  (dulled out, not clickable)
[*]Disconnected  (dulled out, not clickable)
[*]VPN connections
[*](check mark) Enable networking
[*]connection information (dulled out, not clickable)
[*]edit connections...
[/LIST]

> **roger_1960 said:**
> 
In your "edit connections", check that under IPV4, "connect automatically" and "automatic DHCP" are selected.  

They are.

> **roger_1960 said:**
> 
Set IPV6 to "ignore" for now.

It is.

> **roger_1960 said:**
> 
Can you use another device to check that the network is actually available?

Yes. The wifi is up. (hence these posts)

---

### Post by praseodym on 2011-10-08
Hi,

please show:

```
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by Roger Dodger on 2011-10-08
> **praseodym said:**
> 
please show:

```
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

Thanks for the reply. I should note that I have been able to connect through a ethernet cable since I last posted. I'm not sure if it is pertinent to these tests, but these tests were run with the ethernet connection enabled.

```

john@john-Inspiron-1000:/tmp$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
john@john-Inspiron-1000:/tmp$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27230  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
pcmcia_rsrc            18292  1 yenta_socket
psmouse                73312  0 
serio_raw              12990  0 
i2c_sis96x             12743  0 
dcdbas                 14054  0 
sis_agp                13127  1 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
sis900                 22568  0 
john@john-Inspiron-1000:/tmp$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

john@john-Inspiron-1000:/tmp$ rfkill list
john@john-Inspiron-1000:/tmp$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

john@john-Inspiron-1000:/tmp$ 

```

---

### Post by roger_1960 on 2011-10-08
Mmm

That suggests that your laptop is not detecting the wlan card at all.  It is probably a driver issue.

If you run
> 
lspci in terminal, and > iwconfig in terminal, and > rfkill list all could you post the output.

---

### Post by praseodym on 2011-10-08
Well, seems like a PCI card?! Show

```
lspci -nnk | grep -iA2 net
```
No wireless module is shown...

---

### Post by roger_1960 on 2011-10-08
Over to praseodym so we don't cross posts.  One thought -  have you pulled out and re seated the PCI card a few times to ensure the connections are OK?

---

### Post by Roger Dodger on 2011-10-08
Roger, yes I pulled the card in and out a few times. Here is the output from the terminal:

```

john@john-Inspiron-1000:/tmp$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

john@john-Inspiron-1000:/tmp$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

john@john-Inspiron-1000:/tmp$ rfkill list all
john@john-Inspiron-1000:/tmp$ 

```

---

### Post by Roger Dodger on 2011-10-08
praseodym,
```

john@john-Inspiron-1000:/tmp$ lspci -nnk | grep -iA2 net
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
    Subsystem: Dell Device [1028:0195]
    Kernel driver in use: sis900
--
02:00.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066]
    Subsystem: Linksys WPC54G v2 802.11g Wireless-G Notebook Adapter [1737:0033]
john@john-Inspiron-1000:/tmp$ 

```

---

### Post by praseodym on 2011-10-08
This device only works with Ndiswrapper:

```
sudo apt-get install --reinstall ndisgtk ndiswrapper-common ndiswrapper-utils-1.9
```
Windows-driver attached.

---

### Post by Roger Dodger on 2011-10-08
Paseodym,

Thanks for this.

I'm not clear, in which directory should I unpack those files?

---

### Post by praseodym on 2011-10-09
Save the folder in /home and install the driver via:

```
sudo ndiswrapper -i ~/ti1130pci_xp/TNET1130.INF
```
Check:

```
ndiswrapper -l
```
If the driver is present, load the module:

```
sudo modprobe -v ndiswrapper
sudo ndiswrapper -ma
sudo depmod -a
sudo service network-manager restart
```
Controls:
```
iwconfig
lsmod
dmesg | grep ndis
sudo iwlist scan
```

---

