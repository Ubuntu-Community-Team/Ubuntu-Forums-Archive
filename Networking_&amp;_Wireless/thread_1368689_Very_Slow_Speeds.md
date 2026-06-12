---
title: "Very Slow Speeds"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by Burky on 2009-12-30
I have a computer with a Netgear WG111v3 usb wireless card. On Windows 7 I get 5.7 mb/s download speeds but on Ubuntu I only get 0.5 mb/s?! Why does this happen and is possible to fix this? Thank you.

---

### Post by Burky on 2010-01-04
When I put lsusb into a terminal I get if that helps. ```
david@UbuntuDesktop:~$ lsusb
Bus 001 Device 003: ID 0c0b:b159 Dura Micro, Inc. (Acomdata) 
Bus 001 Device 004: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]
Bus 001 Device 002: ID 18e3:9102 Fitipower Integrated Technology Inc Multi car reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Can anyone please help me? Possibly using the windows driver with Ndiswrapper?

---

### Post by puppywhacker on 2010-01-04
First of all make sure that it is not a byte v.s. bit problem because you'll be hunting a ghost. run iperf between two computers on the link to get better readings. A well maintained windows will outperform a lousy linux anyday ... and so is the reverse. There are literally thousends of factors that have an influence and a few can be tweaked. 

I think the realtek RTL8187B should be supported in linux properly without ndiswrapper driver. using windows drivers in linux just feels wrong and dirty, so if possible I try to avoid it, it's better to go through the pain of getting it to work once than having to do it over and over again.

From an lsusb it is very hard to troubleshoot. "iwconfig" will show you the linkstrength and quality, the powersettings, the lost or corrupted packets. Beware that the linkspeed will go down to 1Mb/s without traffic. It's mainly the link quality that needs to be over 75% for a real stable connection (like in 50/71)

"dmesg" will show kernel output, so search for wlan related info. Errors will show up here or in the /var/log/messages

---

### Post by Burky on 2010-01-04
iwconfig: ```
david@UbuntuDesktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NETGEAR-2.4-G"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:B2:AC:6E:67   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


As far as the dmesg goes, I have multiple entries with word "wlan" that state > Jan  3 16:28:03 UbuntuDesktop kernel: [   20.183144] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  3 16:28:15 UbuntuDesktop kernel: [   31.431119] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

Thank you a lot puppywhacker for at least replying. This really bothers me how slow it is. It did it on a fresh install of 32bit Ubuntu as well as 64bit Ubuntu, the speed are always slow. Think you're able to help me? Or anyone else?

---

### Post by jbslaw on 2010-01-04
I agree with puppywhacker that the speed numbers in the original post don't make sense, but there is a genuine speed problem with the RT8187B chipset under Karmic, one you can definitely observe and measure.

The 8187B card works out of the box with Karmic - except it works slowly as the OP has experienced.  I typically got 11 Mb/s.  In order to get 54 Mb/s, I had to use ndiswrapper.  In Karmic, that is an adventure all its own.

The ndiswrapper version in the Karmic repositories has a bug that prevents it from accessing an encrypted network, either WPA or WEP.  That was resolved by downloading the source code, adding a couple of patches, compiling it, and installing it.  Blacklisting the native 8187 module, unloading it, loading the ndiswrapper module, installing the windows driver using ndiswrapper, and all was well, almost.

The next hitch was that netmanager didn't work correctly with ndiswrapper.  I replaced netmanager with wicd and it logged in successfully to my network.  An additional script to the power management code to remove the ndiswrapper module when suspending and install it when resuming fixed my remaining issues.  I now get a reliable 54 Mb/s connection that comes back when I resume from a suspend.  I haven't yet tested what happens when I hibernate.  There is still a modest delay in dns lookup that I can't fix through the usual workarounds (blocking ipv6, reordering the "hosts" line in /etc/nsswitch.conf).  But it works well enough and downloads are as fast as under windows.

All of the details about these workarounds are available by searching this forum.  

> **puppywhacker said:**
> First of all make sure that it is not a byte v.s. bit problem because you'll be hunting a ghost. run iperf between two computers on the link to get better readings. A well maintained windows will outperform a lousy linux anyday ... and so is the reverse. There are literally thousends of factors that have an influence and a few can be tweaked. 

I think the realtek RTL8187B should be supported in linux properly without ndiswrapper driver. using windows drivers in linux just feels wrong and dirty, so if possible I try to avoid it, it's better to go through the pain of getting it to work once than having to do it over and over again.

From an lsusb it is very hard to troubleshoot. "iwconfig" will show you the linkstrength and quality, the powersettings, the lost or corrupted packets. Beware that the linkspeed will go down to 1Mb/s without traffic. It's mainly the link quality that needs to be over 75% for a real stable connection (like in 50/71)

"dmesg" will show kernel output, so search for wlan related info. Errors will show up here or in the /var/log/messages

---

### Post by Burky on 2010-01-04
> **jbslaw said:**
> I agree with puppywhacker that the speed numbers in the original post don't make sense, but there is a genuine speed problem with the RT8187B chipset under Karmic, one you can definitely observe and measure.

The 8187B card works out of the box with Karmic - except it works slowly as the OP has experienced.  I typically got 11 Mb/s.  In order to get 54 Mb/s, I had to use ndiswrapper.  In Karmic, that is an adventure all its own.

The ndiswrapper version in the Karmic repositories has a bug that prevents it from accessing an encrypted network, either WPA or WEP.  That was resolved by downloading the source code, adding a couple of patches, compiling it, and installing it.  Blacklisting the native 8187 module, unloading it, loading the ndiswrapper module, installing the windows driver using ndiswrapper, and all was well, almost.

The next hitch was that netmanager didn't work correctly with ndiswrapper.  I replaced netmanager with wicd and it logged in successfully to my network.  An additional script to the power management code to remove the ndiswrapper module when suspending and install it when resuming fixed my remaining issues.  I now get a reliable 54 Mb/s connection that comes back when I resume from a suspend.  I haven't yet tested what happens when I hibernate.  There is still a modest delay in dns lookup that I can't fix through the usual workarounds (blocking ipv6, reordering the "hosts" line in /etc/nsswitch.conf).  But it works well enough and downloads are as fast as under windows.

All of the details about these workarounds are available by searching this forum.

So you think I should use Ndiswrapper?

---

### Post by apokaliptik on 2010-01-04
So has many of the users around here, I'm new to the whole linux thing and only know a few basic commands yet, and lucky me I happen to have a network adapter who works with RTL8187B. Just my luck. I have a WPA Shared key network at home, and I just can't get the connection to work properly, It's so slow I can barely open websites. At campus, I have a WPA2 Enterprise, and in that case I can't even connect to the network. Like I read in here, I have installed wicd and used ndiswrapper for the rtl8187b driver; That however, didn't do much difference since I still can't get the usual internet speed I get in Windows 7. I also tried installing a Belkin N1 USB Wireless Adapter, I had to install the driver with ndiswrapper too, but that one when tried to connect to the home network would just crash my ubuntu, I couldn't press any buttons at all, and doing the shutdown command on the ctrl+alt+f2 console wouldn't work. So I came back to the RTL8187B board.


My question is if someone could direct me to those posts around the forums that could help me fix the problem; I have searched enough however I haven't been able to find anything that could help me.

---

### Post by jbslaw on 2010-01-04
If you're convinced that the speed problem you're experiencing isn't just the dns lookup delay that has been discussed so much, if you want to roll up your sleeves, and if you don't mind having a bit of windows code running on your system, sure.  But knowing how to search the forums is the main skill.  The problem with encryption, the problem with netmanager, problems with trying to use 32-bit drivers in a 64-bit environment, all have been experienced by others.  Even the problem with suspend and resume and ndiswrapper took some digging.  

The advantage to using the native rt8187 driver is that it works, albeit slower than I liked.  The main problem that I had with wireless was my old router's inability to deal with Karmic's dns lookups.  Fix that and it's almost tolerable for me.  If you need speed to avoid streaming video delays, etc., you might benefit from ndiswrapper and the windows driver from Realtech.

> **Burky said:**
> So you think I should use Ndiswrapper?

---

### Post by Burky on 2010-01-04
Maybe it's best I just abandon Linux altogether...

---

### Post by Burky on 2010-01-05
One other quick thought, could this be running at B speeds instead of the N?

---

### Post by Burky on 2010-01-06
I'm currently using the rtl8187 driver and this is rtl8187b chipset, so if i install the driver from [here]("http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/") will this work better?

---

### Post by jbslaw on 2010-01-06
Take a look at this: [https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b]("https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b").  It has everything you need to know about getting the 8187B working under ndiswrapper.  

> **Burky said:**
> I'm currently using the rtl8187 driver and this is rtl8187b chipset, so if i install the driver from [here]("http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/") will this work better?

---

### Post by Burky on 2010-01-06
> 3 post 2.6.24 kernels have been released in use for Ubuntu and still these limitations apply. If anyone knows what is wrong with the kernel module in use, please share with me [email]onewithnature83@gmail.com[/email] or Ubuntu Kernel Team, or your distribution to push development of drivers that make our wifi work as it should. 

Does this mean they're working on fixing this problem and in future releases it will be possibly fixed?

And thank you a lot for the link and help jbslaw, I appreciate it a lot.

---

### Post by Burky on 2010-01-06
I tried installing that driver, but I got an error when I ran ```
sudo ./makedrv
```

---

### Post by puppywhacker on 2010-01-07
Which error?

---

### Post by Burky on 2010-01-07
NVM, I got it to work all the way through on 8.04... it was unable to detect the wireless...

---

### Post by Burky on 2010-01-07
Good news! Ndiswrapper seems to work wonders with this. =)

---

### Post by starwobble on 2010-01-11
Okay, I have a similar problem here, but I don't think it's related to the wireless. Like Burky, my wireless is unbearably slow when I'm trying to download something, but an ethernet connection is just as bad. I'm trying to sudo apt-get jdk and other programs in the ubuntu software center, but I can't do anything because the downloads are so slow. I'm running the STA drivers on my BCM4312 wireless card. Is it something with the network manager?

---

### Post by starwobble on 2010-01-11
Okay, I don't think NetworkManager is the problem. I just installed Wicd and am having the same problems again. I'm getting transfer rates on my download at 455 B/s. Any ideas?

---

