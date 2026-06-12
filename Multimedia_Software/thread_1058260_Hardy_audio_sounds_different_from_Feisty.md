---
title: "Hardy audio sounds different from Feisty"
date: 2009-02-02
forum: Multimedia Software
---

### Post by Macintosh SE on 2009-02-02
I know this is bizarre, but two IDENTICAL audio files, on the same computer, sound different between Feisty and Hardy. Things sound slightly muffled in Hardy. Has anyone else noticed this? How can I go back to the Feisty audio playback while keeping Hardy?

By the way, I don't think it is PulseAudio, because I removed it to test and things sounded the same.

---

### Post by Crafty Kisses on 2009-02-03
What is the results of this command?
```
lspci
```

---

### Post by markbuntu on 2009-02-03
Are you using the same application to play the file?

---

### Post by Macintosh SE on 2009-02-07
> **Codename said:**
> What is the results of this command?


```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
01:0a.0 Multimedia audio controller: Fortemedia, Inc Xwave QS3000A [FM801] (rev b2)
01:0a.1 Input device controller: Fortemedia, Inc Xwave QS3000A [FM801 game port] (rev b2)

```

---

### Post by Macintosh SE on 2009-02-07
> **markbuntu said:**
> Are you using the same application to play the file?

Yes (not the same version, but the same apps).

---

