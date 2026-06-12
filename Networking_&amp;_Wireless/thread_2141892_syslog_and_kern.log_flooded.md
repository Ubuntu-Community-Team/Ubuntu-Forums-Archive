---
title: "syslog and kern.log flooded"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by shane84 on 2013-05-04
My syslog and kern.log seems to be flooded with messages continuously logged many times each second! The frequent ones usually begin with "wlan0: authenticate with...", "wlan0: associate with..", "wlan0: authenticated", "wlan0: deauthenticated", "cfg8011...", or "iwlwifi...". 

Is this an indication of a problem with either the Network Manager or something else? I have not noticed any poblems with the network speed or connectivity besides a number of these messages being logged, but I really do not want this constantly writing on my hard drive and possibly reducing its life!

I use an encrypted wireless network on a university campus. When I switch to a wired connection, it does not seem to log so many messages. The university has instructions for setting up the wireless network using Ubuntu's Network Manager, which only needs the username and password. When I try wicd, besides the username and password, it also asks me for a domain name despite choosing the same encryption method as the one selected on Network Manager, which is WPA & WPA2 Enterprise/ PEAP. I am sorry, I am clueless about how this works so this might be a stupid question, but how do I know what domain name to enter?

If there is nothing to worry about other than my syslog being flooded,  how do I change the settings to prevent so much information from being  logged? 

Thanks!

---

### Post by praseodym on 2013-05-04
There is a bug with the N-mode of the iwlwifi driver. Deactivate it via
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by shane84 on 2013-05-04
I tried your suggestion, but it is not helping. My internet may have become a bit slower; in case I need to reverse the change, do I just delete the line from iwlfifi and restart my computer?

I forgot to mention that my I have Ubuntu 12.04.

---

### Post by praseodym on 2013-05-05
Yes, just remove the file. You may want to update the driver via the backport-modules 3.6

---

### Post by shane84 on 2013-05-05
Thanks!
I decided to update to Ubuntu 13.04, which seems to have  solved the problem. However, although my syslog is no longer flooded like before, I occasionally get the following  error in my syslog:

```
NetworkManager[1458]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
```

---

