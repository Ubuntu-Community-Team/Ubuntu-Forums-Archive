---
title: "HP Pavilion DV5000 Internal Speakers not working anymore"
date: 2010-03-20
forum: Multimedia Software
---

### Post by ets2006 on 2010-03-20
Yesterday I was on Youtube, and I had headphones plugged into the headphone socket on my laptop.
I unplugged them a few times because they were needed elsewhere, but on the last time I unplugged them, the sound didn't return to the internal speakers.
I plugged the headphones back in, and there was sound out of the headphones, but not speakers. I rebooted the laptop, still to find sound only out of the headphones. I then was very bad, and booted into wingdoze, and still sound only out of the headphones.
I've tried doing the muting channels in alsa-mixer as well. Muting didn't work. 
I've also tried cleaning the headphone socket with ispopropyl alcohol too. And removing the bios battery and battery and ac adaptor... just incase it will do a reset of some description. No. Still nothing.

If anybody is able to help me, I'd be really grateful!

My system;

Running Ubuntu Karmic 9.10 with Kernel 2.6.33-020633-generic

```
jamie@LXS-DV5000:~$ cat /proc/asound/cards
 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 80 with Cx20468-31 at 0xc0003400, irq 17
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 80 at 0xc0003800, irq 17
jamie@LXS-DV5000:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```I hope I haven't missed any crucial details.

Thanks in advance,
Jamie

EDIT:
The "mute" media button light appears to be lit, however pressing it only feeds a software into the computer, and doesn't turn the light off. I'll try playing around a bit more...
EDIT:
I just discovered that if you hold down the M key on alsamixer to mute/unmute the "external amplifier" channel, the light flashes! This is beginning to look promising....
EDIT:
If I unmute the external amplifier before I log out, it stays unmuted until I log back in again. What can I do to stop it from muting as soon as I log back in again?????

---

### Post by ets2006 on 2010-06-17
Ok, I've diagnosed the issue, it's hardware, not Ubuntu's fault - it was just a really weird coincidence. It's the sound board, or if not, the motherboard, both are equally as faulty.
I made the discovery after the laptop started to repeatedly cut out whilst I was using the processor at speeds of 1.6GHz-1.8GHz(the max) - it was rather hot. I was given it in a condition of "broken/junk" but was amazed when it worked, I've since spoken to the previous owner who said she used to use it to put in on her bed, hence the dodgy motherboard. The fan's probably blocked up with girl hair, dust and there's probably powder puff shorting across god knows how many chips! I think some hp models are known to have fan issues, the DV5000 may possibly be one of them.
Totally unrelated, seems the faulty cdrom drive, it randomly pops open and gives I/O errors - I think there's a dodgy connection somewhere as my new dvdrw works in it.
Anyways... thanks for *cough* all the support the community has given me, it's solved now. :lolflag:

Happy Linuxing,
Jamie

---

