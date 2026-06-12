---
title: "Kubuntu automatic wireless connection"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by tzcomwiz on 2006-06-10
Hi, I've used Ubuntu for a couple of months and it works beautifully. Then I decided to try Kubuntu. I got wireless set up fine but it won't connect to the network during the boot. I always have to go into Wireless Assistant after Kubuntu boots up and connect from there. This gets kind of tedious after a while. Is there a way to make the network automatically connect during boot up? I use ndiswrapper and I have it set so that ndiswrapper is automatically loaded during boot up.

Thanks a lot. :)

---

### Post by kb3hkg on 2006-06-14
I know it can be done I used to have mine do that in breezy. I believe it can be set through the GUI for different network connections

---

### Post by vagrantgeek on 2006-08-04
I am having this exact problem -- only I haven't messed with ndiswrapper.

Anyone have any ideas on how to set this? It is a bit frustrating to constantly open Wireless Assistant and connect to my network. And just like tzcomwiz when I was using Ubuntu 6.06 prior to moving to Kubuntu 6.06 it worked perfectly.

Thanks!

(first post on Ubuntu Forums!)

---

### Post by Dave Klinzman on 2006-08-04
I am not sure if this will help BUT - I have my Toshiba with a Linksys wireless card that can use the bcm43xx driver.  However, I ended up installing and using ndiswrapper and got everything to work (because that is what was working in Breezy).  

I was curious and changed everything to use the bcm43xx driver and found that I could not automatically connect to a wireless network when booting.  I had to do a "sudo iwlist eth1 scan" to get things to connect.  No amount of fiddling around would make it auto associate on boot.  Sooooo, I blacklisted the "bcm43xx" driver in the /etc/modprobe.d/blacklist file (as it was originally) and reinstalled ndiswrapper.  Voila - now everthing connects automatically on startup.

Now my story - the reason I moved to the bcm43xx driver is because I cannot connect to wireless access points other than my "home" ap.  I though the difference in drivers might make a difference.  It didn't and, in fact, made it more difficult to use my wireless connection.

Hope these comments help.  BTW, the configuration of the bcm43xx driver and its replacement by ndiswrapper is well documented in the Wiki.

---

### Post by Baruch on 2006-08-15
I had the same problem. I solved it by creating a bash script which runs on startup and does the connecting.
1) To get the commands for the script, open a console\terminal window and run```
sudo wlassistant
```if you are connected to the network, disconnect. Then click on the network to connect. After it connects, close Wireless Assistant, and look in the terminal for the commands it ran to connect. These are the commands for the batch file.
Open a new document in your home folder (I called mine wirelss-setup). add the line```
#! /bin/bash
```to the file, and after that all the commands for connecting.
My script file looks like this:```
#! /bin/bash
dhclient -r wlan0
ifconfig wlan0 up
iwconfig wlan0 mode managed channel 11 key open 3216549870 essid burstein
iwconfig wlan0 ap 00:C0:49:EE:04:F2
dhclient -q wlan0
```
Right click on the file in Konqueror, select Properties, select the Permissions tab, and mark it as executable. Select "Advaned Permissions" and mark it as "Exec" for everyone (or you could run chmod 755 ~/wireless-setup).
Now you need to open Konqueror with sudo (I put "kdesu konqueror" in the Run Command dialog), and copy your script to /etc/init.d .
The last step is to create a link to the script in rcS.d . I used #94. Open a terminal again and type```
sudo ln -s /etc/init.d/wireless-setup /etc/rcS.d/S94wireless-setup
```
That's it! (trust me, it looks more complicated then it is) :mrgreen:

---

### Post by Baruch on 2006-08-15
Deleted

---

### Post by pludov on 2006-08-17
I managed to get it working : in short, try kwifimanager...

With adept, I installed kwifimanager. Then, I configured my wifi connection with kwifimanager instead of wireless assistant.  It has some options to activate the connection when it starts. 

To have it starting on each login, I saved a new KDE session with kwifimanager started and minimized. Now when I boot my laptop, it automatically starts kwifimanager minimized. This activates the wifi connection if possible... And I have a new icon with the connection status :cool:

---

