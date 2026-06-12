---
title: "linksys wmp54g and ndiswrapper on 9.04"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by dextruction on 2009-08-02
As it can be seen I am a nublet but I am supremely enjoying my first taste of ubuntu, right now i'm not entirely sure that ndiswrapper is installed right on my system, I do have the driver files from the Disk on my system in a folder on the desktop.  When i enter command

ndiswrapper -i bcmwl5.inf this is my output

dextruction@dextruction-desktop:~$ ndiswrapper -i bcmwl5.inf
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

unfortunately i don't know enough to move through the system and figure out what is going on, let alone how to figure out the outputs and deduce my main issue, and help will be greatly appreciated. 
so far this has held me up for about a week with my system direct connected in the kitchen.  So this for my wireless adapter on my desktop.  again any help is greatly appreciated. thank you

---

### Post by Crafty Kisses on 2009-08-02
Save the the file to your desktop, it looks like it's looking in the wrong directory, so if you're still in that directory type the following:
```
cd
```
Then put the .inf file on your desktop and run:
```
cd /home/username/Desktop
```
Then from there you can run:
```
ndiswrapper -i
```

---

### Post by dextruction on 2009-08-03
i've got the .inf .sys and .cat on the desktop, when i run 

ndiswrapper -i   its still the same results, its telling me there is no such file or directory 
in the executable text file ndiswrapper 1.9 in line 219.

i don't know what that means, but i cand cd to it in /usr/sbin  
and when i'm in the desktop and run ndiswrapper -i thats all it will give me

couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

maybe something is up with ndiswrapper 1.9 i don't know how to figure out? thanks for the help though, XD

---

### Post by dextruction on 2009-08-03
I'm gonna make sure i've got ndiswrapper and everything it needs properly installed and set up, it is overwhelmingly possible and likely that i am at fault, i just don't know where my mistake was made, so i'm going to continue trying.  
I very much appreciate any new ideas or solutions and thank you for helping teh nube XD

---

### Post by dextruction on 2009-08-03
Nm i made a rooky mistake, forgot to capitalize. thank you again for the help

---

### Post by Crafty Kisses on 2009-08-03
Did you actually get it to work? Yeah I forgot to mention it's case sensitive.

---

### Post by dextruction on 2009-08-03
yeah it did install the driver, 
although i am very nube cake now i don't know how to get my card active cause i still have no connection on wireless, not sure what to do but i'll look around iz new problem now
i should have it from here, thank you for the help.

---

### Post by Crafty Kisses on 2009-08-03
Alright, if you have any questions let me know.

---

### Post by calbaker on 2009-08-09
I've been having the same problem.  I installed the bcml5.inf driver using ndiswrapper, and it's not showing up when I try to look at my network connections.  Is it possible this is not a "known-to-work" driver?  Any help would be appreciated.

---

### Post by calbaker on 2009-08-09
When I use the command ndiswrapper -l, I get a warning:
Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.  I tried the command sudo cp /etc/modprobe.conf /etc/modprobe.d.  This copied the file to the new location, but it did not solve the warning.  Also, the PCI card is still not showing up.

---

### Post by calbaker on 2009-08-09
I connected my desktop to my LAN with an ethernet cable, and it automatically found the correct driver.  Once I installed it, everything worked fine on the Wireless network.

---

