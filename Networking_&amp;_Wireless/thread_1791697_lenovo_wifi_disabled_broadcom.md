---
title: "lenovo wifi disabled broadcom"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by amalnath on 2011-06-27
hi, 
  Im using natty in lenovo b460. After installation was not able to connect to wifi. Ethernet is working alright.
So searched for additional drivers and installed the Broadcom 43xx drivers. After restart the network applet says the wireless is disabled by hardware switch, even after it is switched on/off several times.
Lenovo B460
kernel:**2.6.38-8-generic 32-bit**
**Broadcom** Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
ubuntu 11.04

tried "***sudo rfkill list***".
The output is
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
6: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no..
any help is appreciated....:sad:

---

### Post by chili555 on 2011-06-27
Please open a terminal and do:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all
```Are you now able to use the wireless? If so, we can tweak one file and make it persistent.

---

### Post by Owenoen on 2011-10-09
> **chili555 said:**
> Please open a terminal and do:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all
```Are you now able to use the wireless? If so, we can tweak one file and make it persistent.
hi, chili555, your solution worked on my laptop. I am using the same lenovo b460 and had the same prolem. You helped me. Thank you so much!:popcorn:

---

### Post by chili555 on 2011-10-09
> **Owenoen said:**
> hi, chili555, your solution worked on my laptop. I am using the same lenovo b460 and had the same prolem. You helped me. Thank you so much!:popcorn:In order to make it persist, please do:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Glad it's working!

---

### Post by sunbird1989 on 2012-04-15
> **chili555 said:**
> Please open a terminal and do:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all
```Are you now able to use the wireless? If so, we can tweak one file and make it persistent.

Thank you very much.With your help,i can use ubuntu as well.&#35874;&#35874;&#65281;&#65281;&#65281;&#65281;:p

---

### Post by chili555 on 2012-04-15
> **sunbird1989 said:**
> Thank you very much.With your help,i can use ubuntu as well.&#35874;&#35874;&#65281;&#65281;&#65281;&#65281;:pIf you'd like to make it permanent, please do:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Glad it's working!

---

