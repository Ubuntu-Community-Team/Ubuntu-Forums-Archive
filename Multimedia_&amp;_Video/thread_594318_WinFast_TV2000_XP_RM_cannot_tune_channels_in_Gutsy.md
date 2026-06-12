---
title: "WinFast TV2000 XP RM cannot tune channels in Gutsy"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by cessna on 2007-10-27
Hi All,

I've read all of the other threads on WinFast TV2000 (analogue TV) card problems, but none match mine. Here's my problem...

I have been using a WinFast TV2000 (card 34) in an older AMD Athlon XP 2400+ system for about a year with Feisty (7.04), and it worked really well. It was recognised as card 34, tuner 51.

I've just bought a new AMD AM2 4800+ system with an ASUS M2A-VM HDMI motherboard to run Gutsy Gibbon on, and I've put the WinFast card into it as I want to get rid of the old Athlon system (it's starting to hang a couple of times a week). Everything works well, and the card is recognised correctly, but I can't tune any channels.

I've tried using scantv (comes with xawtv) to scan for channels, but it doesn't find any channels. I've also tried using g4vl and tvtime to scan for channels, but they can't find any either.

So, I'm not sure what's wrong. I suspect that it's either a kernel problem (maybe the driver for this card has gained a bug between Feisty and Gutsy??), or possibly it's something with the motherboard. There is some weird **"i2c"** error which occurs after the bttv driver loads, but I don't know if this is related to the problem or not.

Does anyone have any ideas what might be wrong? Has anyone else got this card working correctly in Gutsy?

Here's the dump from /var/log/messages if that helps anyone work out my problem. Thanks in advance.

Dean


Oct 27 17:22:37 amd64 logger: Loading tuner probe=1
Oct 27 17:22:37 amd64 logger: Loading msp3400 debug=2
Oct 27 17:22:37 amd64 logger: Loading bttv pll=1 card=34 tuner=51 autoload=1 bttv_verbose=2 gbuffers=32 vbibufs=32
Oct 27 17:22:37 amd64 kernel: [  160.793218] bttv: driver version 0.9.17 loaded
Oct 27 17:22:37 amd64 kernel: [  160.793224] bttv: using 8 buffers with 2080k (520 pages) each for capture
Oct 27 17:22:37 amd64 kernel: [  160.793543] bttv: Bt8xx card found (0).
Oct 27 17:22:37 amd64 kernel: [  160.793556] bttv0: Bt878 (rev 17) at 0000:03:06.0, irq: 21, latency: 64, mmio: 0xfdfff000
Oct 27 17:22:37 amd64 kernel: [  160.793572] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
Oct 27 17:22:37 amd64 kernel: [  160.793574] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
Oct 27 17:22:37 amd64 kernel: [  160.794704] i2c-adapter i2c-1: Invalid probe address 0xfffe
Oct 27 17:22:37 amd64 kernel: [  160.798790] bttv0: using tuner=51
Oct 27 17:22:37 amd64 kernel: [  160.799315] bttv0: i2c: checking for MSP34xx @ 0x80... not found
Oct 27 17:22:37 amd64 kernel: [  160.799916] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
Oct 27 17:22:37 amd64 kernel: [  160.800808] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
Oct 27 17:22:37 amd64 kernel: [  160.801724] bttv0: i2c: checking for TDA9887 @ 0x86... not found
Oct 27 17:22:37 amd64 kernel: [  160.812124] bttv0: registered device video0
Oct 27 17:22:37 amd64 kernel: [  160.812801] bttv0: registered device vbi0
Oct 27 17:22:37 amd64 kernel: [  160.813408] bttv0: registered device radio0
Oct 27 17:22:37 amd64 kernel: [  160.814003] bttv0: PLL: 28636363 => 35468950 . ok
Oct 27 17:22:37 amd64 kernel: [  160.823017] input: bttv IR (card=34) as /class/input/input7

---

### Post by cessna on 2007-10-28
> **cessna said:**
> Hi All,

I've read all of the other threads on WinFast TV2000 (analogue TV) card problems, but none match mine. Here's my problem...

I have been using a WinFast TV2000 (card 34) in an older AMD Athlon XP 2400+ system for about a year with Feisty (7.04), and it worked really well. It was recognised as card 34, tuner 51.

I've just bought a new AMD AM2 4800+ system with an ASUS M2A-VM HDMI motherboard to run Gutsy Gibbon on, and I've put the WinFast card into it as I want to get rid of the old Athlon system (it's starting to hang a couple of times a week). Everything works well, and the card is recognised correctly, but I can't tune any channels.

I've tried using scantv (comes with xawtv) to scan for channels, but it doesn't find any channels. I've also tried using g4vl and tvtime to scan for channels, but they can't find any either.

So, I'm not sure what's wrong. I suspect that it's either a kernel problem (maybe the driver for this card has gained a bug between Feisty and Gutsy??), or possibly it's something with the motherboard. There is some weird **"i2c"** error which occurs after the bttv driver loads, but I don't know if this is related to the problem or not.

Does anyone have any ideas what might be wrong? Has anyone else got this card working correctly in Gutsy?

Here's the dump from /var/log/messages if that helps anyone work out my problem. Thanks in advance.

Dean


Oct 27 17:22:37 amd64 logger: Loading tuner probe=1
Oct 27 17:22:37 amd64 logger: Loading msp3400 debug=2
Oct 27 17:22:37 amd64 logger: Loading bttv pll=1 card=34 tuner=51 autoload=1 bttv_verbose=2 gbuffers=32 vbibufs=32
Oct 27 17:22:37 amd64 kernel: [  160.793218] bttv: driver version 0.9.17 loaded
Oct 27 17:22:37 amd64 kernel: [  160.793224] bttv: using 8 buffers with 2080k (520 pages) each for capture
Oct 27 17:22:37 amd64 kernel: [  160.793543] bttv: Bt8xx card found (0).
Oct 27 17:22:37 amd64 kernel: [  160.793556] bttv0: Bt878 (rev 17) at 0000:03:06.0, irq: 21, latency: 64, mmio: 0xfdfff000
Oct 27 17:22:37 amd64 kernel: [  160.793572] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
Oct 27 17:22:37 amd64 kernel: [  160.793574] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
Oct 27 17:22:37 amd64 kernel: [  160.794704] i2c-adapter i2c-1: Invalid probe address 0xfffe
Oct 27 17:22:37 amd64 kernel: [  160.798790] bttv0: using tuner=51
Oct 27 17:22:37 amd64 kernel: [  160.799315] bttv0: i2c: checking for MSP34xx @ 0x80... not found
Oct 27 17:22:37 amd64 kernel: [  160.799916] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
Oct 27 17:22:37 amd64 kernel: [  160.800808] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
Oct 27 17:22:37 amd64 kernel: [  160.801724] bttv0: i2c: checking for TDA9887 @ 0x86... not found
Oct 27 17:22:37 amd64 kernel: [  160.812124] bttv0: registered device video0
Oct 27 17:22:37 amd64 kernel: [  160.812801] bttv0: registered device vbi0
Oct 27 17:22:37 amd64 kernel: [  160.813408] bttv0: registered device radio0
Oct 27 17:22:37 amd64 kernel: [  160.814003] bttv0: PLL: 28636363 => 35468950 . ok
Oct 27 17:22:37 amd64 kernel: [  160.823017] input: bttv IR (card=34) as /class/input/input7

I re-installed my old disk with Ubuntu 7.04 installed on it, and now the WinFast card works as expected! So, it would seem that a bug has slipped into either the linux kernel or some of the modules which are supplied with Gutsy 7.10 which prevents some WinFast TV2000 cards from working correctly. 

This is good, as it means that the chipsets on the ASUS motherboard are well supported by Feisty, and therefore should work with Gutsy eventually. I'll report the bug to the right folks, and hopefully they can resolve it soon.

---

### Post by b4t3m4n on 2007-11-02
it would be nice if we could find a solution for this that doesn't involve using an old version of ubuntu :(

---

