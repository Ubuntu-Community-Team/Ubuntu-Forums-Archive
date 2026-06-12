---
title: "Network Manager is not running"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by jw1949 on 2011-03-22
I am a bit new to this - Ubuntu is ok with a gui but I am struggling with commands and I think I may have disabled Network Manager.  

The icon is there in the notification area but when I try to connect it says NetworkManager is not running and when I rightclick the icon the "enable networking" box is greyed out.   It is on a desktop which now has no net access so I have not tried to remove and reinstall network-manager.

Any ideas or suggestions would be most welcome.:cry:

---

### Post by jw1949 on 2011-03-23
I guess the best plan will be to reinstall Ubuntu from a CD ? or go back to Windows ? ):P

---

### Post by dineshs on 2011-03-23
Can you post the result of```
cat /etc/network/interfaces
```?

---

### Post by jw1949 on 2011-03-23
auto lo
iface lo inet loopback

---

### Post by dineshs on 2011-03-23
Run ```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```and ensure that *NetworkingEnabled=true*
Run```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```and ensure that ```
managed=true
```
Restart
If nothing works see 
[http://www.ubuntugeek.com/how-to-fix-network-manager-disabled-problem-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-fix-network-manager-disabled-problem-in-ubuntu-10-04-lucid.html)
Note: use* sudo *before commands

---

### Post by jw1949 on 2011-03-23
Hi again Dinesh

No further forward I'm afraid.   Did your suggested edits, these were OK so tried the steps from the geek link - see below:

++++
jack@jack-desktop:~$ service network-manager stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop network-manager
jack@jack-desktop:~$ sudo rm /var/lib/NetworkManager/NetworkManager.state
[sudo] password for jack: 
jack@jack-desktop:~$ 
jack@jack-desktop:~$ service network-manager start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start network-manager
start: Unknown job: network-manager
jack@jack-desktop:~$ 
++++

The nm applet icon is there with an "x" attached and when I click it still says "Network Manager not running" and when I right click the "Enable Networking" box is greyed out !!!

---

### Post by jw1949 on 2011-03-23
If I do an apt-get remove and then an apt-get install will it re-install network manager or is that a bad idea ?

---

### Post by jw1949 on 2011-03-23
Hi again Dinesh

I found a file in /etc/init called network-manager.conf but the .conf was missing; when I renamed & rebooted it is OK again.

Apologies, I think I know what I did wrong now - hope I did not waste your time.

THX, Jack

---

