---
title: "Ubuntu 10.4 Not letting me connect to internet"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by DarkEnergy.0 on 2010-07-31
Ok i was perfectly running the internet, i restarted the computer because i installed some software.
Then when i start it up again it does not connect to the internet. 
So i check the network connection and even when i type my wep key my ssid and mac adress i cant connect. 
I go to my modem home menu on another computer and it says that my pc laptop where i have ubuntu installed was connected but it is uknown and in the description there appears no computers to be connected to ethernet port 2 wich is where i have my computer connected to the ethernet
I go to google chrome and it doesnt open google.com  so i check the error and it says, error 105 (net:: ERR_NAME_NOT_RESOLVED): the server could not be found.
I also tried to run some commandos in terminal like:
sudo ifconfig eth0 up This one asks for my password then all of the sudden it gets and error that says:
eth0: ERROR while getting interface flags: No such device found
sudo ifconfig wlan0 up  same for this one.

So i run the ubuntu disk and i run the try it ubuntu so i wont delete my stuff and it the ineternet works perfectly on it.

Tried running fro  the computers start up menu with f12 to boot from lan doesnt load anything.
Tried enabling the lan on the esc start up menu.

My computer is an Hp pavilion ze5200 with pentium 4

Note: I restarted my computer various times and it wont connect, I restarted my modem, and it still wont connect. This laptops wich is a mac book pro connect to the modem easily so does my wd share space drive.

Can anybody help

I already tried everyhting. 
And the best possible solution is to erase and reinstall but man having to download a lot of themes intall again all the theme engines and some software having to install the awn dock again, having to download emerald, gimp, chrome, some  204 updates.

C'mon is there anyway to slove this PLEASE HELP!!!!!!!.

Everything i tried tried it with the ethernet connection and the wireless connection.

---

### Post by dineshs on 2010-07-31
what does```
sudo lshw -C network
```say?

---

### Post by DarkEnergy.0 on 2010-07-31
Asks me for my password and says:
sudo 1shw command not found.

??? is ishw with I or with 1 like ishw or 1shw

---

### Post by DarkEnergy.0 on 2010-07-31
Ok i also tried running these in terminal.

```
$ sudo service network-manager status network-manager start/running, process 708
```

This says that:
The script you are attemting to invoke has been converted to an Upstart job, but start/running is not supported for Upstart jobs.

```
$ sudo service networking status networking stop/waiting
```

This one says:

status: Env must be KEY=VALUED pairs

Also tried running one similar as the first:


sudo service network-manager status
network-manager start/running, process 1080

This one says the same as sudo service networking status networking stop/waiting it says Env must be Key= valued pairs.

---

### Post by amsterdamharu on 2010-07-31
It's a lower case L.

---

### Post by DarkEnergy.0 on 2010-07-31
Ok so i runned:

```
sudo lshw -c network
``` and this appeared


 *-network DISABLED      
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:16:b8:3e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:10 ioport:2400(size=256) memory:d000a000-d000afff memory:34000000-3400ffff(prefetchable)

---

### Post by DarkEnergy.0 on 2010-07-31
Oh and another thing is that for some reason i dont have the network applet for the gnome panel nor the awn dock

---

### Post by dineshs on 2010-07-31
Can you right click the Network manager ?Is enable networking ticked?

---

### Post by DarkEnergy.0 on 2010-07-31
On my preferences and administration there is nothing called network manager i only have network proxy, Network connections and Network Tools.

---

### Post by dineshs on 2010-07-31
On the top of the panel near the loudspeaker symbol-a double arrowed icon...?

---

### Post by DarkEnergy.0 on 2010-07-31
No such thing!!!

---

### Post by ajgreeny on 2010-07-31
Make sure you have the "Notification area" in your panel.  This is where the NM Applet now sits.

---

### Post by DarkEnergy.0 on 2010-07-31
Ok this worked.

I clicked on  the double arrows and nothing happened then i rentred the commando from one of the previous comments wich

 ```
was sudo service network-manager status
network-manager start/running, process 1080
```

And everything worked again.

So weird THANKS TO ALL !!!!!!!!!!!!!!!!!!

---

### Post by Huss on 2010-08-27
Wow. That's all it took. Add notification area to panel an bam! 

Thanks for the help!

---

### Post by maravingian on 2010-08-28
Hi guys,

I`m getting the same problem with my main computer.  Only thing is that my computer can see my wired connection but refuses to connect to it.  Top right is the sonar with the red exclamation mark.  I`m typing this from my netbook so me internet connection/router is not at fault. Main computer was able to access the internet successfully last night but not today.

I did download the latest recommended updates for Ubuntu 10.4 yesterday, Could one of those have possibly caused this?

Network is Enabled, when I edit connection then click apply I type in the password but it does not try to search for the network, like it used to.

Any ideas?

---

### Post by Lizardwithhat on 2012-07-04
I am having a similar problem, when I connect to **any** WiFi or Ethernet the internet connection does not work, what is interesting that on the network I can go to directories and other files on the network server, Chromium and Firefox give an error 105 but also plugging don't download and the weather can't update but Ubuntu says it is connected, I have tried the commands in this forum but that that not solved anything yet, it is a 10.04 lts usb and it worked yesterday and today when i turned it on it won't, different computers and restarts etc. (usual stuff) does not work. :(

---

### Post by wildmanne39 on 2012-07-04
Hi, this is an old thread so it has been closed, please start a new thread.
Thanks

---

