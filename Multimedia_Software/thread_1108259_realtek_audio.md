---
title: "realtek audio"
date: 2009-03-27
forum: Multimedia Software
---

### Post by 762sks on 2009-03-27
i just tried to hook up my audio speakers to the pc, no sound. i thought could be my speakers so i plug in a set of headphones i know work. nothing. now i would have posted what audio i have except i cant find the system spec icon anymore. i used it once and it seems to have dissapeared. i know its a realtek audio device on a 64bit evga motherboard. i tried checking the existing settings, and there is an option in there for realtek, but when i select it i still dont get any sound. 

i know you guys will want to know more about my specs, but like i said i cant find the program in the system menu anymore. 

so lets start with that if we could and go from there! 


thanks

---

### Post by wolfen69 on 2009-03-27
do
```
lspci
```
and post the output here.

i would check your BIOS settings to see if the onboard audio is enabled. also, right click the speaker icon on the desktop and open volume control and make sure all the settings are correct.

---

### Post by 762sks on 2009-03-27
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
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
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)



also i checked the setting and it seem like everything is in order. now i did see a realtek device and also an nvidia audio device.

i tried both and neither worked. might have to download a new one and uninstall those and install the new one.

---

### Post by 762sks on 2009-03-28
bump?

---

### Post by wolfen69 on 2009-03-29
see [this]("https://help.ubuntu.com/community/SoundTroubleshooting") and post back if it does not work.

---

