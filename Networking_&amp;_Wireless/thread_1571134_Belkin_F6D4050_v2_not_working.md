---
title: "Belkin F6D4050 v2 not working"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by wah fun on 2010-09-09
After the Belkin usb worked in 10.10 (32 bit), I was cleaning out my file folder regarding this matter and was reading everything to see if I wanted to save anything since this has been such a laborious effort. I viewed a file that I had named incorrectly (my naming convention)and could not remember ever using it so I saved it. Well, out of curiosity and never one to just give up on anything, I installed ubuntu 9.10(32 bit) and used the file - to my surprise it worked! I installed ubuntu 10.04(32 bit) and used the file - it worked! I installed Mepis 8.5 and used the file - it worked! I installed debian 5(32 bit) and used the file - it worked!

So, I can't say this is 'the' solution but it does seem to work. Give it a try, it might work for you. One note: do your install without the usb inserted then apply the solution.

Here it is: (I am sorry I can't give credit to the individual who discovered this, so if you are that person and you recognize your work, Thank You!)
__________________________________________________ ___________
A little Trick to add the ID 050d:935b for the Belkin F6D4050 v.2000 to the System and
simply (and hopefully) use the rt2870sta that comes with the system (staging), if the new driver v2.3.0.0 from Ralink don't work properly.

First remove the new compiled driver if necessary:

cd
cd RT2870_LinuxSTA_V2.3.0.0
su
make uninstall

(or -if you used the make//checkinstall routine- : use synaptic to remove+purge the 'rt2870' .deb)


If you previously did not manually compile the driver from Ralink start here.

Add the ID:

su
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "050d 935b" > /sys/bus/usb/drivers/rt2870/new_id' | tee /etc/modprobe.d/rt2870sta.conf
modprobe -rf rt2870sta
modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig


The solution works? Ok, load the driver at startup
su
echo rt2870sta | tee -a /etc/modules
__________________________________________________ ___________

Good luck and I hope this saves someone some valuable time.

---

