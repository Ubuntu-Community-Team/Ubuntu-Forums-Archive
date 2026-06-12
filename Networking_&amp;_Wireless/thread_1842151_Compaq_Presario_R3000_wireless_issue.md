---
title: "Compaq Presario R3000 wireless issue"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by Reddbull on 2011-09-10
I have a Presario R3000 that didn't ship with a wireless card in it. I have installed Zorin OS (ubuntu hybrid) on it and it is working fine. I pulled the wireless card and antenna from a dead hp z5000 and installed it in the R3000. The card is recognized and seems that the driver is loaded according to the results from iwconfig. In the list for wlan1 under iwconfig it says the wireless card is off. I don't know how to turn it on since this computer did not come with the blue light or switch that others have commented on in similar posts with wireless problems on the R3000. Does anyone know if there is a way to add a switch and precisely where it would hook to the motherboard. Or is there a bios update that would let me turn it on there. I have looked in the current bios and it's very basic and nothing about enabling the mini pci or wireless. I am a computer tech but a linux noob. 
Any suggestions would be greatly appreciated

---

### Post by nm_geo on 2011-09-10
> **Reddbull said:**
> I have a Presario R3000 that didn't ship with a wireless card in it. I have installed Zorin OS (ubuntu hybrid) on it and it is working fine. I pulled the wireless card and antenna from a dead hp z5000 and installed it in the R3000. The card is recognized and seems that the driver is loaded according to the results from iwconfig. In the list for wlan1 under iwconfig it says the wireless card is off. I don't know how to turn it on since this computer did not come with the blue light or switch that others have commented on in similar posts with wireless problems on the R3000. Does anyone know if there is a way to add a switch and precisely where it would hook to the motherboard. Or is there a bios update that would let me turn it on there. I have looked in the current bios and it's very basic and nothing about enabling the mini pci or wireless. I am a computer tech but a linux noob. 
Any suggestions would be greatly appreciated

I also have a partition with Zorin 5 on it but I rarely boot it up.  It is built on Ubuntu so it should operate basically the same.

```
uname -r

```Above gives us the kernel you are running.

```
lspci -nn
```Info on installed cards 


```
sudo lshw -C network
```Networking information
```

lsmod
```Drivers and modules loaded

```
nm-tool
```More info on network .. If you don't have it follow instructions to install.

Please copy and paste the results in thread.  If you click on the # symbol and paste your results in the middle it will make the boxed information easier to read.

---

