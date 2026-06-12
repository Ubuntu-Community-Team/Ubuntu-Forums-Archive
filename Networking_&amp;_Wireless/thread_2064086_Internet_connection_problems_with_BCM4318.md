---
title: "Internet connection problems with BCM4318"
date: 2012-09-28
forum: Networking &amp; Wireless
---

### Post by rockingwing on 2012-09-28
Hello there,
yesterday I installed Xubuntu on my HP Pavilion ze2000 via PXE/netboot, because the CD/DVD drive is not really working anymore.

After installing the b43 driver with "sudo apt-get install firmware-b43-installer" everything worked fine. After a reboot tho, the network-manager didn't show up anymore and I couldn't get the WLAN to show up anymore unless I plugged in a ethernet cable. 
A friendly user on #ubuntu @ Freenode then told me to try some commands right after the reboot:
```
sudo ifconfig wlan0 up
sudo service network-manager restart
```
After putting these two lines in the terminal, the wlan works absolutely fine, in fact I'm just writing from the notebook.

I just want to know if there is a permanent fix, so I don't have to use this workaround all the time.
Also, my boot sequence get's delayed by probably 2 minutes, because Xubuntu tries to find a network configuration like seen here: [http://i.imgur.com/D9t8D.jpg](http://i.imgur.com/D9t8D.jpg)

I hope anyone can come up with a fix for this :)
Kind regards,
Christopher

---

