---
title: "Wireless freezes followed by the computer"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by jwr_1986 on 2009-06-01
I recently installed a linksys mini pci wireless card in my old laptop. I installed the one that would have come with the laptop had I purchased it originally but I didn't think to look for native linux drivers.

Ndiswraper has been working fine for the most part. However, The wireless connection will apparently fail at times (mostly when I'm checking my gmail) and I won't be able to access the menu for the network manager. The computer will get progressivly less responsive from there. Firefox will fail to close correctly. Other widows that are open may respond but not all functions. Switching desktops becomes impossible as well. Finally if I try to restart it goes to the black screen that reads out each step of the shutdown and freezes at Asking all other processes to terminate.

The end result invariably is that I just have to kill it and reboot. 

Any thoughts on where to look to solve this would be greatly appreciated.

Thanks

Jesse

---

### Post by coffeeaddict22 on 2009-06-01
Hi,
Sounds like you need to go hunting through the log files.  You can use the GUI in System/Administration/Log File Viewer; alternatively, they're all in /var/log/ . or for crashes, immediately after reboot type in a terminal```
dmesg
``` and look at the bit just before the timestamp changes (the numbers on the left of the output are seconds).
Having said that, what you're saying is the network is packing a sad.
To start with, try the following commands in a terminal.  You can post it back here if you want more help..
```
lspci
lshw -C network
nm-tool
```
They're all separate commands, one per line.

---

### Post by jwr_1986 on 2009-06-02
I looked through the logs. Dmesg didn't give me anything that jumped out at me but under regualar messages I find that this always appears at the time I am forced to restart.

Jun  1 22:40:07 jesse-laptop -- MARK --
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.460548] *pde = 00000000 
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.460566] Dumping ftrace buffer:
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.460570]    (ftrace buffer empty)
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.460574] Modules linked in: binfmt_misc ppdev bridge stp bnep input_polldev lp parport joydev pcmcia snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device iTCO_wdt psmouse dcdbas yenta_socket rsrc_nonstatic pcmcia_core iTCO_vendor_support snd pcspkr serio_raw ndiswrapper nvidia(P) soundcore snd_page_alloc shpchp intel_agp video output agpgart ohci1394 ieee1394 b44 ssb mii fbcon tileblit font bitblit softcursor
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.460641] 
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.460647] Pid: 2627, comm: wpa_supplicant Tainted: P           (2.6.28-11-generic #42-Ubuntu) Inspiron 5150                   
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.460653] EIP: 0060:[<f7f054b0>] EFLAGS: 00210202 CPU: 0
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.460659] EIP is at 0xf7f054b0
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.460663] EAX: 000000dc EBX: 00000004 ECX: 40000000 EDX: 00000001
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.460669] ESI: f583fd6c EDI: f583fd30 EBP: f583fcf4 ESP: f583fc7c
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.460673]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.460685]  f67a3500 c1c0fba0 f5826480 f70b2400 f6b829b0 00000000 f583fcb8 c02120fe
Jun  1 22:40:54 jesse-laptop kernel: [ 1261.461111] ---[ end trace a51e228f85f39e1e ]---

Sorry for the long stream of stuff but I'm not sure what will be the most relevant if any.

I tried the list of commands you gave and they do list my network information correctly. however I tried them when things were working so they didn't show me anything unexpected. 

Hopefully the stream from the logs above can help.

Thanks for your help so far

Jesse

---

### Post by coffeeaddict22 on 2009-06-02
OK.  I'm NOT a Linux guru, but it still looks like a wireless driver problem.  ftrace buffer is just a kernel buffer for a variety of stuff; the important line is probably the one where your wpa supplicant is tainted.  You may be dealing with [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275359") bug, although I'm not sure.

It'd be helpful if you'd post the chipset of interest.  The best place to get the info is lspci -v.  That's also got what driver's you have loaded in the network components, and that's another common source of problems.

---

### Post by jwr_1986 on 2009-06-03
The card in question is a Linksys WMP11. I was using Ndiswrapper to run it. I finally just decided to yank out the card and that has solved the problem so far. I have purchased an intel 2200 mini pci card instead. That card does have linux drivers.

Thanks for the help

Jesse

---

