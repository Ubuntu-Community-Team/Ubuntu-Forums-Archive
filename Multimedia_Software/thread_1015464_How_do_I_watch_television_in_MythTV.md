---
title: "How do I watch television in MythTV?"
date: 2008-12-18
forum: Multimedia Software
---

### Post by Maheriano on 2008-12-18
I installed an old MSI tuner card and I have no idea if it works or if I have to configure it or what the deal is. I open MythTV and click Television but nothing happens. The screen flashes but it doesn't go into any sort of television interface, it stays on the menu. All I did was turn off the computer, put in the MSI (PCI) tuner card and turn the computer back on. Here's the output of my lspci:

deemar@Chugger:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
05:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
05:07.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
05:08.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

---

### Post by Maheriano on 2008-12-18
And when I click Tuner Status in MythTV, nothing is listed. But on that list I posted above, it looks like the Conexant Systems entry is my tuner card. What do I do now?

---

### Post by Maheriano on 2008-12-19
Nobody knows?

---

### Post by Chris Musampa on 2008-12-19
Have you been through mythtv-setup to set up the backend?

---

### Post by Maheriano on 2008-12-19
I believe so. I don't think the front end would run without the backend being set up. Or would it?

---

### Post by Chris Musampa on 2008-12-19
> **Maheriano said:**
> I believe so. I don't think the front end would run without the backend being set up. Or would it?

Not sure as I always setup the backend first. 

You'll probably get help from people more clued up than me if you make clear what you have done so far.

---

### Post by Maheriano on 2008-12-19
> **Chris Musampa said:**
> Not sure as I always setup the backend first. 

You'll probably get help from people more clued up than me if you make clear what you have done so far.

I'm nearly positive I've set up the backend, it asked me to do that when I installed it and I remember going through a configuration. That's really all I did, then I put in the card, rebooted and here I am. When I click WATCH TV, the screen flashes but does nothing else. And like I said, there's nothing listed under Tuner Status.

---

### Post by canoemoose on 2008-12-19
You should have set up the backend after the card was installed.

---

### Post by wolfen69 on 2008-12-19
during setup, you have to select the right drivers for your card. there is a pull down menu that has video4linux as the default. i'm not sure which driver is right for your card, but i bet you didn't select the right one. run setup again (you don't have to reinstall) and select a different one. or just go to the mythtv website and forums for answers.

---

### Post by Maheriano on 2008-12-19
> **wolfen69 said:**
> during setup, you have to select the right drivers for your card. there is a pull down menu that has video4linux as the default. i'm not sure which driver is right for your card, but i bet you didn't select the right one. run setup again (you don't have to reinstall) and select a different one. or just go to the mythtv website and forums for answers.

Will do. You'll hear from me again over the weekend! Thanks!

---

### Post by Maheriano on 2008-12-19
Okay, I ran mythtv-setup and the answer is no, I hadn't run that before. So I got in there and set up my card, it was automatically detected as a MSI TV@NYWHERE card, that's good. I entered a PIN (not sure why but it said it was required) and then saved everything. It asked if I wanted to run MYTHFILLDATABASE so I did and it did......something......so I fired up MythTV Frontend and clicked WATCH TV again, it did the same thing. It flashed the screen but didn't go anywhere. So I went back into Information Settings and under Tuner Status it says, "Tuner 1 Unavailable." Oh I'm so close! What do I do now?

---

