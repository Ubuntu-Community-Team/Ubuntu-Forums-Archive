---
title: "what am I forgetting to do here?"
date: 2006-02-02
forum: Networking &amp; Wireless
---

### Post by closeyourwindows on 2006-02-02
have a wpc54g linksys card:
googled it and tried their fixes, tried ubuntu forum fixes, tried how to's all over and I have the hardware present and the driver present but cannot get wlan0  to show up to activate it.  I edited the /etc/network/interfaces file and added wlan0 in there and that still did no work.  I am at a loss here and could use a little help.  
```
nate@picfix:~$ sudo iwconfig
Password:
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

nate@picfix:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

nate@picfix:~$ sudo ndiswrapper -m modprobe config already contains alias directive

nate@picfix:~$ ndiswrapper -l Installed ndis drivers:
bcmwl5  driver present

nate@picfix:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:DA:2F:16:9B
          inet addr:xx.xx.131.159  Bcast:255.255.255.255  Mask:255.255.255.128
          inet6 addr: fe80::250:daff:fe2f:169b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3 txqueuelen:1000
          RX bytes:2376667 (2.2 MiB)  TX bytes:177308 (173.1 KiB)
          Interrupt:9 Base address:0x4800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:858776 (838.6 KiB)  TX bytes:858776 (838.6 KiB)

```

I even installed another driver and here is the results:
```
nate@picfix:/etc/ndiswrapper/lsbcmnds$ sudo ndiswrapper -l Installed ndis drivers:
bcmwl5  driver present, hardware present
lsbcmnds        driver present, hardware present

```

---

### Post by towsonu2003 on 2006-02-02
sudo modprobe ndiswrapper

edit: I guess I gave too little info?

---

### Post by Lambert on 2006-02-02
adding wlan0 to the interfaces file is just telling the system how to configure the already present interface when activating it.

If you don't have wlan0 showing up when you run the command iwconfig then you basically don't have a working driver. ndiswrapper shows both driver and device but the driver is still not functioning as it should.

Now the simple question... is ndiswrapper loaded

```
lsmod | grep ndis
```

should give you this.

```
ndiswrapper           170388  0
usbcore               129668  3 ndiswrapper,uhci_hcd

```

if not you need to load ndiswrapper

```
sudo modprobe ndiswrapper
```

If it is loaded then there is a problem with the driver you're using.

these are just common things I've seen before.

1. is the driver on your hard drive? it should be as it can't be loaded via cd-rom
2. There is at least a .sys file that needs to be in the same folder as the .inf file You may also need a .bin file
3. Make sure there is only one copy of each file in the folder. 
4. You need to consider trying other drivers until you find one that works.
5. depending how new the device is, you may need to install a newer version of ndiswrapper. version in breezy is 1.1 and current release is 1.8

---

### Post by closeyourwindows on 2006-02-03
```
nate@picfix:~$ lsmod | grep ndis
ndiswrapper           114376  0
usbcore               104188  3 ndiswrapper,uhci_hcd

```

```
nate@picfix:~$ sudo modprobe ndiswrapper
Password:
nate@picfix:~$

```

I get nothing when I try sudo modprobe ndiswrapper and I have tried all the drivers I can find from linksys website.  any other suggestions, I am ready to re install at this point and start from scratch.

---

### Post by towsonu2003 on 2006-02-03
no output to modprobe ndiswrapper means the module (driver) was loaded. but, of course, it doesn't mean it is working...

it seems you don't have the right driver for the wireless (if you still don't have any wireless in the output of sudo iwconfig). no need to re-install ubuntu. you can just uninstall the current ndiswrapper drivers and try other drivers (read end of this post as well). 

The **list of drivers** and what people tried for them is available from here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

**First section** of this ubuntu wiki page shows **how to find which driver** you need in that list: [https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

This ubuntu wiki page describe how to **install the latest ndiswrapper** (download the latest instead of the one it suggests) [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

Use the latest ndiswrapper after uninstallning the one you have

**download** here: [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

**installation howto from ndiswrapper itself** here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

**uninstallation info from ndiswrapper itself** here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall)

A particular path to follow would be: 
1. use ndiswrapper page to uninstall driver and ndiswrapper (use synaptic to uninstall anything ndiswrapper related as well)
2. use ndiswrapper page to download latest version
3. use ubuntu wiki (but adjust it to your version) to install it
4. use ubuntu wiki to find out which wifi you are using
5. use ndiswrapper page to find which drivers worked for your wifi. 
6. get them and try each one by one using the ubuntu wiki (uninstall the one that didn't work, install the one that you will try next)*****. 

I bolded stuff just to make this readable.

*****To uninstall a driver (not ndiswrapper itself):
```
sudo ndiswrapper -l
``` to get the name of the driver you will uninstall
```
sudo ndiswrapper -e drivernamehere
```to remove that driver

PS. Stop and post any errors you get during the process here (if you get any). It is not supposed to give any errors.

PS2. The five point that Lambert mentioned are very important.

---

### Post by closeyourwindows on 2006-02-03
will try that and post results,  thanks you for all your help so far!  This is why I will always use ubuntu.

---

### Post by closeyourwindows on 2006-02-03
this may seem hard to believe but I followed every bit of that, which by the way was extremely helpful, and I got the exact same error.  the only thing I did not do was uninstall ndiswrapper because sourceforge seems so be having an issue right now, so I will uninstall and as soon as I can get the latest version I will install it and hopefully get this thing running.  I did try the page on 2 other computers, one here and another from a friends network, so I know for sure that sourceforge is updating or getting ready for the deadly worm to strike.  

in any case, I did learn a lot and will keep try this later and thanks again for all the replies, they have all been helpful.

---

### Post by towsonu2003 on 2006-02-03
while you are waiting, try other drivers from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) that users reported as working with your thingy. uninstall one driver, install the other one and so on (one driver at a time). If the latest ndiswrapper doesn't work either, you might wanna file a bug report with them (after checking existing bugs).

---

### Post by closeyourwindows on 2006-02-03
ok, so last night I was waiting and waiting for source forge to come back on line and I got too frustrated, and I really did try all the drivers and read all the info that was posted in this thread.  It helped me realize that I needed to back up all my data and re install.  so after work I came home and reinstalled and followed the links and I finally got it working.

```
nate@ubuntupicfix:~/Linksys$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:17 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:518   Missed beacon:0

```
wifi radar found the router and connected to it and I think I need to tweak it alittle more, but all is good, for now.  Thank you all for your help.

---

### Post by closeyourwindows on 2006-02-03
one final note.  I installed gtkwifi, which is a lifesaver to a non scripter, and I am now posting this using wireless.  y'all are awesome.
wooooohoooooo!:mrgreen:

---

### Post by towsonu2003 on 2006-02-03
that's great to hear!

---

