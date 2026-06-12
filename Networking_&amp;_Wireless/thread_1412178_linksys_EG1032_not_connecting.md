---
title: "linksys EG1032 not connecting"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by mparker1113 on 2010-02-20
I have loaded ubuntu 9.10, and am not getting internet from my router using a linksys EG1032. I have found articles stating that i should use the sk ([http://manpages.ubuntu.com/manpages/hardy/man4/sk.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/sk.4.html)) or nge (http://manpages.ubuntu.com/manpages/hardy/man4/nge.4.html)drivers. According to the instructions i found, they require that i make changes to my kernel config. I do not know  how to do that, or if doing so is wise.

If someone would help me figure out how to connect this NIC card, i would appreciate it.

---

### Post by RedSingularity on 2010-02-20
Is it USB or PCI?  Wired or wireless?

---

### Post by northd_tech on 2010-02-20
Can you open a terminal and post the results of these commands here to diagnose your hardware, mparker:

```

lspci 

lsusb

lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig
```

Also, those Hardy Heron instructions are pretty old and there might be a better, faster, easier fix now.

---

### Post by mparker1113 on 2010-02-21
Here are the configuration results you asked for. I had to type them by hand, so if there is anything that needs clarification, just let me know. Thank you for your help with this.
 
[QUOTE=northd_tech;8858149]Can you open a terminal and post the results of these commands here to diagnose your hardware, mparker:
 
[CODE]
lspci 
<--start results for lspci: -->
00:00.0 Hst bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hu Interface (rev 03)
00:02/0 VGA compatible controller: Intel Corporation 82845G/GL[Brooooddale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 83801DB/DBL/DBM (ICH4/ICH4-L/CH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 83801DB/DBL/DBM (ICH4/ICH4-L/CH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 83801DB/DBL/DBM (ICH4/ICH4-L/CH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 83801DB/DBL/DBM (ICH4/ICH4-L/CH4-M) USB EHCI Controller 
00:1e.0 PCI bbridge Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Croporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge(rev02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller(rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM(ICH4/ICH4-L/ICH4-M)SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC97 Audio Controller(rev 02)
01:05.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 10)
<--end results for lspci-->
lsusb
<-- start results for lsusb:-->
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

<-- end results for lsusb -->
 
lsmod
<-- start results for lsmod -->
sn_seq_oss   28576  0
snd_seq_midi   6432  0
iptable_filter   3100  0
snd_rawmidi   22208  1  snd_seq_midi
ip_tables   11692  1  iptable_filter
snd_seq_midi_event   6940  2  snd_seq_oss,snd_seq_midi
x_tables   16544  1 ip_tables
snd_seq   50224  6  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer  22276  2 snd_pcm,snd_seq
snd_seq_device   6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp   8964  0
snd   59204  14  snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi   2564  0
shpchp   32272  0
soundcore   7264  1  snd
ppdev   6688  0
snd_page_alloc   9156  2  snd_intel8x0,snd_pcm
parport_pc   31940  1
psmouse   56180  0
serio_raw   5280  0
dcdbas   7292  0
parport   35340  3  op,ppdev,parport_pc
fbcon   36640  72
tileblit   2460  1  fbcon
font   8124  1  fbcon
bitblit   5372  1  fbcon
softcursore   175  1 bitblit
i915   221064  2
drm   159584  2  i915
i2c_algo_bit   5760  1  i915
r8169   32064  0
mii   5212  1  r8169
floppy   54916  0
intel_agp   27484  2 i915
agpgart   34988  2  drm,intel_agp
video   19380  1  i915
output   2780  1  video

<- end  results for lsmod -->
 
uname -a
results: Linux familyUbuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i6867 GNU/Linux
sudo lshw -C network
<--results for sudo lshw -C network -->
*-network
   description : Ethernet interface
   product: Gigabit Network Adapter
   vendor: Linksys
   physical id: 5
   bus info: [EMAIL="pci@0000:01:05.0"]pci@0000:01:05.0[/EMAIL]
   logical name: eth0
   versio: 10
   serial: 00:22:6b:be:5:d8
   size: 100MB/s
   capacity: 1GH/s
   width: 32 bits
   clock: 66MHz
   capabilities: pm bus_master cap_list room ethernet physical tp mii 10bt 10bt-fd 100b 100bt -fd 1000bt 100bt -fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
   resources: irq:17 ipport:c000(size=256) memory:ed000000-ed000ff memory:10000000-1001ffff(refetchable)
<-- end results for sudo lshw -C network -->  
ifconfig
<-- start results for ifconfig -->
eth0
   Link encap: Ethernet HWaddr 00:22:6b:be:56:d8
   inet6 addr: fe80::222:6bff:febe:56d8/64 Scope:Link
   UP BROADCAST RUNING MULTICAST MTU:1500 Metric:1
   RX packets:0 errors:0 dropped:0 overruns:0 frame:0
   TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueuelen:1000
   RX bytes:0 (0.0 B) TX bytes:2178 (2.1 KB)
   Interrupt: 17
lo
   Lind encap: Local Loopback
   inet addr:127.0.0.1 Mask: 255.0.0.0
   inet6 addr: ::1/128 Scope:Host
   UP LOOPBACK RUNNING MTU:16436 Metric:1
   RX packets:4 errors:0 dropped:0 overruns:0 frame:0
   TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueuelen:0
  RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
<-- end of results for ifconfig --> 
iwconfig
io   no wireless extensions.
eth0  no wireless extensions.

---

### Post by northd_tech on 2010-02-21
> **mparker1113 said:**
> 
**lspci **
01:05.0 Ethernet controller: **Linksys Gigabit Network Adapter** (rev 10)

**lsmod**
Module      Size     Used by

[COLOR=Blue]**r8169**   32064  0
mii   5212  1 ** r8169**[/COLOR]

uname -a
results: Linux familyUbuntu **2.6.31-14-generic** #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 **i686** GNU/Linux

sudo lshw -C network
<--results for sudo lshw -C network -->
*-network
   description : Ethernet interface
   product: **Gigabit Network Adapter**
   vendor: **Linksys**
   physical id: 5
   bus info: pci@0000:01:05.0
   logical name: eth0
   versio: 10
   serial: 00:22:6b:be:5:d8
   size: 100MB/s
   capacity: 1GH/s
   width: 32 bits
   clock: 66MHz
   capabilities: pm bus_master cap_list room ethernet physical tp mii 10bt 10bt-fd 100b 100bt -fd 1000bt 100bt -fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
   resources: irq:17 ipport:c000(size=256) memory:ed000000-ed000ff memory:10000000-1001ffff(refetchable)
<-- end results for sudo lshw -C network -->  
ifconfig
<-- start results for ifconfig -->
eth0
   Link encap: Ethernet HWaddr 00:22:6b:be:56:d8
   inet6 addr: fe80::222:6bff:febe:56d8/64 Scope:Link
   **UP BROADCAST RUNNING** MULTICAST MTU:1500 Metric:1
   RX packets:0 errors:0 dropped:0 overruns:0 frame:0
   TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueuelen:1000
   **RX bytes:0 (0.0 B) TX bytes:2178 (2.1 KB)**
   Interrupt: 17

Yowzers!  Sorry to make you type all that- I should have mentioned that you could copy output from the terminal window and paste into either the Kate or "gedit" text editors and save them to a USB stick to post here on another computer.  Sorry about that.

Anyway, I think I found your problem.  lspci identifies your ethernet card as a "Linksys Gigabit" but you have got the modules loaded for a [COLOR=Blue]Realtek 8169[/COLOR] ethernet card (the part in [COLOR=Blue]blue[/COLOR]).  Maybe this is correct, but I don't know for sure.

It does look you are transmitting a little to the ethernet switch (2.1KB in the bolded TX above), but nothing is coming back from it.

I haven't worked with that card before, but according to this old post #10, the driver for that is built in to ubuntu (it's probably worth you reading that whole thread though):

[http://ubuntuforums.org/showpost.php?p=7063845&postcount=10](http://ubuntuforums.org/showpost.php?p=7063845&postcount=10)

There is also an old archived/abandoned read only thread about that Linksys card here:

**Linksys EG1032 PCI gigabit adapter - driver?**
[http://ubuntuforums.org/showthread.php?t=117788](http://ubuntuforums.org/showthread.php?t=117788)

You are also running a 32-bit version of the **2.6.31-14-generic **kernel (which is a little old I believe).  If you can't get a wired connection though, installing/updating kernels would be a huge pain.  It is possible that the newer (or even older) kernels will support that Linksys Gigabit network card a little better.

Hopefully someone will read this that has experience with that particular network card.  I'll tag the thread with what we found out to make it more visible.

edit:  also that first link was for this network card :" SysKonnect SK-984x and SK-982x PCI Gigabit Ethernet"

and the second link is for "National Semiconductor PCI Gigabit Ethernet adapter driver" here:

[http://manpages.ubuntu.com/manpages/hardy/man4/nge.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/nge.4.html)

I don't think those are the same "gigabit" network card as your Linksys that the hardware is identified as above.

---

### Post by mparker1113 on 2010-02-21
Regarding the other ethernet card, I do have a NIC that is soutered to the computer, but doesn't work. So, i added the linksys card.
 
Would all of my problems be solved if i bought another card, like a intel chipset card?
 
 
 
 
> **northd_tech said:**
> Yowzers! Sorry to make you type all that- I should have mentioned that you could copy output from the terminal window and paste into either the Kate or "gedit" text editors and save them to a USB stick to post here on another computer. Sorry about that.
 
Anyway, I think I found your problem. lspci identifies your ethernet card as a "Linksys Gigabit" but you have got the modules loaded for a [COLOR=blue]Realtek 8169[/COLOR] ethernet card (the part in [COLOR=blue]blue[/COLOR]). Maybe this is correct, but I don't know for sure.
 
It does look you are transmitting a little to the ethernet switch (2.1KB in the bolded TX above), but nothing is coming back from it.
 
I haven't worked with that card before, but according to this old post #10, the driver for that is built in to ubuntu (it's probably worth you reading that whole thread though):
 
[http://ubuntuforums.org/showpost.php?p=7063845&postcount=10](http://ubuntuforums.org/showpost.php?p=7063845&postcount=10)
 
There is also an old archived/abandoned read only thread about that Linksys card here:
 
**Linksys EG1032 PCI gigabit adapter - driver?**
[http://ubuntuforums.org/showthread.php?t=117788](http://ubuntuforums.org/showthread.php?t=117788)
 
You are also running a 32-bit version of the **2.6.31-14-generic **kernel (which is a little old I believe). If you can't get a wired connection though, installing/updating kernels would be a huge pain. It is possible that the newer (or even older) kernels will support that Linksys Gigabit network card a little better.
 
Hopefully someone will read this that has experience with that particular network card. I'll tag the thread with what we found out to make it more visible.
 
edit: also that first link was for this network card :" SysKonnect SK-984x and SK-982x PCI Gigabit Ethernet"
 
and the second link is for "National Semiconductor PCI Gigabit Ethernet adapter driver" here:
 
[http://manpages.ubuntu.com/manpages/hardy/man4/nge.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/nge.4.html)
 
I don't think those are the same "gigabit" network card as your Linksys that the hardware is identified as above.

---

### Post by northd_tech on 2010-02-21
> **mparker1113 said:**
> Regarding the other ethernet card, I do have a NIC that is soutered to the computer, but doesn't work. So, i added the linksys card.
 
Would all of my problems be solved if i bought another card, like a intel chipset card?
So do you have 2 network cards in the same computer then?  If so, I would try pulling one out and rebooting ubuntu.  If you still don't have ethernet, then pull the first one, install the second one only, and try rebooting again.

It might be worth saving the output of lspci, lsmod, ifconfig, etc. for each configuration while you've got them installed.

On the 2nd question, if you have access to a cheap (or preferably free) NIC card that could possibly make life much easier.  I'd do a lot of research here and about "working linux network card" before I spent much money though, because a new one might be just as difficult.

My laptop has an NVIDIA nForce ethernet interface that** I believe** is derived from the old IBM "100 Pro/E" NIC, and I have yet to see a Linux distribution that it won't work with "out of the box".  If you're going to spend money, you will want ubuntu kernel support "built in" for whatever card you choose- it's really nice when you need to run updates (or re-installs, G-d forbid).  Also "gigabit" might not be such a good thing for compatibility- most ISPs aren't much faster than a 100Mbps card anyway.

Here is a good place to read about which NIC's work:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I went to Linksys [Cisco's] website to see what they've got, and it does mention 3 hardware versions of that card (if EG1032 is the correct model):

[http://www.linksysbycisco.com/US/en/support/EG1032/download](http://www.linksysbycisco.com/US/en/support/EG1032/download)

And here is a forum for that same card:

[http://forums.linksysbycisco.com/linksys/board/message?comm_cc=US&comm_lang=en&board.id=Wired_Adapters&message.id=914#M914](http://forums.linksysbycisco.com/linksys/board/message?comm_cc=US&comm_lang=en&board.id=Wired_Adapters&message.id=914#M914)

There is the possibility that another Linux LiveCD distribution might work better with one of those NIC cards you have (ArchLinux, SUSE, and PCLinuxOS would be what I would try first) if you have a way to download those large .ISO files.

If not, it's always a good idea to keep a copy of Damn Small Linux around for testing/resurrecting old Windoze machines (or embedded PC's):

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Right now, ubuntu is #1 though so it is good to ask questions here- you'll see the biggest audience.

Here are some older threads I found when searching for Linksys "EG1032" here:

[http://ubuntuforums.org/showthread.php?t=919348](http://ubuntuforums.org/showthread.php?t=919348)

Note that this one does show having Realtek 8169 modules, so that might be version-dependent since Linksys has 3 hardware versions:
[http://ubuntuforums.org/showthread.php?t=711966](http://ubuntuforums.org/showthread.php?t=711966)

[http://ubuntuforums.org/showthread.php?t=536922](http://ubuntuforums.org/showthread.php?t=536922)

Good luck.

---

### Post by northd_tech on 2010-02-21
One more thought- you don't have on-motherboard "built in" ethernet do you?  Some of those are pretty well supported by Linux.  You might want to poke around in the BIOS settings and see what it says, or try enabling (or disabling) on-board LAN if you see one.

---

