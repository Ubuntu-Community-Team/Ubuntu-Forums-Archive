---
title: "Ubuntu 11. Wifi stops working."
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by kernel_mode on 2011-07-10
Wifi is working fine for some time then it stops working. Wifi icon shows that all is fine, but there is no connection and I can not disable wifi through GUI. Network Tools GUI utility also don't start up. I am not able to restart or disable wifi through the console because some console programs like sudo, iwconfig, ifconfig stop working too when those lags appear (after I launch the program nothing happens and ctrl+c escape sequence also don't work, so I am forced to kill the terminal program). I am using ndiswrapper and wg311v3 driver.
Thanks in advance for your answers.

---

### Post by kernel_mode on 2011-07-18
bump
Here is my lsmod and lspci
```

kernelmode@kernelmode-System-Product-Name:~$ lsmod
Module                  Size  Used by
vesafb                 13449  1 
snd_hda_codec_analog    75442  1 
binfmt_misc            13213  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
nvidia               9766978  40 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           192828  0 
ppdev                  12849  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
asus_atk0110           17664  0 
parport_pc             32111  1 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
ahci                   21591  0 
hid                    77084  1 usbhid
libahci                25548  1 ahci
r8169                  42534  0 
floppy                 60032  0 
pata_jmicron           12651  0 
kernelmode@kernelmode-System-Product-Name:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2)
02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
02:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:02.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

```

---

### Post by cpaempire52 on 2011-08-08
I'm having the same problem - completely fresh install a few days ago of 64 bit Ubuntu. I have a USB wireless card that I'm using WUSB54GC. The symptoms are exactly the same as the OP, network activity stops including the green light on my card. The indicators look completely normal except the lack of Internet.

I can fix the problem by removing the USB cable from the NIC and waiting a few seconds. This gets me pretty much instant access again, until the problem rears its head again within the hour usually.

I'm pretty sure my issue is related to using Transmission to download a torrent. The problem doesn't seem to happen or nearly as much if I'm not pegging the Internet connection with Transmission.

OP...you wouldn't happen to be downloading torrents would you?

---

### Post by lkjoel on 2011-08-09
Could you give me the output of these Terminal commands?
```
sudo /etc/init.d/networking restart
sudo ifconfig
sudo iwconfig
sudo nm-tool
lsb_release -s -c
uname -a
lspci -vvnn

```

---

