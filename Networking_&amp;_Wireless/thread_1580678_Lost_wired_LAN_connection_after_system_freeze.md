---
title: "Lost wired LAN connection after system freeze"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by distractor on 2010-09-23
Hi there,
I installed Lucid a week ago and have been having a blast with it after a two year break from Ubuntu (been using Mandriva). 
So the other day I went to hibernate the system and it froze. I naturally did a hard reset and when I log back in, no network connection. 
That is to say, the system tray says it's connected but there is no LAN light on the router or network card. 
ifconfig shows it's connected too. When I boot into XP (cringes) it works just fine.
Can anyone help me solve this issue please?

No specifics ATM but the card is a D-Link PCI with a Realtek R8***** chipset

Regards,
Chris

---

### Post by leclerc65 on 2010-09-23
Open a terminal and try:

sudo dhclient

---

### Post by GalgoLance on 2010-09-23
Not sure if this is helpful, but I have Lucid 10.04 and after a recent "update" lost my wired LAN connection.  

Solution:
Go to Applications and open the Terminal window:

 

 Type:  sudo Gedit /etc/network/interface
 

make sure to put the "space" before and after "Gedit".  no spaces elsewhere.


You must know the Root password.  If not, you will be unable to edit the file.


 make sure the file is like this one.  If the file is not like this one, then somehow your interface definition file has been corrupted.  No idea how such things happen.


If the file doesn't look like this one,  replace what is there with this:
 
# This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5).  
# The loopback network interface 

auto lo 
iface lo inet loopback 

# The primary network interface 

auto eth0 
iface eth0 inet dhcp


Then save the file under Gedit.  


Next you must restart network connections.  

Either reboot  your computer or use the Terminal to issue a network restart command:

 sudo /etc/init.d/networking restart
 

 it should work.  
Make sure to have a "space" after "sudo"  and "networking".  
Otherwise, no spaces in the command. 
 

 Then exit the terminal.


Worked for me.   Good luck with your situation.

---

### Post by Iowan on 2010-09-23
See if one of these helps:
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")
[http://ubuntuforums.org/showthread.php?t=1537792]("http://ubuntuforums.org/showthread.php?t=1537792")

---

### Post by distractor on 2010-09-23
Hi again. I do thank everyone for their suggestions but none of them work.
I still have no LAN light on the router or network card but still works fine in windows.
Here is my terminal session followed by a ifconfig query:

```
chris@chris-desktop:~$ sudo service network-manager stop
network-manager stop/waiting
chris@chris-desktop:~$ sudo rm /var/lib/NetworkManager/NetworkManager.state
chris@chris-desktop:~$ sudo service network-manager start
network-manager start/running, process 1777
chris@chris-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:58:eb:fb:a0  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:58ff:feeb:fba0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2690 (2.6 KB)  TX bytes:2690 (2.6 KB)
```

Would it be best to un-install the network card in Ubuntu and then re-install it somehow?
If so, how would I go about doing that?

Regards,
Chris

---

### Post by distractor on 2010-09-24
So can anyone help me please or do I have to perform a reinstall?

---

### Post by distractor on 2010-09-27
Nevermind. Solved the problem. Went back to a working distro (Mandriva).

---

