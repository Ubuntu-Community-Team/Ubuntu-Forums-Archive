---
title: "rt2860 pseudonym for rt2860sta ?"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by Mattias on 2010-09-27
Hello 
I recently bought a linksys WMP600N PCI card (rt2860 chip) as my pre purchase googling told me it would work out of the box. You all know how the rest on this story goes.... a week later  I`m here looking for help.
I think I have thrown everything in the book on this, compiling new drivers, blacklisting modules and having a /etc/Wireless/RT2860STA/RT860STA.dat
My problem is that the card connects fine now on a Lucid x32 installation but only connects with my DIR-655 router WPA2-TKIP only at 24Mb/s 

some info with comments 
```
mattias@suris3:~/Desktop$ dmesg | grep -i rt2
[    3.805596] rt2860 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.382295] rt2860 0000:05:01.0: firmware: requesting rt2860.bin
[    9.483439] <==== rt28xx_init, Status=0
[ 5150.432018] <==== rt28xx_init, Status=0
```
rt2860 ? should it not be rt2860sta ?
and lspci -v
> 05:01.0 Network controller: RaLink RT2800 802.11n PCI
	Subsystem: Linksys Device 0067
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta, rt2800pci
again rt2860?

and iwconfig:
```
wlan0     Ralink STA  ESSID:"NATET"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.432 GHz  Access Point: 00:1E:58:40:FF:B3   
          Bit Rate=36 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=32/100  Signal level:-78 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
should not this be ra0 not wlan0 with rt2860sta ?

anybody have some success with this card in lucid ?

---

### Post by gzarkadas on 2010-09-27
Your driver seems to load ok, according to the procedure I have read [there]("http://www.ab9il.net/linuxwireless/rt2860.html"), and wlan{X} is the default name for wireless interfaces. 

Your link quality though is low (32%) and probably this is what makes your connection slow. 

Try to approach your wireless router closer -without walls and such intervening in your line of site- and see if things get better. Also check for interferences by near by radio sources (such as other wireless networks, for example).

---

### Post by Mattias on 2010-09-28
Hello, Thank you for your reply. 
I did a quick test this morning. connected external antennas with cable got signal quality 96/100 but still only g connection 54 mb/s . 
A post only a few hours after mine in [http://ubuntuforums.org/showthread.php?t=1279672](http://ubuntuforums.org/showthread.php?t=1279672)
indicates that I´m not the only one here with this problem.
I´m thinkin of trying Maverick and see if the problem persists. Anyone tried Maverick with this card ?
//Mattias

---

### Post by gzarkadas on 2010-09-28
I googled around and there seem to be problems with those cards with both windows and linux. I suppose, from your post, that you use the latest RaLink drivers, as mentioned for example [here]("http://forums.fedoraforum.org/showthread.php?t=235691"); so the only thing that remains before switching to another kernel is to try and tweak your connection settings, like for example to change frequency, or (as the 2nd poster in the thread you mentioned reports) disable security.

As I see in the kernel.org git, the [driver for PCI (rt2800pci.c)]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=history;f=drivers/net/wireless/rt2x00/rt2800pci.c;h=39b3846fa340a83704a69d8a252bb7a6d6fa87b5;hb=050026feae5bd4fe2db4096b63b15abce7c47faa") had numerous new patches during this year, so it seems it is definitely worth to try Maverick.

Unfortunately, I do not have a piece of that hardware, so I cannot go much further; I wish you luck in finding quickly a solution.

---

### Post by Mattias on 2010-09-30
Ok 
I have now tried upgrading to Maverick. For your information this didn´t help still no n connection. I guess I have to wait for a new driver or a new kernel that will fix this. Frustrating but thats life I guess
/M

---

### Post by Mattias on 2010-10-04
Ok, after installing the ralink 2.40 driver in maverick kernel the network connects fine with 270MB/s, odd
Hope this helps someone reading this.
//Mattias

---

### Post by gzarkadas on 2010-10-04
Glad to hear; driver issues are frustrating ones and a solution is usually good news for a lot of people :).

---

