---
title: "reroute audio to usb and name output channel"
date: 2009-11-20
forum: Multimedia Software
---

### Post by nafihsus on 2009-11-20
I am rerouting my amarok output to usb where I have a DAC converter for my high end hifi. To make it work Amarok (xine engine) needs the parameter plughw: <nn> in the stereo field. Here <nn> is the result of the command 

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa700000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfa010000 irq 17
 2 [default        ]: USB-Audio - USB Audio DAC   
                      Burr-Brown from TI               USB Audio DAC    at usb-0000:00:1a.1-1, full s

showing my USB DAC, in this case "2". The problem I have is that the number changes each time I boot and I have to reconfigure Amarok accordingly.  

Is there an option to give the output a fixed name and use this one in Amarok?

I am running Hardy.

---

