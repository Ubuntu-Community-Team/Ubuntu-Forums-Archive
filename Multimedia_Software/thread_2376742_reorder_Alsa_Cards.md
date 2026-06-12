---
title: "reorder Alsa Cards?"
date: 2017-11-05
forum: Multimedia Software
---

### Post by bjlockie on 2017-11-05
I mostly have sound (Audacity works, vlc lets me set the output device :-)).
I can't get Flash to work.
Card 2 is my video card and I want sound to go through the HDMI.
I think I read that Flash is hard coded to use Card 0.
Is there any way of reordering the cards?

$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe100000 irq 16
 1 [C615           ]: USB-Audio - HD Webcam C615
                      HD Webcam C615 at usb-0000:00:12.2-4, high speed
 2 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe080000 irq 41
 3 [CX23885        ]: CX23885 - Conexant CX23885
                      Conexant CX23885 at cx23885[0]|`

---

### Post by bjlockie on 2017-11-05
I turned off Card 0 in the pulse audio volume control and it all works. :-)

---

