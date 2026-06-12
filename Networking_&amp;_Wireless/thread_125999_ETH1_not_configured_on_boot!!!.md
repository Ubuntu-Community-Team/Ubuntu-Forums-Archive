---
title: "ETH1 not configured on boot?!?!?!"
date: 2006-02-05
forum: Networking &amp; Wireless
---

### Post by LiteHedded on 2006-02-05
after the install everything worked fine
eth1 is my wireless card
everything was fine until i set it to auto ESSID and DHCP to connect to a different AP
now when I restart the interface is 'NOT READY' 
i have to ifconfig up it and set everything manually
i have to set all the ip info and route add the default gateway and everything
I really don't want to have to reinstall to get this working
please help!
everything in /etc/network/interfaces looks fine by the way

---

### Post by LiteHedded on 2006-02-05
also samba isn't working right.
i can't browse samba shares or print to my samba printer
in fact clicking on print in firefox makes the app freeze
I can do smbclient -L computer and show the shares on computer but smbtree doesn't show anything and i can't browse the shares in konqueror

---

### Post by bscbrit on 2006-02-05
Well, if you set it back the way it was, does it work again?

If yes, then there is something wrong with the way that you are changing it, and if not, then you have a different problem which might be unrelated.  I'm not surprised that samba isn't working if your network isn't behaving.  Do you have 2 AP?  Are you trying to use a hotspot or is this a home network?

---

### Post by LiteHedded on 2006-02-05
[QUOTE=bscbrit]Well, if you set it back the way it was, does it work again?

If yes, then there is something wrong with the way that you are changing it, and if not, then you have a different problem which might be unrelated.  I'm not surprised that samba isn't working if your network isn't behaving.  Do you have 2 AP?  Are you trying to use a hotspot or is this a home network?[/QUOTE]
just one ap at home
yea it's set the way it used to be
and when i /etc/init.d/networking restart it fails

---

### Post by LiteHedded on 2006-02-06
no one has any ideas?
I don't want to have to reinstall and never switch aps to be able to use ubuntu

---

### Post by bscbrit on 2006-02-07
There are plenty of options before you need to re-install!

Firstly, change directory to /var/log.   The files to look through are dmesg, syslog and messages.  There might well be an obvious error being flagged up in one of those logs.  They can be huge files so 'dmesg | less' or ' cat <filename> | less' will give you plenty of control while viewing them (apologies if I am teaching Granny to suck eggs.... [and, for the none native English speakers, that means 'stating the obvious']).

If init.d/networking is failing, there is probably an error in your /etc/network/interfaces file, or a file connected with it in some way.  Lets start with the obvious - can you show me the contents of /etc/network/interfaces please?

If you have a single AP at home, why did you change the file to connect to a different AP?

EDIT:  Apologies for not responding sooner, but I am unable to monitor this forum anywhere near as much as I would like to.  My wife wants me to share my attention between my computer and her, my Boss wants me to do some work for him, and I even slept for a few hours.... :D

---

### Post by LiteHedded on 2006-02-07
[QUOTE=bscbrit]There are plenty of options before you need to re-install!

Firstly, change directory to /var/log.   The files to look through are dmesg, syslog and messages.  There might well be an obvious error being flagged up in one of those logs.  They can be huge files so 'dmesg | less' or ' cat <filename> | less' will give you plenty of control while viewing them (apologies if I am teaching Granny to suck eggs.... [and, for the none native English speakers, that means 'stating the obvious']).

If init.d/networking is failing, there is probably an error in your /etc/network/interfaces file, or a file connected with it in some way.  Lets start with the obvious - can you show me the contents of /etc/network/interfaces please?

If you have a single AP at home, why did you change the file to c
onnect to a different AP?

EDIT:  Apologies for not responding sooner, but I am unable to monitor this forum anywhere near as much as I would like to.  My wife wants me to share my attention between my computer and her, my Boss wants me to do some work for him, and I even slept for a few hours.... :D[/QUOTE]
```


brian@sager:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet static
        network 192.168.1.1
        broadcast 192.168.1.255
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid network
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 24.95.227.35 24.95.227.36
        address 192.168.1.101
        netmask 255.255.255.0
        gateway 192.168.1.1

iface eth0 inet

auto eth1

```
I don't see any errors in dmesg or /var/log/messages

and I didn't change the file to connect to a different AP
i set it to auto in the gui control panel
or with iwconfig I don't remember
but I didn't even know about that file until this happened and I started asking around for help

---

### Post by bscbrit on 2006-02-07
Ok, try the following:

Your network should be 192.168.1.0   (192.168.1.1 is your gateway)

Add:
 wireless-channel <your_channel_number>  (It hasn't been told which channel to use)

Remove:

iface eth0 inet  (There is no evidence that you have eth0 fitted)

Let me know how you get on. :-D

EDIT: Don't use the GUI for wireless set up - I don't know why but it doesn't seem to work very well.

---

### Post by LiteHedded on 2006-02-07
eth0 is my wired ethernet
I had network set to .0 but was told to change it by someone on #ubuntu

---

### Post by bscbrit on 2006-02-07
Well, I cannot see where your eth0 is configured. Is it DHCP, static?

When you set the wireless-channel, did you get the wireless network working?

---

### Post by LiteHedded on 2006-02-07
i added the channel and it still fails
eth0 is not configured because I don't use it

---

### Post by bscbrit on 2006-02-08
If you are not using eth0, please remove it from your interfaces file.

This is my interfaces file for my wifi card :

> 
# The loopback network interface
auto lo wlan0
allow-hotplug wlan0
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

iface wlan0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid bscbritnet
wireless-nick spare
wireless-channel 6
wireless-mode managed
wireless-ap 00:13:46:9E:FF:FF
wireless-key1 aa11bb22cc33dd44ee55ff6600
wireless-defaultkey 1
wireless-keymode open


Are you able to ping the wifi card from the command line i.e. are you sure that it is installed correctly with the correct drivers under Ubuntu?

---

### Post by LiteHedded on 2006-02-08
yea once I ifconfig eth1 up and config it manually it works fine
like I said right after install everything worked fine

---

### Post by bscbrit on 2006-02-08
So when you made the changes that I proposed in my last post, did it solve the problem?  

Secondly, can you ping the network card from the computer i.e. can the computer see its _own_ network card?

---

### Post by LiteHedded on 2006-02-09
once I configure it manually it works fine
I can do anything I want with it
the interface is down and not connected to the ap so you wouldn't be able to ping it from another machine

---

### Post by bscbrit on 2006-02-09
We're going round in circles here.  If your network is not configuring at boot up then it would suggest that /etc/network/interfaces is wrong or there is some error that will appear in one of the log files.  You have checked the logs and assured me that there are no errors so I can only surmise that there is perhaps still a fault in the interfaces file.

When you say that you have configured the network manually, what exactly do you mean?  Are you simply starting it by 'sudo /etc/init.d/networking restart' or are you having to rewrite values in the interfaces file? If the latter, which values are you changing?

---

### Post by LiteHedded on 2006-02-09
like I said I have to "ifconfig eth1 up" and then set the static ip via ifconfig 
and set the essid with iwconfig
then route add default gw 192.168.1.1
then it works

---

