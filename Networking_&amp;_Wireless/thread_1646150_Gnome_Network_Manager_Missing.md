---
title: "Gnome Network Manager Missing"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by Bobsieflopsie on 2010-12-15
I had this problem so many times and finally found an easy way to fix it ! :p

First make sure if your using wireless to install wicd to maintain internet connection. (To download network-manager package)

Then sudo apt-get remove network-manager

Then sudo (Editor of your choice example = gedit) /etc/network/interfaces

Then remove all the lines and save the blank file. (make a copy of interfaces just in case)

Then sudo apt-get install network-manager

Reboot

And then from terminal : nm-applet



And your missing network manager should come back !

---

### Post by woodmaster on 2011-02-28
> **Bobsieflopsie said:**
> I had this problem so many times and finally found an easy way to fix it ! :p

First make sure if your using wireless to install wicd to maintain internet connection. (To download network-manager package)

Then sudo apt-get remove network-manager

Then sudo (Editor of your choice example = gedit) /etc/network/interfaces

Then remove all the lines and save the blank file. (make a copy of interfaces just in case)

Then sudo apt-get install network-manager

Reboot

And then from terminal : nm-applet



And your missing network manager should come back !
didn't work for me :-(  
```
Reboot

And then from terminal : nm-applet
```
gives Error: an instance of network manager is already running.

---

### Post by Bobsieflopsie on 2011-02-28
> **woodmaster said:**
> didn't work for me :-(  
```
Reboot

And then from terminal : nm-applet
```gives Error: an instance of network manager is already running.

Did you remove it first ? 

Also you can use sudo killall nm-applet and then nm-applet :)

---

### Post by woodmaster on 2011-02-28
> **Bobsieflopsie said:**
> Did you remove it first ? 

Also you can use sudo killall nm-applet and then nm-applet :)
yes, i followed the code u posted 2 remove it first.  sudo killall then restart & it still doesn't show in the indicator bar

---

### Post by Bobsieflopsie on 2011-02-28
> **woodmaster said:**
> yes, i followed the code u posted 2 remove it first.  sudo killall then restart & it still doesn't show in the indicator bar

Also cleaned the file ? 

Then sudo (Editor of your choice example = gedit) /etc/network/interfaces

That's so strange :confused: it worked perfect on my install i did it like 10 times.

But with the new release 10.10 never had any problems maybe just upgrade ?

---

### Post by woodmaster on 2011-02-28
yes I had cleaned the file with gedit.  My system is fully up to date install of 10.10

---

### Post by Bobsieflopsie on 2011-02-28
> **woodmaster said:**
> yes I had cleaned the file with gedit.  My system is fully up to date install of 10.10

Hmm that's so strange i only had this on 10.04 never on 10.10 :confused:

Sorry i can't think of anything else that could make it work :(

---

### Post by dineshs on 2011-03-01
Rightclick on top panel-add to panel-select notification area - click add

---

### Post by woodmaster on 2011-03-01
notification area is there, just not the network manager applet.  all the others are still there

---

### Post by dineshs on 2011-03-03
Please follow step-1 and 2[ here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")
Or run
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
set *managed=true*  and restart

---

### Post by woodmaster on 2011-03-04
> **dineshs said:**
> Please follow step-1 and 2[ here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")
Or run
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```set *managed=true*  and restart
didn't change anything

---

### Post by woodmaster on 2011-03-13
bump...i can manage it from the command line, but i like to have gui access to the settings.  Just easier, especially when I'm explaining things to my family over the phone.

---

