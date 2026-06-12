---
title: "bug: TV Card Kworld 878RF /Jetway (card=78)"
date: 2010-06-21
forum: Mythbuntu
---

### Post by skolnick on 2010-06-21
Hi!

I just installed Mythbuntu 10.04 32 bits on an old PC of mine (Pentium 4 2.4 GHz, 768MB RAM). I have the subject kworld 878RF  card installed in this PC. The card was configured for watching TV and it works fine. Then I tried to configure the remote control. In the list of configurable remotes appears this card, but the remote control doesn't work. I tried to configure it and it failed. For me, the bug is not that it fails to configure the remote, since this remote control requires the lirc_gpio module, which is not present since kernel 2.6.16. The bug IMHO is that this card is still present in the lirc remotes list, despite not being supported since more that 3 years ago. However if anybody knows the trick to make it work with mythbuntu 10.04, I would appreciate it, because I currently own this card and the only thing that it's not working is the remote control.

Thanks!

---

### Post by aaalbatrosss on 2010-10-19
Please post "dmesg | grep bttv" to help you

---

### Post by Tux4 on 2011-08-16
> **aaalbatrosss said:**
> Please post "dmesg | grep bttv" to help you
I have a same type tv tuner also. 
I am trying to make it work on a 11.04 Ubuntu.

This the output of the ***dmesg | grep bttv***  command:

```
[   11.638341] bttv: driver version 0.9.18 loaded
[   11.638354] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   11.638362] bttv: Host bridge needs ETBF enabled.
[   11.644576] bttv: Bt8xx card found (0).
[   11.644614] bttv 0000:00:0d.0: enabling device (0004 -> 0006)
[   11.644642] bttv 0000:00:0d.0: PCI INT A -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[   11.644666] bttv0: Bt878 (rev 17) at 0000:00:0d.0, irq: 9, latency: 32, mmio: 0xe2000000
[   11.644708] bttv0: using: Jetway TV/Capture JW-TV878-FBK, Kworld KW-TV878RF [card=78,insmod option]
[   11.644736] bttv0: enabling ETBF (430FX/VP3 compatibilty)
[   11.644780] bttv0: gpio: en=00000000, out=00000000 in=003fffff [init]
[   11.645296] bttv0: tuner type=5
[   11.992816] bttv0: audio absent, no audio device found!
[   13.214289] bttv0: registered device video0
[   13.214571] bttv0: registered device vbi0
[   13.218335] bttv0: registered device radio0
[   13.218399] bttv0: PLL: 28636363 => 35468950 .. ok
```

---

### Post by nickrout on 2011-08-16
bugs should be filed at launchpad

---

