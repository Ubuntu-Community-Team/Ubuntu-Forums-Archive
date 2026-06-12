---
title: "can't connect to wireless as normal user minimal install"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2011-12-02
I am trying to run as bare bones of an XFCE system as I can.  I installed a minimal Ubuntu 11.10 install, just the base system.  Then on first boot, I installed the packages 
```
sudo apt-get install xorg, xfce4, midori network-manager gnome-network-manager
``` 
and that is it so far.
Then I did
```
sudo nano /etc/network/interfaces
```
and commented out everything except the lines 
```
auto lo
iface lo inet loopback
```
Then I did
```
sudo nano /etc/NetworkManager/NetworkManager.conf
```
and changed manged to "true".  Then I rebooted.  Now when I boot up, I get a nm-applet in the notification area, and it properly connects and disconnects when ethernet is plugged in or unplugged.  It shows the list of wireless networks but I can't connect to any of them.   executing nm-applet in the terminal and then trying to connect gives the following error
```
** (nm-applet:1911): WARNING **: Failed to add/activate connection: (32) not authorized to control networking.
```

Seems like its a simple permissions problem, but the issue is there is no group "network" or "networking" to add myself to.  Very strange...

Oddly enough, when logging in as root and executing "startx", my networkmanager works just fine, able to connect and disconnect from wireless networks.  Unfortunately, starting x as root hosed my previous install and it was just easier to do a fresh install (minimal install takes about 10 minutes to set up, all said and done)

Any suggestions?

---

### Post by praseodym on 2011-12-02
Change back to "false". "true" means that the NM also reads out the interfaces-file if network interfaces are configured there. Remove your wired connections in "wired" and "DSL" (if any) and reboot.

---

### Post by N00b-un-2 on 2011-12-02
I changed it back to false and rebooted with no change.  same error, same lack of connection.  Also I noticed that I can't disconnect from ethernet using nm-applet, but manually unplugging (obviously) works.  I've read up on this error, but i can only find information pertaining to gentoo and arch, something about consolekit and/or polkit, both of which are installed.
Also worth noting, I installed slim and when I logged in under slim, I had no network connection at all, no wireless detected.

---

### Post by praseodym on 2011-12-02
Please show:

```
lspci -nnk | grep -iA2 net
ifconfig -a
iwconfig
lsmod
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by N00b-un-2 on 2011-12-03
I was up really late last night, figuring things out.  I got the wireless working finally (was an issue with various services not starting up when I logged in, etc)  It took forever to configure wireless, then the sound applet, then the power applet... in the end with all the services and such running, my ram usage went up from about 90mb to 125mb, which is right about what a normal install of xubuntu uses.  The moral of the story; unless you like manually configuring EVERYTHING, or you are trying to install a modern linux distro on legacy hardware, just go with a working distro from the start.

---

