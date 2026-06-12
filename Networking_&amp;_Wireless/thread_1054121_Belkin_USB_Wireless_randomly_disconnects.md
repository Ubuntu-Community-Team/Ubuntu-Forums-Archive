---
title: "Belkin USB Wireless randomly disconnects"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by dorkdork777 on 2009-01-29
I've got a [Belkin F5D7050 3xxx series USB WiFi dongle]("http://www.belkin.com/support/article/?lid=en&aid=5381"). When it's connected to my open network (named "parkymeh"), it gets somewhere between 45% and 68% connection - however sometimes it will suddenly drop it. Sometimes I can go days without it dropping, other times (like now) it will go three or four times in one hour.

sudo iwconfig output:
```
chris@chris-desktop:~$ sudo iwconfig
[sudo] password for chris: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"parkymeh"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:A9:50:38   
          Bit Rate=54 Mb/s   Tx-Power=18 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=50/100  Signal level:-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

I've heard ndiswrapper might solve my problem - but I don't know where to start with that.

Any help at all would be much appreciated :)

---

### Post by pritamps on 2009-01-29
Hey,

You might not need ndiswrapper. With the new updated kernel (2.6.27-11 or something), these disconnects don't happen. I had the same problem. It has something to do with the way the Belkin and the USB port interact, I guess (even though I might be completely wrong :P)

If you are rebooting every time this happens, you might not need to. When the network disconnects, run the following in a terminal

```
 sudo modprobe -r zd1211rw 
sudo modprobe zd1211rw
```

That will removes and reloads the driver module for the dongle. If that doesn't work, try

```
sudo modprobe -r ehci_hcd
sudo modprobe ehci_hcd
```

This removes and reloads the driver module for the USB 2.0 port. If this doesn't work, you could try ohci_hcd, and then reboot :)

---

### Post by dorkdork777 on 2009-01-29
Really? Thanks a lot for the reply! I've installed the new kernel, but it doesn't work with my manually installed NVIDIA drivers; I need to reinstall them. I'll do that ASAP.

Thanks a lot; I'll report back after a week or so. :D

---

