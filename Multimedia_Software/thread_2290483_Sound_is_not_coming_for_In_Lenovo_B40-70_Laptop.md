---
title: "Sound is not coming for In Lenovo B40-70 Laptop"
date: 2015-08-12
forum: Multimedia Software
---

### Post by pradeep16 on 2015-08-12
I have ubuntu 12.04 64 bit installed. As I try connecting to a wireless   connection, it asks for credentials and then every 2 minutes it asks  for  credentials again. Just doesn't connect. 

**$ uname -a**
*Linux user-Lenovo-B40-70 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:20:02 UTC 2013 i686 i686 i386 GNU/Linux*

[B]$ lspci
[/B]
[I]00:00.0 Host bridge: Intel Corporation Device 0a04 (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Device 0a16 (rev 0b)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 0b)
00:14.0 USB controller: Intel Corporation Device 9c31 (rev 04)
00:16.0 Communication controller: Intel Corporation Device 9c3a (rev 04)
00:1b.0 Audio device: Intel Corporation Device 9c20 (rev 04)
00:1c.0 PCI bridge: Intel Corporation Device 9c10 (rev e4)
00:1c.1 PCI bridge: Intel Corporation Device 9c12 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Device 9c14 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Device 9c16 (rev e4)
00:1d.0 USB controller: Intel Corporation Device 9c26 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 9c43 (rev 04)
00:1f.2 SATA controller: Intel Corporation Device 9c03 (rev 04)
00:1f.3 SMBus: Intel Corporation Device 9c22 (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 10)
09:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device b723


[/I]**$ lsmod**
[I]
Module                  Size  Used by
snd_hda_codec_realtek   174313  0 
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  17948  2 
bluetooth             158479  23 rfcomm,bnep,btusb
snd                    62218  13  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,   snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,sn  d_seq_device
soundcore              14635  1 snd
ideapad_laptop         17890  0 
video                  19115  0 
sparse_keymap          13658  1 ideapad_laptop
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
psmouse                96718  0 
serio_raw              13027  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0 

[/I][B]Note:If I connect Headphone(Inserting Jack) sound is coming...If i remove jack sound not coming........
[/B]Please let me know, if more  info. is needed. Would greatly appreciate any help.Thanks In Adv.,
Pradeep Kumar G.

---

### Post by ajgreeny on 2015-08-12
In view of the problems you are having with sound in this thread and wifi in [http://ubuntuforums.org/showthread.php?t=2290481&p=13337355#post13337355](http://ubuntuforums.org/showthread.php?t=2290481&p=13337355#post13337355) on the same hardware, I wonder if you have tried a live version of 14.04 or even 15.04, which both have later kernel versions than you are using and may be able to solve your difficulties without any other action from you.

More recent kernels can often solve this sort of problem, however, you may need to open sound settings from the volume icon in the panel and check that none of your audio hardware is muted or volume set too low.

---

