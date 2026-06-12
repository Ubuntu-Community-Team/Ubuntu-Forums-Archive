---
title: "Verizon Actiontec M1424 Connection"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by rgaskins on 2011-07-22
I just loaded Ubuntu 10.10 on a Dell Dimension 4550 and deleted the Windows XP OS. I have a Verizon Actiontec M1424 modem that was working fine before I installed Ubuntu. I have several laptops and other wireless devices using the modem and they are working fine. 
 
My Dell is hardwired (CAT5) into the modem. After the install I went to System -> Preferences -> Network Connections. When the window opened up with the "Wired" tab I saw "Auto eth0". So when I click on edit, it asks for the "Device MAC address" which I assume is the modem's MAC address. Then it asks for the "Clone MAC address". I have no idea what that is but I re-entered the modem's MAC address. I still had no internet connection.
 
The other tabs were 802.1x, IPv4, and IPv6. If my memory serves me correct, I don't need to worry about entering any information on those because I think those deal with network security for a wireless connection.
 
Since I just installed Ubuntu, I re-installed it to ensure I did nothing wrong. I went through the same procedure and got the same results; no internet connection. What do I need to do? Verizon refuses to help saying, "It's not the modem since the other devices are working and we don't support Linux."
 
I am not totally familiar with vi, so if I have to edit a script please realize you are dealing with a novice.

---

### Post by floodeye_ on 2011-07-22
try wvdial

---

### Post by rgaskins on 2011-07-24
Thanks for the reply.  Here is what I did and what I got.  I typed in wvdial and the system came back with: "The program 'wvdial" is currently not installed.  You can install it by typing: sudo apt-get install wvdial.
 
After I typed in the command this is the reply: 
 
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package wvdial is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package 'wvdial" has no installation candidate 
 
Where do I go from here?  I installed Ubuntu from the disk that came with the book *Ubuntu Unleashed 2011 Edition Covering 10.10 and 11.04.* 
 
Is there something on the disk that I will need to install?  Or is there something online somewhere that I need to download?

---

### Post by jtarin on 2011-07-26
In a terminal issue the command ```
ifconfig
``` and post the results. Let's see if your system recognizes your ethernet card.

---

### Post by rgaskins on 2011-07-27
Here is the output from ifconfig:
 
eth0       Link  encap: Ethernet  Hwaddr  00:07:e9:b0:60:e0
                UP  BROADCAST  MULTICA ST  MTU: 1500 Metric: 1
                RX packets: 0  errors: 0  dropped: 0  overruns: 0  frames: 0
                TX packets: 0  errors: 0  dropped: 0 overruns: 0
                Collisions: 0  txqueuelen: 1000
                RX bytes: 0  (0. 0 B)    TX bytes: 0  (0.  0 B)
 
lo            Link encap: Local  Loopback
                inet  addr: 127.0.0.1  Mask: 255.0.0.0
                inet6 addr:  : : 1/128  Scope: Host
                UP  LOOPBACK  RUNNING  MTU: 16436  Metric: 1
                RX packets: 128  errors: 0  dropped: 0  overruns: 0 frames: 0 
                TX packets: 0  errors: 0  dropped: 0 overruns: 0
                Collisions: 0  txqueuelen: 1000
                RX bytes: 9840  (9. 8 KB)    TX bytes: 9840  (9.  8 KB)

---

### Post by jtarin on 2011-07-28
OK...it looks as if your module for your eth0 card is not loaded, so let's find out what kind it is and see if we can get it loaded.
Type ```
lspci
``` in a terminal and post the results. Likewise, issue the command ```
lsmod
``` and post the results.

---

### Post by rgaskins on 2011-07-29
On my terminal window, I typed the lspci and lsmod commands.  Since I completely deleted Windows XP from my system, I have to manually type in on another computer the results of the commands.  Hopefully I typed what I saw.  If there is a problem with results that you see I will check it again.  Too bad I cannot do a cut and paste.
 
$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL [Brookdale-G]/GE/PE]
DRAM Controller/Host-Hub Interface (rev 01)[/SIZE][/FONT]
00:01.0 PCI bridge: Intel Corporation 82845G/GL [Brookdale-G]/GE/PE 
Host &#8211;to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM 
(ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801 DB/DLB/DBM 
(ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM 
(ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM 
(ICH4/ICH4-M) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI Bridge: Intel Corporation 82801 PCI Bridge (rev81)
00:1f.0 ISAbridge: Intel Corporation 82801DB/DBL
(ICH$/ICH4-L) LPC Interface bridge (rev 01)
00:1f.1 IDE Interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:01f.3 SMBus: Intel Corporation 82801DB/DBL/DBM
(ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia Audio Controller: Intel Corporation 82801DB/DBL/DBM 
(ICH4/ICH4-L/ICH4-M) AC&#8217;97 Audio Controller (rev 01)
01:00.0 VGA compatible controller ATI Technologies Inc Rage 128 Pro Ultra TF
02:08.0 Ethernet Controller: Intel Corporation 82801DB
PRO/100 VE (LOM) Ethernet Controller (rev 81)
 
$ lsmod
Module                                   Size        Used by
R128                                      35342      3
Drm                                        168054    4
Binfmt_misc                          6599         1
Snd_intel8x0                          25632      2
Snd_ac97_codec                    99227      1            snd_intel8x0[/SIZE][/FONT]
Ac97_bus                               1014        1            snd_ac97_codec
Snd_pcm                                71475      2            snd_intel8x0, snd_ac97_codec[/SIZE][/FONT]
Snd_seq_midi                        4588        0
Snd_rawmidi     `                    17783     1            snd_seq_midi
Snd_seq_midi_event              6047       1            snd_seq_midi
Snd_seq                                  47174      2           snd_seq_midi, snd_seq_midi_event
Snd_timer                               19067      2            snd_pcm, snd_seq
Snd_seq_device                      5744       3             snd_seq_midi, snd_rawmidi, snd_seq
Ppdev                                      5556         0
Usblp                                      10615        0
Parport_pc                              26058        1
Intel_agp                                 26360       1
Dcdbas                                    5402         0
Snd                                          49006      11         snd_intel8x0,  snd_ac97_codec, snd_pcm, snd_rawmidi, snd_seq, snd_timer, snd_seq_device
Psmouse                                59033      0
Agpgart                                  32011      2            drm, intel_app
Serio_raw                              4022         0
[Shpchp                                   29886      0
Soundcore                             880           1            snd
Snd_page_alloc                    7120         2            snd_intel8x0, snd_pcm
Lp                                          7342         0
Parport                                  31492      3            ppdev, parport_pc, lp
E100                                      30356      0
Floppy                                    5433         0
Mii                                         4421         1            e100

---

### Post by jtarin on 2011-07-29
> **rgaskins said:**
> 
 So when I click on edit, it asks for the "Device MAC address" which I assume is the modem's MAC address. Then it asks for the "Clone MAC address". I have no idea what that is but I re-entered the modem's MAC address. I still had no internet connection.
 Use the MAC address of eth0 card (from ifconfig-[COLOR="Red"]00:07:e9:b0:60:e0[/COLOR]) not the modem. I just caught that.
Leave "Clone" alone.:P

---

### Post by jtarin on 2011-07-29
I'm assuming this is a static address (never changes)as your always connected with the same address, so Network Manager is not needed..
Try to follow [these]("http://www.liberiangeek.net/2010/08/quickly-disable-network-manager-ubuntu-10-04-lucid-lynx/") instructions and configure for a Static IP not DHCP.Note the part about:_To configure a Static IP, enter the lines as shown below and save. Replace the IP addresses with your own._

---

