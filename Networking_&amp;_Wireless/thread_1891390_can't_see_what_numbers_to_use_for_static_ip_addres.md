---
title: "can't see what numbers to use for static ip address"
date: 2011-12-05
forum: Networking &amp; Wireless
---

### Post by 118118 on 2011-12-05
hi,

i'm trying to share an internet connection to a second pc via ethernet [the first has internet wirelessly].
google says i need to set it up as a static ip address.
but i don't know what gateway address or netmask to use.

after trying google i had a go at finding out with

```
luke@luke-AOD260:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
luke@luke-AOD260:~$
```route -n on the pc with the wireless connection but none of these settings will save in network manager.


thanks for any help :popcorn:

---

### Post by jonobr on 2011-12-05
Hello

[This howto]("https://help.ubuntu.com/community/Internet/ConnectionSharing") shows how to setup ICS.

Given that your wlan0 interface is on 192.168.0.x, then your eth0 which is on your internal lan could probably be something like
192.168.1.x  provided there is no other 192.168.1.x network.
Anyway, have a read through this and setup accordingly

---

### Post by 118118 on 2011-12-05
hi

i followed that guide word for word [using the same numbers suggested by the guide] until i got to the dhcp3 file that i needed to edit. it does not exist in the pc 2.
so i cannot finish the guide.

also, i do not have internet access on the wireless machine anymore.

---

### Post by 118118 on 2011-12-05
i'm sorry, that was foolish of me - i assume i actually had to replace any instance of "eth0" with wlan0 and eth1 with eth0 and any 192.168.0 with 192.168.1 and it should have worked?


well how do i undo what i have done so i have internet wirelessly again?

---

### Post by 118118 on 2011-12-05
i typed in the commands as i suggested they should be above ^^ and still don't have a wireless connection.

---

### Post by 118118 on 2011-12-05
i'm relatively new to ubuntu... so i don't much mind doing a fresh install. but can i at least be told if what i posted above is the right way to type the commands, the how to guide just says
> In summary:

eth0 = the network adapter with internet (external or WAN).
eth1 = the network adapter to which a second computer is attached (internal or LAN).
192.168.0.x = IP subnet for eth1
Your setup may be different. If so, make sure to change them accordingly in the following commands.??

and what i should do given the absence of that file on pc2.

thanks.

---

### Post by jonobr on 2011-12-05
Hello


I get the feeling you modified the wrong information.

Can you post your ifconfig and /etc/network/interfaces

Also , just FYI, there are two methods described, the GUI client method is the most applicable for your installation,
you shouldn't have worried about the Dhclient modofocatopm

---

### Post by 118118 on 2011-12-05
well the gui client is the method i had already tried but google suggested that the error i got means i should use a static ip.
connection established / disconnected / connection established etc. kept flashing up.


i have internet again after restart. anything else i should do?
there seems to be no such interface file that i can call up in gedit.

---

### Post by 118118 on 2011-12-05
```
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:1e:7a:20  
          inet6 addr: fe80::8aae:1dff:fe1e:7a20/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9882 (9.8 KB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14640 (14.6 KB)  TX bytes:14640 (14.6 KB)

wlan0     Link encap:Ethernet  HWaddr c4:46:19:1d:9c:a1  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c646:19ff:fe1d:9ca1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:865698 (865.6 KB)  TX bytes:168515 (168.5 KB)

```

---

### Post by 118118 on 2011-12-05
[http://serverfault.com/questions/264308/ubuntu-wired-network-disconnected](http://serverfault.com/questions/264308/ubuntu-wired-network-disconnected)


was the basis of my idea that i needed to setup static ip's.

---

### Post by jonobr on 2011-12-05
So ok, if your stuck on setting up a static IP ,
you could in you nm settings, set eth0 to be a static IP

You could use the following in there (so its different to wlan0

IP eth0 192.168.1.2
subnet mask 255.255.255.0

On your client connecting to eth0 you could set that up with a static IP address also,
eg 192.168.1.3
subnet mask 255.255.255.0
dns 8.8.8.8 (this is just a test for the time being.

You can then go to edit settings and share.

Once thats done, get ifconfig, hopefully it will shouw a static IP on the interface

---

### Post by 118118 on 2011-12-05
> You can then go to edit settings and share.i'm not sure i understand what you mean here??

i went to network manager and entered those numbers as manual ipv4 settings but now have lost the connection to pc2.


thanks.

---

### Post by jonobr on 2011-12-05
Ok,

lets back up a bit and restore everything to the way it was,
Maybe I misunderstood your setup.

You have a wireless connection going from your ubuntu machine to the wireless network, from which your getting an ip address.
(wlan0 192.168.0.x) This is the device you want to share, correct?

Then you have a wired connection , ETH0 which is connected to either another machine or another wired device , correct?

How are you connected on this part of the lan?
Are you connecting eth0 to a hub a switch or directly to another device?

---

### Post by 118118 on 2011-12-05
yes.
directly to another device.


sorry if i am being thick and it has nothing to do with static ip's.

---

### Post by 118118 on 2011-12-05
i found this [http://askubuntu.com/questions/64494/wired-connection-shared-with-other-computers-connects-then-disconnects-in-11-10](http://askubuntu.com/questions/64494/wired-connection-shared-with-other-computers-connects-then-disconnects-in-11-10)


but i don't get internet on pc2. also, i used to get internet when i got this error message, but don't anymore...

---

### Post by 118118 on 2011-12-05
hi,

i tried the workaround mentioned above with live-usb and it worked. so it looks like something i have done in this thread means that i can't share internet. is there any way to reset network settings to default, or anything like that?

---

### Post by jonobr on 2011-12-05
A dopey question from me,

Are you using a crossed over Ethernet cable to connect the two pcs together?

If you connect through a hub or a switch you can use standard ethernet cables, but if you connect the two directly, that would required a cross cable which is a specific cable type

---

### Post by 118118 on 2011-12-06
hi there,

i freshly installed it - it was no bother. working now! thanks!

---

### Post by jonobr on 2011-12-06
I dont think I did anything,
my guess is that something got changed that sharing didnt like, 
reinstalling probably just overwrote the config.

Recommend you mark this as solved in the title so anyone searching can go through the troubleshooting done to get to the bottom of this....

Have a good one.

---

