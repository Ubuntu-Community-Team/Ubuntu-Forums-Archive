---
title: "iBurst wireless connectivity problems: Dialer &amp; driver"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by Julian@Tokelau on 2009-11-09
Hi there,

Just moved to Linux from Windows, so still learning my way around the system. I am running kernel 2.6.28 through Linux Mint 7 (which I believe to be built largely off Jaunty). I am connecting (or attempting to) to the internet using an iBurst desktop modem using an ethernet (not USB) connection.

I have attempted to install as per the instructions on the following Ubuntu HowTo: [https://help.ubuntu.com/community/MobileWirelessBroadband](https://help.ubuntu.com/community/MobileWirelessBroadband)
(which is a great resource for anyone else who finds themselves stuck) and encounter no error messages in the '$ make' and '$ sudo make install' steps, and the pppoe config seems to work out fine, but whenever I try to run it, it fails to recognise the device.

The error output line in the terminal is:
   julian@Tokelau /lib/modules/rp-pppoe-3.10 $ sudo ifup ib0
  
  ib0: ERROR while getting interface flags: No such device
  
  Failed to bring up ib0.
  
  
Also, the output to the 
lsmod | grep ib_
Gives no output at all.

My PC is connected to the modem, but it can't transfer data (no internet for me) because (I think) I can't get the dialer up and running.

If anyone has suggestions, they would be greatly appreciated. Also, if anyone has managed to run the iBurst dashboard successfully through Wine, I'd be interested to know.

Thanks

---

### Post by wRatte on 2010-01-04
> **Julian@Tokelau said:**
> I am running kernel 2.6.28 through Linux Mint 7...
 
...iBurst desktop modem using an ethernet (not USB) connection.

 
i'm also an iburst desktop modem user.
 
first thing: since you're using a desktop modem, not a usb modem, i'll quote the phrase from the given link (because it looks to me like you tried installing the usb stuff):
> 
 
[SIZE=2]**[SIZE=2]1.1. The Ethernet Device[/SIZE]**
 
**[SIZE=2]If you have the Ethernet type, you don't need any special driver and can ignore the rest of this page. [/SIZE]**
 

[B]
[LIST]
[*][SIZE=2]Plug in the modem, you should see your computer connect to the local network [/SIZE]
[*][SIZE=2]Right click on network-manager (the network icon), choose "Edit Connections" [/SIZE]
[*][SIZE=2]Change to the DSL tab [/SIZE]
[*][SIZE=2]Add a new connection, using your login credentials. All the other default settings should be fine [/SIZE]
[*][SIZE=2]Connect to it. (you can tell it to automatically connect whenever connected to the modem) [/SIZE]
[/LIST][/B]
 
[/SIZE][SIZE=2]
 
second thing: linux mint 7 has a bug with their PPPOE wireless connection (which is what the desktop modem uses). i used mint 6, no problem. mint 7 - could connect... but no internet O_o
here's a link about the bug and how to fix it:
[http://forums.linuxmint.com/viewtopic.php?f=90&t=27314#p165799](http://forums.linuxmint.com/viewtopic.php?f=90&t=27314#p165799)
 
i haven't tried linux mint 8 yet, so not sure if the upgrade would help you... but in general it's best to always post linux mint stuff on the linux mint forums also (and then give feedback here if they could answer you over there, etc)[/SIZE]

---

### Post by Julian@Tokelau on 2010-01-07
Simply plugging in didn't work I'm afraid - hence the quest to download and install drivers. I'l try out the bug fix and see if I have any success that way. Thanks a lot for the assistance.

---

