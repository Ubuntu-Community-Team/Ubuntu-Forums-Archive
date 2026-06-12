---
title: "Linksys WMP54G"
date: 2006-05-25
forum: Networking &amp; Wireless
---

### Post by Numbah51 on 2006-05-25
I got the internet working with ndiswrapper but the only problem is wlan0 doesn't automatically connect.  I'm just wondering how i make it do that.  Everytime I start ubuntu i have to run 'modprobe ndiswrapper'.  Then i have to go into the network configuration and enable wlan0.  Any help would be greatly appreciated and btw, i'm fairly new to linux so please try to put things in easy to understand terms. :)

---

### Post by DarthMandeep on 2006-05-25
Instead of having to type "modprobe ndiswrapper" every time you boot, you could add ndiswrapper to your /etc/modules file. 

You can do that by opening the terminal (or console, whatever people call it these days) and typing "sudo gedit /etc/modules" and hitting enter. That will ask you for your password and open up the /etc/modules file in the gedit text editor. Then you can just type "ndiswrapper" at the bottom and save the file.

Now, the next time you boot, the ndiswrapper module will load automatically.

---

