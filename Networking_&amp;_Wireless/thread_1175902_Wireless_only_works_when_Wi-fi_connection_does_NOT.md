---
title: "Wireless only works when Wi-fi connection does NOT have a security password"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by el canadiano on 2009-06-01
Hey guys,

Whenever I try to connect to my wireless router, I would put my passcode (128-bit) in, and after a while, it just gives up on me. This is my lspci (I'm Atheros-based).

> awpoon@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:08.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
00:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
awpoon@ubuntu:~$ 


Hope that helps.

---

### Post by lindsay7 on 2009-06-01
Some wireless devices and routers are happier with wpa other with wep. Try them both and see if it makes a difference.

---

### Post by el canadiano on 2009-06-01
I only have WEP settings, for some reason when it comes to the passphrase.

---

### Post by jobo1313 on 2009-06-01
Have you tried both options when it asks you for password. there is a 128-bit passphrase and then there is a 128-bit key option. I dont know if that is the problem but it would make a difference.

---

### Post by el canadiano on 2009-06-01
Yeah, I did, it tries to connect both times, and two green lights come on, then it gives up.

---

### Post by lindsay7 on 2009-06-01
Have you gone into your router set up and looked at the settings for wpa or wep security or are you only getting the wep passpharase request when trying to connect?

---

### Post by MidsummerDawn on 2009-06-01
I thought this question would be appropriate here. I just got my Dell Mini 9 today and I tried connecting to the wireless here at my work..and..I can't figure out how to do it. I've gone into the Network settings and it will connect after I put in the name and password, but  when I go into Firefox it won't load. What's up with it?

---

### Post by lindsay7 on 2009-06-01
There should be an icon on your top menu bar. Does it show that you are connected?

---

### Post by MidsummerDawn on 2009-06-01
Is it the computer thing? Is it supposed to light up or something? All it says is Manual Configuration.

---

### Post by lindsay7 on 2009-06-01
Right click on the top menu panel, add to Panel, and pick the following on the screen shot, it will tell you if you are connected.


[ATTACH]116116[/ATTACH]

---

### Post by MidsummerDawn on 2009-06-01
I'm still having issues. My computer thing next to the volume completely disappeared.

---

### Post by Gausian on 2009-06-02
Does it show up if you type this command?

```
sudo /etc/init.d/networking restart
```

---

### Post by el canadiano on 2009-06-02
> **lindsay7 said:**
> Have you gone into your router set up and looked at the settings for wpa or wep security or are you only getting the wep passpharase request when trying to connect?

My router settings only have 64 and 128 bit WEP. It's one of those Microsoft ones.

---

