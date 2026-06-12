---
title: "Sound card stopped working"
date: 2005-11-07
forum: Multimedia &amp; Video
---

### Post by benbalbo on 2005-11-07
Hi all,

I came into work this morning and was greeted by a speaker with an X next to it for a volume control in the top panel.

Clicking on it tells me I have no sounds card, or the wrong gstreamer plugin installed.

What confuses me is that it worked yesterday, and in fact has worked out of the box for 3 weeks so far.

Here's some info that hasn't really helped me so far:

```
ben@computer~:$ lspci
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corp. 82915G Express Chipset Family Graphics Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 11)
0000:0a:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

```
ben@computer~:$ dmesg |egrep -i "(alsa|audio|ac.?97)"
[4294690.843000] intel8x0_measure_ac97_clock: measured 49558 usecs
```

Any pointers or advice on how to troubleshoot this would be very much appreciated!

Thanks!
Ben

---

### Post by benbalbo on 2005-11-07
Okay - I have no idea if this is related. I just stuck an audio CD in, and Sound Juicer poped up saying it couldn't access /dev/scd0.

Mounting it manually gives me this in dmesg:

```
[4303665.604000] cdrom: sr0: mrw address space DMA selected
[4303665.735000] cdrom: sr0: mrw address space DMA selected
[4303665.846000] end_request: I/O error, dev sr0, sector 64
[4303665.846000] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
```

I can mount data CDs (tested with Unubtu CD).

Cheers
Ben

---

### Post by pminetti on 2005-11-14
hi,well i have today the same extrange problem, the most strange is that in the same computer if I boot Kubuntu insted of ubuntu, the sound card works OK

I think is a genome problem, and worst there's no alsaconf in ubuntu
Can any one explain this

thanks!

pablo minetti

---

### Post by pminetti on 2005-11-14
well the probles seems to be only in my user, if I log like an other user, my sound card work fine, if someone helps, i will thanks

Pablo Minetti

---

