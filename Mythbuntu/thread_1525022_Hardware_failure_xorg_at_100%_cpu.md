---
title: "Hardware failure? xorg at 100% cpu"
date: 2010-07-06
forum: Mythbuntu
---

### Post by percula on 2010-07-06
Hi All

Strange one. I have had a working Mythbuntu 10.4 box for sometime now. Today the frontend interface was frozen. I SSH'ed in and ran top, xorg was eating the CPU alive. I killed the frontend process and xorg settled down to normal.

Thinking that this might be a update issue, and no real way to downgrade the x related updates, I decided to go ahead and reinstall...

But with a fresh install of Mythbuntu 10.4 xorg is eating the CPU alive again with any GUI application be it mythfrontend, gedit, mplayer, etc, etc.

Since a fresh install is hosed too, the only thing I can think of is hardware failing. All the hardware is older, I am assuming the GPU is going.

Has anyone seen anything like this before?

---

### Post by ian dobson on 2010-07-06
Hi,

What do you need in your X log file (/var/log/X something log)?


Regards
Ian Dobson

---

### Post by percula on 2010-07-06
> **ian dobson said:**
> Hi,

What do you need in your X log file (/var/log/X something log)?


Regards
Ian Dobson

Hi Ian

Thanks for the reply.

The only thing I see in the xorg log that is abnormal are these lines...

```
(WW) Jul 06 01:50:08 NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000c558, 0x0000c558)
(WW) Jul 06 01:50:11 NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000ce10, 0x0000d060)
(WW) Jul 06 01:50:24 NVIDIA(0): WAIT (0, 6, 0x8000, 0x00001638, 0x00001638)
(WW) Jul 06 01:50:27 NVIDIA(0): WAIT (2, 6, 0x8000, 0x00001638, 0x00002140)
(WW) Jul 06 01:50:36 NVIDIA(0): WAIT (0, 6, 0x8000, 0x00005cb0, 0x00005cb0)
(WW) Jul 06 01:50:48 NVIDIA(0): WAIT (0, 6, 0x8000, 0x00002b74, 0x00002b74)
(WW) Jul 06 01:50:51 NVIDIA(0): WAIT (2, 6, 0x8000, 0x00002b74, 0x0000372c)
(WW) Jul 06 01:51:01 NVIDIA(0): WAIT (0, 6, 0x8000, 0x00006748, 0x00006748)
(WW) Jul 06 01:51:04 NVIDIA(0): WAIT (2, 6, 0x8000, 0x00006748, 0x00006bf8)
(WW) Jul 06 01:51:22 NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000ca14, 0x0000ca14)
(WW) Jul 06 01:51:25 NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000ca14, 0x0000cce8)
(WW) Jul 06 01:51:35 NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000ba10, 0x0000ba10)
(WW) Jul 06 01:51:38 NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000ba10, 0x0000bce4)
(WW) Jul 06 01:51:47 NVIDIA(0): WAIT (0, 6, 0x8000, 0x000007cc, 0x000007cc)
(WW) Jul 06 01:51:50 NVIDIA(0): WAIT (2, 7, 0x8000, 0x000007cc, 0x000007f8)
(WW) Jul 06 01:52:32 NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000b910, 0x0000b910)
(WW) Jul 06 01:52:35 NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000b910, 0x0000bc0c)
(WW) Jul 06 01:52:45 NVIDIA(0): WAIT (0, 6, 0x8000, 0x00000c34, 0x00000c34)
(WW) Jul 06 01:52:48 NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000c34, 0x00000f08)
(WW) Jul 06 01:52:58 NVIDIA(0): WAIT (0, 6, 0x8000, 0x00000938, 0x00000938)
(WW) Jul 06 01:53:01 NVIDIA(0): WAIT (2, 6, 0x8000, 0x00000938, 0x00000c34)
(WW) Jul 06 01:53:10 NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000b908, 0x0000b908)
(WW) Jul 06 01:53:13 NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000b908, 0x0000bc04)
(WW) Jul 06 01:53:23 NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000573c, 0x0000573c)
(WW) Jul 06 01:53:26 NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000573c, 0x00005ec8)
(WW) Jul 06 01:53:35 NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000c758, 0x0000c758)
(WW) Jul 06 01:53:38 NVIDIA(0): WAIT (2, 6, 0x8000, 0x0000c758, 0x0000cee4)
(WW) Jul 06 01:53:48 NVIDIA(0): WAIT (0, 6, 0x8000, 0x00008750, 0x00008750)
(WW) Jul 06 01:53:51 NVIDIA(0): WAIT (2, 6, 0x8000, 0x00008750, 0x00008edc)
(WW) Jul 06 01:54:01 NVIDIA(0): WAIT (0, 6, 0x8000, 0x0000c2fc, 0x0000c2fc)
```

---

### Post by ian dobson on 2010-07-06
Hi,

That doesn't look normal, but I can'r say what it means.

Maybe try reseating the RAM/CPU/Graphic card, Resetting the BIOS options to default, cleaning any dust out of the box.

Other than that I have no idea.

Regards
Ian Dobson

---

### Post by percula on 2010-07-06
> **ian dobson said:**
> Hi,

That doesn't look normal, but I can'r say what it means.

Maybe try reseating the RAM/CPU/Graphic card, Resetting the BIOS options to default, cleaning any dust out of the box.

Other than that I have no idea.

Regards
Ian Dobson

Thanks Ian

I did a fair amount of Googling this AM and have found lots of examples of this Wait "error" and it looks like this is a signal of a failing GPU.

I guess this is the kick in the rear I needed to go to a 9800 card.

Thanks for the help!

---

