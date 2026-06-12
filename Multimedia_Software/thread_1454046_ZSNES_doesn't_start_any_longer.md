---
title: "ZSNES doesn't start any longer"
date: 2010-04-14
forum: Multimedia Software
---

### Post by Zyrando on 2010-04-14
I hop I am posting in the right thread if not switch, tell or whatever.

A few Days ago I wanted to install the 1.42 version of ZSNES to enable the netplay. I uninstalled all packages for ZSNES, downloaded the Linnux, 1.42 Version from the official homepage and startet the configure-file. A few times the Console told me there are Packages missing, eg: NASM and/oder SDL. So I downloaded those packages and the configuring worked without any probleme. 
Then I type "Make" but this message ist comming up:

```

g++ -o zsnes chips/sfxproc.o chips/fxemu2.o chips/dsp1proc.o chips/fxemu2b.o chips/fxemu2c.o chips/fxtable.o chips/sa1proc.o chips/sa1regs.o chips/dsp1emu.o chips/st10proc.o chips/seta10.o chips/dsp2proc.o chips/sdd1emu.o cpu/addrni.o cpu/dma.o cpu/dsp.o cpu/dspproc.o cpu/execute.o cpu/executec.o cpu/irq.o cpu/memory.o cpu/spc700.o cpu/stable.o cpu/table.o cpu/tableb.o cpu/tablec.o linux/copyvwin.o linux/sdlintrf.o linux/sdllink.o linux/sw_draw.o linux/zloaderw.o linux/ztcp.o linux/zipxw.o linux/zfilew.o dos/debug.o dos/joy.o dos/modemrtn.o dos/vesa2.o dos/initvid.o dos/sw.o dos/gppro.o dos/vesa12.o gui/gui.o gui/menu.o video/makev16b.o video/makev16t.o video/makevid.o video/mode716.o video/mode716b.o video/mode716d.o video/mode716e.o video/mode716t.o video/mode7.o video/mode7ext.o video/mv16tms.o video/newg162.o video/newgfx16.o video/newgfx2.o video/newgfx.o video/m716text.o video/2xsaiw.o video/procvid.o video/sw_draw.o video/hq2x16.o video/hq2x32.o video/hq3x16.o video/hq3x32.o video/hq4x16.o video/hq4x32.o cfgload.o endmem.o init.o initc.o uic.o patch.o ui.o vcache.o version.o zip/unzip.o zip/zpng.o effects/burn.o effects/water.o effects/smoke.o jma/7zlzma.o jma/crc32.o jma/iiostrm.o jma/inbyte.o jma/jma.o jma/lzma.o jma/lzmadec.o jma/winout.o jma/zsnesjma.o  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro  -L/usr/local/lib -L/usr/lib  -lz -L/usr/local/lib -Wl,-rpath,/usr/local/lib -lSDL -lpthread  -lpng -lm -L
g++: Argument für »-L« fehlt

make: *** [zsnes] Fehler 1


```So I thought if I can't make that vVersion get to work, I reinstall the most actual version by the normal Add/Delete Window and the installation does work, but ZSNES doesn't start any longer..
When I try to start ZSNES with console another ERROR is comming up..
```
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: SynPS/2 Synaptics TouchPad
Mouse 1: Macintosh mouse button emulation
Error opening file!

```I hope that someone can help :( 

PS: Hope my english isn't thaaat bad ^^'

---

