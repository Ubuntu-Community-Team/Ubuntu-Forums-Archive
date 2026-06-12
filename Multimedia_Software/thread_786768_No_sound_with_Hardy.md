---
title: "No sound with Hardy"
date: 2008-05-08
forum: Multimedia Software
---

### Post by Bart Ellebaut on 2008-05-08
I have installed Kubuntu hardy heron on my desktop, but I get no sound.

lspci -v
```

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	I/O ports at dc00 [size=256]
	I/O ports at e000 [size=256]
	Memory at d3003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

```

I have downloaded the driver, tried to install this, 
nothing, then I tried Alsamixer, but it wasn't installed yet, but when I tried to install, I got this:

```
 /usr/src/modules/alsa-driver/drivers/pcsp/pcsp.c:55: interne fout (Each    &#9618;
 &#9474; undeclared identifier is reported only once                                &#9618;
 &#9474; /usr/src/modules/alsa-driver/drivers/pcsp/pcsp.c:55: interne fout for      &#9618;
 &#9474; each function it appears in.)                                              &#9618;
 &#9474; make[6]: *** [/usr/src/modules/alsa-driver/drivers/pcsp/pcsp.o] Fout 1     &#9618;
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/drivers/pcsp] Fout 2            &#9618;
 &#9474; make[4]: *** [/usr/src/modules/alsa-driver/drivers] Fout 2                 &#9618;
 &#9474; make[3]: *** [_module_/usr/src/modules/alsa-driver] Fout 2                 &#9618;
 &#9474; make[3]: Map '/usr/src/linux-headers-2.6.24-16-386' wordt verlaten         &#9618;
 &#9474; make[2]: *** [compile] Fout 2                                              &#9618;
 &#9474; make[2]: Map '/usr/src/modules/alsa-driver' wordt verlaten                 &#9618;
 &#9474; make[1]: *** [build-stamp] Fout 2                                          &#9618;
 &#9474; make[1]: Map '/usr/src/modules/alsa-driver' wordt verlaten                 &#9646;
 &#9474; make: *** [kdist_image] Fout 2   
```

---

