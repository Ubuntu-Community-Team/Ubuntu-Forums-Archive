---
title: "Installation driver ALSA on audiophile 192"
date: 2012-02-08
forum: Multimedia Software
---

### Post by skunktp on 2012-02-08
I hope to be in the right place for the new discussion.

I’ll try to be concise. It’s several days I’m trying to let my computer recognizing my new sound card “pci

audiophile 192”. This sound card is necessary to record the guitar. Looking for information in different

forums, someone suggested to use OSS driver. I tried with them but, apart from the fact that the card was

recognized correctly by the computer, there was no input signal and there was no sound except the one of

the test. In the end I decided to start again after having formatted the pc.

Once more I installed Ubuntu 10.10, updated it and noticed that whilst the sound card had been recognized

by the pc and there was the sound, there still wasn’t the possibility to have an input signal. Therefore I found

the guide to install “alsa” driver necessary for my sound card

(ICE1724) [http://www.alsa-project.org/main/index.php/Matrix:Module-ice1724](http://www.alsa-project.org/main/index.php/Matrix:Module-ice1724)

There were no problems till the upload of the modules in the kernel:

modprobe snd-ice1724 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

I launched the commands one by one. The first one was ok, the second failed: here’s what it sayed

root@rec-sala1:/home/rec# modprobe snd-pcm-oss
FATAL: Error inserting snd (/lib/modules/2.6.35-28-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.35-28-generic/kernel/sound/acore/snd-page-alloc.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.35-28-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.35-28-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm_oss (/lib/modules/2.6.35-28-generic/kernel/sound/acore/oss/snd-pcm-oss.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I checked the installed packets and everything seems to be ok, so that I decided to reboot the pc (damned

Windows!)

When the pc started again the sound card was no more recognized and there was no sound. I tried to launch

again the commands to upload the modules and also “modprobe snd-ice1724” command doesn’t work,

panic!

I tried with lspci and noticed that the sound card was recognized.*I tried with “aplay” and that’s the result:

aplay: device_list:240: no sound card found

I tried alsamixer:

the mixer cannot be opened: file or directory not existing.

At that point I don’t know what else to do. I wander from forum to forum to find a solution but, nothing!

I’ve been using “Ubuntu” for 2 years now and I found all the answers to different problems on this forum.

Please help me!

This is my pc configuration.

Processor 4x Intel(R) Core(TM) i3 CPU 550 @ 3.20GHz
Memory   8184MB (654MB used)
Operating System   Ubuntu 10.10
Kernel   Linux 2.6.35-28-generic (x86_64)
Compiled   #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011
C Library   GNU C Library version 2.12.1 (stable)
Default C Compiler   GNU C Compiler version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5)
Host bridge   Intel Corporation Core Processor DRAM Controller (rev 18)
PCI bridge   Intel Corporation Core Processor PCI Express x16 Root Port (rev 18) (prog-if 00 [Normal decode])
USB Controller   Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
PCI bridge   Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
PCI bridge   Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) (prog-if 00 [Normal decode])
PCI bridge   Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) (prog-if 00 [Normal decode])
PCI bridge   Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06) (prog-if 00 [Normal decode])
PCI bridge   Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 06) (prog-if 00 [Normal decode])
USB Controller   Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
PCI bridge   Intel Corporation 82801 PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
ISA bridge   Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
IDE interface   Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
SMBus   Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
IDE interface   Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
VGA compatible controller   nVidia Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
Audio device   nVidia Corporation High Definition Audio Controller (rev a1)
Ethernet controller   Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
IDE interface   VIA Technologies, Inc. PATA IDE Host Controller (prog-if 85 [Master SecO PriO])
Multimedia audio controller   VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)


I think that’s all I had to say. I just want to record using this sound card, please tell me the prayer I have to

say to whom or the politician I have to vote!

---

