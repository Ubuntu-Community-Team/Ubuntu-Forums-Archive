---
title: "Atheros AR5001 Wireless (Acer AAO150) not detecting networks. UNR 9.04-9.10."
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by Repgahroll on 2009-08-18
Hello.

I have an Acer Aspire One A150, and it was working just fine until this week, when wireless just began to refuses to work... i tried Ubuntu(9.10, 9.04 was installed) and Moblin(latest) from usb, and both system also could not connect any wireless networks nor detect them, so i thought it was a hardware fault, then, i restored the original linpus system today to send it to the warranty repair service, but when i tried to connect the wireless network using linpus, it was working very well...

So i installed Ubuntu 9.10 and the network was working until i toggle the network 'hardware switch' off (to test if it was working), then the thing stopped, and even if i switch it on again, it stays "off"(?).

I'm going to install 9.04 again because 9.10 is pretty unstable, but i want to know if there's a way to fix this, i found a lot of topics talking about its old thing that don't work on >=9.04 versions.

lspci detects the card as Atheros AR5001, and the hardware drivers program display nothing about it (it used to display something before).

Thank you very much and sorry my english.

---

### Post by Katalog on 2009-08-18
Have you tried out Linux4One? It's an Ubuntu based distro made specifically for the Acer Aspire One, so you might have better luck with it than regular UNR 9.04:

[http://www.linux4one.it/#inglese](http://www.linux4one.it/#inglese)

---

### Post by jurelex on 2009-08-22
Hi, I'm having the same problem with my AAO, I'm using Linux Mint 7 (based on Ubuntu 9.04).

First of all, here is some hardware info:
> 
ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:24:2b:b7:48:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

> iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


When I try:
> sudo ifconfig wlan0 up
[sudo] password for renato: 
SIOCSIFFLAGS: Resource temporarily unavailable


I've noticed that the problem starts either when coming back from suspend or when the front switch is tuned off.
I've been able to make the wireless work again, but I don't know exactly how. Here's a list of things I've done, hopefully somebody can help us.
1. Enabled the Atheros "madwifi" driver (Menu>Administration>Hardware Drivers), restarting the computer, disabling the Atheros madwifi driver and restarting again.
2. Using the following code (I found it on other forum, supposedly has something to do with the hardware switch)
> 
sudo /usr/bin/setkeycodes e056 158
sudo /usr/bin/setkeycodes e055 159

3. Uninstalling network-manager-gnome, istalling wicd, uninstalling wicd, reinstalling network-managr-gnome

As I said, eventually after trying all those things over and over, the wireless network comes back, but I lose it again after coming back from suspend or by using the hardware switch.

Any comments or suggestions will be greatly appereciated.

@Katalog
I just downloaded linux4one, will try it and post the results.

---

### Post by johnnyspflame on 2009-10-30
I have had roughly the same issue. I am able to join the wireless network (wap protected) however the only app that will access the internet thus far has been empathy. Firefox will not load the page and in fact will usually result in a loss of connection. I have replaced the gnome network manager with wicd and have tried many of the suggested fixes but have thus far not been able to fix this issue. 

Any suggestions??

---

### Post by kellopes on 2010-01-22
ok.. I am having problems with my AR5001 as well. However, my computer is not a Acer.. is a Compaq Presario CQ50-110US

i just installed linux ubuntu 9.10 (first time user) in my machine.. now.. i cant find the wireless card.. the Compaq website doesnt have a driver for linux and i start to read some thing about the NDISwrapper but i dont know how to make that work.. 

can someone help me please.. 

Thanks.

---

### Post by kellopes on 2010-01-22
Up

---

