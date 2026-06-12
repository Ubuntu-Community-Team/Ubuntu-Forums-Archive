---
title: "Forced to &quot;ifup eth0&quot; after boot"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by Bootsy Collins on 2008-12-22
Hi.  I'm a longtime Debian user giving Ubuntu a spin.  I'm having an odd networking issue, and the first things to occur to me to try aren't helping.

First, some background:  our home networking configuration is a DSL modem (with a static IP address) connected to a wired/wireless router doing network address translation into 192.168....our intended configuration is for static IP address from .1 to .99, and DHCP starting at .100.

The installer effectively configured my primary ethernet interface; networking worked just fine after installation.  However, it was configured as DHCP (pulling a dynamic IP address of 192.168.1.100 from our house wireless/wired router), and I wanted this machine's address to be static (192.168.1.2).  From my Debian experiences, the way to set this up was via my /etc/network/interfaces file, which I then edited to include:

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
	address 192.168.1.2
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1

I also noticed, however, that ubuntu seemed to have a GUI means of configuring this -- bizarrely (to me), this "Network Configuration" GUI appears to be done at the *personal* level (it's under System --> Preferences rather than System --> Administration, and does not require a sudo password check).  I made sure the IPv4 settings were correct -- manual, address / netmask / gateway as per above, etc.  I restarted networking via scripts in /etc/init.d, and everything worked, with the correct parameters showing up in ifconfig.

Today, I rebooted for the first time, and something odd happened:  the eth0 interface didn't come up.  It wasn't that it was misconfigured -- it was that it just didn't come up at all.  ifconfig showed no sign of eth0, and the Notification Tray icon for Network Configuration showed a white-on-red X, indicating "No valid active connections found."  However, a simple "sudo ifup eth0" got everything working again, and ifconfig looked good:

eth0      Link encap:Ethernet  HWaddr 00:15:f2:55:3f:60  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe55:3f60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8415 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7943 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8376680 (8.3 MB)  TX bytes:1332445 (1.3 MB)
          Interrupt:21 Base address:0xe000 

However, the white-on-red X hasn't left the "Network Configuration" icon in the Notification Try.  More importantly, the same thing happened after another reboot:  no eth0 on boot, as if it doesn't even exist; but everything works fine if I do "ifup eth0" manually after boot.

Any advice here?  And to enable me to figure this stuff out better on my own in the future, where's the best place to read up on the way Ubuntu handles network configuration, the role of the different network-related init scripts, etc.?  I haven't found writeups at that level just yet.

Thanks much,

---

### Post by Iowan on 2008-12-22
Add an "auto eth0" line to the */etc/network/interfaces* file.  If other problems pop up with static address, check this [workaround]("http://ubuntuforums.org/showthread.php?t=974382").
Besides the forums, my next favorite source for information is [http://help.ubuntu.com](http://help.ubuntu.com)

---

### Post by albinootje on 2008-12-22
> **Bootsy Collins said:**
> Hi.  I'm a longtime Debian user giving Ubuntu a spin.  I'm having an odd networking issue, and the first things to occur to me to try aren't helping.


If you don't like the GUI network-manager (I found it annoying at times) you can easily remove it. (sudo apt-get remove network-manager)
In older Ubuntu releases it would then also want to remove the ubuntu-desktop package, but it doesn't do that anymore in Intrepid (and Hardy I think).
After that it's a matter of just using plain old /etc/network/interfaces.

From the link mentioned by another posting :
> 
sudo update-rc.d –f NetworkManager remove
This will disable and remove the Gnome Network Manager application. Now you will have to edit your configuration manually.

This is only disabling NetworkManager during boot up.
It is not removing the actual software from the disk.

---

### Post by JAID on 2008-12-22
Hi,

There are a couple elements similar in this thread, hope I am not being too off-topic.

I must have a basic missunderstanding going on here. Attempting to use Ubuntu 8.04.1 Server 64-bit on an HP DL380 G4 with 6GB Ram and SCSI interface everything seemed to load fine. I gave the machine a static IP address during the process. It doesnt ping out nor can be pinged. A bit slow with these things, after loading I realised the D-Link DIR655 router is dynamically serving IP addresses and although the fixed address I gave is within range there must be a conflict. I tried reserving the fixed name in the router but that doesnt seem to make any difference.

Oddly, the router log shows that the computer to have been accepted once (but refused several times.)

Maybe the acceptance was during one of the times I was fiddling around with the /etc/network/interfaces file.

That file is the area it seems to me that I am having trouble (apart from myself that is.) I had opened it to edit removing the fixed IP address and replacing the iface line with: 

'eth0 inet dhcp' 

I have tried both just removing the fixed IP and also the word address. 
The 'auto eth0' command is in place. The other port is eth1 but I am confident '0' is the correct one.

The removal can happen sometimes with difficulty but there doesnt seem to be a way to save out of the file and I end up crashing out. I have been opening with vi and attempting to quit with quit vi (or something like that) but on opening the command line doesnt seem to be available and the quit command is made part of the file content as far as I can see. There must be a keystroke i am not finding to take you back to the command line as the active function. Something like spacebar or CD but neither seem to do the job.

The intention is to use our static IP and serve our domain as well as use this to server the local and a virtual network but I thought it was worth while just sitting it on the network for a while until I get a bit more familiar and tackle the other elements. Hence, the present intention to just have its address allocated to it dynamically. 

It looks like the process would have been painless if I had not got it wrong on installation but I am lost now so would be obliged if someone could take the time to put me straight firstly about the basic CLI task of opening and closing and secondly on the network editing necessary.

Thanks

Ian
PS I think one of the first things that may need to be done when on-line is to download the desktop and start using it when things get ticklish.

---

### Post by albinootje on 2008-12-22
> **JAID said:**
> 

Maybe the acceptance was during one of the times I was fiddling around with the /etc/network/interfaces file.

That file is the area it seems to me that I am having trouble (apart from myself that is.) I had opened it to edit removing the fixed IP address and replacing the iface line with: 

'eth0 inet dhcp' 

I have tried both just removing the fixed IP and also the word address. 
The 'auto eth0' command is in place. The other port is eth1 but I am confident '0' is the correct one.


Can you test whether it is indeed eth0 which has a cable connected by running the following in a terminal and posting the output here :
```

sudo dhclient
ifconfig -a
route -n
cat /etc/resolv.conf

```

---

### Post by JAID on 2008-12-22
Just a few things to add on this.

I have tried eth0 up and down

On installation, Ubuntu said it wast going off to a time server and didnt complain that it couldnt find one (perhaps it can get out under some circumstances.)

Ian

---

### Post by JAID on 2008-12-22
Hello Albinootje,

Thank you for your incredibly rapid response.

Before the output, oddly this time on starting the machine, the addition of a new computer running Ubuntu/Samba is reported on my Windows XP PC. First time and with no changes except perhaps my fiddling in the /network/interfaces file which appeared to fail last night.

Am using the server edition and have only seen a cli so far.

The readout has been written by hand and re-written here from the Win machine so I may have a few typos. 

It looks like you were onto me straight away and it was not eth0 (which I was postiive it was) but eth1. The readout also shows that it has both the address of the router (a D-link DIR-655 N-wireless and wired router and the D-link ADSL modem) hope it shows any problems with the setup too.

sudo dhclient
-------------

listenting on LPF/eth1/00:11:85:be:78:58
Sending on LPF/eth1/00:11:85:be:78:58
Listening on LPF/eth0/00:11:85:be:78:59
Sending on LPF/eth0/00:11:85:be:78:59
Sending on Socket/fallback
DHCP Discom on eth1 to 255.255.255.255 port 67 interval 3
eth0 to 255.255.255.255 port 67 interval 4
eth1 to 255.255.255.255 port 67 interval 3
CHCPoffe of 192.168.0.195 from 192.168.0.1
DHCPrequest of 192.168.0.195 on eth1 to 255.255.255.255 from port 67
DHCpath of 192.168.0.195 from 192.168.0.1
*Retaly(??) /etc/samba/smb.conf smbd only
....dn(??)
bond to 192.168.0.195 reconnect(??) ub 41629 sec


ifconfig -a
-----------

(likely the last part of the eth0 readout - scrolled instantaneously)

TX packets:0 errors:0 Dropped:0 Overuns:0 ?????:0
Collisions:0 txqueue??:1000
RX bytes:0(0.0b) TX bytes:0(0.0b)

eth1 Link encase?: Ethernet HWaddr 00:11:be:78:58
inetaddr: 192.168.0.195 Bcast 192.168.0.255 Mask 255.255.255.0
up broadcast running multicast MTU 1500 metric 1
RX packets:207 Errors:0 Dropped:0 Overruns:0 Frame:0
TX packets:109 Errors:0 Dropped:0 Overruns:0 Carrier:0
Collisions:0 TXqueuelin?:1000
RXbytes 17848 (17.4kb)
TX bytes 13801 (13.4kb)
Interupt 26

lo Link encap??:Local return
net addr 127.0.0.1 Mask 255.0.0.0
inet6 addr.::1/128 scope host
UP loopback running MTV 16436 Metric1
Rx packets:47 Errors:0 Dropped:0 Overruns:0 Frame:0
Tx packets:47 Errors:0 Dropped:0 Overruns:0 Frame:0
Collision:0 TXqueuelin?:0
Rx Bytes 23653 (23.0k) Tx 23653 (23.0k)


route -n
--------

Kernal IP routing term???

Destination
1.92.162.0.0
0.0.0.0

Gateway
0.0.0.0
192.168.0.1

Gen Mask
255.255.255.0
0.0.0.0.

Flags
U
Ug

Metric 
0
0

Rx??
0
0

UCC??
0
0

iface
eth1
eth1


cat /etc/resolve.conf
---------------------

Reported that no such file or directory could be found

Phew! thats a lot of typing for me. The question marks indicate where I couldnt read my own writing.

If that means I am connected OK does the server edition load browsers and email clients or do you think I need to download and load these?

Thanks again.

---

### Post by albinootje on 2008-12-22
> **JAID said:**
> 
cat /etc/resolve.conf
---------------------

Reported that no such file or directory could be found

That's okay, because it's /etc/resolv.conf, but it doesn't matter now. 

> 
Phew! thats a lot of typing for me. The question marks indicate where I couldnt read my own writing.

If that means I am connected OK does the server edition load browsers and email clients or do you think I need to download and load these?


Thanks for all the hand writing :)

Can you try in a terminal :
```

mtr ping.xs4all.nl

```
to check whether you actually have internet.

And if you want a full-blown desktop on that machine, it's a matter of choosing between the packages ubuntu-desktop,kubuntu-desktop or xubuntu-desktop.

For example :
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```
would install the regular Ubuntu desktop as if you had used the Ubuntu desktop installation cdrom.

---

### Post by JAID on 2008-12-22
The mtr ping worked albinootje. It shows an array with 16 addresses. It is now up to a50 pakcets sent and an average of 5 or 6 % loss though address 1, mygateway1.ar7 shows 0% loss.

I will get on with the next parts of your last post now. 

You are quick.


Thanks
Ian

---

### Post by albinootje on 2008-12-22
> **JAID said:**
> The mtr ping worked albinootje. It shows an array with 16 addresses. It is now up to a50 pakcets sent and an average of 5 or 6 % loss though address 1, mygateway1.ar7 shows 0% loss.

I will get on with the next parts of your last post now. 


Cool, I'm glad you're having internet-access on that machine now :)

By the way. My question to run "dhclient" was mainly to check whether eth0 was indeed connected to the ethernet-cable.

But now you need to either :

Edit /etc/network/interfaces
or
Use Network-manager from the Ubuntu desktop after you've installed that.
Or
Install wicd from [http://wicd.sf.net](http://wicd.sf.net)

For a server it makes sense to edit /etc/network/interfaces and make sure you use a static ip-address.

(I'm off to catch some sleep)
Have a nice day.

---

### Post by JAID on 2008-12-22
Thanks albinootje,

The update download worked fine and it is currently installing the ubuntu desktop. I sort of hoped I might not put that on but given my poor literacy will probably work better with it even if it slows the machine a bit.

Big group of files being downloaded. Takes longer than the entire Ubuntu server OS load :-) probably says something about the resources it will use.

Thanks again

Ian

---

### Post by Bootsy Collins on 2008-12-23
> **Iowan said:**
> Add an "auto eth0" line to the */etc/network/interfaces* file.
Hi.  That was indeed the issue, I'm embarassed to say; thanks for pointing out that missing bit.

I don't have any particular attachment to the NetworkManager service/applet in the Notification Tray, except for one thing -- it appears to be an easy way to connect/disconnect VPNs.  In fact, I used it for this just fine and was impressed with how easy it was to configure/connect-to my workplace VPN.  I'm not sure why this applet now shows the red and white "x" / says no valid active connections found (and thus won't connect to the VPN when requested).  I guess I'll dig around some more.

Thanks!

---

