---
title: "Nvidia tv-out Geforce Ti500?"
date: 2006-07-19
forum: Multimedia &amp; Video
---

### Post by Vilhelmo on 2006-07-19
Hi! 
I have searched around the forum for some time now and cant find any thread about this. 
I have a geforce3 Ti500, (I know; old.) trying to make tv-out. Problem is it only supports one screen at a time. 
From xorg.log: 
```
(WW) NVIDIA(1): There are only 1 CRTCs available, trimming display device list
(WW) NVIDIA(1):     from "TV-0" to "".
```

So I guess I can either use the tv or the monitor. 

I tried nvtv, and it worked, but not so good. Half of my screen was below the television, ie the screen didn't fit inside the TV. 
I played around some in nvtv and now the list with resolutions is empty, and i can't get anything on the tv-screen any more. What have I done? So my qustion kind of was, is there any easy way to know the right resolution and refreshrates to my tv so i can get a picture, except with nvtv?

---

### Post by ManfredU on 2006-08-20
Hi,

I get similiar error messages when I try to use all three connectors of my card, which has got two VGA connectors and on TV-Out. I want to connect two monitors and one tv, but I can't get it to work. The message in the log is:

There are only 2 CRTCs available, trimming display device list from "TV-0" to "".

Grafics Adapter: NVIDIA GPU GeForce4 MX Integrated GPU
Driver: 1.0-8762

```

(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen[0]" (0)
(**) |  |-->Monitor "Monitor[0]"
(**) |  |-->Device "Device[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |  |-->Monitor "Monitor[1]"
(**) |  |-->Device "Device[1]"
(**) |-->Screen "Screen[2]" (2)
(**) |  |-->Monitor "Monitor[2]"
(**) |  |-->Device "Device[2]"

[...]

(II) NVIDIA X Driver 1.0-8762 Mon May 15 13:09:21 PDT 2006

[...]

(--) NVIDIA(0): Connected display device(s) on GeForce4 MX Integrated GPU at
(--) NVIDIA(0): PCI:3:0:0:
(--) NVIDIA(0): ___ 48??-? (CRT-0)
(--) NVIDIA(0): ___ 48??-? (CRT-1)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): ___ 48??-? (CRT-0): 300.0 MHz maximum pixel clock
(--) NVIDIA(0): ___ 48??-? (CRT-1): 300.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 300.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Mode Validation Overrides for ___ 48??-? (CRT-0):
(II) NVIDIA(0): NoEdidMaxPClkCheck
(II) NVIDIA(0): Assigned Display Device: CRT-0

[...]

(--) NVIDIA(1): Connected display device(s) on GeForce4 MX Integrated GPU at
(--) NVIDIA(1): PCI:3:0:0:
(--) NVIDIA(1): ___ 48??-? (CRT-0)
(--) NVIDIA(1): ___ 48??-? (CRT-1)
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1): ___ 48??-? (CRT-0): 300.0 MHz maximum pixel clock
(--) NVIDIA(1): ___ 48??-? (CRT-1): 300.0 MHz maximum pixel clock
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 300.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): Assigned Display Device: CRT-1

[...]

(--) NVIDIA(2): Connected display device(s) on GeForce4 MX Integrated GPU at
(--) NVIDIA(2): PCI:3:0:0:
(--) NVIDIA(2): ___ 48??-? (CRT-0)
(--) NVIDIA(2): ___ 48??-? (CRT-1)
(--) NVIDIA(2): NVIDIA TV Encoder (TV-0)
(--) NVIDIA(2): ___ 48??-? (CRT-0): 300.0 MHz maximum pixel clock
(--) NVIDIA(2): ___ 48??-? (CRT-1): 300.0 MHz maximum pixel clock
(--) NVIDIA(2): NVIDIA TV Encoder (TV-0): 300.0 MHz maximum pixel clock
(--) NVIDIA(2): TV encoder: NVIDIA
(WW) NVIDIA(2): There are only 2 CRTCs available, trimming display device list
(WW) NVIDIA(2): from "TV-0" to "".
(II) NVIDIA(2): Assigned Display Device:

```


I would also be happy if it would be possible to use TV-0 instead of CRT-1 as second device.

Thanks,
Manfred

---

### Post by ManfredU on 2006-08-20
> **ManfredU said:**
> Hi,
I would also be happy if it would be possible to use TV-0 instead of CRT-1 as second device.


OK, found a way to make this work:

Option "ConnectedMonitor" "TV-0" is no longer supported. With Option "UseDisplayDevice "TV-0" TV-0 is used instead of CRT-1!

---

