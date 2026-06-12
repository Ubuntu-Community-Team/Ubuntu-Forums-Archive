---
title: "1680x1050 is one of the &quot;Supported Future Video Modes&quot; in Xorg.0.log"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by rtsa on 2008-01-04
I have installed gutsy on an old (8 years) PIII box but with a shiny new Samsung SyncMaster 216BW monitor (because I intend to use the machine merely to connect to other more powerful ones at work, in case you were wondering).

I am finding that the native resolution of 1680x1050 does not work. In my Xorg.0.log I see the lines:

```

(II) R128(0): Supported Future Video Modes:
(II) R128(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179

```

I have read quite a few accounts of 1680x1050 for various monitors requiring some modeline tweaking, with many successes and some failures. I have tried some of what I have read but without success so far.

Before I walk too far down that road, I want to check whether the above means that I need to buy a new (second hand of course, given the AGP vintage of the motherboard) video card. From lspci my existing one is:

```

01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

```

Thanks in advance for any help.

---

### Post by overdrank on 2008-01-04
> **rtsa said:**
> I have installed gutsy on an old (8 years) PIII box but with a shiny new Samsung SyncMaster 216BW monitor (because I intend to use the machine merely to connect to other more powerful ones at work, in case you were wondering).

I am finding that the native resolution of 1680x1050 does not work. In my Xorg.0.log I see the lines:

```

(II) R128(0): Supported Future Video Modes:
(II) R128(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179

```

I have read quite a few accounts of 1680x1050 for various monitors requiring some modeline tweaking, with many successes and some failures. I have tried some of what I have read but without success so far.

Before I walk too far down that road, I want to check whether the above means that I need to buy a new (second hand of course, given the AGP vintage of the motherboard) video card. From lspci my existing one is:

```

01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

```

Thanks in advance for any help.

Hi and welcome,  a quick search found the max resolutions for that card
[http://ati.amd.com/products/faqs/rage128faq.html](http://ati.amd.com/products/faqs/rage128faq.html)
As you can see it really depends on the amount of memory on the card. It will usually tell the amount of memory on the flash screen on start up. If not you can use the command in the terminal ```
lshw | less
``` and scroll down to you graphics card and it should be stated there 
Example 
```
 *-display
                description: VGA compatible controller
                product: NV43 [GeForce 6600/GeForce 6600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a2
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5

```

---

### Post by rtsa on 2008-01-04
Hi overdrank and thanks for your help - I really appreciate it,

I was wondering - if 1920x1200 is listed as the max resolution, can I assume the card can support every resolution below that?

My "sudo lshw -class display" output is:

```

  *-display               
       description: VGA compatible controller
       product: Rage 128 RF/SG AGP
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga bus_master cap_list
       configuration: latency=64 mingnt=8

```

so that doesn't give me a size. Also, I'm not sure exactly what you mean by the flash screen on startup - do you mean the information the BIOS displays? If so then I don't think the video RAM is displayed there. I have examined dmesg for the info but found nothing there either.

I see this line in my /var/log/Xorg.0.log

```

(II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers

```

but I doubt that it is what I am looking for.

Having said all that, I am now wondering whether it would be best to just upgrade the card to something with a little more power because (a) I use virtual desktops a lot and (b) it is a little slow to redraw all the windows in screen even at the current resolution, which is:

```

$ xvidtune -show
"1400x1050"   122.00   1400 1488 1640 1880   1050 1052 1064 1082 +hsync +vsync

```

Anyway, thanks again.

---

### Post by oheh on 2008-04-06
I just figured out how to do this with the same card.  Install gvidm (sudo aptitude install gvidm) and then run it and you can pick the resolution you want.  It will have two options for each resolution.  Mine was set to one of the 1680x1050 options so I picked the other one and now the resolution is right!

---

