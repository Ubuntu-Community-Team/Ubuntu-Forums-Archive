---
title: "wireless problem"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by phoenixfire900 on 2010-01-05
hi i just installed ubuntu 9.10 and i added my 2WIRE512 router to the wireless networks and enabled it checked boxes that said detect automatically and available to all users.  when i restart the computer it will not connect.  i need fast response please!

---

### Post by bkratz on 2010-01-05
> **phoenixfire900 said:**
> hi i just installed ubuntu 9.10 and i added my 2WIRE512 router to the wireless networks and enabled it checked boxes that said detect automatically and available to all users.  when i restart the computer it will not connect.  i need fast response please!

Perhaps it is just me, but I don't really understand what you are asking (perhaps that is why no one has responded).  Are the check boxes referred to on the wireless router or in the network manager function in Ubuntu.

If you go to Applications>>Accessories>>Terminal and type in 
lspci -nn  (that is LSPCI in lowercase) and at least we will know what wireless card you have, and a direction to proceed.

---

### Post by phoenixfire900 on 2010-01-05
i have broadcom 802.11g network adapter, broadcom netlink (TM) fast ethernet, and microsoft virtual wifi miniport adapter.   by the way i am dual booting with windows 7.  I tried to look for drivers but it said i had no persistent drivers.

---

### Post by bkratz on 2010-01-05
> **phoenixfire900 said:**
> i have broadcom 802.11g network adapter, broadcom netlink (TM) fast ethernet, and microsoft virtual wifi miniport adapter.   by the way i am dual booting with windows 7.  I tried to look for drivers but it said i had no persistent drivers.

Did the lspci command tell you which one you have, would have been in the format

BCM43XX   (most likely)

---

### Post by phoenixfire900 on 2010-01-05
yes that is the one

---

### Post by bkratz on 2010-01-05
> **phoenixfire900 said:**
> yes that is the one



No, you need to fill in the XX!  Like BCM4312

---

### Post by phoenixfire900 on 2010-01-05
good guess cause it is 4312

---

### Post by bkratz on 2010-01-05
> **phoenixfire900 said:**
> good guess cause it is 4312

You are in luck, there is a very good description of it's use here

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by phoenixfire900 on 2010-01-05
Thanks alot!!

---

### Post by bkratz on 2010-01-05
> **phoenixfire900 said:**
> Thanks alot!!

If this works for you be sure and come back and let us know and also use the thread tools above to mark the thread [solved] in case it helps someone else.

---

### Post by phoenixfire900 on 2010-01-05
so it recognized my wireless and connected the only thing now is that firefox wont go to the internet

---

### Post by bkratz on 2010-01-05
I assume that since you have a wired connection you have used Firefox on it so it is enabled and you don't have a check in "work-offline", also assuming that your AP has wireless turned on to accept connections, and that you have setup the connection correctly for the wireless. Are you using encryption? For now i would turn it off until we have a good connection.

Also in the terminal can you ping something, like google.

ping google.com

if so, can you ping by IP address

ping 74.125.95.105

Also please copy and paste the output of the following commands

sudo iwlist scan     
sudo lshw -C network   (that is LSHW in  lowercase)

When you do the sudo iwlist scan command do you see your AP?

---

### Post by phoenixfire900 on 2010-01-06
i got it nevermind thanks anyways

---

### Post by bkratz on 2010-01-06
Could you expand on what you found? Also mark the thread solved in the thread tools to help others.

---

