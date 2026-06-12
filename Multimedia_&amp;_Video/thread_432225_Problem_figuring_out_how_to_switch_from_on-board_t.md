---
title: "Problem figuring out how to switch from on-board to PCI-Express video card"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by agamotto on 2007-05-03
I hope someone can help me with this.  I have a MSI mpc 51pv, with built-in nvidia 6150 video.  I have purchased a GeForce 7300 GT card to boost my video for newer games that have come out, but I can't seem to get things to default to the new video card.
There is an option to change the default video in the BIOS, and when I set it to PCI-Express, I get the POST screen, and the first Ubuntu splash, then it goes black with a blinking cursor.  This is the output from the PCI card.  If I switch the monitor to the on-board output, I get the usual log-on screen, but very faint and unreadable.  How do I convince Xorg/Ubuntu to ignore the on-board video, and use only the PCI-Express card?

---

### Post by phidia on 2007-05-03
I believe you need to look at the output from lspci -v and determine which address is the pci-e slot then do sudo dpkg-reconfigure xserver-xorg and when the configuration asks for the video card address plug in the pci-e's.

---

### Post by agamotto on 2007-05-05
Ok, here is what I think is relevant from the lspic -v output:


0000:03:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0393 (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp.: Unknown device c443
        Flags: fast devsel, IRQ 58
        [virtual] Memory at fa000000 (32-bit, non-prefetchable) [disabled] [size =16M]
        Memory at e0000000 (64-bit, prefetchable) [disabled] [size=256M]
        Memory at fb000000 (64-bit, non-prefetchable) [disabled] [size=16M]
        I/O ports at 9c00 [disabled] [size=128]
        Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <available only to root>

If I am reading this right, the address for the PCI-Express video card would be 0000:3:00.0?  The video card is from EVGA, so I presume that this section has the correct information.

---

### Post by rockingmtranch on 2007-05-05
> **agamotto said:**
> Ok, here is what I think is relevant from the lspic -v output:


0000:03:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0393 (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp.: Unknown device c443
        Flags: fast devsel, IRQ 58
        [virtual] Memory at fa000000 (32-bit, non-prefetchable) [disabled] [size =16M]
        Memory at e0000000 (64-bit, prefetchable) [disabled] [size=256M]
        Memory at fb000000 (64-bit, non-prefetchable) [disabled] [size=16M]
        I/O ports at 9c00 [disabled] [size=128]
        Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <available only to root>

If I am reading this right, the address for the PCI-Express video card would be 0000:3:00.0?  The video card is from EVGA, so I presume that this section has the correct information.

Here's mine for comparison if it helps:

05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1) (prog-if 00 [VGA])
        Subsystem: Unknown device 19f1:201f
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        Memory at fd000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at 9f00 [size=128]
        [virtual] Expansion ROM at c0000000 [disabled] [size=128K]
        Capabilities: <access denied>

---

