---
title: "Improving audio clarity"
date: 2011-09-22
forum: Multimedia Software
---

### Post by kaldor on 2011-09-22
Excuse me if this is redundant, but none of the small solutions I found when searching seemed to work for me.

I can't help but feel like the sound quality is slightly tinny on Ubuntu as compared to Windows 7. Windows 7 has a "deep" and clear feel to it, while it feels more harsh and tinny on Ubuntu. What's a possible solution to improve the clarity?

lspci:

```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc NI Caicos [AMD RADEON HD 6450]
01:00.1 Audio device: ATI Technologies Inc Device aa98
02:00.0 Network controller: Ralink corp. Device 5390
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

```

---

### Post by cornelis spronk on 2011-09-22
What do you use, headphones or speakers?

What is your soundcard?

I always thought the sound quality was mostly dependent of the sound device, not the operating system?

---

### Post by kaldor on 2011-09-22
> **cornelis spronk said:**
> What do you use, headphones or speakers?

What is your soundcard?

I always thought the sound quality was mostly dependent of the sound device, not the operating system?

I'm using logitech speakers + subwoofer. Soundcard seems to be a RealTek:

```
$ cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC888-VD

```

It's definitely lesser quality compared to Windows 7. I guess it sounds a bit flat.

---

### Post by tpprynn on 2011-09-22
Is this for music? The graphic equaliser in Banshee is pretty good if you hadn't noticed and activated it - it turned my initially muddy-sounding Logitech speakers to a very pleasant hi-fi sound. I use the 'Soft' preset.

---

### Post by kaldor on 2011-09-22
> **tpprynn said:**
> Is this for music? The graphic equaliser in Banshee is pretty good if you hadn't noticed and activated it - it turned my initially muddy-sounding Logitech speakers to a very pleasant hi-fi sound. I use the 'Soft' preset.

It's in everything requiring sound. YouTube, games, music, etc.

Edit for more info:

Dunno if it matters or not, but when I am on Windows 7 I can make the audio go a *lot* higher than on Ubuntu. I have the audio bar on roughly 80% listening to music right now. On Windows 7, this same volume level would be only about a 20 (out of 100) on the audio slider. Max volume on the slider would only be about 40-50% volume on Win7; I can still crank it up on the speakers itself, but just thought I would include this bit of info.

---

### Post by cornelis spronk on 2011-09-22
If I understand you correctly, you are using the audio output from your motherboard.  Most older boards have rubbish sound in my opinion.  Some of the newer boards are somewhat better, but none that I know are near as good as some PCI or USB external sound cards.

I look for clarity in sound.  This means very low distortion. I am using a USB Behringer UCA202 external sound card, which for its low price gives amazing clarity of sound.  You have to use the RCA output, which comes directly off the DAC converter.  The headphone audio amplifier is very poor.  Do not buy this for headphone use unless you are willing to modify it as suggested in the website below.

If you feed this into your computer speaker system, you will not be disappointed.

See:

[http://nwavguy.blogspot.com/2011/02/behringer-uca202-review.html](http://nwavguy.blogspot.com/2011/02/behringer-uca202-review.html)

---

