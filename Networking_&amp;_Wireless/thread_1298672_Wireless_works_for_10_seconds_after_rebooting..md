---
title: "Wireless works for 10 seconds after rebooting."
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by jon_markw on 2009-10-23
Hello, I'm a complete Ubuntu noob.  I have managed to get my wireless card working on one network, but trying to connect to my network (using no encryption, WEP (64) WEP (128) and WPA Personal, I've had no luck.  Seen a lot of people with this problem but found no solution.  Has anyone fixed this?  Here are my detail.  Very grateful for any help.  Don't wanna get ripped off by Windows again!

lspci -v | less

30:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
        Subsystem: Hewlett-Packard Company Device 1361
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at c8000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Express Legacy Endpoint, MSI 00
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb

dmesg

[   20.350422] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.377836] input: b43-phy0 as /devices/virtual/input/input4
[   20.426137] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   20.535956] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   20.554616] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   20.602252] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   20.726159] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   20.726166] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed in July 2008.
[   20.726170] b43-phy0 warning: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   20.806746] Registered led device: b43-phy0::tx
[   20.806764] Registered led device: b43-phy0::rx
[   20.806783] Registered led device: b43-phy0::radio
[   20.830168] b43-phy0: Radio turned on by software
[   20.830587] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.350506] wlan0: direct probe to AP 00:25:3c:ee:87:24 try 1
[   22.353757] wlan0 direct probe responded
[   22.353762] wlan0: authenticate with AP 00:25:3c:ee:87:24
[   22.356262] wlan0: authenticated
[   22.356267] wlan0: associate with AP 00:25:3c:ee:87:24
[   22.361469] wlan0: RX AssocResp from 00:25:3c:ee:87:24 (capab=0xe21 status=0 aid=1)
[   22.361473] wlan0: associated
[   22.362279] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   22.382773] wlan0: disassociating by local choice (reason=3)
[   33.031431] wlan0: no IPv6 routers present
[   41.075793] spurious 8259A interrupt: IRQ7.
[   50.773556] wlan0: authenticate with AP 00:24:17:aa:72:b7
[   50.789511] wlan0: authenticated
[   50.789517] wlan0: associate with AP 00:24:17:aa:72:b7
[   50.795992] wlan0: RX AssocResp from 00:24:17:aa:72:b7 (capab=0x411 status=0 aid=2)
[   50.795997] wlan0: associated
[   62.802924] wlan0: No ProbeResp from current AP 00:24:17:aa:72:b7 - assume out of range
[   64.414790] wlan0: authenticate with AP 00:24:17:aa:72:b7
[   64.422409] wlan0: authenticate with AP 00:24:17:aa:72:b7
[   64.622200] wlan0: authenticate with AP 00:24:17:aa:72:b7
[   64.822121] wlan0: authenticate with AP 00:24:17:aa:72:b7
[   65.022041] wlan0: authentication with AP 00:24:17:aa:72:b7 timed out
[   78.173189] Marking TSC unstable due to cpufreq changes
[   78.770525] Clocksource tsc unstable (delta = -277627462 ns

uname -a

Linux VMlaptop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

---

### Post by jon_markw on 2009-10-23
Just for clarification....  The machine is an HP Compaq nx6235.  After installing Jaunty, I got the wireless card working using the following HowTo

[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/]("http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/")

So I'm not using ndiswrapper (as I could not get it to work that way).  I can connect to an open network around me for as long as I need and the connection never drops.  I can connect to my network successfully for about the first 10 seconds of logging on, then the network connection is disconnected and gnome network manager then attempts a reconnect.  The "Network requires authentication" box appears and will not let me connect.

Thanks in advance for any info.

---

### Post by jon_markw on 2009-10-26
This seems like a common problem, does anyone know the solution?  Googling this seems to bring up thread after thread but no answers.  Does anyone know where I can report it as a bug or something?

---

