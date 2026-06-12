---
title: "Can't connect to Wireless-N network. WICD"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by jpepin on 2010-11-16
I'm currently using WICD, which I switched to after network manager was unable to retain a wireless connection for more than 10 minutes at a time.

Using WICD, my connection has been stable for months, and I've had no problems connecting to my network using WPA2.  

However, I just noticed that in the WICD connection info, my **connection speed never tops 54Mbps **(don't know how long it's been like that, since I never really looked before).  I seem to be unable to connect to an N network.  My router is configured as "auto g/n".  If I switch it to "n only", changing nothing else, I'm unable to connect.  I've tried this on two seperate routers, on both 2.4 and 5 Ghz freq's.  In all cases, the network is detected, and appears in the list of available networks.  It just won't connect.

(Of note, others have mentioned problems connecting using WPA2.  I've had not issues with that.)

**SO why can't I connect to a wireless-N network?**  

System specs:
Dell XPS M1530 Laptop
Intel 4965agn wireless card
Ubuntu 10.10

---

### Post by jpepin on 2010-11-16
No one else has had this problem, or has possible answers?

---

### Post by deerewright on 2010-11-17
I have the same problem, using network manager.  My card is an Intel Pro wireless 4965 AGN, but it will only connect on G.  On an 'N' only network it will not connect.  Connects fine in Vista however.

---

### Post by Xarlith on 2010-11-17
Same on 5100AGN. Connects only in g mode. It even can't find a network if the router is set to an 11n mode. It not depends on wicd cause the problem is with network-manager too.

---

### Post by jpepin on 2010-11-17
I should have pointed out that it connects fine in Windows 7.  

I hadn't tried it with network manager yet, but it looks like I'll get the same results as WICD.

---

### Post by Xarlith on 2010-11-20
I've made some progress. The card connects to my router at 150Mbps (250-300Mbps on Windows 7). 
The bad news is that transfers between PC's are lower than before...

If you want to test it on your machines you must to edit /etc//etc/modprobe.d/options and add the following line
```
options iwlagn 11n_disable=0 11n_disable50=0
```
After that reload iwlagn
```
sudo modprobe -r iwlagn
sudo modprobe iwlagn
```

---

