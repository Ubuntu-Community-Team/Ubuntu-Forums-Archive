---
title: "cannot connect to internet in ubuntu 8.04/8.10"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by bogart_2003 on 2009-03-11
hi to everyone. i'm new to ubuntu, and i installed 8.04 a few days ago, dual boot with windows xp using wubi.

my internet connection works fine in windows, yet i can't get it to work in ubuntu. i tried reading some forums, and tried the "sudo pppoeconfig" command, and the message that appeared was

"Sorry, I scanned 2 interfaces, but the Access concentrator of your provide did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem"

I've seen this message occur to other users as well in different forums, but i can't find the right solutions for me. i know the ubuntu community is very friendly, and any response will be highly appreciated.

---

### Post by marsdend on 2009-03-11
Are you using a USB Modem or Wired/Wireless ADSL Router?

---

### Post by bogart_2003 on 2009-03-11
hey there. i'm using a wired ADSL router.

---

### Post by x33a on 2009-03-11
post the output of
```
cat /etc/network/interfaces
```

---

### Post by bogart_2003 on 2009-03-11
cat: /etc/networking/interfaces: No such file or directory

---

### Post by punx45 on 2009-03-11
its /etc/network/interfaces 

:-D

---

### Post by bogart_2003 on 2009-03-11
haha my bad punx 45. now here's what it had to say:


auto lo 
iface lo inet loopback 
 
 
iface eth0 inet dhcp 
 
 
 
iface ppp0 inet ppp 
provider ppp0 
 
auto ppp0

---

### Post by x33a on 2009-03-12
can you ping 192.168.1.1

and try deleting the interfaces file and then run pppoeconf, again.

---

### Post by bogart_2003 on 2009-03-12
ok i'll do the ping test in awhile, but how do i delete the interfaces file? i mean, yeah, delete it, hehe but where? i'm still sort of knew to linux. thanks dude!

---

### Post by bogart_2003 on 2009-03-12
ok x33a, i tried pinging 192.168.1.1 and here's what i got:

connect: Network is unreachable


and so i did some searching and found the interfaces file (is this the one inside the "/etc/network"?) and tried to delete it. however, i got another message:

"Cannot move file to trash, do you want to delete immediately? The file 'interfaces' cannot be moved to the trash." 

then

"Unable to trash file: Permissioned denied"


then proceeded to hit the delete button, and it said the same thing = permission denied.

---

### Post by x33a on 2009-03-12
do this

to backup file
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

to delete file
```
sudo rm /etc/network/interfaces
```

then
```
sudo pppoeconf
```

you got a permission denied, because you didn't run as root, and sudo here grants us root privileges.

---

### Post by bogart_2003 on 2009-03-13
first of all thanks for helping man, really appreciate it.

ok so i did what you said, and after "sudo pppoeconf", here's what i got:


Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please    check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.

---

### Post by x33a on 2009-03-13
how do you connect to the net in windows? do you use a dialer (bridged mode) or does you use the router inbuilt dialer (pppoe mode)?

---

### Post by bogart_2003 on 2009-03-13
i think it's the pppoe mode because i don't use a dialer; it's already connected when i log on to windows

---

### Post by x33a on 2009-03-13
and do you use dhcp or have you configured lan in windows?

---

### Post by bogart_2003 on 2009-03-13
hmmm. ok so i'm a little lost here. i have basic knowledge, although the dchp stuff is beyond my grasp, so i how do i know which is which? please forgive my ignorance.

---

### Post by bogart_2003 on 2009-03-13
ok wait, sorry for being a noob here, but when i looked at the Network Connections, only the LAN is activated. does that help? when i clcik on the status of the LAN, address type is "assigned by DHCP".  I'm not really sure what these all mean, but i hope these are helpful to you.

---

### Post by x33a on 2009-03-13
sorry for the delay, i was facing some network problems.

on topic, yes that helps, it means that you are using dhcp.

could you again post the output of

```
cat /etc/network/interfaces
```

---

### Post by bogart_2003 on 2009-03-13
ok so here's what i got:

cat: /etc/network/interfaces: No such file or directory 

Was this because i deleted the interfaces file? Or is it what you were expecting?

---

### Post by x33a on 2009-03-13
i thought you ran pppoeconf again, but ok there's no need to run it now.

assuming you did the backup as i had suggested, do

```
sudo mv /etc/network/interfaces.bak /etc/network/interfaces
```

then 

```
gksudo gedit /etc/network/interfaces
```

delete the contents of the file and copy/paste this to the file
> auto lo 
iface lo inet loopback 

auto eth0
iface eth0 inet dhcp 


save the file.

then
```
sudo /etc/init.d/networking restart
```

see, if you able to connect to the net after this.

---

### Post by bogart_2003 on 2009-03-13
ok i was able to do all of the above except for the last part. after the "sudo /etc/init.d/networking restart", i got this: 

sudo: /etc/init.d/networking/: command not found

And i was not able to connect to the internet.

---

### Post by x33a on 2009-03-13
yes, i put the wrong command, stray / 

copy and paste it from my previous post, i have edited it now.

---

### Post by bogart_2003 on 2009-03-13
nothing changed with your previous post?

---

### Post by x33a on 2009-03-13
well, i did edit the post. anyway, copy/paste this:

```
sudo /etc/init.d/networking restart
```

---

### Post by bogart_2003 on 2009-03-13
ok sorry so here's what i got:

 * Reconfiguring network interfaces...                                         
There is already a pid file /var/run/dhclient.eth0.pid with pid 5647 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
Listening on LPF/eth0/00:22:15:c5:3b:27 
Sending on   LPF/eth0/00:22:15:c5:3b:27 
Sending on   Socket/fallback 
grep: /etc/resolv.conf: No such file or directory 
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
Listening on LPF/eth0/00:22:15:c5:3b:27 
Sending on   LPF/eth0/00:22:15:c5:3b:27 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
grep: /etc/resolv.conf: No such file or directory 
                                                                         [ OK ]

---

### Post by x33a on 2009-03-13
so no net yet? are you able to ping 192.168.1.1?

the problem lies with resolv.conf. unfortunately, i have no idea how to fix it, i am using bridged mode.

take a look here:

[http://ubuntuforums.org/showthread.php?t=812783](http://ubuntuforums.org/showthread.php?t=812783)

---

### Post by bogart_2003 on 2009-03-13
ok so i tried to ping it, and here's the end result:

--- 192.168.1.1 ping statistics --- 
197 packets transmitted, 0 received, +180 errors, 100% packet loss, time 196352ms 
, pipe 3 


it seems it has changed, seeing as how the response i got is different from when i tried to ping yesterday (connect: Network is unreachable).

i'm still not able to connect though. i'll be reading those things. thanks.

---

### Post by bogart_2003 on 2009-03-14
ok so now it seems that the problem revolves around resolv.conf. is there anyone else who can help me? hehe i don't want to give up on this yet, so i'm reading stuff, but this is all too much for me at the moment. any help would be highly appreciated.

---

