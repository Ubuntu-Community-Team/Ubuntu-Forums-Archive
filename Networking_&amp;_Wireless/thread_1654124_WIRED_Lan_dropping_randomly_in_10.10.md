---
title: "WIRED Lan dropping randomly in 10.10"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by KaibutsuX on 2010-12-27
lspci:
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)

My wired LAN keeps dropping randomly, average of every 30-60 minutes. Fresh install of 10.10 from iso, Been installed for about 4 days now, just performed system update today, no change.

My router actually completely resets itself. You can watch the lights power off and recycle doing their POST. Absolutely no problems in windows 7 dual boot configuration.

I am no downloading anything, not streaming, not doing anything actually. My computer is completely idle (save for BOINC) and all of a sudden my phone loses the wireless connection which lets me know that my router just reset.

Ubuntu is actually doing this, my wireless stays up indefinitely in windows. Once the router resets, it does automatically reconnect without a PC reboot, but why is it resetting my router?

If you need the bootscript, already posted here: [http://ubuntuforums.org/showthread.php?t=1651262](http://ubuntuforums.org/showthread.php?t=1651262)

---

### Post by KaibutsuX on 2010-12-28
No one huh? Already purged and reinstalled network-manager.

I realize that 10.10 isn't supposed to be a LTS, but generally when I consider something an upgrade, I don't expect it to start rebooting my router every 30 minutes, nor do I expect random dropouts in my bluetooth mouse as mentioned both on these forums and in multiple google results.

Seriously, wtf developers?

---

### Post by KaibutsuX on 2011-01-04
Reverted to 10.04. Was working great until I installed the recommended security updates. Started the very next day.

Output of System Log: Messages - 
```

Jan  3 20:56:57 kaibutsux-desktop kernel: [ 3945.221279] sky2 eth0: Link is down.
Jan  3 20:57:46 kaibutsux-desktop kernel: [ 3993.281495] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Jan  3 21:27:12 kaibutsux-desktop kernel: [ 5758.768709] sky2 eth0: Link is down.
Jan  3 21:28:01 kaibutsux-desktop kernel: [ 5807.652786] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Jan  3 21:28:10 kaibutsux-desktop pulseaudio[1935]: sink-input.c: Failed to create sink input: sink is suspended.
Jan  3 21:28:42 kaibutsux-desktop pulseaudio[1935]: sink-input.c: Failed to create sink input: sink is suspended.
Jan  3 21:32:36 kaibutsux-desktop pulseaudio[1935]: ratelimit.c: 115 events suppressed
Jan  3 21:46:49 kaibutsux-desktop kernel: [ 6935.401351] sky2 eth0: Link is down.
Jan  3 21:47:35 kaibutsux-desktop kernel: [ 6981.305138] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Jan  3 21:52:53 kaibutsux-desktop kernel: [ 7298.766093] tcpdump uses obsolete (PF_INET,SOCK_PACKET)
Jan  3 21:52:57 kaibutsux-desktop kernel: [ 7302.559598] type=1503 audit(1294109577.056:18):  operation="capable" pid=5281 parent=5257 profile="/usr/sbin/tcpdump" name="net_admin"
Jan  3 21:53:23 kaibutsux-desktop kernel: [ 7328.689740] device eth0 entered promiscuous mode
Jan  3 22:04:59 kaibutsux-desktop kernel: [ 8024.867467] device eth0 left promiscuous mode
Jan  3 22:07:44 kaibutsux-desktop kernel: [ 8189.772162] sky2 eth0: Link is down.
Jan  3 22:08:30 kaibutsux-desktop kernel: [ 8236.135458] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Jan  3 23:01:49 kaibutsux-desktop kernel: [11433.739647] sky2 eth0: Link is down.
Jan  3 23:02:35 kaibutsux-desktop kernel: [11479.588167] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Jan  3 23:34:29 kaibutsux-desktop kernel: [13392.315148] sky2 eth0: Link is down.
Jan  3 23:35:16 kaibutsux-desktop kernel: [13439.136621] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Jan  4 07:49:31 kaibutsux-desktop kernel: [43078.615179] sky2 eth0: Link is down.
Jan  4 07:50:17 kaibutsux-desktop kernel: [43124.673884] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Jan  4 07:50:34 kaibutsux-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="895" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan  4 19:53:04 kaibutsux-desktop kernel: [86469.450017] sky2 eth0: Link is down.
Jan  4 19:53:50 kaibutsux-desktop kernel: [86515.003706] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Jan  4 20:03:01 kaibutsux-desktop kernel: [87066.344956] sky2 eth0: Link is down.
Jan  4 20:03:58 kaibutsux-desktop kernel: [87123.230158] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Jan  4 20:10:13 kaibutsux-desktop pulseaudio[1935]: ratelimit.c: 4 events suppressed
Jan  4 20:14:59 kaibutsux-desktop kernel: [87783.695790] sky2 eth0: Link is down.
Jan  4 20:15:45 kaibutsux-desktop kernel: [87829.744822] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both

```

Once again this is a wired connection. The router is fine. Computer off or in windows, my other 3 computers, PS3 and Droid stay connected to wireless just fine. Connect Ubuntu, router resets every 10-30 minutes.

Seems like this might be some sort of high priority bugfix that someone should look into.

---

### Post by PatchesTheCaveman on 2011-01-04
Try booting in an older version of the Linux kernel.  To that, you will first need to reboot.

If you don't dual boot with Windows or another operating system, you will need to hold down TAB before Ubuntu starts so you get the GRUB boot menu.  (If you dual-boot, you always get the GRUB menu.)  From that menu, select an older version of the kernel than the default option.

See if that fixes your problem.  As always, if you still have trouble, let us know.  Good luck!

---

### Post by BigMeanMikeRich on 2011-02-20
Was there any progress on this issue?  Did running an older kernel solve this for you, KaibutsuX?

I'm running 10.10 32-bit, and after running fine for months my connection has started dropping every 30 minutes or so.  My fix has been to switch the LAN cable to a different port on my router, then run ifconfig eth0 down, followed by up.  This gets me online again, but only for another 30 minutes or so (sometimes less, especially if I'm downloading something)

---

