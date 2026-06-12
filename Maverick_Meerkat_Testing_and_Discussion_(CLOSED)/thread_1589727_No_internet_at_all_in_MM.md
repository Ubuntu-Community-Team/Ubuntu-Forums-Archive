---
title: "No internet at all in MM"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by PuddingKnife on 2010-10-06
Did a fresh install of 10.10 on a Dell Mini 10v. Everything works flawlessly except internet; wire and wireless.

> 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Im guessing that's the culprit. I think I'd be able to fix this if the wired connection worked, but I dont know what to do with this one.

Any ideas?

---

### Post by 23dornot23d on 2010-10-06
iwconfig ..... what does it show .....

Mines gone too .... no wireless

```

keith@keith-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
keith@keith-laptop:~$ uname -a
Linux keith-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
keith@keith-laptop:~$ 


keith@keith-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:53:ac:06  
          inet addr:192.168.1.60  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe53:ac06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3916712 (3.9 MB)  TX bytes:741301 (741.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:32:f8:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

keith@keith-laptop:~$ 

lspci

07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)



```I just checked my latest update .... 
I too have lost my wireless connection ..... but the wired etho is ok .........

I will check a earlier version .........

---

### Post by DougieFresh4U on 2010-10-06
My wireless went with updates last night. Wired is working ok.

```
dougie@Dougie64Beta:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
dougie@Dougie64Beta:~$
```

---

### Post by 23dornot23d on 2010-10-06
Yep seems like the last few updates killed the wireless .....

This is a version of MM on the same drive ..... that I have not fully updated and it is ok 

```

keith@keith-laptop:~$ uname -a
Linux keith-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
keith@keith-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Livebox-90A8"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:7E:02:6D:A4   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

keith@keith-laptop:~$ 


```

---

### Post by PuddingKnife on 2010-10-06
Results from iwconfig:

> 
lo     no wireless extensions

eth0   no wireless extensions

wlan0  IEEE 802.11bg  ESSID: off/any
       Mode:Managed  Access Point: Not-Associated  Tx-Power=20 dBm
       Rety  long limit:7  RTS thr: off  Fragment thr: off
       Power Management: off

---

### Post by 23dornot23d on 2010-10-06
Have you tried selecting it in the top panel ..... the blue wire coming out of the socket icon ......

[IMG]http://img808.imageshack.us/img808/87/screenshot2we.jpg[/IMG]

Seems weird but mine had been switched off at startup never usually does this ........ 
its ok now ..... after selecting the wireless icon

---

### Post by PuddingKnife on 2010-10-07
Anyone? I dont understand why the ethernet connection doesn't work..

---

### Post by DougieFresh4U on 2010-10-07
> **PuddingKnife said:**
> Anyone? I dont understand why the ethernet connection doesn't work..
Only thing I can offer is that my ethernet wouldn't work until I **disabled** wireless. I am on my Win7 at the moment and gonna boot MM later and check out updates to see if all is sorted out.

---

### Post by davrosuk on 2010-10-07
My experience through this cycle has been that certain updates have done odd things to my eth connections. More wired issues than wireless. I've found that a number of times I've had to do:
```
ifconfig eth0 down
ifconfig eth0 up
dhclient
```
A reboot wouldn't fix it, the above would... Then it would be fine on subsequent bounces.

---

### Post by cariboo on 2010-10-07
I did some iso testing this nmorning, I decided to do the install without a network connection. I used a usb device to do the install, I couldn't install the Broadcom restricted STA directly from the USB device, and synaptic kept asking for a cdrom, so I mounted my usb device to /cdrom, marked as present in software sources, then reloaded the repositories. I was then able to install the restricted drivers. In my case the command was:

```
sudo mount /dev/sdb1 /cdrom
```

Once the repositories were reloaded just search for bcmwl-kernel-source and mark it for installation, and click apply. All the dependencies were automatically installed.

---

### Post by PuddingKnife on 2010-10-07
Oh, my goodness. 

I got it working, using guidelines found here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

under the b43 - No Internet Access heading.

Thank you guys for your help!

---

