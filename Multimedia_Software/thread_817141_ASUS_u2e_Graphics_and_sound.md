---
title: "ASUS u2e Graphics and sound"
date: 2008-06-03
forum: Multimedia Software
---

### Post by hp3 on 2008-06-03
I have an ASUS u2e Video works, but Ubuntu does not detect that this is a wide sceerrn laptop. (see pictues). 

No sound but I found a thread on another forum that said:

    snd-hda-intel must be changed to lenovo

But I am unable to find out where it should be changed.

I have looked in the forums, but I seam to the only one having problems with this new ASUS laptop.

lspci : (sound and video)

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1783
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fe9f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>



00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 14e2
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Grap
hics Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Unknown device 14e2
	Flags: bus master, fast devsel, latency 0
	Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>


I then followd the forum post on sound installation, but 
there are no files on my disk starting with snd- 

When I installed Ubuntu I used the alternate CD 
I have installed 64 bit, and encrypted the hd (if not I am not allowed to use the system outside my work).

Please help me out, I think my first Ubuntu try is very near 100% success.

---

