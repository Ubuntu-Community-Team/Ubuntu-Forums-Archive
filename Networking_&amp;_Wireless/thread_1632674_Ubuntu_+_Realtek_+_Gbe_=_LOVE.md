---
title: "Ubuntu + Realtek + Gbe = LOVE"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by LOIREE on 2010-11-28
Hey everyone!

I wanted to share with you some of my observations concerning problem that touches some people here, in the Ubuntu community. The problem usually noted as:

[LIST]
[*]Slow Samba
[*]Slow Realtek
[*]Slow gigabit connection
[*]etc
[/LIST]
First of all, my configuration:
S/W: Ubuntu 10.10 with xUbuntu mod (the problem was there since 9.04, which was my first one)
H/W: Intel D510MO dedicated for Linux file-server & downloads.
Ethernet: Realtek R8169/R8168

Now I suffered from really slow file transfer from Ubuntu to Vista. I do run gigabit lan, using cat5e cables, and naturally, when I first saw file copying speed of 6Mb/sec, I was shocked! Of course, ethtool was showing everything is fine: 1000Mb/s, auto negotiation, full duplex, and there was no errors of connection shown by ifconfig.

I tried various old hacks to smb.conf - rsize/wsize, etc. Ziltch! Although at some moment, there were various strange bugs, for example, increasing buffer sizes, caused connection to be 60Mb/s for 30 seconds, then dropping to 0 and stalling there, or jumping between 45Mb/s and 2Mb/s. Minimum CPU and RAM usage.

Anyway, for months I've being crawling around Ubuntu forums and Internet in general for the solution. I was updating my ethernet drivers from realtek website. I tried really obscure advises of playing with "tc" and "ip" utilities, as in "change traffic queue settings" - nothing seems to have helped.

Finally, I've used an advise, which seems to be primitive, but working, taken from some forum here. Disconnect from power socket, wait (2mins+), reconnect. How surprised I was to see that speed now tops at 24Mb/s - which is quite good for samba.

**NOTE:**

[LIST=1]
[*]I've upgraded to Ubuntu 10.10 (step-by-step (distro-by-distro) from 9.04).
[*]I use latest [Realtek driver]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false") : LINUX driver for kernel 2.6.x and 2.4.x (Support x86 and x64), v8.020.00 from 2010/11/15. (Installed via autorun.sh)
[/LIST]
So, then I've investigated what have been change, and here are my observations:

Since that "reset", output of ethtool eth0 has changed:

[LIST=1]
[*]Supported ports: [ TP MII ] - before was [ TP ] only.
[*]Advertised pause frame use: **No** - before was Yes.
[*]Link partner advertised pause frame use: **No** - before I haven't saw this line.
[*]Port: MII
[*]lsmod | grep r81 now lists additional mii module, associated with r8169
[*]lshw -C network shows "RTL8111/8168B PCI Express Gigabit Ethernet controller", and version : 03
[/LIST]
Now few comments:

[LIST=1]
[*]In 9.04 I also had TP and MII (in ethtool output), but saw no difference.
[*]Before the "reset", I've installed realtek driver, however here (if I understand right), we see that kernel's driver is loaded (questionable).
[*]Before the "reset" I had only "TP" link mode.
[*]Before the "reset" Advertised pause frame use was "Yes".
[/LIST]
In other words, may people here forgive my incompetence, I believe that problem might be either in MII module (or absense of such), or in realtek's driver, OR, and this seems to me the bulls eye, pause frame use.

I don't want to jump to a conclusions, since I've no intention to investigate it deeper, but I believe the problem with Realtek cards can be solved installing latest distro (and/or kernel), and making sure that your adapter running in a mode without pause frame use. To me, that pause frame seems to be the problem. But I might be wrong, I'm not linuxoid.

Goodluck everyone suffering from the same problem! :)

P.S. It is always better to try and solve the problem, than to abandon it switching to something else. Few people here went on purchasing cards with different chipsets. For my "leecher box", which is too small, and with very small chassis, that wasn't an option, really. I'm glad I finally could make it work without replacing anything.

**Update:** Apparently, that wasn't a full-time fix. And after some time of using Vista, speed still goes down to 4-6MB/sec. So, I've followed these advises and now have 34-40 MB/sec:

[http://www.speedguide.net/articles/windows-7-vista-2008-tweaks-2574](http://www.speedguide.net/articles/windows-7-vista-2008-tweaks-2574)
[B]netsh int tcp set global congestionprovider=ctcp

[http://www.alternativerecursion.info/?p=48](http://www.alternativerecursion.info/?p=48)
Very good article on the subject of Samba on Vista

[/B][B][http://www.ehow.com/how_5223943_enable-gigabit-ethernet-windows-vista.html](http://www.ehow.com/how_5223943_enable-gigabit-ethernet-windows-vista.html)
[/B]
And
[http://blogs.msdn.com/b/openspecification/archive/2009/04/10/smb-maximum-transmit-buffer-size-and-performance-tuning.aspx](http://blogs.msdn.com/b/openspecification/archive/2009/04/10/smb-maximum-transmit-buffer-size-and-performance-tuning.aspx)

Funny thing: after continuous tests with jperf, I found out (to my surprise) that in *my gigabit environment*, these are best working settings:
  net.core.rmem_max = 33554432
  net.core.wmem_max = 33554432
  net.ipv4.tcp_rmem = 4096 87380 33554432 
  net.ipv4.tcp_wmem = 4096 65536 33554432
  net.ipv4.tcp_mem = 33554432 33554432 33554432
See:
[http://fasterdata.es.net/TCP-tuning/linux.html](http://fasterdata.es.net/TCP-tuning/linux.html)
Also see (not tried yet):
[http://www.zdnet.com/blog/ou/vista-mmcss-gigabit-throttling-a-victim-of-hard-coding-jumbo-frames-to-the-rescue/711?pg=3&tag=mantle_skin;content](http://www.zdnet.com/blog/ou/vista-mmcss-gigabit-throttling-a-victim-of-hard-coding-jumbo-frames-to-the-rescue/711?pg=3&tag=mantle_skin;content)

Oh, and one more thing, the above explanation has been re-studied: it actually Linux kernel driver that was loaded. Most likely ./autorun.sh does not remove it, and to keep it, you should follow some other guidelines (like, perhaps, blacklisting previous module or something).

**Update #2: **Please, see [http://forums.steampowered.com/forums/showthread.php?t=1043281](http://forums.steampowered.com/forums/showthread.php?t=1043281) for slow vista on gigabit ethernet.

---

