---
title: "Help needed for ATI Rage 128 RF/SG"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by Handssolow on 2006-10-07
My knowledge of using Ubuntu is limited so please be patient. I'm using Dapper Drake 6.06.

I've a old ATI Rage 128 RF/SG and I want to get Google Earth to run but it quits within about 5 seconds of it loading. I'm still looking for solutions.

I've posted for advice on the Desktop Forum and done some searches.

glxgears looks fast enough but the printout shows it's fast for 10 seconds then much slower.

Following Forum advice I edited /etc/modules

Initially I had just two lines

lp
psmouse

So I added three lines to see if this worked or changed things.

lp
psmouse
fglrx
agpgart
r128 

Google Earth now loaded with a window-
Google Earth: Recommends a Driver Upgrade
You are currently running Google Earth in "Open GL" with software emulation, Google Earth will work but run very slowly.

There was also a link to the ATI website but it's not much help to me.

But I could now get Google Earth to run and zoom in to view my house. Yes it was a bit slow but at least it worked.


With glxgears however the gears were virtually static.

If I re-edit /etc/modules and remove the line 
fglrx

glxgears is back moving but Google Earth quits.

Can I check if I'm using AGP x4?
How do I maximise the features of my video card?
Any suggestions?
It does seem that the drivers with 6.06 aren't optimal for the ATI rage 128 RF/GS video card.

---

### Post by sp4rd on 2006-10-08
*Can I check if I'm using AGP x4?*

grep -i "using agp" /var/log/Xorg.0.log
should tell you what agpmode you're using.  Don't think those cards support AGPx4 though.  This is what my lspci -vv says

01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Magnum/Xpert128/X99/Xpert2000
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (2000ns min), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Region 1: I/O ports at 9000 [size=256]
        Region 2: Memory at dd000000 (32-bit, non-prefetchable) [size=16K]
        [virtual] Expansion ROM at dc000000 [disabled] [size=128K]
        Capabilities: [50] AGP version 2.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- [COLOR="Blue"]Rate=x1,x2[/COLOR]
                Command: RQ=32 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x2
        Capabilities: [5c] Power Management version 1
                Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

My motherboard is AGP x4 capable but the bios only detects AGP x2
for this card.

But you can try using this option with your Section "Device"

        Option          "AGPMode"       "4"

if that doesn't work try 

        Option          "AGPMode"       "2"

---

### Post by Handssolow on 2006-10-08
Thanks for your help and reply Sp4rd.
Like you my motherboard an Asus A7A266-E supports AGP x4 but I'm realising that my ATI Rage 128 RF/SG is only AGP x2.

sudo lspci -v gave the following info-

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc: Unknown device 0048
        Flags: bus master, stepping, 66MHz, medium devsel, latency 64, IRQ 11        Memory at ec000000 (32-bit, prefetchable) [size=64M]
        I/O ports at d800 [size=256]
        Memory at eb000000 (32-bit, non-prefetchable) [size=16K]
        Expansion ROM at ebfe0000 [disabled] [size=128K]
        Capabilities: [50] AGP version 2.0
        Capabilities: [5c] Power Management version 1

grep -i "agp" /var/log/Xorg.0.log gave the following-

(--) Chipset ATI Rage 128 GL RF (AGP) found
(--) R128(0): Chipset: "ATI Rage 128 GL RF (AGP)" (ChipID = 0x5246)
(II) R128(0): [agp] Mode 0x1b000211 [AGP 0x10b9/0x1647; Card 0x1002/0x5246]
(II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
(II) R128(0): [agp] ring handle = 0xf0000000
(II) R128(0): [agp] Ring mapped at 0xb56ff000
(II) R128(0): [agp] ring read ptr handle = 0xf0101000
(II) R128(0): [agp] Ring read ptr mapped at 0xb56fe000
(II) R128(0): [agp] vertex/indirect buffers handle = 0xf0102000
(II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb54fe000
(II) R128(0): [agp] AGP texture map handle = 0xf0302000
(II) R128(0): [agp] AGP Texture map mapped at 0xb501e000
(II) R128(0): Using 8 MB AGP aperture
(II) R128(0): Using 5 MB for AGP textures 


I'm not sure about your suggestion of
lspci -vv

I didn't get all they information you posted but it does look as if I've got  AGPx2.

Can you run Google Earth?
How is glxgears running?

Only if I add 
fglrx
to /etc/modules is it possible to run Google Earth but glxgears is vitually static.

Any suggestions?
I'm still not certain if my graphics card drivers are optimal.
Should I look towards changing my graphics card?

---

### Post by sp4rd on 2006-10-09
I have debian unstable and xorg 7.1 on the box that has the r128 card in it so it probably is slighty different readout, but close enough.  I had the same card in my ubuntu box and worked fine in celestia and the gl screensavers performed like they were accelerated.

*How is glxgears running?*
I get around 800 fps running in a window

glxinfo | grep -i "direct rendering"
direct rendering: Yes

should confirm that direct rendering is working

*Only if I add fglrx*
From what I know about fglrx I believe those drivers are only meant for radeon and above cards.  Could that be adding to the problem?.  I would try just xorgs dri and mesa glx drivers.  You could probably reduce your DefaultDepth to 16 in your xorg.conf if it's set to 24.

You can try Google Earths linux forum here
[http://bbs.keyhole.com/ubb/postlist.php/Cat/0/Board/SupportGELinux]("http://bbs.keyhole.com/ubb/postlist.php/Cat/0/Board/SupportGELinux")
I don't run Google Earth but Celestia runs good I get around 25-30 fps in that and it runs smooth on both debian and ubuntu dapper.

---

### Post by parigigi on 2006-12-31
Hi, 

my video card uses this chipset: ATI Rage 128 Pro GL PF (AGP). I have a similar problem, but in my case the direct rendering doesn't work:

```

stranger@alvaro:~$ glxinfo | grep "direct rendering"
direct rendering: No

```

I use Kubuntu 6.10 and I found a wiki page in italian that explains how to force the system to use direct rendering:

[http://wiki.ubuntu-it.org/Mesa/Dri](http://wiki.ubuntu-it.org/Mesa/Dri)

That wiki explains how to get from the net the latest mesa drivers for the card and how to compile and install them. It also explains that mesa drivers are installed by default on Ubuntu, but it says also that recompile them is a way to enable the direct rendering.

I followed all instructions but the problem remanins: no direct rendering....


Any ideas?

---

