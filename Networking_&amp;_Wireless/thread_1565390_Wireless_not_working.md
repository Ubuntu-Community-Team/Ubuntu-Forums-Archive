---
title: "Wireless not working"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by rhb on 2010-08-31
I installed Wubi on an acer ferrari 4000 laptop.  It works ok except I can't connect to the wireless internet.  I checked the switch in both settings and verified that it worked unchanged in Win 7.  I got an error message with the ifconv command; console output follows.  If you need more info, I would appreciate having a list of commands to get it.  Thanks for the help.

Console output:

(missing file.  sudo ifconv wlan0 up got error.
<something> not found.
I  a gain to get the output and edit this post.)

---

### Post by Darkness Des on 2010-08-31
The command you are thinking of is ifconfig, not ifconv.

---

### Post by MaindotC on 2010-08-31
I think what you mean is "ifconfig" not ifconv.  For issues with your wireless card, first consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  I'm betting that at some point you'll need to find which driver is appropriate for your wireless card and that may need to be changed.  I know I had an Acer before and they had a linux driver that you could download.

---

### Post by rhb on 2010-08-31
Too many editors, too many reboots, posting using an OS that wouldn't know an ifconfig command from a hole in the wall.  Anyway, here's the output:

acer@ubuntu:~$ 
acer@ubuntu:~$ 
acer@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:f4:6c:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16080 (16.0 KB)  TX bytes:16080 (16.0 KB)

acer@ubuntu:~$ 
acer@ubuntu:~$ 
acer@ubuntu:~$ 
acer@ubuntu:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory
acer@ubuntu:~$ 
acer@ubuntu:~$ 
acer@ubuntu:~$ 

     I will check the troubleshooting guide.  If that doesn't help, maybe the name of the missing file or directory will, or I can post some log entries if needed.  Thanks for your quick responses.

---

### Post by MaindotC on 2010-09-01
Can you also verify the Acer site with your model number and see if there's a Linux driver?

---

