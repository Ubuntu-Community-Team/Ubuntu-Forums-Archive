---
title: "Z77 &amp; i3570 on board graphics HDMI issues (audio and video)"
date: 2012-07-21
forum: Multimedia Software
---

### Post by guisar on 2012-07-21
HTPC using a ASRock Z77 Pro with i5 3570.  Have a Razer AC1 sound card using TOSlink to AVR and an Intel 9400GT installed.  HDMI output is routed through Pioneer VSX23 to a Panasonic Plasma.

Problem 1: HDMI video out via on-board graphics results in snow and period "glitch".  The BIOS screen shows up fine but KDM and GDM both just result in snow on the plasma.  I installed the 9400GT and it works fine.  Are the on-board graphics just not acquiring the Pioneer EDID or is there some other some other glitch I should be looking at.

Problem 2: This board has "HD Intel Graphics" including an HDMI out port which I presumed would allow HDMI audio out. However, no HDMI audio device shows up in the pulseaudio options or lspci.  Does Ubuntu (Precise) or Linux not have a driver which recognizes the HDMI device in the on-board graphics or am I missing something else?  I'm not above saying Fit and getting a new video card which 'just works' but I'd hoped the on-board graphics of the 3570/Z77 would be golden instead of completely non-functional.  Here are the lspci results:

00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0150] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Ivy Bridge PCI Express Root Port [8086:0151] (rev 09)
00:02.0 Display controller [0380]: Intel Corporation Ivy Bridge Graphics Controller [8086:0162] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c4)
00:1c.5 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 6 [8086:1e1a] (rev c4)
00:1c.7 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 8 [8086:1e1e] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e44] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e02] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G96 [GeForce 9400 GT] [10de:0641] (rev a1)
03:00.0 PCI bridge [0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 01)
04:01.0 Multimedia audio controller [0401]: C-Media Electronics Inc CMI8788 [Oxygen HD Audio] [13f6:8788]
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
06:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)

---

### Post by orzetto on 2012-08-07
Hi, I have a similar problem. My mainboard is a [Gigabyte GA-H77-DS3H]("http://www.gigabyte.com/products/product-page.aspx?pid=4146#ov"), which has the Intel H77 chipset ([a budget version of Z77]("http://www.pugetsystems.com/blog/2012/04/12/z68-z77-and-h77-whats-the-difference/")).
I looked forward to connecting my PC to my TV with a single digital cable instead of the previous VGA+sound, so I was disappointed when I saw that HDMI was carrying video only.

Searching specifically for my board, I found that the issue is solvable in Windows [by updating the drivers with Intel's latest]("http://forums.anandtech.com/showpost.php?p=33247140&postcount=11").
A common trap is that people confuse the audio and the video chipset in this problem: even though we want audio, it is the video chipset support that is important, because that is what passes the sound to the HDMI socket.

So, hm, no solution yet but I confirm the issue. I tried to start jockey, but no proprietary driver is available for the on-board graphics card.

Maybe with some later kernel update things will start to work. If pavucontrol one day shows a "Intel Display Audio" that you had not seen before, you have struck gold.

Intel does not seem to offer binary blobs for Linux that we might try out (though I would probably prefer to stick to VGA, it is not that bad).

---

### Post by orzetto on 2012-08-08
And here is the solution (at least to your Problem 2)!

In Pavucontrol, there should be only one device under Configuration, namely "Internal Audio". Under the profiles, there is usually an option for HDMI (which I initially overlooked because I expected two devices). However, choosing it will stop analogue output, which means you will need to HDMI and back to analogue every time you want to use the HDMI device (in my case the telly).

Fortunately, you can follow [[COLOR="Blue"]this simple procedure[/COLOR]]("https://wiki.archlinux.org/index.php/PulseAudio/Examples#Simultaneous_HDMI_and_Analog_Output") from the PulseAudio wiki to output to both HDMI and analogue. It boils down to adding the following at the end of [FONT="Courier New"]/etc/pulse/default.pa[/FONT]:
```
### Load analog device
load-module module-alsa-sink device=hw:0,0
load-module module-combine-sink sink_name=combined
set-default-sink combined
```

You can then restart the PC (or log out, restart Pulseaudio and log back in), and hey presto, a new combined output device has appeared in pavucontrol's Output Devices tab! (Note, not the Configuration tab)

However, it will default to HDMI only (at least it did for me). The above-referenced wiki suggests assigning the simultaneous output one application at a time, which is obviously tedious and silly. In KDE, I went to the System Settings, Hardware, Multimedia, Phonon and put the Simultaneous Output as first option for all playback classes.

This did the trick for me, I hope it works just as well for you!

---

