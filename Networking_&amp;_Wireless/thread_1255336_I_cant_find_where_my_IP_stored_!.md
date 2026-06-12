---
title: "I cant find where my IP stored !"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by Mosaab on 2009-09-01
I know ip address is supposed to be stored in /etc/network/interfaces

but I set my static IP address for wlan0 using GUI to 192.168.1.16 but the content of "interfaces" is as follows :

```

mosab@mosab-laptop / $ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

even nothing is mentioned about wlan or eth0 !! Why ?

---

### Post by i.r.id10t on 2009-09-01
It is stored in your gnome network manager area...

---

### Post by DamITman on 2009-09-01
using console, try typing "ifconfig" it should give you readings on every network device, in my case i want to check ath0, but it is likely different for you. 

should look something like this

"ath0               Link encap:Ethernet  HWaddr 00:11:22;33:44:66   
          ip ---> inet addr:10.0.0.2           Bcast:10.0.0.255  Mask:255.255.255.0
                      inet6 addr: Scope:Link      
                      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1      
                      RX packets:18808 errors:0 dropped:0 overruns:0 frame:0  
                      TX packets:8777 errors:0 dropped:0 overruns:0 carrier:0 
                      collisions:0 txqueuelen:0                               
                      RX bytes:22874996 (22.8 MB)  TX bytes:1283807 (1.2 MB) "

---

### Post by shredder12 on 2009-09-01
Well, I don't really know the reason why does the interfaces file doesn't show anything about the eth0 or wireless wlan0.

but if you want to check ur ip address try running 
```
ifconfig
```

---

### Post by Niko Johnson on 2009-09-01
```
ifconfig
```

this will show you your ipadress and other information as well like your mac adress and your wireless card. another command to use if you have a wireless connection is
```
iwconfig
```
i hope this helped you even just a little

---

### Post by Mosaab on 2009-09-01
Yes I know the command ... I know how to get the ipaddress... but just for learning I am wondering where does the ifconfig get the ip address if they are not in the interfaces file .!!!

any one knows ?

---

### Post by dbalascak on 2009-09-01
It might be in */etc/NetworkManager/system-connections* directory if you have enable Netork Manager.  Do you have the icon with 2 blue screens and/or the green dots with with the blue swirl WITHOUT a red X on it?

If you are using wicd the settings are in */etc/wicd*.

Depends on which manager you have enabled.

---

### Post by Mosaab on 2009-09-01
yes THANK YOU ... :)

they are in networkmanager as you said :) .. but why ? arent they supposed to be in interfaces ?

---

### Post by dbalascak on 2009-09-01
There are several ways to configure interfaces each having it's own place to store configs.  The first is */etc/network/interfaces*. Pretty stright forward. Not very visable or glitzy.  A second is Network Manager. If the entry in the file */etc/NetworkManager/nm-system-settings.conf* reads 
```

[ifupdown]
managed=true  

```

then the Network Manager is enabled and you get the icon on the desktop (without a red X) and the popup icon when the link goes down etc. You also have some control over a wired and wireless interface. A littl more flashy.  A third method is "wicd". When you install it, the previous Network manager packages are removed and yet a different directory * /etc/wicd/* is used for config info.  If you are using the Network Manager the */etc/network/interfaces* must have very little in it ( as you have right now). This file will conflict with the config in */etc/NetworkManager/nm-system-settings.conf*. You can run any one of them but you need to be sure that only that specific directory structure holds the interface config.

---

### Post by Mosaab on 2009-09-02
Thats really  what I was looking for... Thank you for the info man.
but one more question .. if I dont have the ntwork manager installed ! how would a program like ifconfig knows that the ips are in the network manager directory.. that means that there should be a file which doent belong to either network manager or even wicd. and that file cannot be a file of one of the 2 programs. am I right ?

---

### Post by t0mppa on 2009-09-02
Ifconfig doesn't read the IP from a file stored on the local file system, rather it just displays the IP you're connected with to the network. The files mentioned earlier are simply ways you can tell the program that is making the connection (whichever one you're using) to use a specific (static) IP address.

If you use dynamic addresses, your system has no idea which IP it will get the next time, it will just make a connection with the DHCP server which will then tell it which address to use.

---

### Post by Mosaab on 2009-09-02
ok .. isnt there a file ... "General Linux File" to tell linux which file holds the static Ip address.. 
when you talk about the network manager file ... its a file that belongs to a software which is installed in linux ... doesnt linux have to have a file that has a flag or something lto tell linux where are the static ip address stored?


or does the network manager initiates the whole thing?

do you know what I mean ?

---

