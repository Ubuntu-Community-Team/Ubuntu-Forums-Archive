---
title: "wireless networking issues"
date: 2008-02-25
forum: Mythbuntu
---

### Post by mr_bungalow on 2008-02-25
This isn't really a mythtv problem per se but since I'm having problems getting an answer on the networking forum I figured I'd ask here to maybe get some help.  I have a myth box connected to my entertainment system.  In order to help out on the wife acceptance factor I dont' have a mouse or keyboard connected.  Lately I've been having some issues with my mythbox losing connection to the network where I need to hook up a mouse and keyboard, exit out of myth, open up the network config tool and uncheck and recheck my connection.  Is there some way to automate this process when the network connection is lost?  My card isn't automatically connecting back to the network.  I've looked at all the settings and don't see any options regarding this.  

I'm using a wrt54g router with hyperwrt installed and a linksys wireless card (54G, not a speedbooster card).  I'm just wondering if there is some tool that will check with the network periodically (every minute/5 minutes) and try to reconnect when it notices the signal is gone.  

When I do shut down mythtv and open up a web browser, I cannot find anything/ping google/etc.  The network is just gone until I uncheck/check the wireless box in network manager.  Maybe someone else here has run into this problem and can lend a hand?

thanks in advance!

---

### Post by haggiscanvas on 2008-02-25
I have been having the same problem.  I tried some things I stumbled across using cron to run some scripts.  They did not work...Well, not for me anyway.  

I don't have the link anymore, but if you search under "wirelesstest" in the forums I think you might find it.  I'm pretty new to linux, so you might have better luck than I did.

---

### Post by mr_bungalow on 2008-02-25
oh my gosh! Thank you thank you thank you!!

I was able to get everything set up using your help.  Did an ifdown wlan0, lost connection, then tried to reconnect a minute later and it works!  Thanks a million!

---

### Post by mr_bungalow on 2008-02-25
I see you are not the person who initially wrote that post.  

Here is what I did:
look at your dmesg to find out where your wireless card is running on (mine is on wlan0).  

change the script to read this, changing to your wireless card:
```
#!/bin/bash
# FILENAME: /usr/bin/wirelesstest
# note the backticks in the next line
if ! `ping -c3 192.168.1.1 >/dev/null 2>&1` ; then
ifdown wlan0
ifup wlan0
fi
exit 0
```

follow all the steps to the end except don't edit crontab -e, edit /etc/crontab (sudo nano /etc/crontab) adding this line:
```
* * * * * root /usr/bin/wirelesstest
```

let me know if you need any help.

---

### Post by mr_bungalow on 2008-02-25
here is a link to that thread, btw:
[http://ubuntuforums.org/showthread.php?p=4405714#post4405714](http://ubuntuforums.org/showthread.php?p=4405714#post4405714)

---

