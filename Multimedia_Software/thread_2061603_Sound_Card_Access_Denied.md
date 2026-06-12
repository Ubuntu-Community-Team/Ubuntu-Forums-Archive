---
title: "Sound Card Access Denied"
date: 2012-09-23
forum: Multimedia Software
---

### Post by widda on 2012-09-23
Dell Latitude d620 has been soundless for a week. It's working still in onboard Maverick, but suddenly not in USB Lucid (my main OS).I've tried going back to other kernel.Here is result of "lspci -vv | grep -i -A10 audio".
 If anyone can tell me if the <access denied> means it IS denied, or just that it CAN BE? Looking for a scrap of useful fact somewhere in the linux sound forest :p.  
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Dell Device 01c2
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 26
    Region 0: Memory at efebc000 (64-bit, non-prefetchable) [size=16K
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
P.S:   this maybe relevant: Command alsaplayer returns a GUI missing  several volume columns. I've uninstalled  and reinstalledalsa-utils:  nothing.

---

### Post by widda on 2012-10-24
Sound restored to same OS as my music hurrah. By following these few precise instructions. It speaks. It sings! Long time silent.
:guitar:
[http://[URL](http://[URL)="http://ubuntuforums.org/forums.linuxmint.com/viewtopic.php?f=42&t=70675"]forums.linuxmint.com/viewtopic.php?f=42&t=70675[/URL]

during which I discovered an unknown-to-me capability of terminal to deal with a whole list of commands pasted in a lump. The author specified before the list "Select all".  Previously I had with such lists gone back and forth singly copy/pasting.

---

### Post by Yellow Pasque on 2012-10-24
<access denied> means only root has access to that information (so you should use sudo lspci if you want to see it).

---

### Post by widda on 2012-10-25
Thanks > [Temüjin]("http://ubuntuforums.org/member.php?u=327594") that will be helpful some time. But I never actually got  that "denied" signal, it was just another desperate attempt at google and here to strike some different and working  response( had been a looong time between sounds), and it seems it was a pulseaudio issue.[]("http://ubuntuforums.org/member.php?u=327594")[ ]("http://ubuntuforums.org/member.php?u=327594")

---

### Post by widda on 2012-10-25
I was thinking I should give thread more useful title and put some tags, but I haven't time to learn that process this week.

---

