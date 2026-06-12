---
title: "Does the Linksys WPC54GX4 work with linux"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by bobmatino17 on 2009-05-25
Well, i was reacently given an old laptop, i installed an old coppy of SUSE 8.0 on it. I was just wondering if the Linksys WPC54GX4 work with linux 2.4.x? If not plese suggest a wireless pcmcia card that does work with kernel 2.4.x that is reletively cheap. 

(if i have to burn the drivers to a cd and put them on the laptop, thats fine with me)

---

### Post by Crafty Kisses on 2009-05-25
Upon some research on this wireless card, you can actually get this card up and running it's doable, but a little complex. First you are going to need to download the legacy driver, which you can get right here: [http://sourceforge.net/projects/rt2400](http://sourceforge.net/projects/rt2400). Once you have that you need to make sure you have all your kernel sources for your current kernel. If you're not sure what kernel you have, open up a **Terminal** and run:
```
uname -r
```
Once you have made sure you have all your kernel sources installed and your ready to go with the driver install, you then need to navigate to the driver directory, I'm going to guess it's going to be saved on your desktop, so run:
```
cd /home/username/Desktop
```
Once you're at your desktop via Terminal, you can now untar the driver and start the install, so you want to run the following commands, and then the install of the driver should start and you should be on your way:
```
tar -xzvf rt2400*.tar.gz
sudo make
sudo make install
```
Then once you have done that you need to reboot, and make sure you see the module, to look for the rt2400 module, you can run the following command:
```
lsmod | grep rt2400
```
If nothing shows up for that command, then you need to manually load that module, which isn't too hard, all you have to do is run the following:
```
modprobe rt2400
```
Then from there your wireless card **should be** working, but you mentioned you had an older kernel, so I'm not sure if these instructions will work for you, but I would still try them and see if they work.

---

