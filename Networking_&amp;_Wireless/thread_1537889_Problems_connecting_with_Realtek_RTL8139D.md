---
title: "Problems connecting with Realtek RTL8139D"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by andy_blah on 2010-07-24
I've had this problem ever since I've installed this ethernet card in the PC (after the 'effin integrated one blew off for some reason), I wasn't ever able to make the networking work again. Every time I try to trigger the PPPoE connection (DSL), the PPP configurator keeps on looking for the concentrator, reaches over 100% and stayed like that for 1 hour.

Here's the terminal log of everything that I've tried:

```
~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 5
       bus info: pci@0000:00:05.0
       logical name: eth0
       version: 01
       serial: 00:e0:a0:00:c0:6d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sc92031 duplex=full latency=32 link=yes maxlatency=40 mingnt=20 multicast=yes port=MII speed=100MB/s
       resources: irq:16 memory:e8521000-e85210ff ioport:e000(size=256) memory:18000000-1801ffff(prefetchable)

	   
~$ lsmod | grep 8139
8139too                18545  0 
mii                     4381  1 8139too

~$ lspci | grep Ethernet
00:05.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)

```

Any solutions to this problem?

---

### Post by andy_blah on 2010-07-28
Nevermind the above post, managed to fix the problem after some more configuring, the new Network Manager gets more and more bizarre. 

Now my problem is that every time I want to connect, I have to start the DSL connection from NM's menu and after that to type in the &#8221;default&#8221; password. That's not a problem for me, only that I won't be using this machine much, instead my dad will and he's a real computer sawy problem, plus that he's quite hostile about doing 100 things before accomplishing one task. So, my question is, are there any ways of making the PPPoE connection start automatically when the OS boots?
I've tried to set the connection through terminal (pppoeconf) since this is the only way of making it connect automatically I knwo, but it cannot find the access concentrator.

---

### Post by andy_blah on 2010-08-02
Anyone... ?

---

### Post by dineshs on 2010-08-02
While configuring DSL via Network manager there is an option `connect automatically'.Did you try ticking that?

---

### Post by andy_blah on 2010-08-02
Unfortunately, no, I did tick the box and it still asks me for the password and I have to manually connect every time.
More importantly I would want the terminal method to work, since I know that would surely connect every time I boot into Ubuntu.

---

### Post by andy_blah on 2010-08-06
*bump* Nobody knows?

---

### Post by dineshs on 2010-08-07
If network manager is running you will not be able to setup the connection using pppoeconf.So I think you may try removing NM,restart the machine and proceed with pppoeconf .The first part of the following link explains how to remove NM (I havent tried this )
[http://www.uluga.ubuntuforums.org/showpost.php?p=8975701&postcount=2](http://www.uluga.ubuntuforums.org/showpost.php?p=8975701&postcount=2)

---

### Post by andy_blah on 2010-08-07
Thank you very much for that resource, but unfortunately that doesn't seem to work as after configuring, pppoeconf still doesn't find anything. I've issued the second last command on the page you suggested after finishing with the removal of NetworkManager and it printed this:


```
~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0c:76:ae:9a:82  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:5922:5efa:4:20c:76ff:feae:9a82/64 Scope:Global
          inet6 addr: fec0::4:20c:76ff:feae:9a82/64 Scope:Site
          inet6 addr: fe80::20c:76ff:feae:9a82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1172099 (1.1 MB)  TX bytes:11232 (11.2 KB)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

---

### Post by dineshs on 2010-08-07
To what device your ethernet cable is connected to?If it is a router/modem why dont you try to configure it in PPPoE mode ?

---

### Post by andy_blah on 2010-08-07
No router, no modem. I'm directly connected to my ISP (don't ask... it's their strange way of doing things XD)

---

### Post by dineshs on 2010-08-07
I am also using 10.04.DSL via NM is working fine for me.Can you try a live CD and see if DSL via Network Manager is working fine.I am attaching two images.

---

### Post by andy_blah on 2010-08-08
The problem wasn't whether it works or not, it was that it doesn't do it automatically like the pppoeconf command. I just want to be able to use that instead of the graphical Network Manager.

---

### Post by dineshs on 2010-08-08
> The problem wasn't whether it works or not, it was that it doesn't do it automatically like the pppoeconf commandI am sorry.
pl try
```
sudo pppoeconf iface eth1
```If it is not working
try a live CD just to check whether it is detecting access concentrator when pppoeconf command is used

---

### Post by andy_blah on 2010-08-09
No need to apologise ^o^;

I've tried with both 10.04 and 9.10 live CD and both have a non-woking pppoeconf X.X

---

### Post by dineshs on 2010-08-09
Recently found a thread where a similar problem was solved by updating.(I am able to connect DSL -configured via NM-automatically on startup).So try reinstalling NM and then update
[http://ubuntuforums.org/showthread.php?t=1548353](http://ubuntuforums.org/showthread.php?t=1548353)

---

### Post by andy_blah on 2010-08-09
Do you happen to know any way of reinstalling NM without having to download a lot of .debs with libraries? I tried installing it but it keeps asking for libraries, and I have to boot to windows (to download the debs) and back to Ubuntu to install them.

---

### Post by dineshs on 2010-08-10
Open synaptic package manager and mark network-manager for installation.(do not apply)
Go to file-generate package download script name it and save.
Store the script say in a pen drive preferably in a folder.
Boot the live cd ,create DSL connection and connect to internet.
Open the folder in pendrive ,rightclick the script and run in terminal.This will download all the required packages and save it in the same folder in the pendrive.
Now go back to the original ubuntu installation,copy and paste all these files - except the script - into /var/cache/apt/archives by opening the folder using
```
gksudo nautilus /var/cache/apt/archives
```
Now open synaptic package manager , mark network-manager for installation and apply
Note:by looking into the contents of the script you can download packages via WINDOWS

---

### Post by andy_blah on 2010-08-10
[QUOTE="dineshs"]Go to file-generate package download script name it and save.[/QUOTE]
Is that a certain feature in Synaptic? And should I do those two indications (1st and 2nd) in the Ubuntu installation without NM, right?

---

### Post by dineshs on 2010-08-10
yes it is a feature in syn
You should generate the script in the original ubuntu installation in which NM was removed
use live cd to download
Copy files to /var/cache/apt/archives in original ubuntu installation

---

### Post by andy_blah on 2010-08-10
Okay, so now I've managed to reinstall NM with the help of your indications, but NM doesn't appear in the tray area anymore. I've tried to access the Network Connections in System->Preferences, but it doesn't seem to start the DSL connection from there even tho the PPPoE connection is set up properly. What should I do now?

---

### Post by dineshs on 2010-08-10
what are the contents of /etc/network/interfaces?```
cat /etc/network/interfaces 
```

---

### Post by andy_blah on 2010-08-10
```
~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.1.112
netmask 255.255.255.0
gateway 192.168.1.1
```

---

### Post by dineshs on 2010-08-10
First backup your /etc/network/interfaces
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
```
gksudo gedit /etc/network/interfaces
```
Edit the file so that it contains only these two lines
```
auto lo
iface lo inet loopback

```
save the file and close
[COLOR="Magenta"]Restart your PC[/COLOR]
If NM icon is back try configuring DSL connection(should tick [COLOR="MediumTurquoise"]Available to all users[/COLOR] and [COLOR="MediumTurquoise"]connect automatically[/COLOR] while configuring)
If you are unable to start it automatically try updating

---

### Post by andy_blah on 2010-08-10
Thank you very much!, it worked right after restarting, smooth and automatically, now my dad doesn't have to fiddle with passwords and multiple clicks every time he wants to connect XD

Thank you again for your help and patience through all those 3 pages of the thread ^o^;

---

### Post by dineshs on 2010-08-10
Happy to hear your problem is solved.please mark the thread as solved (via thread tools)
Did you update ?

---

### Post by andy_blah on 2010-08-11
No, it wasn't needed, and I don't know how exactly I would do that. The Update Manager didn't show any updates for NM.

---

### Post by dineshs on 2010-08-11
> **andy_blah said:**
>  The Update Manager didn't show any updates for NM.Then it is uptodate

---

