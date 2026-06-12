---
title: "Ralink RT3092 wireless issues on Lucid"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by Ikirak on 2010-10-16
I was up all last night dual booting Lucid and Windows 7 on my new machine and just as I was finishing up, I discovered that Ubuntu couldn't access the internet via wireless (Windows had no problems). I followed the instructions (ALL of them) detailed in this thread: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1573370&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1573370&page=2) 
But to no avail. I noticed that some of my outputs were different from the original posters and so I'll post those here. Help me Ubuntu forums, you're my only hope. 

```
master@Igore:~$ dmesg | grep rt2
[   14.422559] !!! rt28xx Initialized fail !!!
[   14.461449] !!! rt28xx Initialized fail !!!
```

```
 master@Igore:~$ lsmod | grep -e rt2 -e rt3
rt3090sta             674216  0 
master@Igore:~$ dmesg | grep -e rt2 -e firmware
[   13.413542] !!! rt28xx Initialized fail !!!
[   13.437360] !!! rt28xx Initialized fail !!!
master@Igore:~$ 
```

```
 
master@Igore:~$ dmesg | grep rt3
[   12.921637] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned.
[   12.933304] rt3090 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.933327] rt3090 0000:02:00.0: setting latency timer to 64
master@Igore:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

master@Igore:~$  
```

I got the same output as the original poster when it came to the rt2860sta.dat bits and so things were looking up, but after following the instructions, my Wireless was still kaput.
Any help will be greatly appreciated.

---

