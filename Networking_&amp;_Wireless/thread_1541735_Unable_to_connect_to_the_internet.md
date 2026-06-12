---
title: "Unable to connect to the internet"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by lordtux on 2010-07-29
Hello all noobie here.  Sorry if I sound abit dumb but I have a asus eee pc 901 notebook, I can’t connect to the internet wirelessly or with a RJ45 connection.  Last week my son came round and thought it was very call the internet worked fine then.  Then he downloaded a programme called wireshark.  Since the installation of that programme there has been no internet.  Even the internet icon on the top bar has gone 
  Aswell as the network manager section has vanished from the preferences menu.  I have uninstalled wireshark thinking it will correct its self but haven’t had much luck.  I am running Ubuntu 10.4 (lucid)
  Kenel Linux 2.6.32-generic GNOME 2.30.2
   
  Thank you in advance:(:(
   
  Lordtux

---

### Post by YesWeCan on 2010-07-29
Try 'sudo /etc/init.d/networking restart'
Check the Ubuntu Software Centre to see whether Network Manager is installed; install it if not.
I have wireshark and it has never done anything bad to my internet connection - it just listens to your networks. So I think something else may have happened.

---

### Post by lordtux on 2010-07-29
Hi I tried that and this is what appears below.

* Reconfiguring network interfaces...                                                 (ok)

But there still isn't any icon on the top right of the screen and no internet still  :(

---

### Post by pebo on 2010-07-29
> **lordtux said:**
> Hello all noobie here.  Sorry if I sound abit dumb but I have a asus eee pc 901 notebook, I can’t connect to the internet wirelessly or with a RJ45 connection.  Last week my son came round and thought it was very call the internet worked fine then.  Then he downloaded a programme called wireshark.  Since the installation of that programme there has been no internet.  Even the internet icon on the top bar has gone 
  Aswell as the network manager section has vanished from the preferences menu.  I have uninstalled wireshark thinking it will correct its self but haven’t had much luck.  I am running Ubuntu 10.4 (lucid)
  Kenel Linux 2.6.32-generic GNOME 2.30.2
   
  Thank you in advance:(:(
   
  Lordtux

No I don't think it's a noobish question. I too  have an eeepc901 and have lost networking.  I'm using  kubuntu 10.04, knetworkmanager tells me "Network management disabled".
Pinging the router gives me "Network is unreachable".
I haven't installed wireshark. Restarting the network doesn't help.
This happened after a recent update.
I've lost both wireless and ethernet connectivity.
You are not alone!

---

### Post by YesWeCan on 2010-07-29
Let's take a look at the outputs of 'ifconfig' and 'route -n'
What is your router address?

---

### Post by ganil on 2010-07-29
Sounds like the problem I just spend 3 hours trying to solve and succeeded.

[http://ubuntuforums.org/showthread.php?p=9401666](http://ubuntuforums.org/showthread.php?p=9401666)

I mean this bug is just nuts.

---

### Post by pebo on 2010-07-30
Yep,  ```
rm /var/lib/NetworkManager/NetworkManager.state
```worked for me. Cheers!

---

### Post by Iowan on 2010-07-30
You can try (re-)installing a Notification Area to the top panel.

---

### Post by lordtux on 2010-07-30
Hi as it was a fresh install I just re-installed it again.  I know it was the easy thing to do and the right thing for a noob to do would be to learn what the problem was and correct it.  But as I'm a noob and there isn't a Linux club near by I need the internet for tutorials.  so one day I'll be able to help others.  thanks again no doubt I'll be on here a lot:p lol.

---

### Post by Iowan on 2010-07-30
Glad you got it to work! If the problem is fixed, consider marking the thread [SOLVED] (under Thread Tools) :)

---

