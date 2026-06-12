---
title: "A lot of dropped rx packets on usb wireless adapter"
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by Lucifiel on 2013-02-01
I've no idea what to do... 

On Linux Mint 14 Xfce using Zyxel ndw2205 with pre-installed wireless drivers blacklisted in modprobe and loading self-compiled drivers from Realtek. 

Any advise on how I can reduce amount of dropped packets?

> 
tomato@tomato-Satellite-L510 ~ $ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2663 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:292481 (292.4 KB)  TX bytes:292481 (292.4 KB)

wlan1     Link encap:Ethernet  HWaddr 50:67:f0:00:25:b9  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5267:f0ff:fe00:25b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:578165 overruns:0 frame:0
          TX packets:94 errors:0 dropped:11 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:146940560 (146.9 MB)  TX bytes:1028191410 (1.0 GB)

> 

tomato@tomato-Satellite-L510 ~ $ ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr 50:67:f0:00:25:b9  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5267:f0ff:fe00:25b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6237 errors:0 dropped:584342 overruns:0 frame:0
          TX packets:5205 errors:0 dropped:11 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:152781180 (152.7 MB)  TX bytes:1029300391 (1.0 GB)



---

### Post by mikewhatever on 2013-02-01
If Zyxel ndw2205 is a USB adapter, you should post the output of lsusb, and if it is an internal pci one, then of lspci. It also wouldn't hurt to know what module is in use.

---

### Post by Lucifiel on 2013-02-01
Err, module? Sorry, I just came back to Linux and all my knowledge is quite rusty! 

Thanks for all the help, though. :)

Is this the right "module" you mentioned? 
> 
tomato@tomato-Satellite-L510 ~ $ lsmod
Module                  Size  Used by

8192cu                506828  0 



> tomato@tomato-Satellite-L510 ~ $ lsusb
Bus 001 Device 003: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 002 Device 003: ID 0bda:8198 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 003 Device 002: ID 0930:020f Toshiba Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0586:341f ZyXEL Communications Corp. NWD2205 802.11n Wireless N Adapter [Realtek RTL8192CU]
Bus 002 Device 005: ID 046d:c05b Logitech, Inc. M-U0004 810-001317 [B110 Optical USB Mouse]
Bus 002 Device 006: ID 08bb:2702 Texas Instruments Japan Speakers


Also, from /etc/modprobe.d:
> #blacklist realtek wireless n drivers for Zyxel nwd2205
blacklist rtl8192cu 


---

### Post by mikewhatever on 2013-02-02
Thanks for the output. You seem to have two wireless adaptes. Are they both on at the same time? Do you still get lots of dropped packets with RTL8187B Wireless Adapter off?

What kernel version does Linux Mint 14 use?

---

### Post by Lucifiel on 2013-02-02
The onboard lan is disabled 'cos it's wonky. Ah, I disabled it a few days ago. 

> 
From blacklist.conf: 
#blacklist on-board sucky and crashy realtek wireless drivers 
blacklist rtl8187
blacklist rtl8187b


Had to google to find out the command again. Why, it's been years since I touched Linux commands. 
> 
tomato@tomato-Satellite-L510 ~ $ uname -a
Linux tomato-Satellite-L510 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux


---

### Post by mikewhatever on 2013-02-02
Hm..., not sure what's the problem. 8192cu from realtek.com is for kernels 3.0.8 and older, and while it worked well in the 3.2 and 3.3 kernels version, I am not sure about the 3.5. Reportedly, it wouldn't even install on 3.8.

PS: I've filed a bug report some time ago, but it is still open.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190)

---

### Post by Lucifiel on 2013-02-02
Hmmm... that's all rather strange indeed. Oh well, I hope Realtek issues more updates soon.

---

### Post by Lucifiel on 2013-02-02
K I'm back in Windows for now but anyone knows how to cleanly uninstall the drivers completely? Also, I might have screwed up the o/s by installing 1 ver of the wireless drivers over an older ver.

Maybe I should just reinstall Mint.

---

### Post by mikewhatever on 2013-02-03
To uninstall the 8192cu driver from realtek.com, open a terminal, change to the installation directory, then run
```
sudo make uninstall
```

Also, installing one version of such a driver over another shouldn't cause any trouble.

---

### Post by Lucifiel on 2013-02-03
Ah well, thanks for all your help! =)

I'll continue working on this issue once I fix my broken Xfce desktop(am posting from Win). Will be a bit busy over the next few days since I'm preparing for CNY so my progress will be slower. 

Yeah, I apparently updated the kernel and image.

---

### Post by Lucifiel on 2013-02-04
In the end, I reformatted. I'd broken too many things and couldn't figure out how to fix some of them.

The errors still continue, lol. I think I'll ignore them for now until my internet grinds to a stop. 

Edit: 
In the end, I found this which might explain the excessive no. of dropped packets. In short, whatever.: 
[http://forums.dlink.com/index.php?PHPSESSID=ce8a98ae4f17869a233c4594b5797efa&topic=2844.0](http://forums.dlink.com/index.php?PHPSESSID=ce8a98ae4f17869a233c4594b5797efa&topic=2844.0)

---

### Post by mikewhatever on 2013-02-04
So, did you have to build the driver from realtek.com, or does the built in now work?

Dropped packets can, indeed, depend on the channel congestion, so, if there are too many wireless station on the same channel, you could try switching the router to a different one.

---

