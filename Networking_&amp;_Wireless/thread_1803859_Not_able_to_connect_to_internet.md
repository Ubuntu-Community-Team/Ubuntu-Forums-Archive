---
title: "Not able to connect to internet"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by Candlehawk on 2011-07-13
Hi, I am using Ubuntu Server version 10.4, and am trying to connect to the internet via an ethernet cable. This may and probably is incredibly simple, however, I could not find anything that pertains to it.

---

### Post by papibe on 2011-07-14
Do you have a router?
Is the server available to other machines on the network?

Could you post the content of this file: /etc/network/interfaces, and the result of this command:
```
$ ifconfig
```
Regards.

---

### Post by Candlehawk on 2011-07-14
Of course I have a router -_- that actually was a tad insulting.
And how would I check to see if the server is available to other machines on the network? If you mean can I ssh to it, no I can not.
Contents of /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
```
```

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:944 errors:0 dropped:0 overruns:0 frame:0
TX packets:944 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:77712 (77.7 KB) TX bytes:77712 (77.7 KB)

```
If anything is slightly off in syntax, it's because I had to manually type that in from my server box.

---

### Post by papibe on 2011-07-14
> **Candlehawk said:**
> Of course I have a router -_- that actually was a tad insulting.
It is a technical question, not an evaluation of your skills. There are people that connects to the Internet with no router, for example if they have a cable ISP and use only a modem.

Now about your concern. It looks you installed and configured your server while not connected to the router. When it is connected during the installation, all the network settings are set at that time.

First thing you need to do is to enable DHCP. Add this lines to your /etc/network/interfaces
```
auto eth0
iface eth0 inet dhcp

```
Then, restart the network services:
```
$ sudo service networking restart
```
Now if all is working correctly you should have an LAN IP associated to your machine, and the other machines on your network should 'see' your server. To test this, post again the result of the command:
```
$ ifconfig
```

Regards.

---

### Post by Candlehawk on 2011-07-14
> **papibe said:**
> It is a technical question, not an evaluation of your skills. There are people that connects to the Internet with no router, for example if they have a cable ISP and use only a modem.
Whoops, sorry thought I said that in the first reply. I was mistaken.

Secondly, when I type in ```
auto eth0
``` it gives me: ```
No command auto found, did you mean:
Command "uuto" from package "uucp" (universe)
```
and when I type in ```
iface eth0 inet dhcp
``` it gives me
```
iface: command not found
```

---

### Post by Bucky Ball on 2011-07-14
I think you almost got there. You need to open /etc/network/interfaces and put it in there rather than the terminal:

```
sudo nano /etc/network/interfaces
```Then add 'dhcp' to the line as suggested by papibe with one change (you shouldn't need 'eth0' in the first line), so it all looks like this:

```
auto lo
iface eth0 inet **dhcp**
```Hit Ctl+x then Enter to close the file, then:

```
sudo service networking restart
```

---

### Post by Candlehawk on 2011-07-14
Firstly, I just woke up and my more awake self is facepalming over not realizing that I had to edit /etc/network/interfaces , not putting it as commands in the terminal. Sorry, I swear I'm not that stupid.

Um, just a touch confused, do you want me to edit the already existing line ```

auto lo
iface lo inet loopback
```?
or do you want me to add
```
auto lo 
iface eth0 inet dhcp
```
after it?

Secondly, ```
sudo service networking restart
```
gives the error "networking: unrecognized service"

---

### Post by WilcoRogers on 2011-07-14
EDIT: I was just as unambiguous. In my setup I add the two lines in question after the loop command. so those two new lines are in addition to the loop already there.
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

As for the other problem, use:
```

sudo /etc/init.d/networking restart

```

---

### Post by Candlehawk on 2011-07-14
Following Wilco's instructions, when I ```
sudo /etc/init.d/networking restart
``` I get ```
*Reconfiguring network interfaces...
ignoring unknown interface eth0-eth0.
```

Oh, I am sorry for not remembering this, but I have a 10/100Mbps Ethernet card adapter, if that changes anything.

---

### Post by Bucky Ball on 2011-07-14
Try:

```
auto lo 
iface lo inet dhcp
```... only. The reason you are getting an error after 'sudo /etc/init.d/networking restart', though, seems to be because there is no driver installed for you ethernet. 

Could you run this command and post the output back here:

```
sudo lshw -C network
```That will show what driver, if any, it is using (I suspect none) and whether it is getting an IP or not (you discover the latter by trying to ping your router with:

```
ping xxx.xxx.xxx.xxx
```... where xxx.xxx.xxx.xxx is the IP of your router.

---

### Post by Candlehawk on 2011-07-14
ok, the output of ```
sudo lshw -C network
``` is

```
*-network DISABLED
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id:1
bus info: pci@0000:06:00.0
logical name: eth0
version: 10
serial: 00:02:dd:7c:7f:07
size: 100MB/s
capacity:100MB/s
width:32 bits
clock: 32MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-f
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex-full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
resources: irq:9 ioport:2400(size=256) memory:14000000-140001ff
```
when I attempted to ping my router it said ```
connect: Network is unreachable 
```

---

### Post by Bucky Ball on 2011-07-15
Okay, are you running a desktop or are you doing all of this in a terminal? (You have no desktop installed?)

If the former, right click the network icon and 'Edit Connections'. Make sure you have 'Connect Automatically' ticked and in IPv4 settings make sure that is set to DHCP (and not Manual).

You are very close and the card is set-up fine, by the looks, despite my suspicions:

```
driver=8139too
```

You are using that driver and that is the right one.

Could you open a terminal and:

```
sudo ifup eth0
```I have a feeling we are missing something minor here. Everything looks good with your setup. It theoretically is working 'out of the box' as this card has done in Ubuntu for awhile now, but for some reason 'Disabled'. 

Your second message is as I expected; 'Network is Unreachable.' Obvious, because the card is disabled.

* Make sure you have this, and only this, in '/etc/network/interfaces';

```
auto lo
iface lo inet loopback
```

Give those things a try, restart the machine, and see how you go. You are very close.

---

### Post by Candlehawk on 2011-07-15
I edited /etc/network/interfaces to have that and only that in the file. I ran ```
sudo ifup eth0
``` and got ```
Ignoring unknown interface eth0=eth0.
``` and still can not connect. Might this be effected by the fact that my router has a password?
And no, I do not have a GUI.

---

### Post by Bucky Ball on 2011-07-15
No, the password should only apply to wireless AP, not wired serving an IP via DHCP. 

I found a couple of other things which might help. See how you go digging through these:

[http://codingexplorer.wordpress.com/2010/10/04/ubuntu-10-04-does-not-recognize-ethernet-interface/](http://codingexplorer.wordpress.com/2010/10/04/ubuntu-10-04-does-not-recognize-ethernet-interface/)

... which links to this:

[http://ubuntuforums.org/showthread.php?t=1262537](http://ubuntuforums.org/showthread.php?t=1262537)

Also:

[http://ubuntuforums.org/showthread.php?p=11047788#post11047788](http://ubuntuforums.org/showthread.php?p=11047788#post11047788)

... and this:

> 1. open /boot/grub/menu.lst
2. go to the line with the kernel entry and add this:  acpi=force pci=noacpiFrom here:

[http://ubuntuforums.org/showthread.php?p=522773#post522773](http://ubuntuforums.org/showthread.php?p=522773#post522773)

... and this:

> 1root@ubuntu:~$ mii-tool eth0 -F 10baseT-FD
2root@ubuntu:~$ rmmod 8139too
3root@ubuntu:~$ modprobe 8139too... from here:

[http://www.question-defense.com/2010/06/03/ubuntu-10-4-eth0-not-available-rtl-81398139c8139c-rev-10](http://www.question-defense.com/2010/06/03/ubuntu-10-4-eth0-not-available-rtl-81398139c8139c-rev-10)

It is really strange you should be having this problem in the newer releases. As I say, we're probably missing something simple, but what? Gotta go out tonight but will check back later and see if you had any luck. ;)

---

