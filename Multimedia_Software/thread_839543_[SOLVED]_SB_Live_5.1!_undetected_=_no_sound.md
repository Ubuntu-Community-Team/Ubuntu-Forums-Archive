---
title: "[SOLVED] SB Live 5.1! undetected = no sound"
date: 2008-06-24
forum: Multimedia Software
---

### Post by Michalxo on 2008-06-24
Hi all, 
as topic says, my hardy (8.04) can't find my second sound card creative labs soundblaster (SB) Live 5.1. 
Sound worked with my onboard card, but it's a piece of cr*p, so I've disabled it in BIOS and I am not getting any sound now. (even when onboard card is On, my SB is not recognized). I am begging you for help.
here are some outputs:

lspci
```

00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
```
aplay -L
```
aplay: device_list:205: no soundcards found... 
```
cat /proc/asound/cards
```
--- no soundcards ---
```

pls help me someone, I am not getting this sound since feisty :(
In dapper it worked well

---

### Post by Michalxo on 2008-06-25
bump :(
really no one? :(

---

### Post by Michalxo on 2008-06-25
It seems, that module emu10k1 is loaded as EMU10k1 so there is the problem probably... solving with another great guyz :)

---

