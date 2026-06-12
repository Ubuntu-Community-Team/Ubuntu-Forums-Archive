---
title: "slow wireless with ath9k"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by granul on 2011-04-26
I install Kubuntu 11.04 on a laptop but the wireless connexion is so slow. It use the integrate wifi ath9k driver, is there any solution?

Thank you

---

### Post by uncaspi on 2011-04-26
Try to turn off power save mode. sudo iwconfig wlan0 power off
I assume your card is wlan0.

---

### Post by granul on 2011-04-27
> **uncaspi said:**
> Try to turn off power save mode. sudo iwconfig wlan0 power off
I assume your card is wlan0.


I tried this but it does not work, I think the problem is with the driver ATH9K of my laptop integrate wifi

---

### Post by wburden on 2011-05-04
After I finished the upgrade to 11.04, my Ath9k wireless driver gave me downloads of 0.90 Mbps where I was previously getting 30.0 Mbps. The solution below worked for me in Ubuntu 11.04... Good Luck!

Enter the following Code in a terminal session:

sudo -s

echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf

reboot

---

### Post by AaronBiddle on 2011-05-04
> **wburden said:**
> After I finished the upgrade to 11.04, my Ath9k wireless driver gave me downloads of 0.90 Mbps where I was previously getting 30.0 Mbps. The solution below worked for me in Ubuntu 11.04... Good Luck!

Enter the following Code in a terminal session:

sudo -s

echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf

reboot

I have altogether about 5 hours experience in Ubuntu and not all that familiar with a unix environment. After reading at least 20 pages of people's not so successful attempts at rebuilding the driver from source I'm glad to have found a simple solution that just works. I'm back up from 50 KB/s to my usual 1.2MB/s.

Thank you Thank you Thank you!!!!!

Aaron

---

### Post by granul on 2011-05-05
Thank you it works

---

### Post by jepong on 2011-05-13
> **wburden said:**
> After I finished the upgrade to 11.04, my Ath9k wireless driver gave me downloads of 0.90 Mbps where I was previously getting 30.0 Mbps. The solution below worked for me in Ubuntu 11.04... Good Luck!

Enter the following Code in a terminal session:

sudo -s

echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf

reboot

I have to say this WORKS!!!! but wireless card still goes to sleep. I still have to try uncaspi's advice.

---

