---
title: "volume problems"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by brianboros on 2007-03-18
okay im having volume problems whenever i click on the peaker it says, "No volume control GStreamer plugins and/or devices found."

I got this running the guide
```

brian@brianslinux:~$ aplay -l
aplay: device_list:221: no soundcards found...
brian@brianslinux:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

```
stopped there because i did not find a soundcard.

I looked in the computer and im sure that i have an onboard sound card.
I went into the BIOS and checked to make sure that the "Onboard sound circuitry is on." 
I'm pretty sure I heard a system beep come out of my speakers so im not sure if that helps.

If there is any other information that you would like me to get just let me know and i will do it ASAP.

Thank you in advance for your help,
Brian

---

