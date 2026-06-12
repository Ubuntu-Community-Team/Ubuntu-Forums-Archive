---
title: "Hoary+No sound and no How-To is helping me..."
date: 2006-02-15
forum: Multimedia &amp; Video
---

### Post by CaptainHowdy on 2006-02-15
Hello all!

I have installed Hoary on a Intel Pentium 4 with 2 GB of RAM
lspci results:
> 
0000:00:00.0 Host bridge: Intel Corp. 82875P Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82875P Processor to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34GL [Quadro FX 500] (rev a1)
0000:02:0c.0 Ethernet controller: Intel Corp. 82540EM Gigabit Ethernet Controller (rev 02)

but KDE gives a message when it starts up:

> Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (No such file or directory)
The sound server will continue, using the null output device.

I did some tricks i found on ubuntu forums but none helped. On 
terminal i entered

>  alsamixer 

and it gave me 

> alsamixer: function snd_ctl_open failed for default: No such file or directory


On the kernel menu, on Device Drivers->Sound->PCI -> ...  it has detected
the sound card...

Anybody has any ideas???

Thanx!

Anybody any ideas?

---

### Post by CaptainHowdy on 2006-02-20
Nobody any ideas???

---

### Post by Crayoneater on 2006-02-20
i think the best thing for you to do is to download alsa drivers, and alsa utilities, and alsa tools from the alsa website.  then install those and run alsaconf and hopefully it will set up your sound for you.

---

