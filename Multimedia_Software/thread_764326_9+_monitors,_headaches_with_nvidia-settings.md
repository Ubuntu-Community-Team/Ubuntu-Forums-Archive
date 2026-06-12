---
title: "9+ monitors, headaches with nvidia-settings"
date: 2008-04-23
forum: Multimedia Software
---

### Post by wclark on 2008-04-23
I am building a _many_ screen desktop machine using xubuntu and Heron(beta) and i'm having some issues getting the nvidia tools to recognise more than one PCI-E video adapter.

I'm using an Asus P5K64-WS, a Nvidia Quadro 440 (Leadtek) and 3x Nvidia 8400GS (PCI-E) for a total of 10 Monitors outputs (although I only need 9 working) to display a series of pictures on each monitor accordig to a script (yay for python-foo!). 

The nvidia-settings tool only seems to see the quadro, and not any of the other cards in the system.

I suspect that i'm going to have to monkey up a custom xorg.conf - Is there an easier way of doing this ?

I've included the current xorg.conf and lspci output.

---

### Post by chaoslord on 2008-06-24
I have a similar problem with 4 monitors - My lspci shows 

0002:81:00.0 VGA compatible controller [0300]: nVidia Corporation G70GL [Quadro FX 4500] [10de:009d] (rev a1)

for my second card, but the nvidia-settings utility produces an xorg.conf file with 

BusID          "PCI:129:0:0"

I know 129=81 in bin-hex conversion, but what about the 0002: prefix? The 3rd and 4th monitors simply won't come on, and Ive tried switching the cards and monitors around, all work fine. I also have the external power connected to them. The first card is a quadro 4500 as well. 

Thanks.

---

### Post by sim-value on 2008-06-24
I dont see the Sanity here but free software makes insane anyway so go on ... (i would be happy with only one big screen)

---

### Post by chaoslord on 2008-06-25
I want it working so I can run my windows XP Virtual machine across 2 of the screens, and have the other 2 dedicated to the linux admin consoles I run. when you use it for work its nice to have a ton of screen space. :)

---

