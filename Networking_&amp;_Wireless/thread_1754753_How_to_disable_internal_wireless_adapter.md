---
title: "How to disable internal wireless adapter?"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by stembot on 2011-05-10
My Intel 5100 AGN adapter works horribly in Ubuntu.  I want to disable it, so I can use a USB wireless adapter that works normally.

I cannot find a reliable way to permanently do this. 

I'm using 10.10.

Suggestions?

Thanks

---

### Post by chili555 on 2011-05-10
What about it works horribly? Usually Intel wireless drivers work well. 

If you are determined to disable it, you might blacklist its driver:```
sudo su
echo "blacklist iwlagn" >> /etc/modprobe.d/blacklist.conf
rmmod -f iwlagn
exit
```I'd be glad to help fix the 5100.

---

### Post by stembot on 2011-05-10
It disconnects randomly and frequently.  Often, the reconnect takes several minutes to complete, which makes it unusable for me.

Some people have seemed to deduce the Intel driver doesn't connect to N very well.

Here are some examples from the web that seem to mimic my issue:

[http://hardc0l2e.wordpress.com/2010/05/19/intel-5100-agn-on-ubuntu-10-04/](http://hardc0l2e.wordpress.com/2010/05/19/intel-5100-agn-on-ubuntu-10-04/)

[http://forums.anandtech.com/showthread.php?p=31348305](http://forums.anandtech.com/showthread.php?p=31348305)

---

### Post by chili555 on 2011-05-10
Here is something to try:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Add one line:```
options iwlagn 11n_disable50=1 11n_disable=1
```Proofread carefully, save and close. Now do:```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn
sudo ifconfig wlan0 up
```Any improvement?

In the same file, you might also try:```
options iwlagn 11n_disable50=1 11n_disable=1 swcrypto=1
```Please post back and let us and the searchers know.

---

### Post by stembot on 2011-05-11
> **chili555 said:**
> Here is something to try:```
sudo gedit /etc/modprobe.d/iwlagn.conf
```Add one line:```
options iwlagn 11n_disable50=1 11n_disable=1
```Proofread carefully, save and close. Now do:```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn
sudo ifconfig wlan0 up
```Any improvement?

In the same file, you might also try:```
options iwlagn 11n_disable50=1 11n_disable=1 swcrypto=1
```Please post back and let us and the searchers know.

This is helpful but I'm not really interested in wasting more of my time on troubleshooting the Intel adapter. 

I have a working USB wireless adapter, and want to get the Intel one disabled and out of the way.  It still tries to connect after I take it offline using 'ifconfig down'.

---

### Post by jerrrys on 2011-05-11
have you checked for an option in bios ?

---

### Post by chili555 on 2011-05-11
> want to get the Intel one disabled and out of the wayThen proceed as outlined in post #2.

---

### Post by stembot on 2011-05-12
> **chili555 said:**
> Then proceed as outlined in post #2.

I went with disabling the adapter in BIOS.

It's comical (not really) my new usb wireless adapter (D-Link DWA-125 as recommended here [http://ubuntuforums.org/showthread.php?t=1748744&highlight=usb+wireless+adapter](http://ubuntuforums.org/showthread.php?t=1748744&highlight=usb+wireless+adapter) ) is having minor issues but not nearly as bad as the Intel 5100 AGN.

---

