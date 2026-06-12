---
title: "Multimedia card recognition woes"
date: 2009-06-10
forum: Multimedia Software
---

### Post by Zarckon on 2009-06-10
I just recently bought a new computer (I fried the motherboard on the old one). The new one has some multimedia aspects to it that the old one didn't. What I'm trying to understand at this point is how to get the multimedia card recognized and working. It has an input for a cable feed. I'd like to be able to watch television through it.

I installed TVtime based on posts in the forums. However, I'm getting /dev/video0 not found.

When I do a lspci -vv I get:

> 04:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 (rev 0f)
	Subsystem: Avermedia Technologies Inc Device d439
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: <access denied>
	Kernel driver in use: cx23885
	Kernel modules: cx23885

And when I did an ls /dev I got:
> 
audio            fuse     loop5               psaux  ram7    sequencer   tty10  tty25  tty4   tty54  ttyS2           usbdev3.2_ep81  usblp0   vcsa1
block            hidraw0  loop6               ptmx   ram8    sequencer2  tty11  tty26  tty40  tty55  ttyS3           usbdev3.2_ep83  usbmon0  vcsa2
bus              hidraw1  loop7               pts    ram9    sg0         tty12  tty27  tty41  tty56  urandom         usbdev4.1_ep00  usbmon1  vcsa3
cdrom            hidraw2  mapper              ram0   random  sg1         tty13  tty28  tty42  tty57  usb             usbdev4.1_ep81  usbmon2  vcsa4
cdrw             hidraw3  mem                 ram1   rtc     sg2         tty14  tty29  tty43  tty58  usbdev1.1_ep00  usbdev4.2_ep00  usbmon3  vcsa5
char             hpet     mixer               ram10  rtc0    shm         tty15  tty3   tty44  tty59  usbdev1.1_ep81  usbdev4.2_ep01  usbmon4  vcsa6
console          initctl  net                 ram11  scd0    snapshot    tty16  tty30  tty45  tty6   usbdev2.1_ep00  usbdev4.2_ep03  vcs      vcsa7
core             input    network_latency     ram12  sda     snd         tty17  tty31  tty46  tty60  usbdev2.1_ep81  usbdev4.2_ep81  vcs1     vcsa8
cpu_dma_latency  kmem     network_throughput  ram13  sda1    sndstat     tty18  tty32  tty47  tty61  usbdev2.4_ep00  usbdev4.2_ep82  vcs2     xconsole
disk             kmsg     null                ram14  sda2    sr0         tty19  tty33  tty48  tty62  usbdev2.4_ep01  usbdev4.2_ep83  vcs3     zero
dsp              log      nvidia0             ram15  sda3    stderr      tty2   tty34  tty49  tty63  usbdev2.4_ep82  usbdev4.2_ep84  vcs4
dvd              loop0    nvidiactl           ram2   sda5    stdin       tty20  tty35  tty5   tty7   usbdev2.4_ep83  usbdev4.3_ep00  vcs5
dvdrw            loop1    oldmem              ram3   sda6    stdout      tty21  tty36  tty50  tty8   usbdev3.1_ep00  usbdev4.3_ep81  vcs6
ecryptfs         loop2    pktcdvd             ram4   sda7    tty         tty22  tty37  tty51  tty9   usbdev3.1_ep81  usbdev4.4_ep00  vcs7
fd               loop3    port                ram5   sda8    tty0        tty23  tty38  tty52  ttyS0  usbdev3.2_ep00  usbdev4.4_ep02  vcs8
full             loop4    ppp                 ram6   sdb     tty1        tty24  tty39  tty53  ttyS1  usbdev3.2_ep02  usbdev4.4_ep81  vcsa

Any thoughts on what I'm missing? And or would another program such as MythTV be more likely to find the input?

Thanks for any thoughts.

---

### Post by Zarckon on 2009-06-19
bump

---

