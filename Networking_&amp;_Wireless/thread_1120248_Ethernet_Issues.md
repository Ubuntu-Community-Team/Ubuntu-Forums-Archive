---
title: "Ethernet Issues"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by cowboy_mcd74 on 2009-04-08
I have an IBM Thinkpad T60, and am trying to run Ubuntu 8.10. I have it working great (I've run it before, used XP for a while, and the other day decided to reinstall Ubuntu). One of the major issues I'm having, though, is with the Ethernet.... it just won't connect. The computer obviously finds it, and even installed a driver for it, but will not connect to networks. I know it's not a hardware issue, because it worked fine when I tried under Windows.

Just to give you the specs, I'm running the kernel 2.6.27-11, on the CU3 model T60 (the smaller one with a 14" screen). My Ethernet controller is an Intel 82573L.

Ubuntu doesn't even have an interface for it.... there's no eth0, eth1, etc. here's the output from ifconfig -a:

```

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

pan0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:172.22.3.13  Bcast:172.22.15.255  Mask:255.255.240.0
          inet6 addr: fe80::213:2ff:fe4b:68f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1148805 (1.1 MB)  TX bytes:246451 (246.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

and lspci | grep Ethernet:

```
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
```

and dmesg | grep e100:

```
[    0.589383] PCI: 0000:01:00.0 reg 18 32bit mmio: [ee100000, ee10ffff]
[    0.589516] PCI: bridge 0000:00:01.0 32bit mmio: [ee100000, ee1fffff]
[    0.655516] pci 0000:00:01.0:   MEM window: 0xee100000-0xee1fffff
[    0.655803] bus: 01 index 1 mmio: [ee100000, ee1fffff]
[    2.600116] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.600121] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.600187] e1000e 0000:02:00.0: Disabling L1 ASPM
[    2.600207] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.600221] e1000e 0000:02:00.0: setting latency timer to 64
[    2.670330] e1000e 0000:02:00.0: PCI INT A disabled
[    2.670343] e1000e: probe of 0000:02:00.0 failed with error -5

```


I've tried uninstalling the e1000e driver and installing the e1000 per instructions at [http://ubuntuforums.org/showthread.php?t=149941&highlight=e1000](http://ubuntuforums.org/showthread.php?t=149941&highlight=e1000), but I'm not exactly sure I did it correctly. I know it still doesn't work, though.

I've seen this issue around, but not a solution. I was hoping, maybe, someone had found one?

---

### Post by cowboy_mcd74 on 2009-04-08
I've been searching Google for 2 hours and haven't found anything that works successfully. Some solutions I can't even do, such as [http://www.linuxquestions.org/questions/slackware-14/eth0-error-while-getting-interface-flags-no-such-device-676915/](http://www.linuxquestions.org/questions/slackware-14/eth0-error-while-getting-interface-flags-no-such-device-676915/) .

I've tried recompiling the e1000e driver, but it gives me the error:
Makefile:188: *** *** Aborting the build. *** This driver is not supported on kernel versions older than 2.4.0.  Stop.

Which doesn't make sense, since my kernel is newer than that, right? But that seems to be the latest driver, as far as Google tells me.

I've tried several solutions around the forum, such as rmmod'ing the e1000e driver and insmod'ing it again, but that doesn't seem to do anything.

I've even booted up the 9.04 live cd to see if it was fixed in a newer version, and no, it's not.

Is this just a problem that no one's solved? It seems like it's been a problem since 8.10 was in its beta stages....

---

### Post by Iowan on 2009-04-09
So you know you're not being ignored (and to provide a bump)...
What are results of **lshw -C network**?

---

### Post by chili555 on 2009-04-09
> Is this just a problem that no one's solved? It seems like it's been a problem since 8.10 was in its beta stages....Yes, and the bug report says it's fixed! However, a few cases, such as yours, crop up. I have the exact same ethernet card and mine works splendidly. 

Are you dual-booting Windows? When you boot into Windows, does the card work? If you then go back to Ubuntu, will it work? I'd suggest a few tries. If you can get it tricked to life in Ubuntu, then I'd suggest running:```
dmesg | grep e1000 > e1000.txt
```Then post the contents of the text file here. 

So far, I have seen nothing in your posts that suggests it's the dreaded checksum error, although, it may be. I am therefor reluctant to recommend any hacks that manipulate the EEPROM.

---

