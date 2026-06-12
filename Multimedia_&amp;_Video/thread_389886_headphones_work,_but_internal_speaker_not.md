---
title: "headphones work, but internal speaker not?"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by Mujaheiden on 2007-03-21
Tiny issue; I have a new pc, and after first running the built in windows, I repartitioned the HD, and put in Edgy Eft, next to a basic windows install, without any original shipped disk (I want some windows available for if i crash Ubuntu, and I have to ask my admin for help).

Strangely, I can remember that the native windows on first boot made some sounds, like the windows tinging, etc. But then I destoyed the NTFS by tryig to reparttion it, and now the current non-native windows doesnt have native sound, and neither does  Ubuntu. I plug in the headphones, i do have (headphone) sound.

So I think the pc has an internal speaker, but im not sure. It actually does beep on errors.

The PC is a [HP Compaq DX2200]("http://h18000.www1.hp.com/products/quickspecs/12426_div/12426_div.HTML#Technical%20Specifications%20-%20Audio"). 

I think sound is

```
$ lspci -v
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 725a
        Flags: bus master, slow devsel, latency 64, IRQ 177
        Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

and 

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So, am I right, should there be sound, or is there no speaker?

---

### Post by entropic_existence on 2007-03-22
I had an odd error several weeks ago where the speakers on my laptop stopped working for seemingly no reason. Messing around with alsa, reinstalling audio drivers... nothing worked but my headphones still worked and so of course would external speakers. After about a week it simply started working again by itself. Probably not related, although it was odd.

---

