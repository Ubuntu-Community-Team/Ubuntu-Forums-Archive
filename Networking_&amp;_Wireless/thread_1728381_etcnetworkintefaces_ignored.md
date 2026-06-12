---
title: "/etc/network/intefaces ignored"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by navique on 2011-04-13
My version of ubuntu is 10.04 LTS X64
I want to have static ip on my ubuntu pc. So i changed /etc/network/interfaces to
 
auto eth1
iface eth1 inet static
address 192.168.1.21
netmask 255.255.255.0
gateway 192.168.1.1
 
eth0 and eth2 are not in use so i didnt include them in the file. 
When i restarted network it was fine but when i restarted the pc it completely ignored my configuration and got IP from DHCP. 
 
windows pc produced some interesting results when i tried to ping my linux pc.
 
d:\home\Navique>ping navique-desktop
 
Pinging navique-desktop [192.168.1.21] with 32 bytes of data:
 
Reply from 192.168.1.31: Destination host unreachable.
Reply from 192.168.1.31: Destination host unreachable.
Reply from 192.168.1.31: Destination host unreachable.
Reply from 192.168.1.31: Destination host unreachable.
 
1-29 are static ips DHCP range starts after 30.
Any idea why this is happening ? Am i missing something ? All the research i did indicates that changing the interfaces file should be enough to get static ip on ubuntu pc so i am a bit lost here.

---

### Post by dineshs on 2011-04-13
Did you try setting static IP via network manger.For this first make /etc/network/interfaces contain only 
auto lo
iface lo inet loopback
restart and 
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)
The reason is
[http://ubuntuforums.org/showthread.php?t=1636154](http://ubuntuforums.org/showthread.php?t=1636154)

---

### Post by navique on 2011-04-20
Tried that. No luck. 
Ubuntu seems to ignore NM settings as well. Just goes for DHCP.

If i remove NM it seems like it tried to apply .21 address but somehow it ends up using DHCP anyway. ;)

The feeling i get while dealing with the issue is that somebody tried to reinvent the bicycle and caused lots of pain and suffering in the process.
I meen common ! its not like i need something fancy here ... static ip address over simple eth1 :) what could be more basic ? and yet Ubuntu struggles because it uses all those auto addon scrips which are at war with each other most of the time :).
I feel that there should be some kinda of fail safe mechanism .. if all this script goodness gets out of control. Which would give you just plain and simple functionality. Thats what i was trying to find here. Ubuntu was great idea when it started but now i am not sure what it is anymore. I think its worse that windows now in some ways ;)

Anyway if I am wrong and there is somebody out there who could prove me wrong don't hesitate ;)

---

### Post by georgemc on 2011-04-20
Post the output of 

netstat -r

You could be missing the default route or its pointing to another interface.

good luck

George

---

