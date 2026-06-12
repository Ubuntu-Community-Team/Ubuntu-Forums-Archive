---
title: "Internet connection not working and Network Manager not helping"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by DJ . on 2009-11-08
I can't connect to the internet. I have looked it up everywhere and found out that more than 50% of this forum is having internet problems. Each thread I select has this problem or close to it but no solution.
 
My problem is that when I use Network Manager and set all my wireless settings it doesn't come up in the wireless drop-down. (Left click on the Network manager and select wireless networks) When I try to use the info in connect to a hidden network it just says disconnected. It doesn't even say attempting to connect or connecting. Just disconnected.
 
When I use terminal and type:
```
iwconfig
```
it shows up as:
```

dj@ubuntu:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:"nr8p2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:eek:ff   Fragment thr=2352 B   
          Power Management:eek:n
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
pan0      no wireless extensions.
```
 
nr8p2 is the name of my router and is password protected. Someone please help so that I can have internet.
EDIT: Why does it say eek:n on next to power managment. Shouldn't it say on?

---

### Post by DarkKitsune on 2009-11-08
What kind of wireless card are you using?

---

### Post by DJ . on 2009-11-08
> **DarkKitsune said:**
> What kind of wireless card are you using?
Broadcom 802.11b/g WLAN

---

### Post by SawyerLX on 2009-11-08
I am too having same problem, ifupdown apears under wired tab and will not connect via DSL tab.

aDead Network Manager Applet!


using "sudo pppoeconf"

sudo "pon dsl-provider"

to make connection.

On new reboot: I have to...

sudo poff -a

then, "sudo pon dsl-provider", again.


Mornday morning is gonna require good coffee.

---

### Post by DJ . on 2009-11-08
> **SawyerLX said:**
> I am too having same problem, ifupdown apears under wired tab and will not connect via DSL tab.

aDead Network Manager Applet!


using "sudo pppoeconf"

sudo "pon dsl-provider"

to make connection.

On new reboot: I have to...

sudo poff -a

then, "sudo pon dsl-provider", again.


Mornday morning is gonna require good coffee.
Yea, it will. But I seem to notice everybody has internet problems with ubuntu. Anyway, do you know how to put a wep pass in this code that I am using?
```
sudo iwconfig <wlan0,eth0, or whatever connection you have> essid <ssid of your internet connection> 
sudo dhclient
```But mine has a wep key, so it wont work. All I need is to know how to put a wep key in there but I can't find out how.

---

### Post by SawyerLX on 2009-11-08
No i do not, sorry:)

---

### Post by lswb on 2009-11-08
> **DJ . said:**
> ...
Anyway, do you know how to put a wep pass in this code that I am using?
```
sudo iwconfig <wlan0,eth0, or whatever connection you have> essid <ssid of your internet connection> 
sudo dhclient
```

Add the key to the iwconfig line like this
```

sudo iwconfig wlan0 essid "name" key abcdefg123

```
If you are using an ascii key instead of a hex key, use "key s:asciikeyhere", i.e prefix the key with 's:'

---

### Post by DJ . on 2009-11-08
> **lswb said:**
> Add the key to the iwconfig line like this
```

sudo iwconfig wlan0 essid "name" key abcdefg123

```
If you are using an ascii key instead of a hex key, use "key s:asciikeyhere", i.e prefix the key with 's:'
 Doesn't seem to work. Just shows a lot of numbers and saying "Network is down." I will post the results later on because right now I can't so I will edit this post and put the results in.

---

### Post by peepingtom on 2009-11-08
Post the output of ```
cat /etc/network/interfaces
```

---

### Post by DJ . on 2009-11-08
after iwconfig wlan0 essid key:
```

dj@ubuntu:~$ sudo iwconfig wlan0 essid "nr8p2" key 1F90453AA3
dj@ubuntu:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 9336
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:ba:5f:32
Sending on LPF/wlan0/00:14:a5:ba:5f:32
Listening on LPF/wmaster0/
Sending on LPF/wmaster0/
Listening on LPF/eth0/00:16:d4:3b:50:3d
Sending on LPF/eth0/00:16:d4:3b:50:3d
Listening on LPF/pan0/5a:aa:13:da:a4:49
Sending on LPF/pan0/5a:aa:13:da:a4:49
Sending on Socket/fallback
receive_packet failed on wlan0: Network is down
receive_packet failed on wmaster0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
send_packet: Network is down
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
dj@ubuntu:~$ 
```
after /etc/network/interfaces
```

dj@ubuntu:~$ /etc/network/interfaces
bash: /etc/network/interfaces: Permission denied
dj@ubuntu:~$ sudo /etc/network/interfaces
[sudo] password for dj: 
sudo: /etc/network/interfaces: command not found
dj@ubuntu:~$ 
```

---

### Post by lswb on 2009-11-08
Try this, substitute your interface, essid, etc.

```

sudo service NetworkManager stop
sudo iwconfig wlan0 mode managed essid "networkname" key abcdef1234
sudo dhclient wlan0

```

---

### Post by Eagl3 on 2009-11-08
Mine has a weird problem related to this. I installed ubuntu 9.10 clean install. After installation no proprietary drivers for wireless were not found. So i connected my laptop via ethernet. I ran update manager and downloaded & installed all updates. Now I checked for Drivers, and sure enough broadcom sta wireless driver was in there. I activated it, and tested the wireless and everything worked fine. It connected to the network. Then after a few minutes I tried to click on the menu bar, and my computer froze, with a black screen and the white cursor. The laptop locked up so i just hard rebooted it. When i logged back in the wireless option is there but it's disabled. The drivers themselves are activated, so i guess it's because of the crash and they're corrupted. How can i uninstall the whole update for that driver and reinstall it?

---

### Post by peepingtom on 2009-11-10
Sorry I posted a misleading command earlier, at least it didn't do any damage :D
Anyone with NetworkManager issues (SawyerLX), please post the output of ```
cat /etc/network/interfaces
```

Many people's NetworkManager issues can be easily explained if it contains anything except ```
auto lo
iface lo inet loopback
```


[http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

---

### Post by DJ . on 2009-11-11
Now using wired connection. Wireless still not working
```
dj@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by simon33 on 2011-06-05
> **peepingtom said:**
> Sorry I posted a misleading command earlier, at least it didn't do any damage :D
Anyone with NetworkManager issues (SawyerLX), please post the output of ```
cat /etc/network/interfaces
```Many people's NetworkManager issues can be easily explained if it contains anything except ```
auto lo
iface lo inet loopback
```[http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

Hi, I am a new poster to the forum, although not reader as I have found many very useful hints and tips on here since converting to Ubuntu 18 months ago. 
To put you in the picture I have been running LTS up until the other day, with little or no problems on my Laptop/Notebook. I decided however to upgrate to the most up-to-date copy of Ubuntu and did so through the correct channels (update manager etc.) Upon upgrading to 10.10 it then asked me if I wanted to upgrade to 11.04. Everything seemed fine until it booted into 11.04! My network manager is not working at all, I have tried both wired and wireless and nothing. Forced to use Windows again (ARGHHH) I searched this forum for some possible answers to my problem.
I guess what I am trying to say in a long winded way is I typed the following code into the terminal  
Code:
cat /etc/network/interfaces

and got exactly what tom has said cannot be easily explained!!!

Is there anything I can do as it is driving me nuts!!

Thanks in advance for your help

Simon

---

### Post by dineshs on 2011-06-06
Can you post the results of ```
sudo lshw -C network
route -n
ping -c3 4.2.2.1
``` when ethernet cable is plugged?

---

### Post by simon33 on 2011-06-06
Hi,

Thank you very much for your help on this!

I am alternating between Vista and Ubuntu, there I can't paste the contents of the terminal window so I have taken a screenshot and attached it to this post! I hope it works!

Thanks Simon

---

### Post by dineshs on 2011-06-07
lshw -C network says link=no for wired connection.Was the cable plugged in while running this command?
[Here]("http://ubuntuforums.org/showthread.php?t=538448") is a similar thread but for Realtek 8168/8169 card .Pl try
> If your ethernet cable is connected at boot time and you are experiencing the no link problem, try this: Shutdown, power down. Unplug your host (this cuts power to the card if wake-on-lan power is maintained). Wait 15 seconds. Plug in. Boot ubuntu.


> To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this option through Windows' device manager.

---

### Post by simon33 on 2011-06-11
Hi,

Thanks for your advice but unfortunately that has had no effect.

The network cable was plugged in at the time I ran the command.

Is there anything else I can do?

Many thanks

Simon

---

### Post by nisbeam on 2011-06-11
I have 2 laptops & cannot upgrade to 11.04 because wireless does not work.  I have reverted to the earlier version on one and it is working again.  But on that one (that works) I get:
auto lo
iface lo inet loopback

but my wireless if working fine.  So what does this mean ? I would just like wireless to work on upgrade.  Is there a fix anyone ?

---

