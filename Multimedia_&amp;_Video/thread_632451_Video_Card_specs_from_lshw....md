---
title: "Video Card specs from lshw..."
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by stanleypane on 2007-12-05
I've been toying around with a new graphics card for my Ubuntu box and I'm a bit confused at to whether it is running at the speeds listed on the video card specs.

I've got a Gigabyte 7600gt with 256MB (128 bit) that should have a clock rate of 560MHz (700MHz memory).

When I do an lshw, the stats don't seem to match. How can I be sure my video card is operating at full capacity? Below is the graphics adapter section of my lshw ouput. My comments are in red.
```

           *-display
                description: VGA compatible controller
                product: G70 [GeForce 7600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 64 bits [COLOR="Red"](128 bits???)[/COLOR]
                clock: 33MHz [COLOR="Red"](560 MHz???)[/COLOR]
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: iomemory:fd000000-fdffffff iomemory:d0000000-dfffffff
 iomemory:fc000000-fcffffff ioport:bc00-bc7f irq:16

```

---

### Post by stanleypane on 2007-12-05
I think I may have found what I'm looking for.

I did an apt-get on a program called nvclock. It seems to report the correct speeds.

I'd still like to find out how I can test the performance of my graphics card on a linux box. I remember running things like SiSoft Sandra and various other programs to test performance on my Windows box. Anything similar out there for Ubuntu or linux in general?

I'm also still curious about the clock and width figures in my lshw specs above. Are those the limits of the PCI-E bus in my system? I seem to remember something about 32-bit systems having 33MHz PCI slots and 64bit systems having 66MHz slots. I've got a C2D 64-bit capable system running on a 32-bit install of Ubuntu. If I go to a 64-bit install of Ubuntu, will that figure read 66MHz? Can anyone link to or explain more about this?

---

### Post by Yellow Pasque on 2007-12-06
I wouldn't worry about the lshw. I've got the same thing (on Ubuntu64).  

33MHz is the base PCI clock. The only time you'll see 66MHz PCI slots is in a server system with PCI-X (different from PCI-E)

---

