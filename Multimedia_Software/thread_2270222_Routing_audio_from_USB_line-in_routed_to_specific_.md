---
title: "Routing audio from USB line-in routed to specific output?"
date: 2015-03-21
forum: Multimedia Software
---

### Post by Miche on 2015-03-21
Hi everyone, 

Thanks for having me here. Apologies if this is a repeated thread. 

I have 2 soundcards, built in and USB. I would like to specify the output of USB's line in, eg USB line in towards build in output or USB output. Using Pulse I can route the audio stream towards both ends as well as the sole USB, but it seems I cannot send it to the PC speakers. I'd like to see under 'playback' some sort of 'USB line in' so I can decide which output to use as it happens with eg Chrome. 

Also, Pulse window and System -> Sound are out of the screen and cannot be resized. 

Any suggestion greatly appreciated. 

I am on Ubuntu 14.04. Output of cat /proc/asound/cards:

```

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0444000 irq 45
 1 [Device         ]: USB-Audio - USB Sound Device
                      USB Sound Device at usb-0000:00:12.0-1, full speed
 2 [Generic_1      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0440000 irq 16
```

Michele

---

