---
title: "How do I set up Jack"
date: 2008-01-02
forum: Multimedia Production
---

### Post by LostArt on 2008-01-02
How exactly do you set up Jack, I'm running Ubuntu gusty which I upgraded to Ubuntu studio right after installing it.

Here is my lspci -v I get this

l00:00.0 Host bridge: ATI Technologies Inc Unknown device 7831
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at ec000000 (32-bit, prefetchable) [size=64M]
        Memory at e8000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP PCI/AGP Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: e8100000-e81fffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at e8001000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at e8002000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at e8003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SMBus (rev 1a)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: 66MHz, medium devsel
        I/O ports at 8060 [size=16]
        Memory at e8004000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8070 [size=16]

00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342 (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=168
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: e8200000-e82fffff
        Prefetchable memory behind bridge: 40000000-43ffffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 11
        Memory at e8004400 (32-bit, non-prefetchable) [size=256]

00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 11
        Memory at e8004800 (32-bit, non-prefetchable) [size=256]

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 9200 IGP (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at e8100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e8120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:02.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7094
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at e8200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at a000 [size=256]
        Memory at e8210000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:04.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at e8211000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 40000000-43fff000 (prefetchable)
        Memory window 1: 44000000-47fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001


Any help would be nice, so far I can get Jack to start with [this tutorial]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/") but I get a ridiculous number of Xruns, any help would be greatly appreciated so I can :guitar:

---

### Post by temcat on 2008-01-03
> **LostArt said:**
> 

[skipped all the rest] 

Any help would be nice, so far I can get Jack to start with [this tutorial]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/") but I get a ridiculous number of Xruns, any help would be greatly appreciated so I can :guitar:

1) Do you have an -rt kernel installed?

2) Do you run Jack with "Realtime" enabled?

3) Have you set up realtime permissions for "audio" group and added yourself to this group?
Realtime permissions are set this way:
```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
```

4) Have you tried more modest settings for "Frames/Period"? Try 512, then go down from that level. Try increasing "Periods/Buffer" from 2 to 3.

---

### Post by TechZilla on 2008-01-03
your lspci -v looks fine, as in you should be able to run JACK

---

### Post by deadgobby on 2008-01-03
I my self do not use Ubie Studio. Yes, it is great and all the O/S can install them all at one shot. I found that just using Ubie and installing the components or software I want and behaves very nicely. I do not need to install the real time kernel to use jack to trigger off my midi keyboard of linux soft synths, rose garden, or even hydrogen. It can be a pain to install the software one by one. Yet, to not to deal with a head ache is worth it. I run Gusty and by doing my own manual install of programs. I have more control over I want to be done.
  It is like buying a cheap Yamaha or Casio with a  bunch of preset sounds and you have very little control over making your own sounds. There is no way to tweak the sound you want to canvas to express the sound you desire. Some have great results with Ubie studio. I the other hand did not. Not to be mean about Ubie studio. I think it is great that people use it. There is fans and not fans. Me being one of the not fans. 
 I am a analog guy and love to play with the slide and pan pots. I have more control over what I want to do and get results with each turn or slide with a simple turn of my hand. 
 In all it depends on what you want to paint and what you want to express. I have tried Musix and Studio 64. Both are Debian based. I found with sticking with Ubie and installing what I want to use a big difference. 
Gobby

---

### Post by LostArt on 2008-01-03
> **temcat said:**
> 1) Do you have an -rt kernel installed?

2) Do you run Jack with "Realtime" enabled?

3) Have you set up realtime permissions for "audio" group and added yourself to this group?
Realtime permissions are set this way:
```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
```

4) Have you tried more modest settings for "Frames/Period"? Try 512, then go down from that level. Try increasing "Periods/Buffer" from 2 to 3.

Let me check on the  -rt kernel

Yes I run with realtime enabled, I'll have to give number 3 a try and I'll get back to you on 4, I'll try what you said, but how exactly does frames/Period work, what does it do???

Thank you all so much for the help

---

### Post by LostArt on 2008-01-03
are only red xruns bad, or all xruns in general, are there any other ways to reduce them, I did everything you said temcat but it doesn't seem to be working

---

### Post by temcat on 2008-01-04
> **LostArt said:**
> 
how exactly does frames/Period work, what does it do???


It sets the buffer size. To quote the LAU Jack Howto, "The buffersize determines the latency between when the sound is received by jack and when it is sent to the pcm device (the card output)."

---

### Post by temcat on 2008-01-04
> **LostArt said:**
> are only red xruns bad, or all xruns in general, are there any other ways to reduce them, I did everything you said temcat but it doesn't seem to be working

All xruns are red,
All xruns are bad :-)

Try changing sample rate. If you currently use 44 kHz, try 48 kHz, and vice versa. 

Try playback only or record only mode (set in qjackctl parameters).

---

### Post by LostArt on 2008-01-04
ok I seemed to get it to work, by changing my sound card in the area in the left of the settings dialogue but now I can't get Ardour to record, nor audacity when I have jack enabled, but jack seems to run perfectly. I'll try as you said Temcat, as well as changing the settings in audacity/ardour, but the thing I don't understand is whey there are so many sound cards listed when I go to change them? Shouldn't there only be one, I have four seperated into two's by a line, I'll list my options later so you all can get a look. tyhank you for the help, I feel like I'm getting closer...

---

### Post by LostArt on 2008-01-05
ok so I hit the play button in Jack control, and got things working, and I get very few xruns, so far only one, but what does the transport state mean??

---

