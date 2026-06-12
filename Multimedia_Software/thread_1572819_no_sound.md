---
title: "no sound"
date: 2010-09-11
forum: Multimedia Software
---

### Post by shallowthought on 2010-09-11
I have a new Dell XPS 9100 with 9GB ram and ATI Radeon HD 5770 1024MB GDDR5. 
I installed a dual boot with Windows 7 and Ubuntu 64bit. Sound worked fine with
the Windows 7, but no sound with Ubuntu. Did a reinstall with just Ubuntu 64 bit (wiping out the Windows 7). No sound.
I first did: 
          System -> Administration->System Testing
(testing only for sound). I get:

0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbbf4000 irq 22
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfbefc000 irq 17


Next I followed: "Comprehensive Sound Problem Solutions Guide v0.5e"


(1) aplay -l

I get:

*** List of PLAYBACK Hardware Devices ***

card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
     Subdevices: 1/1
     Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
     Subdevices: 1/1
     subdevice #0: subdevice #0

(2)    lspci -v

I get

Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
    Subsystem: ATI Technologies Inc Device 2543
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fbec0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at fbea0000 [disabled] [size=128K]
    Capabilities: <access denied>

03:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
    Subsystem: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fbefc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

(3)  went to  [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) 
Under ATI I get:

Soundcard List for ATI
Product     Chipset(s)     Driver & Docs     Tags, Notes
ATI-IXP southbridge AC97 audio
    
IXP SB150
IXP SB200
IXP SB250
IXP SB300
IXP SB400
    Details     [PCI] [ANALOGio]
ATI-IXP southbridge AC97 modem
    
IXP SB150
IXP SB200
IXP SB250
IXP SB300
IXP SB400
    Details     [PCI] [ANALOGio]
ATI-IXP southbridge HD-audio and modem
    
SB450
    Details     [PCI]

Matrix:Soundcard-Tags 

Don't see the ATI HD 5700. I guess this is "Failure."

Under Intel I get:

Soundcard List for Intel
Product     Chipset(s)     Driver & Docs     Tags, Notes
ICH southbridge AC97 audio
    
440MX
i810
i810E
i820
ICH4
ICH5
ICH6
ICH7
    Details     [PCI] [Sample16bit] [48kHz]
ICH southbridge AC97 modem
    
440MX
i810
i810E
i820
ICH4
ICH5
ICH6
    Details     [PCI] [Sample16bit]
ICH southbridge HD-audio and modem
    
ICH6
ICH6M
ICH7
ESB2
    Details     [PCI]

Matrix:Soundcard-Tags 

I guess this is also "Failure"?

Not sure what to do next....

Help would be greatly appreciated.
(I'm barely computer literate.)

Thanks in advance ...

---

### Post by shallowthought on 2010-09-16
Solved:  it helps to plug the speakers into the correct jack.

---

