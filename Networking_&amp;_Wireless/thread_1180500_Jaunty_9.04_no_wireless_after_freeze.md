---
title: "Jaunty 9.04 no wireless after freeze"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by lurker_above on 2009-06-06
Hello, friends.

I've been using Ubuntu for about a year now, and I've been largely problem-free, until now.

I'm running 9.04 Jaunty on a Dell Inspiron 6000 laptop. After backing up a dvd using k9copy, my system froze completely. Unable to use mouse or keyboard, and I couldn't call a system terminal. So I was forced to do a hard power-off (hate to do that).

Rebooting took much longer than normal--about 5 minutes. When I was logged in again, I found that I couldn't access my wireless network. Clicking the network icon in the title bar showed that both the "Wireless" and "Wired" options are greyed out and inaccessible.

I tried ```
sudo /etc/init.d/networking restart
``` to no effect.

I re-enterd my wireless info and WEP and rebooted several times. No joy.

I'm a bit stumped at this point. Any suggestions would be appreciated. Thanks.

---

### Post by coffeeaddict22 on 2009-06-06
Hi,
Could be anything, esp if you're on an ext4 filesystem.
What's the output of ```
lshw -C network
ifconfig
nm-tool
```

---

### Post by lurker_above on 2009-06-07
[FONT="Arial"]Thank you for the reply, coffeeaddict22.  I am using ext4.  Although I am rather new to linux, I greatly enjoy learning it.  I appreciate any assistance.

The output is:[/FONT]



jim@jim-laptop:~$ sudo lshw -C network
[sudo] password for jim: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:dc:fa:aa
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:97:21:43
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f6:76:09:aa:d6:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
jim@jim-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:dc:fa:aa  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:97:21:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xa000 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

jim@jim-laptop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            NULL(info.linux.driver)
  State:             unavailable
  Default:           no
  HW Address:        00:12:3F:DC:FA:AA

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             disconnected
  Default:           no
  HW Address:        00:12:F0:97:21:43

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

### Post by coffeeaddict22 on 2009-06-07
Hi,
No prob.  It's a fun system to learn. 
It all looks good there; the only problem is your wireless is off.  Try ```
sudo ifconfig eth1 up
```  and see if that fixes it.

---

### Post by lurker_above on 2009-06-07
No, that didn't work.  The laptop's showing some funky behaviors during startup, so there may be more than one thing gone wrong here.  Maybe it would be easier to reinstall the system?

---

### Post by coffeeaddict22 on 2009-06-07
Funky behaviours??
If you aren't going to lose too much, a reinstall might be easiest.  The ext4 filesystem is quick, but it achieves part of that by storing up stuff to write, and doing it later (I think the delay can be up to 30 sec or so, but am happy to be corrected by any gurus out there).
What that means is a hard powerdown that wasn't expected can really mess up your filesystem.  The hard disk might have been told stuff got written that wasn't, or was only partially written.  I leave the rest to your imagination.  

If that's happened, there are no rules as to what got hurt, and a reinstall might be the quickest option.

---

### Post by lurker_above on 2009-06-09
Thanks, I appreciate the help.  The wireless was off, but Fn+F2 brought it back up.  I went ahead and reinstalled the system anyway, because I had /home backed up on an external drive and restoring it was simple enough.  

As I said, I've largely been problem free with Ubuntu, but researching and experimenting with the command line is especially fun.  Clearly there are commands to perform many tasks and fix just about any problem; it's just a matter of finding time to learn them.  Thanks again.

---

### Post by coffeeaddict22 on 2009-06-09
Really useful command line tool is apropos.  If you know what you want to find out about, but don't know what commands are available, apropos essentially does a grep of the man pages and returns hits.  So, for example, "apropos sound" will return all commands that have something to do with sound.

---

