---
title: "Atheros AR5900 b/g/n built in/Hp G60 120US laptop/Ubuntu 10.10"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by kbz1960 on 2011-01-19
Hello, first off my wireless use to work on the live usb and now doesn't. It also has changed behavior in windows where the button to activate/deactivate is no longer flashing blue for orange while booting windows and then going solid blue by the time it gets to where I type my password in. Now it no longer does the flash and when I get to where I enter my password I have to push the button twice to get it blue (active).
 
If this can't get resolved can you recommend a wireless N usb adapter that will work both in windows 7 and Ubuntu.
 
Thanks in advance and here is the output from the codes. Sorry if something is messed up because I'm using my phone to tether in windows for a connection right now so I had to run the commands and paste into word then come back to windows and copy/paste to here.
 
Went to post and got a message about too many images and never put any images in but went thru and sure enought smilelys all over. I imagine that messed things up too. If you need something reposted just ask and I will.
 
> 
[SIZE=3][FONT=Batang]:~$ lspci[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)[/FONT][/SIZE]
 
[FONT=Liberation Serif]07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)[/FONT]
 

 
> 
[SIZE=3][FONT=Batang]:~$ lspci -nn | grep 'AR928X'[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]07:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)[/FONT][/SIZE]

 
> 
[SIZE=3][FONT=Batang]:~$ ifconfig[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]eth0 Link encap:Ethernet HWaddr 00:1d:72:75:ee:ec [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]UP BROADCAST MULTICAST MTU:1500 Metric:1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]collisions:0 txqueuelen:1000 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]Interrupt:42 Base address:0x8000 [/FONT][/SIZE]
 
 
 
[SIZE=3][FONT=Batang]lo Link encap:Local Loopback [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]inet addr:127.0.0.1 Mask:255.0.0.0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]UP LOOPBACK RUNNING MTU:16436 Metric:1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]RX packets:12 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]TX packets:12 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]collisions:0 txqueuelen:0 [/FONT][/SIZE]
 
[FONT=Liberation Serif]RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)[/FONT]
 

 
> 
[SIZE=3][FONT=Batang]:~$ iwconfig[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]lo no wireless extensions.[/FONT][/SIZE]
 
 
 
[SIZE=3][FONT=Batang]eth0 no wireless extensions.[/FONT][/SIZE]
 
 
 
[SIZE=3][FONT=Batang]wlan0 IEEE 802.11abgn ESSIDff/any [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]Mode:Managed Access Point: Not-Associated Tx-Power=off [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]Retry long limit:7 RTS thrff Fragment thrff[/FONT][/SIZE]
 
[FONT=Liberation Serif]Power Managementff[/FONT]
 

 
> 
[SIZE=3][FONT=Batang]:~$ lsmod[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]Module Size Used by[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]binfmt_misc 6599 1 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]parport_pc 26058 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]ppdev 5556 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]nvidia 9329739 40 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]joydev 8767 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_hda_codec_nvhdmi 13615 1 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_hda_codec_conexant 29971 1 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]arc4 1165 2 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_hda_intel 22107 2 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_hda_codec 87552 3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_hwdep 5040 1 snd_hda_codec[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_pcm 71475 2 snd_hda_intel,snd_hda_codec[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]ath9k 88756 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_seq_midi 4588 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_rawmidi 17783 1 snd_seq_midi[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_seq_midi_event 6047 1 snd_seq_midi[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]ath9k_common 5982 1 ath9k[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_seq 47174 2 snd_seq_midi,snd_seq_midi_event[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]ath9k_hw 292297 2 ath9k,ath9k_common[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]ath 8153 2 ath9k,ath9k_hw[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_timer 19067 2 snd_pcm,snd_seq[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_seq_device 5744 3 snd_seq_midi,snd_rawmidi,snd_seq[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]mac80211 231541 2 ath9k,ath9k_common[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]hp_wmi 5223 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]uvcvideo 55847 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]video 18712 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]cfg80211 144470 4 ath9k,ath9k_common,ath,mac80211[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]output 1883 1 video[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd 49038 13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]agpgart 32011 1 nvidia[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]videodev 43098 1 uvcvideo[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]soundcore 880 1 snd[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]v4l1_compat 13359 2 uvcvideo,videodev[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]psmouse 59033 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]serio_raw 4022 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]led_class 2633 1 ath9k[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]k10temp 2607 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]snd_page_alloc 7120 2 snd_hda_intel,snd_pcm[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]i2c_nforce2 5179 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]shpchp 29886 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]lp 7342 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]parport 31492 3 parport_pc,ppdev,lp[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]usb_storage 40172 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]ahci 19198 4 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]libahci 21664 1 ahci[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]pata_amd 8746 0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]forcedeth 49433 0 [/FONT][/SIZE]

 
> 
[SIZE=3][FONT=Batang]kernal boot msg[/FONT][/SIZE]
[SIZE=3][FONT=Batang][ 0.208833] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.208837] pci_root PNP0A08:00: host bridge window [mem 0x000f0000-0x000fffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.208840] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209095] pci 0000:00:01.0: reg 10: [io 0x1a00-0x1aff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209147] pci 0000:00:01.1: reg 10: [io 0x3080-0x30bf][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209163] pci 0000:00:01.1: reg 20: [io 0x3040-0x307f][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209170] pci 0000:00:01.1: reg 24: [io 0x3000-0x303f][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209196] pci 0000:00:01.1: PME# supported from D3hot D3cold[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209203] pci 0000:00:01.1: PME# disabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209237] pci 0000:00:01.3: reg 10: [mem 0xc0080000-0xc00fffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209392] pci 0000:00:02.0: reg 10: [mem 0xc0006000-0xc0006fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209428] pci 0000:00:02.0: supports D1 D2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209431] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209435] pci 0000:00:02.0: PME# disabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209463] pci 0000:00:02.1: reg 10: [mem 0xc0007000-0xc00070ff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209505] pci 0000:00:02.1: supports D1 D2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209508] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209512] pci 0000:00:02.1: PME# disabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209547] pci 0000:00:04.0: reg 10: [mem 0xc0008000-0xc0008fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209583] pci 0000:00:04.0: supports D1 D2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209585] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209590] pci 0000:00:04.0: PME# disabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209618] pci 0000:00:04.1: reg 10: [mem 0xc0007400-0xc00074ff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209661] pci 0000:00:04.1: supports D1 D2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209663] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209668] pci 0000:00:04.1: PME# disabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209715] pci 0000:00:06.0: reg 20: [io 0x30c0-0x30cf][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209767] pci 0000:00:07.0: reg 10: [mem 0xc0000000-0xc0003fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209810] pci 0000:00:07.0: PME# supported from D3hot D3cold[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209814] pci 0000:00:07.0: PME# disabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209896] pci 0000:00:09.0: reg 10: [io 0x30f0-0x30f7][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209902] pci 0000:00:09.0: reg 14: [io 0x30e4-0x30e7][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209908] pci 0000:00:09.0: reg 18: [io 0x30e8-0x30ef][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209913] pci 0000:00:09.0: reg 1c: [io 0x30e0-0x30e3][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209919] pci 0000:00:09.0: reg 20: [io 0x30d0-0x30df][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209924] pci 0000:00:09.0: reg 24: [mem 0xc0004000-0xc0005fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209981] pci 0000:00:0a.0: reg 10: [mem 0xc0009000-0xc0009fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209987] pci 0000:00:0a.0: reg 14: [io 0x30f8-0x30ff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209992] pci 0000:00:0a.0: reg 18: [mem 0xc0007c00-0xc0007cff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.209998] pci 0000:00:0a.0: reg 1c: [mem 0xc0007800-0xc000780f][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210030] pci 0000:00:0a.0: supports D1 D2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210032] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210038] pci 0000:00:0a.0: PME# disabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210092] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210096] pci 0000:00:0b.0: PME# disabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210324] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210333] pci 0000:00:14.0: PME# disabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210598] pci 0000:00:08.0: PCI bridge to [bus 01-01] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210603] pci 0000:00:08.0: bridge window [io 0xf000-0x0000] (disabled)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210609] pci 0000:00:08.0: bridge window [mem 0xfff00000-0x000fffff] (disabled)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210614] pci 0000:00:08.0: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210617] pci 0000:00:08.0: bridge window [io 0x0000-0x0cf7] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210620] pci 0000:00:08.0: bridge window [io 0x0d00-0xffff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210623] pci 0000:00:08.0: bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210627] pci 0000:00:08.0: bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210630] pci 0000:00:08.0: bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210633] pci 0000:00:08.0: bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210636] pci 0000:00:08.0: bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210640] pci 0000:00:08.0: bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210643] pci 0000:00:08.0: bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210646] pci 0000:00:08.0: bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210649] pci 0000:00:08.0: bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210652] pci 0000:00:08.0: bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210656] pci 0000:00:08.0: bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210659] pci 0000:00:08.0: bridge window [mem 0x000ec000-0x000effff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210662] pci 0000:00:08.0: bridge window [mem 0x000f0000-0x000fffff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210665] pci 0000:00:08.0: bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210712] pci 0000:02:00.0: reg 10: [mem 0xc1000000-0xc1ffffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210722] pci 0000:02:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210731] pci 0000:02:00.0: reg 1c: [mem 0xc4000000-0xc5ffffff 64bit pref][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210736] pci 0000:02:00.0: reg 24: [io 0x4000-0x407f][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210742] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210786] pci 0000:00:0b.0: PCI bridge to [bus 02-02][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210791] pci 0000:00:0b.0: bridge window [io 0x4000-0x4fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210796] pci 0000:00:0b.0: bridge window [mem 0xc1000000-0xc1ffffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.210802] pci 0000:00:0b.0: bridge window [mem 0xc4000000-0xdfffffff 64bit pref][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211002] pci 0000:07:00.0: reg 10: [mem 0xc2000000-0xc200ffff 64bit][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211063] pci 0000:07:00.0: supports D1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211065] pci 0000:07:00.0: PME# supported from D0 D1 D3hot[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211070] pci 0000:07:00.0: PME# disabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211095] pci 0000:07:00.0: disabling ASPM on pre-1.1 PCIe device. You can enable it with 'pcie_aspm=force'[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211110] pci 0000:00:14.0: PCI bridge to [bus 07-07][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211126] pci 0000:00:14.0: bridge window [io 0xf000-0x0000] (disabled)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211135] pci 0000:00:14.0: bridge window [mem 0xc2000000-0xc20fffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211150] pci 0000:00:14.0: bridge window [mem 0xfff00000-0x000fffff pref] (disabled)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211175] pci_bus 0000:00: on NUMA node 0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211180] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211288] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.211390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.233467] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.233648] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 11 14 15) *0, disabled.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.233825] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.234004] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.234180] ACPI: PCI Interrupt Link [Z012] (IRQs 19 20 21 22 23) *10[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.234356] ACPI: PCI Interrupt Link [Z013] (IRQs 19 20 21 22 23) *0, disabled.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.234534] ACPI: PCI Interrupt Link [Z014] (IRQs 19 20 21 22 23) *0, disabled.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.234711] ACPI: PCI Interrupt Link [Z015] (IRQs 19 20 21 22 23) *0, disabled.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.234889] ACPI: PCI Interrupt Link [LSMB] (IRQs 1 *10[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.235062] ACPI: PCI Interrupt Link [LUS0] (IRQs 17) *11[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.235238] ACPI: PCI Interrupt Link [LUS2] (IRQs 17) *7[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.235420] ACPI: PCI Interrupt Link [LMAC] (IRQs 19 20 21 22 23) *11[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.235596] ACPI: PCI Interrupt Link [LAZA] (IRQs 19 20 21 22 23) *10[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.235772] ACPI: PCI Interrupt Link [LGPU] (IRQs 19 20 21 22 23) *10[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.235949] ACPI: PCI Interrupt Link [LPID] (IRQs 19 20 21 22 23) *0, disabled.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.236130] ACPI: PCI Interrupt Link [LSI0] (IRQs 19 20 21 22 23) *11[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.236308] ACPI: PCI Interrupt Link [LSI1] (IRQs 19 20 21 22 23) *0, disabled.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.236485] ACPI: PCI Interrupt Link [Z010] (IRQs 16) *5[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.236664] ACPI: PCI Interrupt Link [Z011] (IRQs 16) *10[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.236838] ACPI: PCI Interrupt Link [LPMU] (IRQs 1 *11[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.236879] HEST: Table is not found![/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.236981] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.236984] vgaarb: loaded[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237171] SCSI subsystem initialized[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237273] libata version 3.00 loaded.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237331] usbcore: registered new interface driver usbfs[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237346] usbcore: registered new interface driver hub[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237373] usbcore: registered new device driver usb[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237646] ACPI: WMI: Mapper loaded[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237649] PCI: Using ACPI for IRQ routing[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237653] PCI: pci_cache_line_size set to 64 bytes[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237755] reserve RAM buffer: 0000000000002000 - 000000000000ffff [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237758] reserve RAM buffer: 000000000009e000 - 000000000009ffff [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237761] reserve RAM buffer: 00000000afed0000 - 00000000afffffff [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237863] NetLabel: Initializing[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237865] NetLabel: domain hash size = 128[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237867] NetLabel: protocols = UNLABELED CIPSOv4[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237881] NetLabel: unlabeled traffic allowed by default[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237919] HPET: 3 timers in total, 0 timers will be used for per-cpu timer[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237927] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.237933] hpet0: 3 comparators, 32-bit 25.000000 MHz counter[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.244032] Switching to clocksource hpet[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.253885] AppArmor: AppArmor Filesystem Enabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.253906] pnp: PnP ACPI init[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.253929] ACPI: bus type pnp registered[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259654] pnp: PnP ACPI: found 12 devices[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259656] ACPI: ACPI bus type pnp unregistered[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259660] PnPBIOS: Disabled by ACPI PNP[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259675] system 00:02: [mem 0xe0000000-0xefffffff] has been reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259682] system 00:03: [io 0x0360-0x0361] has been reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259685] system 00:03: [io 0x04d0-0x04d1] has been reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259689] system 00:03: [mem 0xff800000-0xff800fff] has been reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259697] system 00:0a: [io 0x1000-0x107f] has been reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259700] system 00:0a: [io 0x1080-0x10ff] has been reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259703] system 00:0a: [io 0x1200-0x127f] has been reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259706] system 00:0a: [io 0x1280-0x12ff] has been reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259709] system 00:0a: [io 0x1400-0x147f] has been reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259713] system 00:0a: [io 0x1480-0x14ff] has been reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259719] system 00:0b: [mem 0xffc00000-0xffffffff] could not be reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259722] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259726] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259729] system 00:0b: [mem 0xfed00000-0xfed00fff] has been reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.259733] system 00:0b: [mem 0xfef00000-0xfef00fff] has been reserved[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.295877] pci 0000:00:08.0: PCI bridge to [bus 01-01][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.295880] pci 0000:00:08.0: bridge window [io disabled][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.295885] pci 0000:00:08.0: bridge window [mem disabled][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.295889] pci 0000:00:08.0: bridge window [mem pref disabled][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.295899] pci 0000:02:00.0: BAR 6: assigned [mem 0xc6000000-0xc601ffff pref][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.295903] pci 0000:00:0b.0: PCI bridge to [bus 02-02][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.295906] pci 0000:00:0b.0: bridge window [io 0x4000-0x4fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.295911] pci 0000:00:0b.0: bridge window [mem 0xc1000000-0xc1ffffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.295916] pci 0000:00:0b.0: bridge window [mem 0xc4000000-0xdfffffff 64bit pref][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296150] pci 0000:00:14.0: PCI bridge to [bus 07-07][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296152] pci 0000:00:14.0: bridge window [io disabled][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296164] pci 0000:00:14.0: bridge window [mem 0xc2000000-0xc20fffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296174] pci 0000:00:14.0: bridge window [mem pref disabled][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296196] pci 0000:00:08.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296205] pci 0000:00:0b.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296508] ACPI: PCI Interrupt Link [Z012] enabled at IRQ 23[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296513] alloc irq_desc for 23 on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296515] alloc kstat_irqs on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296527] pci 0000:00:14.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296536] pci 0000:00:14.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296543] pci_bus 0000:00: resource 4 [io 0x0000-0x0cf7][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296546] pci_bus 0000:00: resource 5 [io 0x0d00-0xffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296549] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296552] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296555] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296558] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296561] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296563] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296566] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296569] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296572] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296575] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296578] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296581] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296584] pci_bus 0000:00: resource 18 [mem 0x000f0000-0x000fffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296587] pci_bus 0000:00: resource 19 [mem 0xc0000000-0xfebfffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296590] pci_bus 0000:01: resource 4 [io 0x0000-0x0cf7][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296593] pci_bus 0000:01: resource 5 [io 0x0d00-0xffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296596] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296599] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000c3fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296602] pci_bus 0000:01: resource 8 [mem 0x000c4000-0x000c7fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296605] pci_bus 0000:01: resource 9 [mem 0x000c8000-0x000cbfff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296607] pci_bus 0000:01: resource 10 [mem 0x000d0000-0x000d3fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296610] pci_bus 0000:01: resource 11 [mem 0x000d4000-0x000d7fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296613] pci_bus 0000:01: resource 12 [mem 0x000d8000-0x000dbfff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296616] pci_bus 0000:01: resource 13 [mem 0x000dc000-0x000dffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296619] pci_bus 0000:01: resource 14 [mem 0x000e0000-0x000e3fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296622] pci_bus 0000:01: resource 15 [mem 0x000e4000-0x000e7fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296625] pci_bus 0000:01: resource 16 [mem 0x000e8000-0x000ebfff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296628] pci_bus 0000:01: resource 17 [mem 0x000ec000-0x000effff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296631] pci_bus 0000:01: resource 18 [mem 0x000f0000-0x000fffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296634] pci_bus 0000:01: resource 19 [mem 0xc0000000-0xfebfffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296637] pci_bus 0000:02: resource 0 [io 0x4000-0x4fff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296640] pci_bus 0000:02: resource 1 [mem 0xc1000000-0xc1ffffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296643] pci_bus 0000:02: resource 2 [mem 0xc4000000-0xdfffffff 64bit pref][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296646] pci_bus 0000:07: resource 1 [mem 0xc2000000-0xc20fffff][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296691] NET: Registered protocol family 2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.296765] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.297081] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.297801] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.298132] TCP: Hash tables configured (established 131072 bind 65536)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.298135] TCP reno registered[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.298141] UDP hash table entries: 512 (order: 2, 16384 bytes)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.298155] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.298259] NET: Registered protocol family 1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.298538] pci 0000:00:07.0: Enabling HT MSI Mapping[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.298665] pci 0000:00:08.0: Enabling HT MSI Mapping[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.298803] pci 0000:00:09.0: Enabling HT MSI Mapping[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.298948] pci 0000:00:0a.0: Enabling HT MSI Mapping[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.299096] pci 0000:00:0b.0: Enabling HT MSI Mapping[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.299181] pci 0000:02:00.0: Boot video device[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.299188] PCI: CLS 0 bytes, default 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.299222] Simple Boot Flag at 0x38 set to 0x1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.299435] cpufreq-nforce2: No nForce2 chipset.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.299470] Scanning for low memory corruption every 60 seconds[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.299638] audit: initializing netlink socket (disabled)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.299650] type=2000 audit(1295430033.296:1): initialized[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.311147] highmem bounce pool size: 64 pages[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.311153] HugeTLB registered 4 MB page size, pre-allocated 0 pages[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.312630] VFS: Disk quotas dquot_6.5.2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.312695] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.313338] fuse init (API version 7.14)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.313434] msgmni has been set to 1663[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.313753] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.313757] io scheduler noop registered[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.313759] io scheduler deadline registered[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.313772] io scheduler cfq registered (default)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.313924] pcieport 0000:00:14.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.314050] alloc irq_desc for 40 on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.314053] alloc kstat_irqs on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.314076] pcieport 0000:00:14.0: irq 40 for MSI/MSI-X[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.314241] pci_hotplug: PCI Hot Plug PCI Core version: 0.5[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.314267] pciehp: PCI Express Hot Plug Controller Driver version: 0.4[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.316326] ACPI: AC Adapter [ADP1] (on-line)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.316397] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.318628] ACPI: Lid Switch [LID0][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.318678] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.318684] ACPI: Sleep Button [SLPB][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.318745] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.318749] ACPI: Power Button [PWRB][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.318792] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.318795] ACPI: Power Button [PWRF][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.319032] ACPI: acpi_idle registered with cpuidle[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.343771] thermal LNXTHERM:01: registered as thermal_zone0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.343780] ACPI: Thermal Zone [TZS0] (74 C)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.352854] thermal LNXTHERM:02: registered as thermal_zone1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.352863] ACPI: Thermal Zone [TZS1] (74 C)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.352976] ERST: Table is not found![/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.353252] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.354718] brd: module loaded[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.355271] loop: module loaded[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.355567] pata_acpi 0000:00:06.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.355911] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 22[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.355918] alloc irq_desc for 22 on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.355921] alloc kstat_irqs on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.355934] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 22 (level, low) -> IRQ 22[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.355960] pata_acpi 0000:00:09.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.355969] pata_acpi 0000:00:09.0: PCI INT A disabled[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356336] Fixed MDIO Bus: probed[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356375] PPP generic driver version 2.4.2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356422] tun: Universal TUN/TAP device driver, 1.6[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356424] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356504] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356797] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 17[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356800] alloc irq_desc for 17 on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356802] alloc kstat_irqs on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356811] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 17 (level, low) -> IRQ 17[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356830] ehci_hcd 0000:00:02.1: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356835] ehci_hcd 0000:00:02.1: EHCI Host Controller[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356879] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356908] ehci_hcd 0000:00:02.1: debug port 1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356918] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.356943] ehci_hcd 0000:00:02.1: irq 17, io mem 0xc0007000[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.357091] isapnp: Scanning for PnP cards...[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406136] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406271] hub 1-0:1.0: USB hub found[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406276] hub 1-0:1.0: 3 ports detected[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406669] ACPI: PCI Interrupt Link [Z011] enabled at IRQ 16[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406673] alloc irq_desc for 16 on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406675] alloc kstat_irqs on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406684] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z011] -> GSI 16 (level, low) -> IRQ 16[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406698] ehci_hcd 0000:00:04.1: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406702] ehci_hcd 0000:00:04.1: EHCI Host Controller[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406740] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406764] ehci_hcd 0000:00:04.1: debug port 1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406774] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.406794] ehci_hcd 0000:00:04.1: irq 16, io mem 0xc0007400[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.450340] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.450447] hub 2-0:1.0: USB hub found[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.450452] hub 2-0:1.0: 4 ports detected[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.450523] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.450811] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 17[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.450816] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 17 (level, low) -> IRQ 17[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.450826] ohci_hcd 0000:00:02.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.450830] ohci_hcd 0000:00:02.0: OHCI Host Controller[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.450918] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.450932] ohci_hcd 0000:00:02.0: irq 17, io mem 0xc0006000[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.472641] Freeing initrd memory: 10508k freed[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.507203] hub 3-0:1.0: USB hub found[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.507212] hub 3-0:1.0: 3 ports detected[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.507632] ACPI: PCI Interrupt Link [Z010] enabled at IRQ 16[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.507639] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z010] -> GSI 16 (level, low) -> IRQ 16[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.507663] ohci_hcd 0000:00:04.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.507667] ohci_hcd 0000:00:04.0: OHCI Host Controller[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.507712] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.507734] ohci_hcd 0000:00:04.0: irq 16, io mem 0xc0008000[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.562133] hub 4-0:1.0: USB hub found[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.562140] hub 4-0:1.0: 4 ports detected[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.562215] uhci_hcd: USB Universal Host Controller Interface driver[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.562323] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13S2M] at 0x60,0x64 irq 1,12[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.579781] i8042.c: Detected active multiplexing controller, rev 1.1.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.593318] serio: i8042 KBD port at 0x60,0x64 irq 1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.593332] serio: i8042 AUX0 port at 0x60,0x64 irq 12[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.593336] serio: i8042 AUX1 port at 0x60,0x64 irq 12[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.593340] serio: i8042 AUX2 port at 0x60,0x64 irq 12[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.593344] serio: i8042 AUX3 port at 0x60,0x64 irq 12[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.593415] mice: PS/2 mouse device common for all mice[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.593580] rtc_cmos 00:06: RTC can wake from S4[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.593622] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.593680] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.593790] device-mapper: uevent: version 1.0.3[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.593917] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL][/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.593997] device-mapper: multipath: version 1.1.1 loaded[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594001] device-mapper: multipath round-robin: version 1.0.0 loaded[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594121] EISA: Probing bus 0 at eisa.0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594125] EISA: Cannot allocate resource for mainboard[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594128] Cannot allocate resource for EISA slot 1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594131] Cannot allocate resource for EISA slot 2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594133] Cannot allocate resource for EISA slot 3[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594136] Cannot allocate resource for EISA slot 4[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594138] Cannot allocate resource for EISA slot 5[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594141] Cannot allocate resource for EISA slot 6[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594144] Cannot allocate resource for EISA slot 7[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594146] Cannot allocate resource for EISA slot 8[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594148] EISA: Detected 0 cards.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594233] cpuidle: using governor ladder[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594235] cpuidle: using governor menu[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594563] TCP cubic registered[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.594694] NET: Registered protocol family 10[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.595069] lo: Disabled Privacy Extensions[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.595310] NET: Registered protocol family 17[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.595345] powernow-k8: Found 1 AMD Turion Dual-Core RM-70 (2 cpu cores) (version 2.20.00)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.595433] powernow-k8: 0 : pstate 0 (2000 MHz)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.595435] powernow-k8: 1 : pstate 1 (1000 MHz)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.595438] powernow-k8: 2 : pstate 2 (500 MHz)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.606067] ACPI: Battery Slot [BAT0] (battery present)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.621198] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.626100] Using IPI No-Shortcut mode[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.626191] PM: Resume from disk failed.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.626205] registered taskstats version 1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.626517] Magic number: 11:481:677[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.626659] rtc_cmos 00:06: setting system clock to 2011-01-19 09:40:34 UTC (1295430034)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.626663] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.626666] EDD information not available.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.712555] isapnp: No Plug & Play device found[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.712580] Freeing unused kernel memory: 688k freed[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.713117] Write protecting the kernel text: 4932k[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.713159] Write protecting the kernel read-only data: 1980k[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.734162] udev[76]: starting version 163[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.749084] usb 1-1: new high speed USB device using ehci_hcd and address 2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.819478] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.819836] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.819843] alloc irq_desc for 21 on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.819845] alloc kstat_irqs on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.819859] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, low) -> IRQ 21[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.819865] forcedeth 0000:00:0a.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.931897] Initializing USB Mass Storage driver...[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.932068] scsi0 : usb-storage 1-1:1.0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.932209] usbcore: registered new interface driver usb-storage[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 0.932212] USB Mass Storage support registered.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.028478] usb 2-2: new high speed USB device using ehci_hcd and address 2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.341659] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1d:72:75:ee:ec[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.341665] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt lnktim msi desc-v3[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.341695] pata_amd 0000:00:06.0: version 0.4.1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.341749] pata_amd 0000:00:06.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.341854] scsi1 : pata_amd[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.341941] scsi2 : pata_amd[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.341982] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.341985] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342026] ahci 0000:00:09.0: version 3.0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342044] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 22 (level, low) -> IRQ 22[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342099] alloc irq_desc for 41 on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342101] alloc kstat_irqs on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342113] ahci 0000:00:09.0: irq 41 for MSI/MSI-X[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342122] ahci 0000:00:09.0: controller can't do PMP, turning off CAP_PMP[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342170] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 2 ports 3 Gbps 0x3 impl IDE mode[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342174] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pio slum part boh [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342180] ahci 0000:00:09.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342474] scsi3 : ahci[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342558] scsi4 : ahci[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342661] ata3: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 41[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.342665] ata4: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 41[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.496448] ata2: port disabled. ignoring.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.934760] scsi 0:0:0:0: Direct-Access Generic- Multi-Card 1.00 PQ: 0 ANSI: 0 CCS[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.935557] sd 0:0:0:0: Attached scsi generic sg0 type 0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 1.940022] sd 0:0:0:0: [sda] Attached SCSI removable disk[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.064470] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.064494] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.065693] ata4.00: ATA-8: Hitachi HTS543225L9A300, FBEOC44C, max UDMA/100[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.065697] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.067537] ata4.00: configured for UDMA/100[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.068737] ata3.00: ATAPI: HL-DT-ST DVDRAM GSA-T50L, SC05, max UDMA/100[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.073661] ata3.00: configured for UDMA/100[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.186937] scsi 3:0:0:0: CD-ROM HL-DT-ST DVDRAM GSA-T50L SC05 PQ: 0 ANSI: 5[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.517444] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.517448] Uniform CD-ROM driver Revision: 3.20[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.517578] sr 3:0:0:0: Attached scsi CD-ROM sr0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.517650] sr 3:0:0:0: Attached scsi generic sg1 type 5[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.517784] scsi 4:0:0:0: Direct-Access ATA Hitachi HTS54322 FBEO PQ: 0 ANSI: 5[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.517925] sd 4:0:0:0: Attached scsi generic sg2 type 0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.517935] sd 4:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.518001] sd 4:0:0:0: [sdb] Write Protect is off[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.518005] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.518030] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.518309] sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 > sdb3[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 2.580660] sd 4:0:0:0: [sdb] Attached SCSI disk[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 3.305195] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.436043] udev[345]: starting version 163[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.467750] Adding 6346748k swap on /dev/sdb6. Priority:-1 extents:1 across:6346748k [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.557841] lp: driver loaded but no devices found[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.652993] i2c i2c-0: nForce2 SMBus adapter at 0x3040[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.653076] i2c i2c-1: nForce2 SMBus adapter at 0x3000[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.660293] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.791500] Linux video capture interface: v2.00[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.795621] uvcvideo: Found UVC 1.00 device CNF7047 (04f2:b091)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.805165] type=1400 audit(1295448047.678:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=561 comm="apparmor_parser"[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.805479] type=1400 audit(1295448047.678:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=561 comm="apparmor_parser"[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.805661] type=1400 audit(1295448047.678:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=561 comm="apparmor_parser"[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.822793] Linux agpgart interface v0.103[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.836038] input: HP WMI hotkeys as /devices/virtual/input/input5[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.852382] cfg80211: Calling CRDA to update world regulatory domain[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.869015] input: CNF7047 as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input6[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.869086] usbcore: registered new interface driver uvcvideo[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.869088] USB Video Class driver (v0.1.0)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.913336] cfg80211: World regulatory domain updated:[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.913341] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.913345] (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.913348] (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.913351] (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.913354] (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.913357] (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.927564] acpi device:11: registered as cooling_device2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.927734] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0f/LNXVIDEO:00/input/input7[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 13.927806] ACPI: Video Device [VGA] (multi-head: yes rom: no post: no)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.011210] ath9k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.011224] ath9k 0000:07:00.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.069054] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.069062] alloc irq_desc for 20 on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.069065] alloc kstat_irqs on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.069079] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.069083] hda_intel: Disable MSI for Nvidia chipset[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.069147] HDA Intel 0000:00:07.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.069210] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.439317] ath: EEPROM regdomain: 0x69[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.439319] ath: EEPROM indicates we should expect a direct regpair map[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.439324] ath: Country alpha2 being used: 00[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.439326] ath: Regpair used: 0x69[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.450981] phy0: Selected rate control algorithm 'ath9k_rate_control'[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.451750] Registered led device: ath9k-phy0::radio[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.451776] Registered led device: ath9k-phy0::assoc[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.451800] Registered led device: ath9k-phy0::tx[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.451821] Registered led device: ath9k-phy0::rx[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.451830] phy0: Atheros AR9280 Rev:2 mem=0xf8f60000, irq=23[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.493092] nvidia: module license 'NVIDIA' taints kernel.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.493098] Disabling lock debugging due to kernel taint[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.738756] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa00000/0x20000[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.803266] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input8[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.892112] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input9[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.892219] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input10[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 14.892291] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input11[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.699167] EXT4-fs (sdb7): mounted filesystem with ordered data mode. Opts: (null)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.908933] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 19[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.908941] alloc irq_desc for 19 on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.908943] alloc kstat_irqs on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.908959] nvidia 0000:02:00.0: PCI INT A -> Link[LGPU] -> GSI 19 (level, low) -> IRQ 19[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.908969] nvidia 0000:02:00.0: setting latency timer to 64[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.908975] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=nonewns=io+mem[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.910023] NVRM: loading NVIDIA UNIX x86 Kernel Module 260.19.06 Mon Sep 13 06:35:06 PDT 2010[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.937353] type=1400 audit(1295448049.810:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=885 comm="apparmor_parser"[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.937675] type=1400 audit(1295448049.810:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=885 comm="apparmor_parser"[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.937910] type=1400 audit(1295448049.810:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=885 comm="apparmor_parser"[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.943431] type=1400 audit(1295448049.814:: apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=884 comm="apparmor_parser"[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.965614] alloc irq_desc for 42 on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.965620] alloc kstat_irqs on node -1[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.965633] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.965837] eth0: no link during initialization.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.966478] ADDRCONF(NETDEV_UP): eth0: link is not ready[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.968471] type=1400 audit(1295448049.838:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=891 comm="apparmor_parser"[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.968905] type=1400 audit(1295448049.838:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=891 comm="apparmor_parser"[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 15.970191] type=1400 audit(1295448049.842:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=888 comm="apparmor_parser"[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 16.069654] ppdev: user-space parallel port driver[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 17.832884] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 18.001551] EXT4-fs (sdb7): re-mounted. Opts: commit=0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][ 21.827364] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0[/FONT][/SIZE]
 
[FONT=Liberation Serif][ 21.831030] EXT4-fs (sdb7): re-mounted. Opts: commit=0[/FONT]
 
> 
[SIZE=3][FONT=Batang]:~$ sudo lshw -C network[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang][sudo] password for kevin: [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]*-network [/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]description: Ethernet interface[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]product: MCP77 Ethernet[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]vendor: nVidia Corporation[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]physical id: a[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]bus info: pci@0000:00:0a.0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]logical name: eth0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]version: a2[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]serial: 00:1d:72:75:ee:ec[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]capacity: 100MB/s[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]width: 32 bits[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]clock: 66MHz[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]resources: irq:42 memory:c0009000-c0009fff ioport:30f8(size= memory:c0007c00-c0007cff memory:c0007800-c000780f[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]*-network DISABLED[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]description: Wireless interface[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]product: AR928X Wireless Network Adapter (PCI-Express)[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]vendor: Atheros Communications Inc.[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]physical id: 0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]bus info: pci@0000:07:00.0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]logical name: wlan0[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]version: 01[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]serial: 00:23:4d:1e:04:88[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]width: 64 bits[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]clock: 33MHz[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]configuration: broadcast=yes driver=ath9k driverversion=2.6.35-24-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn[/FONT][/SIZE]
 
[FONT=Liberation Serif]resources: irq:23 memory:c2000000-c200ffff[/FONT]
 

 
> 
[SIZE=3][FONT=Batang]:~$ iwlist scan[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]lo Interface doesn't support scanning.[/FONT][/SIZE]
 
 
 
[SIZE=3][FONT=Batang]eth0 Interface doesn't support scanning.[/FONT][/SIZE]
 
 
 
[SIZE=3][FONT=Batang]wlan0 Failed to read scan data : Network is down[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]ubu version[/FONT][/SIZE]

 
> 
[SIZE=3][FONT=Batang]:~$ uname -mr[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]2.6.35-24-generic i686[/FONT][/SIZE]

 
> 
[SIZE=3][FONT=Batang]:~$ sudo /etc/init.d/networking restart[/FONT][/SIZE]
 
[SIZE=3][FONT=Batang]* Reconfiguring network interfaces... [ OK ][/FONT][/SIZE]
 


---

### Post by kbz1960 on 2011-01-21
So for my wireless since the button to turn it off/on doesn't work is there any kind of work around or file that will do this? It works fine in windows just that I have to push the button twice for it to come on but doesn't work in Ubuntu.
 
I think that Ubuntu/linux just doesn't like my laptop.
 
Is this forum so big that it's hard to get an answer on things here?

---

