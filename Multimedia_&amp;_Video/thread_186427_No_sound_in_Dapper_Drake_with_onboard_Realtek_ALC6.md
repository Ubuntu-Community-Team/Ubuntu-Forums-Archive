---
title: "No sound in Dapper Drake with onboard Realtek ALC655."
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by GForce64 on 2006-06-01
I'm having issues getting the sound to work on the Live CD of Dapper Drake. I was directed here by another user when I posted a topic on the beginner forums. I currently have two sound cards installed: a Creative Labs X-Fi XtremeMusic add-on card and the onboard Realtek audio. 

Link to beginner forums thread:
[http://ubuntuforums.org/showthread.php?t=186384]("http://ubuntuforums.org/showthread.php?t=186384")

Here's what I've tried and discovered:
Tried unmuting everything in alsamixer and the GNOME Mixer, didn't accomplish anything.

Discovered my onboard sound is being reported as nVidia CK804 in System>Preferences>Sound.  Not sure if this is a version of the Realtek onboard or not.

Anyway, here is the lspci output.

ubuntu@ubuntu:~$ lspci
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

---

### Post by charims on 2006-08-25
haha, you must have gotten an Emachines, or at least we must have the same motherboard? Same exact problem here, cept i don't have 2 sound cards. Well, chances are no-one's going to read this since this is an ancient thread, but whatever.

---

