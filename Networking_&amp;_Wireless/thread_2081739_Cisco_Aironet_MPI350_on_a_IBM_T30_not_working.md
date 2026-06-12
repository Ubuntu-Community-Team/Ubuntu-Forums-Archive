---
title: "Cisco Aironet MPI350 on a IBM T30 not working"
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by dstke on 2012-11-07
Hi,

I've been having a heck of a time trying to get this old IBM T30 running with wireless.  First I tried to get an old PCMCIA card, Linksys WPC54G ver2, running via this thread, [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148), without success.  

Then I bought one of those micro-usb adapters, a Netgear WNA1000M and was able to get it running for a little while using these instructions, [http://ubuntuforums.org/showthread.php?t=2036445](http://ubuntuforums.org/showthread.php?t=2036445).  However, the range was poor and the bandwidth degraded over time such that within an hour it lost connection.

So I decided to replace the built-in wireless card (it hadn't worked back when the laptop was running XP), a Cisco aironet mpi350 and have been following these instructions: [http://ubuntuforums.org/showthread.php?t=1778604](http://ubuntuforums.org/showthread.php?t=1778604).  However, it looks like while "lspci -nn" shows the card, "iwconfig" shows no wireless extensions and "dmesg | grep airo" seems to indicate that the card is not installed onto the system.  Results from these commands and "lsmod" shown below.

doug@doug-laptop:~$ ndiswrapper -l
netrtwlanu : driver installed

doug@doug-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801CA/CAM SMBus Controller [8086:2483] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV200 [Mobility Radeon 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:02.0 Network controller [0280]: Cisco Aironet Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]
02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 42)

doug@doug-laptop:~$ lspci -nn | grep Network
02:02.0 Network controller [0280]: Cisco Aironet Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]

doug@doug-laptop:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
pcmcia                 39791  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                86486  0 
radeon                737891  2 
airo                   77500  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              13027  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    62064  12 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
soundcore              14635  1 snd
shpchp                 32325  0 
nsc_ircc               23240  0 
irda                  185517  1 nsc_ircc
nvram                  14029  1 thinkpad_acpi
rfcomm                 38139  0 
video                  19068  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
crc_ccitt              12595  1 irda
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197599  4 radeon,ttm,drm_kms_helper
mac_hid                13077  0 
i2c_algo_bit           13199  1 radeon
ndiswrapper           192268  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
e100                   36289  0 
floppy                 60310  0 

doug@doug-laptop:~$ rfkill list all

doug@doug-laptop:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

doug@doug-laptop:~$ dmesg | grep airo
[   27.489942] airo(): Probing for PCI adapters
[   28.081605] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   28.081657] airo(): Found an MPI350 card
[   34.317851] airo(): Max tries exceeded when issuing command
[   34.317866] airo(): Couldn't allocate RX FID
[   34.317989] airo(): Could not map memory
[   34.318031] airo 0000:02:02.0: PCI INT A disabled
[   34.326353] airo(): Finished probing for PCI adapters


As you can see Ndiswrapper and the associated netrtwlanu driver is installed.  Should I remove these?

Appreciate any assistance.  Thanks, Doug

---

