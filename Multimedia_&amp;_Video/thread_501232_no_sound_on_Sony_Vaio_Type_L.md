---
title: "no sound on Sony Vaio Type L"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by el-sio on 2007-07-15
Hi !
I have installed Ubuntu 7.04 on my Vaio Type L ([http://www.vaio.sony.co.jp/Products/L1/feat2.html]("http://www.vaio.sony.co.jp/Products/L1/feat2.html")) computer and everything works fine except that I have only a very faint sound output, only audible when I plug in earphones in a very quiet room...
YES of course, I have all my volumes levels at maximum.

here is the output of aplay :

```
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : STAC92xx Analog [STAC92xx Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

```

here are the lspci lines :

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Sony Corporation Unknown device 8205
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at dc3c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

and here is my audio codec output :

```
el-sio@moria:~$ cat /proc/asound/card0/codec\#*
Codec: SigmaTel CXD9872RD/K

```

I have followed the instructions of the comprehensive sound problem guide, installed brand new ALSA 1.0.14 drivers and followed the instructions specific to HDA-Intel driver in order to manually select my model according to my codec, using the very good ubuntu community guide :  [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

According to this guide and the ALSA documentation, I am supposed to use the option "model=vaio" or "model=vaio-ar" in my module conf file, but none of this gave me an audible sound through my speakers...

this is very frustrating because I know that the driver is somehow working (faint sound in the headphones) but it just needs a little something to output a higher levels.. It is also infuriating since it's the last thing that prevents me from getting rid of WinXP :)

If anybody knows this problem, or a way to fix it (or get the driver fix if that is indeed the problem), Iwill warmly greet any of their comment remarks or hints.

Thank you !

---

### Post by el-sio on 2007-07-15
Nobody here who got the sound working with this kind of codec ?
No ideas about how to tell a sound card driver to just play louder ?
I am really depressed with this issue now...

Thanks anyway !

---

### Post by BigP on 2007-07-23
DId you ever get this working?  I'm having identical problem on Vaio desktop.  Any help would be appreciated.

---

