---
title: "Ubuntu Studio, EMU-1212, and ALSA"
date: 2013-03-17
forum: Multimedia Software
---

### Post by bnilsson on 2013-03-17
Hi!

I am running Ubuntu Studio 64-bit 12.04 LTS.
I just installed a Creative Labs EMU1212 sound card, and managed to get it accepted by installing alsa-firmware from medibuntu.
Everything looks fine, it shows up correctly in lspci:
> 
07:04.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

and aplay -l, aplay -L, (too lengthy to quote) and there are a lot of settings for it in alsamixer.

Only problem is that I cannot get any sound out of it.

I even booted a Windows 7 disk and installed the drivers just to check my connection cables and it was ok, I got sound.

I suspect and hope that my only problem is to figure out how to set up the alsamixer patch matrix properly.
I set all the alsamixer "analog" controls to 100 percent.
I tried to connect 0202 DAC Right and 0202 DAC Left to DSP 0 and DSP 1, no luck.
I spent a few hours testing other patch possibilities in alsamixer before giving up.
If I define it as the default audio output in the pulseaudio mixer and play some music I see the amplitude bar jumping around like it should. But no sound.
I tried to connect VLC to 
> 
hw:CARD=EMU1010,DEV=0
    E-mu 1010 PCIe [MAEM8986], ADC Capture/Standard PCM Playback
    Direct hardware device without any conversions

and it succeeded without any VLC errors, but no sound.

I must have missed something crucial.

What is the relation between the DSP's and the aplay -L entries?

Can someone assist me on more places to look, or tell me how to do it?

Edit:
1) Got Capture working, DSP 0/1 connected to 0202 ADC Left/Right enables me to record using Audacity.
2) 0202 DAC connected to 0202 ADC gives me a positive feedback beep, which is logical. So it is the alsa output that don't reach the DAC's. So what should I connect the 0202 DAC's to???

Edit2:
A local friend adviced me to install ld10k1, a patchloader daemon for Audigy 2 cards.
I will do that as soon as I get home.

---

### Post by bnilsson on 2013-03-18
Installed ld10k and got a surprise: 
ld10k1 Error: not a EMU10K1/EMU10K2 based card
Ok, the card setting was wrong, but it seems the ld10k1 was a dead end anyway...still no sound.

---

### Post by cpolymeris on 2013-03-21
Hi, bnilsson, received your msg.

I honestly don't remember which of the DSPs was the one ALSA used (maybe DSP10-11?). Using alsamixer, try rotating your [COLOR=#008800][FONT=Monaco]0202 DAC Left/Right Playback Enum[/FONT][/COLOR]s through all the possible values. Be aware that some numerical "level sliders" actually affect internal routing, I think they are labeled "DSP routing", and are usually hidden.

[COLOR=#000000][I]07:04.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
[/I][/COLOR]
This is strange... don't remember seeing that card id. Did you disable your motherboard's built-in sound card?

I don't have the card anymore, so take this all with a grain of salt, my memory might fail me.
I can't even test it, but I wrote a software that handled that for you, assuming the standard firmware was installed on your card: [https://code.google.com/p/emutrix/](https://code.google.com/p/emutrix/)
I haven't updated that program in a while, not sure if it works.

---

### Post by bnilsson on 2013-03-23
Hi,

I have iterated the Playback 0202 L/R connection thru all values, with all levels I could find set to 100%. No output.
Yes, I did disable the on-board audio (ATI Radeon HDA) so now alsamixer only sees my mobo HDMI and the EM-U card.
Emutrix works, but since the item labeling in the GUI is not the exactly same as what I see in alsamixer, I am not sure how much help it gives when I haven't grasped the principles of EMU1010/0202 yet.
I still have a feeling that I may have set the output (Playback?) side correctly, but that the input (Capture?) side plays a role I not yet understand. After all, I think I have understood that the 1010 is really a mixer, and should be handled accordingly.

I will now boot up my Win7 again and play with the Patchmix DSP program for a while, maybe that will give me a hint about the principles that I can transfer to the Ubuntu environment.

---

### Post by bnilsson on 2013-03-23
The Windows Patchmix DSP didn't really make me any wiser. If I defined the EMU as the default "Sound card" in Windows, I could get a signal into a Patchmix DSP WAVE 1/2 strip, but not if I used the HDMI as default sound. 

Ok, assuming if it is necessary to set the alsamixer Capture to channel the signal into the 1010 mixer to get anything out, what is the name of the input? There is no WAVE in the alsamixer list.

In alsamixer Capture, there are DSP 0-15 and DSP A-F sockets.
They can be connected to:
Silence
Dock [Mic L/R, ADC(1-3) L/R]
0202 [ADC L/R, SPDIF L/R]
ADAT 0-7
DSP 0-31

In alsamixer Playback, there are 0202 L/R, ADAT 0-7 and SPDIF L/R sockets.
Each of them can be connected to the same entries as the Capture.

Translation from Windows Patchmix DSP WAVE 1/2 to alsamix lingo would be greatly appreciated.

Where can I find detailed docs on the emu10k1 driver? Have googled, have not found much.

---

### Post by bnilsson on 2013-03-24
dmesg says about emu:

[   14.751909] snd_emu10k1 0000:07:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.751970] emu1010: Special config.
[   14.752073] emu1010: EMU_HANA_ID = 0x3f
[   14.752074] emu1010: filename emu/emu1010b.fw testing
[   18.134822] emu1010: Hana Firmware loaded
[   18.134874] emu1010: Hana version: 1.6
[   18.134936] emu1010: Card options = 0x1
[   18.134962] emu1010: Card options = 0x1
[   18.135526] emu1010: Card options3 = 0x1
...
[   18.160671] Audigy2 value: Special config.
[   18.161132] EMU outputs on
[   18.161134] EMU2 inputs on



"Special config" looks alarming. Can someone explain?

---

### Post by cpolymeris on 2013-03-25
> **bnilsson said:**
> dmesg says about emu:

[   14.751909] snd_emu10k1 0000:07:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.751970] emu1010: Special config.
[   14.752073] emu1010: EMU_HANA_ID = 0x3f
[   14.752074] emu1010: filename emu/emu1010b.fw testing
[   18.134822] emu1010: Hana Firmware loaded
[   18.134874] emu1010: Hana version: 1.6
[   18.134936] emu1010: Card options = 0x1
[   18.134962] emu1010: Card options = 0x1
[   18.135526] emu1010: Card options3 = 0x1
...
[   18.160671] Audigy2 value: Special config.
[   18.161132] EMU outputs on
[   18.161134] EMU2 inputs on



"Special config" looks alarming. Can someone explain?

So... I dug out the old soundcard and installed it on my system, no issues getting sound to work. (I am on Debian)
My dmesg reads:[INDENT][FONT=lucida console][    5.472994] snd_emu10k1 0000:03:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    5.473201] emu1010: Special config.
[    5.473335] emu1010: EMU_HANA_ID = 0x7f
[    5.473340] emu1010: **filename emu/hana.fw testing**
[   13.796065] emu1010: Hana Firmware loaded
[   13.796116] emu1010: **Hana version: 3.4**
[   13.796176] emu1010: Card options = 0x1
[   13.796202] emu1010: Card options = 0x1
[   13.796725] emu1010: Card options3 = 0x1[/FONT]
[/INDENT]


Note that: a) it uses a different firmware (different version of the card?) and (b) the version number is higher (whatever that means). I get no messages related to "Audigy".

The file[FONT=lucida console]/var/lib/alsa/asound.state[/FONT]stores your mixer settings. I have attached my own, so you can diff it with yours. Note that the first section is the state of the built-in card. The relevant section starts at[INDENT][FONT=lucida console]**state.EMU1010 {**
[/FONT][/INDENT]
[FONT=lucida console][FONT=arial]Alternatively, you might want to delete that file or replace it with mine.

asound.state:
[/FONT][/FONT]```

state.SB {
    control.1 {
        iface MIXER
        name 'Front Playback Volume'
        value.0 42
        value.1 42
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 42'
            dbmin -6300
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.2 {
        iface MIXER
        name 'Front Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.3 {
        iface MIXER
        name 'Surround Playback Volume'
        value.0 42
        value.1 42
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 42'
            dbmin -6300
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.4 {
        iface MIXER
        name 'Surround Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.5 {
        iface MIXER
        name 'Center Playback Volume'
        value 42
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 42'
            dbmin -6300
            dbmax 0
            dbvalue.0 0
        }
    }
    control.6 {
        iface MIXER
        name 'Center Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.7 {
        iface MIXER
        name 'LFE Playback Volume'
        value 42
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 42'
            dbmin -6300
            dbmax 0
            dbvalue.0 0
        }
    }
    control.8 {
        iface MIXER
        name 'LFE Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.9 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 23
        value.1 23
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.10 {
        iface MIXER
        name 'PCM Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.11 {
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 42
        value.1 42
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 42'
            dbmin -6300
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.12 {
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.13 {
        iface MIXER
        name 'Loopback Mixing'
        value Enabled
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Disabled
            item.1 Enabled
        }
    }
    control.14 {
        iface MIXER
        name 'Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -1650
            dbmax 3000
            dbvalue.0 -1650
            dbvalue.1 -1650
        }
    }
    control.15 {
        iface MIXER
        name 'Capture Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.16 {
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -1650
            dbmax 3000
            dbvalue.0 -1650
            dbvalue.1 -1650
        }
    }
    control.17 {
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.18 {
        iface MIXER
        name 'Input Source'
        value 'Front Mic'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 'Rear Mic'
            item.1 'Front Mic'
            item.2 Line
            item.3 'Stereo Mixer'
        }
    }
    control.19 {
        iface MIXER
        name 'Rear Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.20 {
        iface MIXER
        name 'Rear Mic Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.21 {
        iface MIXER
        name 'Front Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 -3450
            dbvalue.1 -3450
        }
    }
    control.22 {
        iface MIXER
        name 'Front Mic Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.23 {
        iface MIXER
        name 'Line Playback Volume'
        value.0 31
        value.1 31
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 31'
            dbmin -3450
            dbmax 1200
            dbvalue.0 1200
            dbvalue.1 1200
        }
    }
    control.24 {
        iface MIXER
        name 'Line Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.25 {
        iface MIXER
        name 'Rear Mic Boost Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3075
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.26 {
        iface MIXER
        name 'Front Mic Boost Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 3'
            dbmin 0
            dbmax 3075
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.27 {
        iface MIXER
        name 'Independent HP'
        value OFF
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 OFF
            item.1 ON
        }
    }
    control.28 {
        iface MIXER
        name 'Smart 5.1'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.29 {
        iface MIXER
        name 'Dynamic Power-Control'
        value Disabled
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Disabled
            item.1 Enabled
        }
    }
    control.30 {
        iface MIXER
        name 'Master Playback Volume'
        value 40
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 42'
            dbmin -6300
            dbmax 0
            dbvalue.0 -300
        }
    }
    control.31 {
        iface MIXER
        name 'Master Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.32 {
        iface MIXER
        name 'Digital Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 120'
            tlv '0000000100000008fffff44800000032'
            dbmin -3000
            dbmax 3000
            dbvalue.0 -3000
            dbvalue.1 -3000
        }
    }
}
state.EMU1010 {
    control.1 {
        iface MIXER
        name 'PCM Front Playback Volume'
        value.0 100
        value.1 100
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.2 {
        iface MIXER
        name 'PCM Surround Playback Volume'
        value.0 100
        value.1 100
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.3 {
        iface MIXER
        name 'PCM Side Playback Volume'
        value.0 100
        value.1 100
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.4 {
        iface MIXER
        name 'PCM Center Playback Volume'
        value 100
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
        }
    }
    control.5 {
        iface MIXER
        name 'PCM LFE Playback Volume'
        value 100
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
        }
    }
    control.6 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 100
        value.1 100
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.7 {
        iface MIXER
        name 'Synth Playback Volume'
        value.0 100
        value.1 100
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.8 {
        iface MIXER
        name 'PCM Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.9 {
        iface MIXER
        name 'Synth Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.10 {
        iface MIXER
        name 'EMU Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.11 {
        iface MIXER
        name 'Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.12 {
        iface MIXER
        name 'Mic Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.13 {
        iface MIXER
        name 'CD Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.14 {
        iface MIXER
        name 'CD Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.15 {
        iface MIXER
        name 'IEC958 Optical Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.16 {
        iface MIXER
        name 'IEC958 Optical Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.17 {
        iface MIXER
        name 'Line Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.18 {
        iface MIXER
        name 'Line Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.19 {
        iface MIXER
        name 'Analog Mix Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.20 {
        iface MIXER
        name 'Analog Mix Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.21 {
        iface MIXER
        name 'Aux Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.22 {
        iface MIXER
        name 'Aux Capture Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.23 {
        iface MIXER
        name 'Front Playback Volume'
        value.0 100
        value.1 100
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.24 {
        iface MIXER
        name 'Surround Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.25 {
        iface MIXER
        name 'Center Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
        }
    }
    control.26 {
        iface MIXER
        name 'LFE Playback Volume'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
        }
    }
    control.27 {
        iface MIXER
        name 'Side Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -9999999
            dbvalue.1 -9999999
        }
    }
    control.28 {
        iface MIXER
        name 'Tone Control - Bass'
        value.0 20
        value.1 20
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 40'
        }
    }
    control.29 {
        iface MIXER
        name 'Tone Control - Treble'
        value.0 20
        value.1 20
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 40'
        }
    }
    control.30 {
        iface MIXER
        name 'Tone Control - Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.31 {
        iface MIXER
        name 'Master Playback Volume'
        value 15
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 100'
            dbmin -9999999
            dbmax 0
            dbvalue.0 -3400
        }
    }
    control.32 {
        iface MIXER
        name 'IEC958 Optical Raw Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.33 {
        iface PCM
        device 2
        name 'Captured FX8010 Outputs'
        value.0 false
        value.1 false
        value.2 false
        value.3 false
        value.4 false
        value.5 false
        value.6 false
        value.7 false
        value.8 false
        value.9 false
        value.10 false
        value.11 false
        value.12 false
        value.13 false
        value.14 false
        value.15 false
        value.16 false
        value.17 false
        value.18 false
        value.19 false
        value.20 false
        value.21 false
        value.22 false
        value.23 false
        value.24 false
        value.25 false
        value.26 false
        value.27 false
        value.28 false
        value.29 false
        value.30 false
        value.31 false
        value.32 true
        value.33 true
        value.34 true
        value.35 true
        value.36 true
        value.37 true
        value.38 true
        value.39 true
        value.40 true
        value.41 true
        value.42 true
        value.43 true
        value.44 true
        value.45 true
        value.46 true
        value.47 true
        value.48 true
        value.49 true
        value.50 true
        value.51 true
        value.52 true
        value.53 true
        value.54 true
        value.55 true
        value.56 true
        value.57 true
        value.58 true
        value.59 true
        value.60 true
        value.61 true
        value.62 true
        value.63 true
        comment {
            access 'read write'
            type BOOLEAN
            count 64
        }
    }
    control.34 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.35 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 1
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.36 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 2
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.37 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 3
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.38 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 4
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.39 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 5
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.40 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 6
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.41 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 7
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.42 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 8
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.43 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 9
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.44 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 10
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.45 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 11
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.46 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 12
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.47 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 13
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.48 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 14
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.49 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 15
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.50 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 16
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.51 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 17
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.52 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 18
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.53 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 19
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.54 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 20
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.55 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 21
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.56 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 22
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.57 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 23
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.58 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 24
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.59 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 25
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.60 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 26
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.61 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 27
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.62 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 28
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.63 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 29
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.64 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 30
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.65 {
        iface PCM
        name 'EMU10K1 PCM Send Routing'
        index 31
        value.0 0
        value.1 1
        value.2 2
        value.3 3
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 0
        value.9 1
        value.10 2
        value.11 3
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 1
        value.18 2
        value.19 3
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 63'
        }
    }
    control.66 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.67 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 1
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.68 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 2
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.69 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 3
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.70 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 4
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.71 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 5
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.72 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 6
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.73 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 7
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.74 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 8
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.75 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 9
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.76 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 10
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.77 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 11
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.78 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 12
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.79 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 13
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.80 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 14
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.81 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 15
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.82 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 16
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.83 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 17
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.84 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 18
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.85 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 19
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.86 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 20
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.87 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 21
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.88 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 22
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.89 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 23
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.90 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 24
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.91 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 25
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.92 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 26
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.93 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 27
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.94 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 28
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.95 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 29
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.96 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 30
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.97 {
        iface PCM
        name 'EMU10K1 PCM Send Volume'
        index 31
        value.0 255
        value.1 255
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        value.8 255
        value.9 0
        value.10 0
        value.11 0
        value.12 0
        value.13 0
        value.14 0
        value.15 0
        value.16 0
        value.17 255
        value.18 0
        value.19 0
        value.20 0
        value.21 0
        value.22 0
        value.23 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 24
            range '0 - 255'
        }
    }
    control.98 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.99 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 1
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.100 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 2
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.101 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 3
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.102 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 4
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.103 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 5
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.104 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 6
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.105 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 7
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.106 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 8
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.107 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 9
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.108 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 10
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.109 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 11
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.110 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 12
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.111 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 13
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.112 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 14
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.113 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 15
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.114 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 16
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.115 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 17
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.116 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 18
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.117 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 19
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.118 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 20
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.119 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 21
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.120 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 22
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.121 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 23
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.122 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 24
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.123 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 25
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.124 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 26
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.125 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 27
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.126 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 28
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.127 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 29
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.128 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 30
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.129 {
        iface PCM
        name 'EMU10K1 PCM Volume'
        index 31
        value.0 65535
        value.1 65535
        value.2 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 3
            range '0 - 65535'
        }
    }
    control.130 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        value.0 0
        value.1 1
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.131 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 1
        value.0 1
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.132 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 2
        value.0 2
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.133 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 3
        value.0 3
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.134 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 4
        value.0 4
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.135 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 5
        value.0 5
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.136 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 6
        value.0 6
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.137 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 7
        value.0 7
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.138 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 8
        value.0 8
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.139 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 9
        value.0 9
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.140 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 10
        value.0 10
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.141 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 11
        value.0 11
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.142 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 12
        value.0 12
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.143 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 13
        value.0 13
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.144 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 14
        value.0 14
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.145 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Routing'
        index 15
        value.0 15
        value.1 0
        value.2 13
        value.3 14
        value.4 60
        value.5 61
        value.6 62
        value.7 63
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 63'
        }
    }
    control.146 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.147 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 1
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.148 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 2
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.149 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 3
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.150 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 4
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.151 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 5
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.152 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 6
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.153 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 7
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.154 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 8
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.155 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 9
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.156 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 10
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.157 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 11
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.158 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 12
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.159 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 13
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.160 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 14
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.161 {
        iface PCM
        device 3
        name 'Multichannel PCM Send Volume'
        index 15
        value.0 255
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access 'read write inactive'
            type INTEGER
            count 8
            range '0 - 255'
        }
    }
    control.162 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.163 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 1
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.164 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 2
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.165 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 3
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.166 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 4
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.167 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 5
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.168 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 6
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.169 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 7
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.170 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 8
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.171 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 9
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.172 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 10
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.173 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 11
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.174 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 12
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.175 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 13
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.176 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 14
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.177 {
        iface PCM
        device 3
        name 'Multichannel PCM Volume'
        index 15
        value 65535
        comment {
            access 'read write inactive'
            type INTEGER
            count 1
            range '0 - 65535'
        }
    }
    control.178 {
        iface PCM
        name 'IEC958 Playback Mask'
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.179 {
        iface PCM
        name 'IEC958 Playback Mask'
        index 1
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.180 {
        iface PCM
        name 'IEC958 Playback Mask'
        index 2
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.181 {
        iface PCM
        name 'IEC958 Playback Default'
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.182 {
        iface PCM
        name 'IEC958 Playback Default'
        index 1
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.183 {
        iface PCM
        name 'IEC958 Playback Default'
        index 2
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.184 {
        iface MIXER
        name 'Dock DAC1 Left Playback Enum'
        value 'DSP 0'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.185 {
        iface MIXER
        name 'Dock DAC1 Right Playback Enum'
        value 'DSP 1'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.186 {
        iface MIXER
        name 'Dock DAC2 Left Playback Enum'
        value 'DSP 2'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.187 {
        iface MIXER
        name 'Dock DAC2 Right Playback Enum'
        value 'DSP 3'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.188 {
        iface MIXER
        name 'Dock DAC3 Left Playback Enum'
        value 'DSP 4'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.189 {
        iface MIXER
        name 'Dock DAC3 Right Playback Enum'
        value 'DSP 5'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.190 {
        iface MIXER
        name 'Dock DAC4 Left Playback Enum'
        value 'DSP 6'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.191 {
        iface MIXER
        name 'Dock DAC4 Right Playback Enum'
        value 'DSP 7'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.192 {
        iface MIXER
        name 'Dock Phones Left Playback Enum'
        value 'DSP 0'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.193 {
        iface MIXER
        name 'Dock Phones Right Playback Enum'
        value 'DSP 1'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.194 {
        iface MIXER
        name 'Dock SPDIF Left Playback Enum'
        value 'DSP 0'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.195 {
        iface MIXER
        name 'Dock SPDIF Right Playback Enum'
        value 'DSP 1'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.196 {
        iface MIXER
        name '1010 SPDIF Left Playback Enum'
        value 'DSP 0'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.197 {
        iface MIXER
        name '1010 SPDIF Right Playback Enum'
        value 'DSP 1'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.198 {
        iface MIXER
        name '0202 DAC Left Playback Enum'
        value 'DSP 7'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.199 {
        iface MIXER
        name '0202 DAC Right Playback Enum'
        value 'DSP 1'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.200 {
        iface MIXER
        name '1010 ADAT 0 Playback Enum'
        value 'DSP 0'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.201 {
        iface MIXER
        name '1010 ADAT 1 Playback Enum'
        value 'DSP 1'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.202 {
        iface MIXER
        name '1010 ADAT 2 Playback Enum'
        value 'DSP 2'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.203 {
        iface MIXER
        name '1010 ADAT 3 Playback Enum'
        value 'DSP 3'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.204 {
        iface MIXER
        name '1010 ADAT 4 Playback Enum'
        value 'DSP 4'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.205 {
        iface MIXER
        name '1010 ADAT 5 Playback Enum'
        value 'DSP 5'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.206 {
        iface MIXER
        name '1010 ADAT 6 Playback Enum'
        value 'DSP 6'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.207 {
        iface MIXER
        name '1010 ADAT 7 Playback Enum'
        value 'DSP 7'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.208 {
        iface MIXER
        name 'DSP 0 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.209 {
        iface MIXER
        name 'DSP 1 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.210 {
        iface MIXER
        name 'DSP 2 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.211 {
        iface MIXER
        name 'DSP 3 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.212 {
        iface MIXER
        name 'DSP 4 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.213 {
        iface MIXER
        name 'DSP 5 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.214 {
        iface MIXER
        name 'DSP 6 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.215 {
        iface MIXER
        name 'DSP 7 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.216 {
        iface MIXER
        name 'DSP 8 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.217 {
        iface MIXER
        name 'DSP 9 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.218 {
        iface MIXER
        name 'DSP A Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.219 {
        iface MIXER
        name 'DSP B Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.220 {
        iface MIXER
        name 'DSP C Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.221 {
        iface MIXER
        name 'DSP D Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.222 {
        iface MIXER
        name 'DSP E Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.223 {
        iface MIXER
        name 'DSP F Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.224 {
        iface MIXER
        name 'DSP 10 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.225 {
        iface MIXER
        name 'DSP 11 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.226 {
        iface MIXER
        name 'DSP 12 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.227 {
        iface MIXER
        name 'DSP 13 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.228 {
        iface MIXER
        name 'DSP 14 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.229 {
        iface MIXER
        name 'DSP 15 Capture Enum'
        value Silence
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 Silence
            item.1 'Dock Mic A'
            item.2 'Dock Mic B'
            item.3 'Dock ADC1 Left'
            item.4 'Dock ADC1 Right'
            item.5 'Dock ADC2 Left'
            item.6 'Dock ADC2 Right'
            item.7 'Dock ADC3 Left'
            item.8 'Dock ADC3 Right'
            item.9 '0202 ADC Left'
            item.10 '0202 ADC Right'
            item.11 '0202 SPDIF Left'
            item.12 '0202 SPDIF Right'
            item.13 'ADAT 0'
            item.14 'ADAT 1'
            item.15 'ADAT 2'
            item.16 'ADAT 3'
            item.17 'ADAT 4'
            item.18 'ADAT 5'
            item.19 'ADAT 6'
            item.20 'ADAT 7'
            item.21 'DSP 0'
            item.22 'DSP 1'
            item.23 'DSP 2'
            item.24 'DSP 3'
            item.25 'DSP 4'
            item.26 'DSP 5'
            item.27 'DSP 6'
            item.28 'DSP 7'
            item.29 'DSP 8'
            item.30 'DSP 9'
            item.31 'DSP 10'
            item.32 'DSP 11'
            item.33 'DSP 12'
            item.34 'DSP 13'
            item.35 'DSP 14'
            item.36 'DSP 15'
            item.37 'DSP 16'
            item.38 'DSP 17'
            item.39 'DSP 18'
            item.40 'DSP 19'
            item.41 'DSP 20'
            item.42 'DSP 21'
            item.43 'DSP 22'
            item.44 'DSP 23'
            item.45 'DSP 24'
            item.46 'DSP 25'
            item.47 'DSP 26'
            item.48 'DSP 27'
            item.49 'DSP 28'
            item.50 'DSP 29'
            item.51 'DSP 30'
            item.52 'DSP 31'
        }
    }
    control.230 {
        iface MIXER
        name 'ADC1 14dB PAD Audio Dock Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.231 {
        iface MIXER
        name 'ADC2 14dB PAD Audio Dock Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.232 {
        iface MIXER
        name 'ADC3 14dB PAD Audio Dock Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.233 {
        iface MIXER
        name 'ADC1 14dB PAD 0202 Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.234 {
        iface MIXER
        name 'DAC1 Audio Dock 14dB PAD Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.235 {
        iface MIXER
        name 'DAC2 Audio Dock 14dB PAD Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.236 {
        iface MIXER
        name 'DAC3 Audio Dock 14dB PAD Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.237 {
        iface MIXER
        name 'DAC4 Audio Dock 14dB PAD Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.238 {
        iface MIXER
        name 'DAC1 0202 14dB PAD Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.239 {
        iface MIXER
        name 'Clock Internal Rate'
        value '48000'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 '44100'
            item.1 '48000'
            item.2 SPDIF
            item.3 ADAT
        }
    }
}


```[FONT=lucida console][FONT=arial]
[/FONT]
[/FONT]

---

### Post by cpolymeris on 2013-03-25
> **bnilsson said:**
> The Windows Patchmix DSP didn't really make me any wiser. If I defined the EMU as the default "Sound card" in Windows, I could get a signal into a Patchmix DSP WAVE 1/2 strip, but not if I used the HDMI as default sound. 

Ok, assuming if it is necessary to set the alsamixer Capture to channel the signal into the 1010 mixer to get anything out, what is the name of the input? There is no WAVE in the alsamixer list.

In alsamixer Capture, there are DSP 0-15 and DSP A-F sockets.
They can be connected to:
Silence
Dock [Mic L/R, ADC(1-3) L/R]
0202 [ADC L/R, SPDIF L/R]
ADAT 0-7
DSP 0-31

In alsamixer Playback, there are 0202 L/R, ADAT 0-7 and SPDIF L/R sockets.
Each of them can be connected to the same entries as the Capture.


My emutrix and alsamixer 0202 ADC configuration (which are the same thing, of course):

 [ATTACH=CONFIG]240549[/ATTACH]

---

### Post by bnilsson on 2013-03-26
Thanks for the files and screenshot.

However, before I tried the alsa state file I borrowed a EMU 1010 PCI (not PCIe) from a friend and connected it to my 0202 board.
It was not difficult to get sound from this combination, I just used your emutrix screenshot.
Didn't work well with 96kHz rate, but that is another story.

I put the 1010PCIe back and got no sound using the same configuration.
I applied your asound.state file, same thing.
I begin to suspect that my new EMU1010 PCIe is different in some way. New firmware?
Should I file a bug?

---

