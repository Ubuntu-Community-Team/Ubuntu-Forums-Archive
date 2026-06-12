---
title: "Can't get WINSTARS wireless adaper working"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by golf_boy on 2011-01-23
I've been trying for some time to get a wireless connection going with a new wireless card I purchased. I've been trying a number of things. My most recent attempt largely followed the advice here.

[http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/](http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/)

In short, I've compiled and installed the RALink driver.

Nothing in my system appears to list wireless access points. When I try to connect to a known unsecured access point the 'wireless radar' icon moves for about 15 seconds and then says I'm disconnected.

I'm running Ubuntu 11.04, fully patched.

Output from various commands follows.

============================================================

john@compaq:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: 00:18:4D:57:8B:F8  
          Bit Rate=1 Mb/s  
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-42 dBm  Noise level:-42 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

============================================================

john@compaq:~$ lspci -vvv

00:04.0 Network controller: RaLink Device 3062
    Subsystem: RaLink Device 3062
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 66 (500ns min, 1000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2860
    Kernel modules: rt3562sta, rt2800pci

=============================================================

I have added these lines to /etc/modprobe.d/blacklist

# don't use these drivers for the wireless card
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2800lib

=============================================================

Any help or advice would be very much appreciated.

---

### Post by chili555 on 2011-01-24
I hope you added the lines to /etc/modprobe.d/blacklist.[COLOR="Red"]conf[/COLOR]. Also your device is also claimed by ancillary driver modules rt2x00pci, et al that will drag in rt2800pci anyway! Find out with:```
lsmod | grep -e rt2 -e rt3
```When you find that rt2800pci and others are loaded anyway, amend /etc/modprobe.d/blacklist.conf to add these lines:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Reboot and give us your report.

If you actually added the lines to blacklist and not blacklist.conf, now that you have blacklist.conf properly set up, remove blacklist:```
sudo rm /etc/modprobe.d/blacklist
```

---

### Post by golf_boy on 2011-01-26
Thanks for the response. Sorry for the original post: I had added to blacklist.conf, not blacklist.

Running your suggested command results in this.

john@compaq:~$ lsmod | grep -e rt2 -e rt3
rt3562sta             923967  1 
john@compaq:~$

---

### Post by chili555 on 2011-01-26
Good! The correct module is loaded and the incorrect modules are now blacklisted. Let's see what's going on under the hood. Please run and post:```
iwconfig
dmesg | grep -e rt3 -e rt2 -e ra0
sudo iwlist ra0 scan
```Thanks.

---

### Post by golf_boy on 2011-01-26
john@compaq:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: 00:18:4D:57:8B:F8   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-92 dBm  Noise level:-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

=====================================================================

john@compaq:~$ dmesg | grep -e rt3 -e rt2 -e ra0
[   52.576056] ra0: no IPv6 routers present
[  196.563655] rt28xx_get_wireless_stats --->
[  196.563660] <--- rt28xx_get_wireless_stats

======================================================================

john@compaq:~$ sudo iwlist ra0 scan
[sudo] password for john: 
ra0       Scan completed :
          Cell 01 - Address: 00:18:4D:57:8B:F8
                    Protocol:802.11b/g
                    ESSID:"jandh"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-90 dBm  Noise level:-85 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s

=====================================================================

'jandh' is the name of the wireless access point I'd like ot connect to.

---

### Post by chili555 on 2011-01-27
Still looking good! With any ethernet cable detached, click the Network Manager icon. Do you see your network? Does it try to connect?

I am a bit troubled by this:> ra0 Scan completed :
Cell 01 - Address: 00:18:4D:57:8B:F8
Protocol:802.11b/g
ESSID:"jandh"
Mode:Managed
Frequency:2.437 GHz (Channel 6)
[COLOR="Red"]Quality:0/100[/COLOR] Signal level:-90 dBm Noise level:-85 dBm
[COLOR="Red"]**Encryption key:off**[/COLOR]
Bit Rates:54 Mb/sI'm not quite sure what Quality 0/100 implies. I suspect it implies that the driver doesn't read this correctly.

I am also troubled that you have no encryption on the network. May I assume you live at least one mile from the nearest road and at least five miles from the nearest neighbor? Or may I assume that, as soon as you fine-tune the wireless connection, you are changing to WPA2???

---

### Post by golf_boy on 2011-01-28
The 'Network Manager' icon is - I assume - the icon in the upper right which looks like an up arrow, followed by a down arrow. If I click on it, the icon gets replaced with a wireless / radar icon that pulses up and down for ~ 15 seconds, after which a fade-over popup informs me that I'm disconnected.

You are correct that I am currently running no encryption. One thing at a time is, in my view. Either that or I plan to permanently enclose my abode in its lead-lined sheath. Just kidding. I'm just trying to eliminate / isolate problems at the moment.

You're right; quality 0/100 is not encouraging.

---

### Post by chili555 on 2011-01-28
The exact look of the icon is a bit different for each version: ubuntu, kubuntu, xubuntu, edubuntu and klingonubuntu. However, when you click it, you ought to see a list of available networks like the attached. Can you select from among networks?

---

### Post by golf_boy on 2011-01-29
I upgraded Ubuntu, which upgraded the kernel, so I had to recompile. I checked the output of the various commands above and nothing particularly significant seems to have changed. The exception might be the signal strength thing you commented on. Below I include an image of my desktop after it was trying to connect.

It includes the state of the Network Manager. It also includes the results of a number of results of 'sudo iwlist ra0 scan'. As you can see, the 'quality' (signal) seems to vary quite a bit over a fairly short period of time. At least that's my take; yours may be different.

[IMG]http://bimbom.net/foo.png[/IMG]

---

### Post by golf_boy on 2011-01-29
Sorry; I wasn't very explicit in my response. 

I can see networks in Network Manager. I can select the one I want to connect to. The icon 'pulses' for a bit but fails to connect. The screen shot shows the result of the command being run while the icon is pulsing.

---

### Post by chili555 on 2011-01-29
Do you notice that at one scan the signal level is -44dBm (nice and strong) and a few moments later it's -92dBm (so weak as to be nearly undetectable)? Are you certain it's not a problem with the router? Do other computers connect seamlessly?

---

### Post by golf_boy on 2011-01-29
I don't think it's the router. It's in the same room as the computer, which is in the same room as the computer I'm typing on, which shows 'full strength' in the (Windows) gui. It's also got two other attached devices two rooms away, and they're stable.

It's odd; as I repeatedly run the command, signal strength is usually in the -38-42db range. Occasionally it drops to -89-92db. There's never been any other value in between those ranges.

I tried to connect to a neighbor's (security protected) wifi and it immediately popped up the appropriate dialog asking for the WEP password. So it's talking to something. It may even be talking to my router.

BTW, the router is not only running no security, there's also no MAC restrictions or anything of that nature. It should be wide open.

---

