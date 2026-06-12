---
title: "How do I setup my PCHDTV HD-5500 tuner card"
date: 2008-09-14
forum: Multimedia Software
---

### Post by Mhawkins1 on 2008-09-14
I just purchased a HD-5500 tuner card for my computer so that I can record TV shows. This is the only tuner card that I could find that is officially supported under Linux. Unfortunately I am a Linux n00b. Can anyone help me set this up? I guess that it is supposed to work in MythTV and Xine.

---

### Post by xc3RnbFO8P on 2008-09-14
In Terminal **lspci**, can you see the card?
If you do try Kaffeine.

---

### Post by Mhawkins1 on 2008-09-14
> **Ringi said:**
> In Terminal **lspci**, can you see the card?
If you do try Kaffeine.

I think that it is listed as 01:07.0 Multimedia video controller, 01:07.1 Multimedia video controller, 01:07.2 Multimedia video controller, & 01:07.4 Multimedia video controller below. I've tried Kaffine, but I am unsure of how to get it to work in there.

```

mhawkins@Ubuntu-Desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
01:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:07.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:07.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:07.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

```

---

### Post by xc3RnbFO8P on 2008-09-14
From linuxtv [http://www.linuxtv.org/wiki/index.php/PcHDTV_HD-5500]("http://www.linuxtv.org/wiki/index.php/PcHDTV_HD-5500")
> The output of **[COLOR="Green"]lspci -vn[/COLOR]** will reveal that the card has a subsystem PCI ID of [COLOR="Green"]7063:5500[/COLOR]. 

---

### Post by Mhawkins1 on 2008-09-14
> **Ringi said:**
> From linuxtv [http://www.linuxtv.org/wiki/index.php/PcHDTV_HD-5500]("http://www.linuxtv.org/wiki/index.php/PcHDTV_HD-5500")

Like I said I'm a Linux n00b. I don't know what this means. All I know is that I have the required hardware and software and have the card hooked up to my cable but don't know how to get it to display on the computer. I have the MythTV installed but again I don't know how to set it up.

---

### Post by xc3RnbFO8P on 2008-09-14
It should work out of the box.
**lspci -vn** should give you the TV card ID 7063:5500.
If you don't see that, show the output of lspci -vn.

---

