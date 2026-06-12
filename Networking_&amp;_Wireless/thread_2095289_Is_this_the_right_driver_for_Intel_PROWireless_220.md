---
title: "Is this the right driver for Intel PRO/Wireless 2200BG?"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by Buntu Bunny on 2012-12-16
Xubuntu 12.04
Dell Inspiron 700m

I recently installed Xubuntu on an old Dell laptop. Now I'm trying to get wifi enabled and the first step seems to be to update the driver. I'm still a little unsteady on my feet in all things Terminal, so I want to verify that I've got the right driver before I proceed and possibly make a mess for myself (which is known to happen). 

Based on 

```
leigh@leigh-Inspiron-700m:~$ dmesg | grep ipw2200
[   16.357910] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   16.357919] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.435959] ipw2200 0000:02:01.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[   16.435980] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.907667] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
```

Am I correct that the current driver version is 1.2.2? If so, is the correct driver from [the SourceForge 2200BG site]("http://ipw2200.sourceforge.net/") is this one...

> driver versions v1.1.1 and newer firmware v3.0 , firmware v3.1

v3.1 being new and therefore preferable. 

Would appreciate confirmation or correction!

---

### Post by ahallubuntu on 2012-12-16
That's an old Intel wireless card - almost ten years old.  If you are using 12.04, you have a fairly new kernel and a very mature driver for the card.  If the wireless works fine, I wouldn't give it another thought.

---

### Post by Buntu Bunny on 2012-12-16
> **ahallubuntu said:**
> That's an old Intel wireless card - almost ten years old.  If you are using 12.04, you have a fairly new kernel and a very mature driver for the card.  If the wireless works fine, I wouldn't give it another thought.

That's just it. The wireless doesn't work.

---

### Post by chili555 on 2012-12-16
> Am I correct that the current driver version is 1.2.2? Yes.> driver versions v1.1.1 and newer firmware v3.0 , firmware v3.1 That's telling us that the driver version at Sourceforge is 1.1.1; older because the maintenance is now in the mainline kernel, and there is a version 3.1 *firmware*.

If your wireless isn't working in 12.04 there is something else wrong; something a newer driver is unlikely to fix. Let's do some diagnostics:```
rfkill list all
nm-tool
iwconfig
```Your dmesg looks pretty solid.

---

### Post by Buntu Bunny on 2012-12-16
> **chili555 said:**
> Let's do some diagnostics:```
rfkill list all
nm-tool
iwconfig
```Your dmesg looks pretty solid.

Chili555, I definitely appreciate the help. 

I might should mention that I do not have a wireless connection at home, so I have to go to the library to test. However, before I installed Xubuntu, WinXP could sometimes detect wireless connections in the neighborhood.

```
$ rfkill list ALL
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

```
$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:12:3F:82:34:EC

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```

```
$ iwconfig 
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
         Mode:Managed  Channel:0  Access Point: Not-Associated   
         Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
         Retry limit:7   RTS thr:off   Fragment thr:off
         Power Management:off
         Link Quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```

---

### Post by chili555 on 2012-12-16
We wonder why eth1 doesn't appear in nm-tool.  Are there any settings in /etc/network/interfaces related to eth1? Does it scan? ```
sudo iwlist eth1 scan
dmesg | grep eth1
```It probably doesn't mean much that you don't see networks if you haven't an access point where you are now.

---

### Post by Buntu Bunny on 2012-12-16
Please see my next comment for the correct answer. 

> **chili555 said:**
> We wonder why eth1 doesn't appear in nm-tool.  Are there any settings in /etc/network/interfaces related to eth1? Does it scan? ```
sudo iwlist eth1 scan
dmesg | grep eth1
```

```
$ sudo iwlist eth1 scan
eth1   No scan results
```

```
$ dmesg | grep eth1
```

That one simply returns to the cursor, no output.

---

### Post by Buntu Bunny on 2012-12-16
> **chili555 said:**
> We wonder why eth1 doesn't appear in nm-tool.  

Wait! My profound apologies! I am copying and pasting to transfer from the laptop to my desktop. I somehow didn't get the entire output copied. Gee do I feel silly. 

Here is the entire thing. 

```
leigh@leigh-Inspiron-700m:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:12:3F:82:34:EC

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             disconnected
  Default:           no
  HW Address:        00:13:CE:32:CF:5A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    2Wire930:        Infra, 98:2C:BE:32:9C:A1, Freq 2432 MHz, Rate 54 Mb/s, Strength 29 WEP


leigh@leigh-Inspiron-700m:~$ 

```

---

### Post by chili555 on 2012-12-16
> 
  Wireless Access Points 
    2Wire930:        Infra, 98:2C:BE:32:9C:A1, Freq 2432 MHz, Rate 54 Mb/s, Strength 29 WEPIt sees networks, albeit weak. I see no sign of ill health and certainly no reason to install a different driver.

---

### Post by Buntu Bunny on 2012-12-16
> **chili555 said:**
> It sees networks, albeit weak. I see no sign of ill health and certainly no reason to install a different driver.

Chili555, thank you for your patience and your help. This is one step in problem solving checked off my list. 

When I'm in a wifi hotspot like the library however, I am unable to connect, but the problem must be something else. With that I should probably start a new thread when I have time for another sit-down at the computer.

---

