---
title: "How to save a iptables change?"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by Roig on 2009-04-26
Hello, 

I messed my iptables trying to make my ubuntu PC as a router.. now everytime! i reboot my PC i have to run this script that i made:

```

#!/bin/sh

sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -F
sudo iptables -X


```

to get acces to internet.. my question is.. (and i know it's a noob question..) How can i save the iptables after i run this script so i will not have to run anymore this script when i reboot my pc?

Thank you and sorry for my poor english.:guitar:

---

### Post by Roig on 2009-04-27
Anyone? :S BUMP

---

### Post by kevdog on 2009-04-27
When you boot prior to running the script, what does 

iptables -L 

show?

---

### Post by uniden9 on 2009-04-28
Ubuntu has so many different ways for auto manipulating  iptables.  With out more info on what you were doing before, its hard to say how to undo it.  You can modify them as a post-up step in the /etc/network/interface file.  This step can be overridden by hundreds of available firewall applications that run after the /etc/init.d/networking step.  I believe that ubuntu does or did at one time install ufw as the default firewall.  Then there are others such as firehol, firestarter, to name a few.  Without know what is setting up the restrictive firewall, its hard to undo it.

I would start looking at whats after networking and has a higher number.
$sudo ls /etc/rcS.d
If you see one, then look for a /etc/default/ file with same name.  Edit the file and see if you have the option to disable it.  Note that not all have a /etc/default config file.

If you do not see you firwall in there, then start looking at
$sudo cat /etc/network/interfaces
Here you are looking of iptable-restore command.
If you find one, take note of the file being restored and 
then run your script and
sudo iptables-save > (iptables-restore_file)


Justin

---

