---
title: "Lost wireless card / presario F500 / ubuntu v10.04"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by Epsylon0 on 2010-06-23
Dear Ubuntu forum members,

Yesterday, I lost wireless capability on my laptop. The card seem to have just vanished from the system, and I do not understand why. There is a switch in the front to activate/deactivate the wireless, but no matter the position, the led stay red (well, orange actually, vs. blue if activated)
I have looked in System>Admin>Hardware drivers and updated every software with no results. Even installed Wicd but it still does not see any wireless device.
Windows drivers seem to exist only for Vista 64bits, and will not load. But that should not be the problem since it has always worked before.

I am posting below the usual system reports. Spare with me if I am posting the wrong reports: I am new to Ubuntu. If you have any idea, thank you for your help!


> **lspci:**
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

> 
**lsmod**
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_conexant    22577  1 
joydev                  8708  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               7087672  27 
soundcore               6620  1 snd
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
psmouse                63245  0 
k8temp                  3024  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_nforce2             5199  0 
agpgart                31724  1 nvidia
vga16fb                11385  1 
vgastate                8961  1 vga16fb
serio_raw               3978  0 
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
pata_amd                8766  0 
sata_nv                19440  2 
forcedeth              49556  0 

---

### Post by friskydiscus on 2010-07-09
Hi

I saw this originally on Ubuntu Addict but couldn't see any way to register on that forum to reply but quite randomly I found your same post here!

Anyway, its been two weeks since you posted so perhaps you have solved this but if not these are my suggestions.

I experienced a similar problem with my F500 within about a year of purchase. It seems the problem was motherboard related and a "known" problem as the laptop was fixed without questions and free of charge out of warranty (I was very late to get in touch with HP support). You may not have the same problem at all though. My wireless card did not give up all at once, it behaved temperamentally for about a week and then gave up, but in the same way you mention, solid orange light and no where in the Device manager (this happened when I still had Vista on here). About 6 months later a problem with a static electric sensor on the motherboard prevented the laptop from booting and I eventually got in touch with HP who picked up and repaired the laptop quick sharp. As I found out the static sensor problem is a common one with this model, as is the wireless problem. I'm not sure this is the most updated site but have a look here and compare your model number, you should be eligible for free repair:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01480071&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01480071&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

Of course the problem might not be hardware at all! If it is not easy for you to boot with Windows to double check I would suggest booting with a Ubuntu Live CD, eg the one you installed from. For some reason it detects, or rather is able to offer the correct proprietary drivers for the Wireless card (not the first choice one, the other one it offers under hardware drivers, I cant remember which one). If Ubuntu fails to detect the wireless card with the Live CD then it might be hardware related.

Also if you bought the laptop with Windows installed I would probably give restoring windows a try as a last resort. If you do end up sending your laptop to HP probably best to restore Windows or take out your HDD before sending as they may try blame the problem on Ubuntu.

Anyway thats my advice. Bit long winded sorry.

C

---

### Post by spegru on 2010-07-30
I have exactly the same problem. Wireless was fine until three days ago (which did in fact coincided with a normal system update although I suspect that was unrelated).
In fact I'm using Linux Mint 9 which is largely the same as Ubuntu 10.04.
I wish I could remember what the lspci command would reveal before but right now I cant see any wireless related items at all, just loads of nvidia & AMD stuff. It's as if someone removed the internal card.
However it does seem a remarkable coincidence that you Epsylon0 had the same problem at seemingly almost the same time!

I am away from home right now, but when I return in a couple of days I intend to dismantle the machine and physically remove the wifi wireless card/refit. If that still fails I'll try a replacement wifi card.

spegru

PS. By the way I'm also interested in friskydiscus's experience. I also had a bad experience with my f500 *just after it went out of warranty*, where it just wouldn't boot at all. However it was not on their list of affected serial numbers and they wouldn't do anything! In the end I got another machine with a broken LCD off ebay and spliced the parts together.
I'd have to say that that experience, combined with that of a friend who had an HP (same company) machine running XP that had exactly the same non booting problem is enough to put me right off buying any HP/Compaq machine in the future!
(However my machine has now been working fine for about 2 yrs so I think this wifi problem is separate.)

---

### Post by spegru on 2010-07-30
A bit of a look into that HP site reveals that my laptop is not running the latest bios f.1f, it's only f.18 (presuming the number is written in hex).

I'll have a go at installing that too. the only problem is that the flash utility is windows only and I don't have that on this any more.
I'll have to go through the rigmarole of installing xp and then removing it I guess - unless anyone has any better ideas

---

### Post by Ubunzo on 2011-03-01
i've experienced the same problem and it seems to depend from the HW.
HP tracked the problem, it might be the fault of nvidia's motherboard.
The two solutions are either cleaning the wireless card's attachement on the motherboard (very risky indeed, if you don't know what u r doing), or buying a usb wireless card.
More information here:
[http://www.fixya.com/support/t1828685-compaq_presario_f500_wireless_or]("http://www.fixya.com/support/t1828685-compaq_presario_f500_wireless_or")

---

### Post by tequese on 2011-03-01
I have a similar problem, I have an acer aspire and was running Ubuntu and recently reinstalled it allong with windows 7 for duel boot. Before I resinstalled ubuntu the wireless worked fine, now it only works on windows 7 and like you said, you can click the button to activate wireless and deactivate but it does nothing. 
 
Have you managed to solve it? if you how?

---

