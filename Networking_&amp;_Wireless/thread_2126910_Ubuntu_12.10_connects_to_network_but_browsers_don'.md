---
title: "Ubuntu 12.10 connects to network but browsers don't work"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by mikegaun on 2013-03-18
I have an Acer with Atheros wireless adapter 9485. Originally when I installed Ubuntu 12.04 I had to turn off hardware encryption so wireless adapter worked then it work fine. However my Kodak 6100 didn't work with scanner so I upgraded to 12.10 and scanner worked. Now I can't get out to the internet using Firefox or Chrome. Using both wire and wireless I can connect but both browsers don't work. tried turning off encryption again but doesn't work.
I tried alot of things suggested in forums to no avail. Frustrated. Fairly new to command line but have some computer skills. Any ideas?

---

### Post by wildmanne39 on 2013-03-18
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by mikegaun on 2013-03-18
The machine I'm having the problem on connects to the network with wired and wireless but browsers don't work.  I typed it in manually and it said couldn't reconcile dl.dropbox.com because there was no connection.

---

### Post by mikegaun on 2013-03-19
reinstall ubuntu 12.10 and it works.  I think something happen when I update thru software center.  Resolved.

---

