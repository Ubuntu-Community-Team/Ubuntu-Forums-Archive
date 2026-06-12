---
title: "Wireless keeps disconnecting. Help!?"
date: 2012-09-29
forum: Networking &amp; Wireless
---

### Post by ubububus on 2012-09-29
Hello everyone,

I'm new to Ubuntu - have used Windows all my life - and, besides some other small problems I've encountered, this one is particularly worrying me. My internet connection keeps dropping off after having been connected for a while (it can take between half an hour and a couple of hours before it disconnects). When this happens there's no way I can get it work again - a window asking me to reconnect will pop up but of course it doesn't work. I simply have to switch off my laptop, wait for 10-15, and then switch it on again. 

I know it has something to do with Ubuntu because this didn't happen with Windows, it only started when I switched to Ubuntu. I also know that it's not my modem because I went to the public library the other day just to check if it would disconnect there, and it did - much of the same, after half an hour of being connected it stopped working, and I couldn't get it work after that.

I've searched through the forum and tried several things some of you have posted here, and I have to say sometimes without even knowing what I was doing, but I'm desperate and I don't know what else to do. Any ideas?

Oh, I have Ubuntu 12.04. Had 11.04 at one point before and encountered the same problem.
Thanks.

---

### Post by uncaspi on 2012-09-29
I assume it is wireless issue?
Open a therminal and issue the following command.


sudo iwconfig wlan0 txpower 20 power off

wlan0 is the logical name of my card replace with yours. You`ll find
it by issuing this command.


sudo ifconfig

---

### Post by ubububus on 2012-09-29
Hey, thanks for replying.
I suppose wlan0 is the name of my card too because this is what I got:

> eth0      Link encap:Ethernet  HWaddr 00:1b:38:65:04:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24623 (24.6 KB)  TX bytes:24623 (24.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:0d:a9:f6  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe0d:a9f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:783909 (783.9 KB)  TX bytes:172594 (172.5 KB)

But then when I ran the command as you said and it gave me this error:

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

What did I do wrong?

---

### Post by uncaspi on 2012-09-29
Nothing is wrong, but your driver does not support these commands. That lead us to a driver issue. But first we had to look if you have enough signal strength from your router. Please issue this command

sudo iwlist scan

and have a look at signal strenght. All below -75 dBm is good.

---

### Post by ubububus on 2012-09-29
Yes, it is below 75. Anyway, I don't think lack of signal is the problem since I have to deal with this issue everywhere every time I try to connect to a wireless network

---

### Post by uncaspi on 2012-09-29
Ok fine. Let us see if it could be a driver issue. Please post the content of 
sudo lshw -C network

---

### Post by ubububus on 2012-09-29
Ok, here's what I got:
> *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: NVIDIA Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:65:04:7f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:42 memory:f2688000-f2688fff ioport:30f8(size=8) memory:f2689c00-f2689cff memory:f2689800-f268980f
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:0d:a9:f6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-31-generic firmware=N/A ip=192.168.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f2200000-f220ffff

---

### Post by uncaspi on 2012-09-29
so you see that the driver is ath5k. Then you had a lot of research in front of you. You must search the forum with keyword ath5k aand look for any problems related to this driver.

---

### Post by ubububus on 2012-09-30
I did what you suggested but couldn't find any clear answer or solution to the problem. Tried different things but none of them helped  because it keeps disconnecting . But thanks anyway

---

### Post by uncaspi on 2012-09-30
Look at this thread.

[http://ubuntuforums.org/showthread.php?t=1973863&highlight=ath5k](http://ubuntuforums.org/showthread.php?t=1973863&highlight=ath5k)

---

### Post by ubububus on 2012-10-01
Thanks for the link, but there are a few things I don't know how to do.

> that didn't work straight away and it threw me off again. However I then  tried deleting the existing config and adding it again. This time it  has not dropped my connection and seems to be working just fine.

> I added
options ath5k nohwcrypt=1
to
/etc/modprobe.d/ath5k.conf

and this seems to have made the change permanent.

How can I delete the existing config and add it back? Also I don't know how to do the second part, 
adding options ath5k nohwcrypt=1 to /etc/modprobe.d/ath5k.conf.
If you could tell me how to do this I'd really appreciate it.

---

### Post by ubububus on 2012-10-01
ups, double post.

---

### Post by uncaspi on 2012-10-01
Just add options ath5k nohwcrypt=1 to /etc/modprobe.d/ath5k.conf

reboot and see id works.

I either cant understand what he ment by deleting and then adding it again.

---

### Post by ubububus on 2012-10-01
You mean in the terminal? It gave me a command not found message.

---

### Post by uncaspi on 2012-10-01
I ment just add the option to the file suggested in the link and just reboot.
There are several editors you could use to edit files. nano,pico and gedit. You must be root to save.

---

### Post by ubububus on 2012-10-02
That didn't work either. I think I'm gonna take it to a repair shop, I've had enough with it. Thank you uncaspi for your help.

---

