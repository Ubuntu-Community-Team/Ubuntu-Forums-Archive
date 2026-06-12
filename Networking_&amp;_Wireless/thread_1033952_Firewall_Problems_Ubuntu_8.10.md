---
title: "Firewall Problems Ubuntu 8.10"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by MrStill on 2009-01-07
First, I don't know much about networking and firewalls. I installed Firestarter to help me maintain my firewall. At first, everything worked quite well; however, this morning it started blocking everything including internet access. If I deactivate and reactivate my firewall everything works as it should; but upon reboot, I have lost my connection again. If anybody has any suggestions it would be great.

---

### Post by akelsall on 2009-01-09
MrStill, I'd say start with this tutorial on iptables (Firestarter is just a user interface to iptables). 

I had an issue similar to yours, and after going through this tutorial, I resolved all of my problems. I had no firewall experience before using the tutorial (although I am very familiar with networking) and it was easy to follow. 

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Andy

---

### Post by MrStill on 2009-01-10
Thanks, I assume set up my own firewall than to use a tool like Firestarter. I like to learn the back end of what is going on. 

I followed these steps and also wrote a shell script for back up. After I followed the walk-through, it seemed as if the problem was solved; however, upon reboot my iptables were once again reset and everything is dropped. If I run the script I wrote I get connection.

It is only a minor inconvenience to run the script; but, I would like to find out what process is resetting the iptables (even though I have network manager set up to run the script as directed).

---

### Post by MrStill on 2009-01-23
I found some configuration scripts for UFW, which I don't remember installing, that were resetting the iptables at start up. I deleted these scripts and I no longer have any problems.

---

### Post by sk72 on 2010-03-01
I cant start/stop iptables under 8.10. iptables is already installed (apt-get install iptables). I tried the following command:

/etc/init.d/iptables stop

The error says "no such file or directory".

---

