---
title: "Any hope of getting this obscure tv-tuner to work?"
date: 2009-08-07
forum: Mythbuntu
---

### Post by JamesClark on 2009-08-07
I recently acquired an older all-in-one pc with a built-in tv tuner: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883102501]("http://www.uniwill.com/products/other/LCDPC/L372N1.htm")

I've been having trouble getting this tv-tuner to work with anything other than the Windows software it came with. The tv-tuner is a Prolink PV-CX881pu+. I haven't been able to find any information about it online, so I'm guessing it's pretty obscure. 

lscpi -vnn reveals:

00:0b.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 03)
    Subsystem: PROLINK Microsystems Corp Device [1554:4811]
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at de000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx8800
    Kernel modules: cx8800

Using tvtime I was able to get composite video to work when I connected something to it, but not any channels. Let me know if you need any other information. Thanks in advance!

---

### Post by JamesClark on 2009-08-11
I've tried xawtv, but no luck. 

xawtv -hwscan tells me:

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : PixelView
    flags:  capture tuner 


I'm getting the feeling that the card has been detected wrong. Is there a way to manually change which card the OS thinks it is working with? I might be able to get lucky trying a bunch.

---

### Post by Caysho on 2009-08-11
Do searches on the PCI ID.
There are several hits on 1554:4811 - [linuxtv]("http://www.linuxtv.org/wiki/index.php/Cx88_devices_%28cx2388x%29") and the [SF PCI ID]("http://pciids.sourceforge.net/pci.ids") list.

---

### Post by JamesClark on 2009-08-12
Thanks, I was able to find more info searching the PCI ID. I now have video working after setting tuner=43. But, unfortunately, I don't have any sound (it works elsewhere, just not through my tuner). 

Any tips on where to look next?

---

### Post by Caysho on 2009-08-12
Check dmesg for what is being detected - you might have to specify the card and tuner and likely other options as well.  It is #3 in CARDLIST.cx88.

The linuxtv page for the Pixelview indicates it is a pretty dodgy item.

---

### Post by JamesClark on 2009-08-12
Yeah, I had to change the tuner type to get the video to work. I checked the WIndows drivers and found it was an FM1236 NTSC MK 3. Now I'm just trying to get the sound working. Sound works everywhere else. I tried out a DVD and a youtube video and sound worked fine.

Here's the result of dmesg | grep cx
[    8.897561] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[    8.900601] cx8800 0000:00:0b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.901594] cx88[0]: subsystem: 1554:4811, board: PixelView [card=3,autodetected], frontend(s): 0
[    8.901600] cx88[0]: TV tuner type 43, Radio tuner type -1
[    9.087033] tuner' 1-0043: chip found @ 0x86 (cx88[0])
[    9.128963] tuner' 1-0060: chip found @ 0xc0 (cx88[0])
[    9.218408] cx88[0]/0: found at 0000:00:0b.0, rev: 3, irq: 16, latency: 64, mmio: 0xde000000
[    9.218696] cx88[0]/0: registered device video0 [v4l2]
[    9.218775] cx88[0]/0: registered device vbi0
[    9.218847] cx88[0]/0: registered device radio0

Let me know if any other info is needed.

---

### Post by Caysho on 2009-08-13
It's an NTSC card, so it is analogue.
You need to configure alsa properly.
The linuxtv page has details.

---

### Post by klc5555 on 2009-08-13
The backend's card configuration page may have defaulted the card's audio output to /dev/dsp This may not be what your Alsa config is expecting. If the dropdown menu has other options in it (you can't type in any of your own options; they won't save), try /dev/dsp1 and /dev/dsp2, etc. One of these may work.

---

### Post by JamesClark on 2009-08-13
I got it!

I played around with a bunch of sound stuff, but nothing worked. In frustration I tried changing the card to a different PixelView card. Changing it to card=27 made the sound work! All I had to do after that was adjust some settings in alsamixer.

Thanks everyone!

---

