---
title: "UbuntuStudio No Better!?"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by shawnrgr on 2008-01-11
I moved from Ubuntu 7.10 to UbuntuStudio. Thinking at least some of my audio recording woes would be fixed out of the box. However I was disappointed to see that this was a dream. 

-Ardour has strange 'click' sounds in my recordings
-Can't configure jack any better then before even with ubuntustudio kernal
-Audacity has strange issues where when I record a track while playing a track, then play the whole thing back, the timing is not right. The second track skips a bit and messes the whole recording up.

Whats strange is, this is a new hp desktop. I used to record multiple tracks in audacity from a 4 year old laptop without any issues! I don't understand!

Someone please shed some light on this. What can I do!? I need help!

---

### Post by shawnrgr on 2008-01-11
shameless bump :(

can anyone help? I don't know where to start. At least in Gusty i could record multiple tracks in audacity. Now in UbuntuStudio i can't. Please im desperate. :(

---

### Post by Mithrilhall on 2008-01-11
My suggestion, is post the hardware specs of the machine.

Issue a 'lspci' and post the results.

---

### Post by shawnrgr on 2008-01-11
Thank you for your reply! here is my output

```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
```

---

### Post by shawnrgr on 2008-01-11
bump :( , my friend is coming over tonight to do some recording. anyone have any ideas an solving any of these problems?

---

### Post by Mithrilhall on 2008-01-11
Could you post the model and the possible specs of the machine?

---

### Post by wolfen69 on 2008-01-11
you could try Studio64 for your music needs. [http://www.64studio.com/](http://www.64studio.com/)  there is a link on the download page for 32bit systems if you prefer. musix is another distro you could try.

---

### Post by shawnrgr on 2008-01-12
Took out my almost 4 year old laptop and loaded the 64linux live cd up on my laptop. Ardour, jack, audacity all worked flawlessly. I don't understand. I have 6mo old HP desktop amd64 X2, 2gig ram. So live cd working better then full install on new pc with better hardware? i don't get it. 

Is there somehting i'm doing wrong?

Should I try installing a 64bit ubuntu system on my desktop? could that be my problem? Any more input?

---

