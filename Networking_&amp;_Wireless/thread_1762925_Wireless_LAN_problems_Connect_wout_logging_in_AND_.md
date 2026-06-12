---
title: "Wireless LAN problems: Connect w/out logging in AND auto reconnect"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by agro666 on 2011-05-19
Ubuntu 10.04 LTS

1. I have been using it for a long time where I have to login to the system (I have auto login) and then once it is logged in under my user, it can access my keystore, it connects to the wireless access point.  Is there a way to have it handled on the back end, like it would be if I had been using ethernet (eth0)?  I would like the networking to come up earlier.

2. If I happen to reset the WAP, my ubuntu workstation will reconnect, but not if it is for an extended period of time.  Then I have to go to it and click and tell it to connect.  I want it to _always _try to reconnect indefinitely.  Is this possible somehow?

3. I want to add specific iptables rules for the wlan0 device, but it doesnt seem as easy as adding a rc script or modifying /etc/network/interfaces, as the interface is not up when that is ran.  How can I go about this?

THANK YOU!

---

### Post by stewdk on 2011-05-27
> **agro666 said:**
> 
2. If I happen to reset the WAP, my ubuntu workstation will reconnect, but not if it is for an extended period of time. Then I have to go to it and click and tell it to connect. I want it to _always _try to reconnect indefinitely. Is this possible somehow?

 
I have the exact same problem/question.
I tried implementing the script described in [http://ubuntuforums.org/showthread.php?t=320282](http://ubuntuforums.org/showthread.php?t=320282), and it successfully detects when the wireless is disconnected, but the command "/etc/init.d/networking restart" does NOT make the wireless attempt to reconnect... Any ideas?
I'm also using Ubuntu 10.04

EDIT: After playing around with the aircrack-ng suite, I found a command that will force the wireless interface to reconnect "sudo airmon-ng check kill wlan0".
This command will kill any processes that have anything to do with that specific wireless interface, and Ubuntu is smart enough to restart them getting our wireless to reconnect.
Here's my script:
```
#!/bin/sh
#must run as root
if ! `ping -c3 192.168.0.1 >/dev/null 2>&1` ; then
date
airmon-ng check kill wlan0
echo "Restarting wlan0 processes"
else
echo "Ping ok"
fi
exit 0

#root crontab entry: */10 * * * * /path/to/your/script/restartnetworking.sh >> /path/to/your/log/wifitest.log 2>&1
```As far as #1 goes, you could give the following a try (though I haven't tried myself):
> How can I make NetworkManager connect to a network before I login? On  version 0.7.1 or later edit the profile of the connection you with to  start prior to login and select the box in the bottom left "Available to  all users"[http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ)
Maybe using unsafe storage for the keyring might also help??? Not sure... I'm just trying to come up with some ideas here, and I am by no means a network manager expert.

---

