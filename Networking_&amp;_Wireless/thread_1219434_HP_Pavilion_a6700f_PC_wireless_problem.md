---
title: "HP Pavilion a6700f PC wireless problem"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by NeilBlack on 2009-07-21
My friend's Vista installation went to crap recently, and since he is without a reinstall disk he has decided to try Ubuntu at least until he can get a Vista disk.

He has an HP Pavilion a6700f PC. I haven't been able to find what wireless card specifically he has, but it's whatever comes with that model of computer, because he hasn't changed any of the hardware.

We've gotten Ubuntu installed ok, and it will connect to his home wireless network, but we can't access the internet. I know the wireless network itself is working, because I'm posting through it right now (from my Ubuntu computer). So the problem should be in his computer.

---

### Post by NeilBlack on 2009-07-22
Now that I've had time I've looked up that the wireless card is a Wireless LAN 802.11 b/g

At least, that's the best that I can find. Is that the name of an actual card? It sounds more like the name of a type of card than a specific one.

---

### Post by superprash2003 on 2009-07-23
post output of **lshw -C network** , that would give a better idea on your wifi card

---

### Post by NeilBlack on 2009-07-28
*-network:0
    description: Wireless interface
    physical id: 1
    logical name: wlan0
    serial: 00:22:5f:58:e4:d3
    capabilities: ethernet physical wireless
    configuration: broadcast=yes ip=192.168.2.100 multicast=yes wireless=IEEE 802.11bg

---

### Post by roosh on 2010-07-02
I have the same computer as your friend. The built in driver works very poorly. 

What I did to get the wireless working is this:

1) install ndiswrapper:
```
sudo apt-get install ndiswrapper-utils
sudo apt-get install ndiswrapper-common 
```


2) get the correct windows XP drivers based on your system architecture (32-bit vs. 64-bit)

If you can't find them (it took me a loooong time to find them), I've attached them (at the bottom of this post).


3) Put all the files together in a folder (or just extract the folder matching the architecture I attached) 


4) Disable the driver that doesn't work (the one that came with Ubuntu):
```
sudo rmmod rt73usb
```


5) Use the graphical interface with ndiswrapper to install the driver. Or use the command: ```
sudo ndiswrapper -i [COLOR="Red"]"path to inf file"[/COLOR]
```

note: [COLOR="Red"]"path to inf file"[/COLOR] should be replaced by the actual path to the .inf file in the folder


6) It should now be installed. Activate ndiswrapper: ```
sudo modprobe ndiswrapper
```


7) Wait a while (~1 minute). Then check the network box at the top -- you should be able to find a network.


8) If it works, then permanently disable any other drivers that would interfere:
```
sudo gedit /etc/modprobe.d/blacklist (if you are using Ubuntu)
sudo kate /etc/modprobe.d/blacklist (if you are using Kubuntu)
```
at the bottom copy and paste the following to the file:
```
# Blacklist rt73usb
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib
```
(note: this step was adapted from diepruis's guide that I could not get to work here: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236))


9) Make sure ndiswrapper starts at boot: a good guide can be found here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Automatically%20loading%20at%20start-up](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Automatically%20loading%20at%20start-up)

---

