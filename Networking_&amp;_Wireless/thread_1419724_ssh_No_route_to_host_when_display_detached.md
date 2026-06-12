---
title: "ssh: No route to host when display detached"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by frafu on 2010-03-02
Hi, 

I have a PC with Ubuntu karmic 64bit, that I would like to use as nfs server.

Everything seems to work as it should when the display is attached to it. However, after I detach the display and restart it, I am not able to connect to it anymore by ssh. It tells me: "no route to host".

If I shut it down, reconnect the display and restart the computer, it works again. 

To be sure that it is not fsck delaying the startup, I disabled it in fstab.

Could anybody please tell me whether it makes sense that ssh stops to work when I detach the display? Or is the problem nevertheless located elsewhere? 

Thanks in advance for any help, 

Francesco.

---

### Post by MaindotC on 2010-03-02
I doubt this has anything to do with your display being detached.  My advice is to leave the ssh session open, gather your network information on the ssh server, disconnect the display, and then compare your network information.  There is absolutely no reason detaching your monitor should have anything to do with your network settings.

---

### Post by frafu on 2010-03-02
Thanks strAlan for your reply. 

When I detach the monitor while the server is running, the network continuous to work apparently without changes. After a reboot, I get again the no rout to host message. 

I now wonder whether the problem might not be related to the network-manager: when the display is attached, the computer boots to the point where the network manager defines the static ip of the server; however, without display, the server does not get to the point where the network manager sets up the static ip and the network remains unconfigured. 

Does it make sense?

Cheers

---

### Post by MaindotC on 2010-03-02
> **frafu said:**
> Thanks strAlan for your reply. 

When I detach the monitor while the server is running, the network continuous to work apparently without changes. After a reboot, I get again the no rout to host message. 

Stop rebooting the machine!!!  If you must reboot, define the ip address statically in /etc/network/interfaces.

---

### Post by frafu on 2010-03-02
> **strAlan said:**
> If you must reboot, define the ip address statically in /etc/network/interfaces.

The server will not run 24/7; it is configured to start up by wol and the clients are able to shut it down by ssh; everything works when the display is attached to it.

Here is the content of /etc/network/interfaces:
```

auto lo
iface lo inet loopback 

auto eth0
iface eth0 inet static
address 192.168.1.17
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

I even removed the network manager from the server: 
```

sudo apt-get remove network-manager network-manager-gnome

```

It still does not work.

Francesco.

---

### Post by Yannick Le Saint kyncani on 2010-03-02
I wonder if it's not your bios that refuse to boot without a display ?

You could remove your display, reboot, wait until it's locked, then reattach your display and see where the computer is hanging ?

---

### Post by frafu on 2010-03-02
> **Yannick Le Saint kyncani said:**
> I wonder if it's not your bios that refuse to boot without a display ?

You could remove your display, reboot, wait until it's locked, then reattach your display and see where the computer is hanging ?

The computer seems to boot without display. If I attach the display after booting, the screen stays black, similar to when a display goes to sleep. Hitting keys on the keyboard or moving the mouse does not wake the screen.

---

### Post by Yannick Le Saint kyncani on 2010-03-02
All right, then maybe xorg starts but a bug deadlock the kernel. Maybe use vesa only (no proprietary driver) for graphics and if it does not work, disable X altogether (don't know how it's done with upstart).

Except that in your first post, you wrote that when ssh'ing into the headless box, you would get a "no route to host" message.
No route to host means that the ssh client machine does not know which network interface to use to try and contact the other machine. Does not matter if the other machine is on or off.

So I guess you made a mistake with your "no route to host" message and the ssh server does lock if it's being headless. Try without X.

Edit: Also, when the screen is black, try hitting ctrl+alt+f1

---

### Post by frafu on 2010-03-05
> **Yannick Le Saint kyncani said:**
> All right, then maybe xorg starts but a bug deadlock the kernel. Maybe use vesa only (no proprietary driver) for graphics and if it does not work, disable X altogether (don't know how it's done with upstart).


The motherboard has an Intel 865G graphic chip on board and I am not using propriety drivers as far as I know. 

The curious thing is that there is an old hardy installation on a partition on that computer and when I start it headless with hardy, it works. But as I will also be using the ext4 file system, hardy is not a long term option anymore.

> 
Except that in your first post, you wrote that when ssh'ing into the headless box, you would get a "no route to host" message.
No route to host means that the ssh client machine does not know which network interface to use to try and contact the other machine. Does not matter if the other machine is on or off.

So I guess you made a mistake with your "no route to host" message and the ssh server does lock if it's being headless. Try without X.


That's strange; but that is the message that I get when I try to start headless from the desktop version of Ubuntu karmic.

> 
Edit: Also, when the screen is black, try hitting ctrl+alt+f1

Unfortunately, ctrl+alt+f1 did not bring me to a VT after starting it head with the desktop version of Ubuntu karmic.  :(

I finally decided to give up with the karmic desktop version and decided to use the lucid server version that I downloaded and successfully installed. 

The box is now running headless with the lucid sever system and wol and remote shutdown are working too. 

Thanks to all for the help provided, even if I was not able to make it work with the desktop edition. 

As the original problem has not been solved, I am not going to mark this thread as solved. 

Cheers, 

Francesco.

---

### Post by MaindotC on 2010-03-05
Sorry that was kind of a dumb remark of me to say "stop rebooting the machine".  I'm not really sure what the problem is, but I was thinking you could just install Ubuntu Server edition which will provide your file server needs and definitely does not require a display after installation.

Too late to reinstall?  If not, I believe the time it takes to reinstall will be less than the amount of time it takes to figure this out.

---

### Post by frafu on 2010-03-06
> **strAlan said:**
> Sorry that was kind of a dumb remark of me to say "stop rebooting the machine".


Don't worry about it.

> 
I'm not really sure what the problem is, but I was thinking you could just install Ubuntu Server edition which will provide your file server needs and definitely does not require a display after installation.

Too late to reinstall?  If not, I believe the time it takes to reinstall will be less than the amount of time it takes to figure this out.

In fact, at some point, I gave it up to try to run the desktop version of karmic headless and installed the lucid server edition, which was easier than I expected. 

Afterwards, I manually installed the nfs server, added wol and my ssh keys and now I am also able to start it and to shut it down remotly. 

A bit off topic: At the moment, I am administering it remotly by ssh; are there also other ways to administer it remotly (for example webinterface)? For the moment, it is configured as a samba, nfs and ssh server. Maybe somebody can point me to some documentation about how to easily administer it. 

Cheers, 

Francesco.

---

### Post by MaindotC on 2010-03-06
I'm not really sure what you need to do seeing as how all your configurations are in configuration files which you can manipulate by ssh'ing into the machine.  If you want to add services then there are [GAdmin Tools](http://gadmintools.flippedweb.com/).

---

