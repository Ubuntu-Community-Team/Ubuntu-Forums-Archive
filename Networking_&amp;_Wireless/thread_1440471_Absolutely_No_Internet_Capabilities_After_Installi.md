---
title: "Absolutely No Internet Capabilities After Installing 9.1"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by jgreen18 on 2010-03-27
I recently installed Ubuntu 9.10 onto an older laptop for my boss. However, after installation I lost all internet capabilities... both through wireless and ethernet connections. There is zero indication that Ubuntu is picking up any wireless connections at all and when I plugged into an ethernet connection Ubuntu acts as if it is trying to connect, however unsuccessfully. I have eliminated the internet connection as my problem because I was able to connect with my laptop running 9.10 with no problem. I have searched and searched everywhere for fixes to this problem however 99% of them need an internet connection to install the required firmware and drivers... is there any OFFLINE solution out there???

The computer is a Compaq Presario 2200 with a Boradcom Corp BCM4306 802.11b/g Wireless LAN Controller

---

### Post by labinnsw on 2010-04-03
When using a live CD, are you able to connect to the internet?

If so, try making a smaller partition and install 9.10 again on this. If that works delete the old partition and increase the size of the new one. If it does not work use the live CD to download .debs or tarballs of the required software and install them off line.

---

### Post by Iowan on 2010-04-04
**sudo lshw -C network** will probably show "Unclaimed" for the wireless, but it'd be useful to see if the wired card has driver/alias, etc...
[This]("http://ubuntuforums.org/showpost.php?p=9076058&postcount=5") post has a couple of links for BCM4312.
[This]("http://ubuntuforums.org/showthread.php?t=939658") one mentions the BCM4306 - but suggests it should be supported out-of-the-box in Karmic...
Yet [another]("http://ubuntuforums.org/showthread.php?t=1368699").

---

### Post by mcoleman44 on 2010-04-04
It probably is supported out of the box. You just need to do an update.
sudo apt-get update
sudo apt-get upgrade
sudo reboot
After you log back in go to system>admin>hardware drivers and install your wireless driver.

missed the part about no Ethernet connection

---

### Post by NZJohn on 2010-04-04
I have the same problem since install... NO INTERNET, tried loading a program that checks for probs but it shut down my keyboard and I couldn't get it to do a thorough test because of not being able to use the password ...tried loading drivers but even this is complicated. It shouldn't be so difficult surely? Someone else must've got an Acer 3050 working with 9.10 - the troubleshooting advice assumes you have some skills with terminal.
Newbs are screwed ...my laptop is not i-net functional. 
WTF? Somewhere there must be a comprehensive help for this 'no internet problem' as it seems VERY common?
Sorry I wasn't any help. Your drivers are not functional I suppose.
Good luck mate.

---

