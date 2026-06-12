---
title: "Acer 4530 wireless won't work on Ubuntu 8.10!!! Help!!!"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by GOO189 on 2009-03-25
hey guys!
i need help on setting my wlan card work.
my laptop is ACER ASPIRE 4530.

I tried quite a lot of method, bt it just don't work!

I am now using Ubuntu 8.10.

I am thinking if i can get my wireless card work, i will switch from windows to linux since it is stable and more beautiful.

So, i hope i can get help with you guys here!

---

### Post by bigbencg on 2009-03-25
We will need to gather some information before we can start troubleshooting.  Open a terminal window, run the following commands and post the results.  

```
lspci
```
```
ifconfig
```
```
iwconfig
```

I tried looking up the chipsets on Acer's website which was a waste of time.

---

### Post by GOO189 on 2009-03-25
code:

1. lspci

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation Device 0ad0 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:15.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9100M G (rev a2)
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
0b:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

2. ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1e:68:98:0d:47  
          inet addr:192.168.0.171  Bcast:192.168.1.255  Mask:255.255.254.0
          inet6 addr: fe80::21e:68ff:fe98:d47/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2921 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1377846 (1.3 MB)  TX bytes:232966 (232.9 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15316 (15.3 KB)  TX bytes:15316 (15.3 KB)

3. iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


That's it.

---

### Post by bigbencg on 2009-03-26
OK!  There is a solution, I had this problem myself.  I have a laptop with the same Atheros chipset.

You will need to download some new drivers, I downloaded this package
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/")
On that page you will see several files, download the one on the bottom with the newest date.  The file is in a compressed package, unpack the files and follow the instructions in the file named "INSTALL"

---

### Post by GOO189 on 2009-03-27
ok, i downloaded the madwifi, unpack it.

Then, i go to terminal, then i type 'make'.

then nothing happen. the command shown:

make: *** No targets specified and no makefile found.  Stop.

i don't know. i search the internet and it says 'inside the madwifi directory.' what does it mean by inside?

:confused:

---

### Post by jkop on 2009-03-27
Hi!
I have the same problem in an Aspire 5315 with the same chipset.
I downloaded the package, unpacked it to a diectory, and run it with the "cd" command and the "make" command.

(GOO189, all you have to do is to unpack the .tar file to somewhere, open the Terminal and type this:
*cd thepathtoyourunpackeddirectory*
e.g. my directory is on the desktop (in the hungarian version it called Asztal), my directory named Dokumentumok, so I typed  this: 
*cd /home/koppany/Asztal/Dokumentumok/madwifi-hal-0.20.5.6-r3942-20090205*
ant then, press enter
and then, type *make*, and then wait. It should work.)

So my problem is, I' ve done this, but I don't know, what to do next. I typed *sudo make install*, *sudo gedit /etc/modules* and the added *ath_pci* to the very end of the text, and rebooted as wrote in [this]("http://ubuntuforums.org/showthread.php?p=6430158") thread, but I still haven't got internet after that. What should I do?
Please help me, I am totally noob in linux. Thanks.

---

### Post by bigbencg on 2009-03-27
When you first open terminal, you should be located in your home folder.  I am assuming you are using firefox, which would have downloaded the file to your desktop.  And I am assuming that the file was unpacked on your desktop.  SO you shoudld have two madwifi "things" on the desktop.  To make it easier I would suggest renaming the unpacked file, right click the folder and select properties.  Erase everything after madwifi.  Then open a terminal window and type 
```
cd madwifi
```
Then the make commands should work.

jkop, you are on the right path, but the instructions are included in the madwifi folder.  The instructions in that post are a bit vague and may assume prior knowledge.  In the madwifi........ folder there is a file called INSTALL, those are the detailed installation instructions.

---

### Post by jkop on 2009-03-28
I've done everything what the INSTALL wrote, restarted, but nothing happened. Typing iwconfig, it says:
```
lo    no wireless extensions
eth0  no wireless extensions
wifi0 no wireless extensions
ath0  IEEE 802.11b  ESSID:" "  Nickname:" "
      Mode:managed  Channel:0  Access Point: Not-Associated
      Bit Rate:0 kb/s  Tx-Power:0 dBm  Sensitivity=1/1
      Retry:off  RTS thr:off  Fragment thr:off
      Power Management:off
      Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBM
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries:0  Invalid misc:0  Missed beacon:0
pan0  no wireless extensions

```
My system is brand new, I've installed it two days ago, the version of the kernel is 2.6.27-7-generic. I really don't know what to do, typing the ifconfig command it only sees the lo, Local Loopback. I don't want to write over the kernel files and the pcmcia config, because I fear that I'll make a mistake and my system become unusable. So please, please write down to step by step what should I do to make the wireless internet working.

---

