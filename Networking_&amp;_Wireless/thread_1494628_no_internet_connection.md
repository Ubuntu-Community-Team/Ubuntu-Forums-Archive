---
title: "no internet connection"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by lovo on 2010-05-27
hello, I do not have Internet anymore on my computer and I dont see the reason. I have kubuntu 10.4, and the icon of the network changed to that :
Mouse over :
[IMG]http://img710.imageshack.us/img710/5415/ss1i.png[/IMG]

Mouse click :
[IMG]http://img241.imageshack.us/img241/6857/ss2.png[/IMG]

what should I do ? Internet is perfectly working on winXP.

swan

---

### Post by Iowan on 2010-05-27
I haven't used Kubuntu, but "unmanaged" frequently means that the interface is defined elsewhere - typically */etc/network/interfaces*.

---

### Post by lovo on 2010-05-28
> **Iowan said:**
> I haven't used Kubuntu, but "unmanaged" frequently means that the interface is defined elsewhere - typically */etc/network/interfaces*.

so what should I do ? Im a beginner.

---

### Post by dorothykinder on 2010-05-28
Have similar kinda problem how can i also solve it.

---

### Post by Iowan on 2010-05-28
[This]("http://ubuntuforums.org/showpost.php?p=7955722&postcount=6") is how I'd check */etc/network/interfaces* in Ubuntu - dunno if Kubuntu has different options.

[This]("http://ubuntuforums.org/showthread.php?p=9372756#post9372756") thread is similar...

---

### Post by lovo on 2010-05-29
well .. it doesnt changed anything ..
Its very strange how we can lose an ethernet internet connection quickly on linux.

---

### Post by Detonate on 2010-05-29
These instructions are intended for those who are having problems getting a wired (Ethernet) connection to work.  If you have exhausted all methods you had found with a search to get network manager working, and you still can't connect try it this way.  Following these instructions will remove network manager from your system and set up your system to connect without any network manager.  I wrote this howto back when I was using 8.10, but no reason it should not work in later versions also.

Recently there seems to have been a lot of posters with problems  getting their internet connection working with a wired connection.  Many of these problems seem to be related to the network manager not working correctly.  

It's nice to have a GUI to help with setup of things, but sometimes they just don't seem to work.  In fact, sometimes they actually break a working system.  So I'm going to explain, step-by-step how to get things working for your network and internet without using the GUI.

First thing you should do is remove any network managers you have installed.  The reason we remove them is because, once you get your network up and running, those programs will try change things in the files we are going to edit, and possibly break things again.  Open a terminal and issue one of these commands.

```
sudo apt-get remove network-manager-gnome
```

```
sudo apt-get remove network-manager
```

And remove any other networking managers you may have installed.

Now we need to make sure that your system is actually recognizing your ethernet hardware.
Issue the command
```
ifconfig
```
in a terminal, and you will quickly see what interfaces are currently active.  Hopefully you will see at least eth0 and lo listed.  If not, you need to get eth0 working, and that is beyond the scope of this howto.  Search the forum for information on getting your network card up and running, then come back here.

Next you will need to edit two files.  The /etc/network/interfaces file and the /etc/resolv.conf file.  Be sure and back up both files before editing them.

Open the interfaces file by issuing the command
```
gksu gedit /etc/network/interfaces
```
in a terminal.  When gedit opens you should see something like this.
[B]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp[/B]
If your file doesn't look like this, edit it.  Then save the file.  You should now be able to connect to a dhcp server, which is your router or cable/dsl modem if you are not using a router.  This setup will get you running with DHCP.  If you want to use a static IP on your network, you would change the line
iface eth0 inet dhcp
to read
iface eth0 inet static

and then enter the following lines below that.
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.0.1

Modify these lines for your system.  The address must be one that will be recognized by your router and outside the DHCP address your router assigns, if DHCP is enabled in you router.

The gateway also must be the gateway of your router.

The following info is only for using a static IP. If you are using dhcp you should not have to edit the resolv.conf file.


But before you get connected, we need to tell your computer  where to find the domain name server. (DNS)

That is the function of the /etc/resolv.conf file.

So let's open up that file with gedit (or any text editor) by issuing the command 
```
gksu gedit /etc/resolv.conf
``` in a terminal.  If there is no resolv.conf you will be presented with a blank page.  If one already exists you will see something like this.  Saving your file will modify or create the resolv.conf file.

This is what mine looks like.

[B]nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.0.1[/B]

You can have up to three nameservers listed in resolv.conf.   These are the places where information is stored that resolves urls into IP addresses.  The first two listed above are for OpenDNS which is the DNS server I have been using for a long time.  The last one is for my router where information is kept to allow you to access other computers on your network.

In your file, you want to put the nameserver (DNS) that matches the one listed in your router or modem.  You will need to access the setup page from a browser to find out exactly what that is.  You can find out how to do this by consulting you router or modem documentation.



Edit your file to include those DNS's listed in your router's or modems setup, preceded by the word "nameserver" before each.  Save the file (you did make a backup earlier didn't you)?

Now we are ready to see if it works.  Issue the following command in a terminal.

```
sudo /etc/init.d/networking restart
```

See:
man interfaces
man resolv.conf

Note:  When I said "router" that could also refer to your modem if you are connected directly without a router.  And of course you can substitute any text editior for "gedit".

Please feel free to point out any mistakes or other helpful hints.

---

### Post by DavorC on 2010-05-31
@Detonate: I thought NetworkManager is the preferred way of doing networking now. Using /etc/network/interfaces as a workaround is fine, but solving the problem in the network manager instead of uninstalling it is even better.

---

### Post by Detonate on 2010-05-31
The preferred method is the one that works.  If network manager works for you, use it.  If it doesn't, and it doesn't for many, then use my method.  Remember, that network manager is merely a GUI interface that basically does what I described for you.

---

### Post by DavorC on 2010-06-09
> **Detonate said:**
> The preferred method is the one that works.  If network manager works for you, use it.  If it doesn't, and it doesn't for many, then use my method.  Remember, that network manager is merely a GUI interface that basically does what I described for you.

That is not correct: NetworkManager is not just a GUI, but a daemon intended to automatically manage interfaces that *are not* manually managed through /etc/interfaces. (There is the GUI bit too, but that's secondary.) 

I'm dealing with a similar issue as the OP myself (LP bug #579941), and had to resort to the manual management using ifup when NM stopped working. While it does get the network running, it affects other bits of system in a negative way: from the network indicator in the panel, to Firefox thinking it's offline when it starts up. So I'm trying to fix the underlying NM issue properly now, and would advise the OP to do the same if he can.

---

### Post by DavorC on 2010-06-09
Apparently, the problem is that the Network Manager marks network interfaces disabled during the hibernate, and re-enables them on suspend. When hibernate fails and the user has to reboot, the second step never executes, and the interfaces remain disabled, as far as NM is concerned.

See [http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html](http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html) (or LaunchPad bug #524565) for a fix (which worked for me): 
```

 service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start

```

Detonate's method will work, but using the default Network Manager is the way Ubuntu has gone for handling networking in recent versions so stick with it if you can, and especially if you don't know what you're doing when editing the network config files.

---

### Post by Detonate on 2010-06-09
I agree that one should use Network Manager if at all possible.  But sometimes you just can't get it to work, or it is too difficult to get working.  I have edited my previous post (#7) to reflect this.  Yes, there is more to Network Manager than just a GUI, but the underlying program only modifies the files that make the network work.  By modifying those files yourself, you are doing the same thing network manager should be doing if it works correctly.

---

### Post by SabreWolfy on 2010-08-16
> **DavorC said:**
> Apparently, the problem is that the Network Manager marks network interfaces disabled during the hibernate, and re-enables them on suspend. When hibernate fails and the user has to reboot, the second step never executes, and the interfaces remain disabled, as far as NM is concerned.

See [http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html](http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html) (or LaunchPad bug #524565) for a fix (which worked for me): 
```

 service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start

```

Detonate's method will work, but using the default Network Manager is the way Ubuntu has gone for handling networking in recent versions so stick with it if you can, and especially if you don't know what you're doing when editing the network config files.

Thanks -- this resolved the problem I was experiencing. Kubuntu 10.04 LTS failed to resume from a hibernate and I was forced to hard-power down the laptop. Upon restarting (several times) I could not get networking to start. Deleting the state file solved the problem. [A little disappointing that I could not resume from hibernation on an LTS release :(]

---

### Post by timarius on 2010-10-10
Thank you for the solution!
Does anyone know if this is solved in any recent updates? Is it safe to use hibernate now?

---

