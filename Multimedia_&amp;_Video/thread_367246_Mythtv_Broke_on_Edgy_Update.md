---
title: "Mythtv Broke on Edgy Update?"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by tshannon on 2007-02-21
I regularly install the updates to Edgy on my Mythbox system.  After doing the required reboot after this last update, MythTv doesn't seem to work properly.

First of all, my remote stopped working, so I tried to startup LIRC.

```
sudo /etc/init.d/lirc start
```

and I got this:

```
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.
```

Also, everything seems to be working fine in the mythtv frontend, except for my scheduled recordings.  It says I have none, and if I try to add any new recordings, it doesn't save the settings.

I'm far from a linux expert, and I can't find anything in the forums here or anywhere else.

Your help is much appreciated.


Also, is there any history of what updates were actually applied?  I tend to just blindly install all the recommended updates.  Can I see what's been updated recently?

---

### Post by newlinux on 2007-02-21
after kernel updates you need to rebuild lirc. [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

i don't know what the problem is with your scheduled recordings. I don't upgrade my mythboxes unless there is a real reason to (like a feature I must have), And when I do that I expect it will be a process of making some things work again. I suggest that if your mythbox is working fine and you use it frequently (like I do) don't upgrade unless there is a specific reason to do so.

---

### Post by tshannon on 2007-02-22
LIRC started up again with the rebuild, but it's still not working in the mythtv frontend.

When I try to watch live TV, it says all the inputs are in use, but nothing is recording.  When I check my system status, I finally get the message that the mythbackend has stopped responding.  

When I try to restart the backend I get this:

```
2007-02-21 23:07:01.741 Using runtime prefix = /usr
2007-02-21 23:07:01.771 New DB connection, total: 1
2007-02-21 23:07:01.777 Connected to database 'mythconverg' at host: localhost
2007-02-21 23:07:01.781 Current Schema Version: 1160
Starting up as the master server.
2007-02-21 23:07:01.788 New DB connection, total: 2
2007-02-21 23:07:01.789 Connected to database 'mythconverg' at host: localhost
2007-02-21 23:07:01.791 EITHelper: localtime offset -6:00:00
2007-02-21 23:07:01.793 Channel(/dev/video0)::Open(): Can't open video device, error "No such file or directory"
2007-02-21 23:07:11.805 New DB connection, total: 3
2007-02-21 23:07:11.806 Connected to database 'mythconverg' at host: localhost

```

I had this system working perfectly, and had all the functionality I wanted.  I'd hate to lose it all and have to start over.

---

### Post by fenian on 2007-02-22
If you use the IVTV driver you need to reinstall the driver by running these commands...
> 
sudo m-a update,prepare
sudo m-a a-i ivtv
sudo depmod -a 

you may also have to run
> 
sudo modprobe ivtv

I'm not 100% sure on the last one but I dont think it would hurt anything.

---

### Post by jlr4u on 2007-02-22
I had a similiar problem and had to repair the database for mythconverg in the MYSQL database. How I have resolved this is by logging into Mysql using phpmyadmin - just bring up firefox and type [http://localhost](http://localhost) in the address bar (hopefully you installed phpmyadmin when you installed MythTV) and login as root.

Next, select mythconverg from the dropdown list in the left hand pane window under databases. Scroll down and use the "select all" to add a check mark in all the database boxes. From the drop down box, select "repair table program" and then once that has completed go back into the drop down box and select "optimize tables." The repair tables program may take a few moments to complete so give it some time. Once it has completed, you should be able to scroll the database to see the results - it should have an ok after each database (you may have to arrow right to see them. Once you have completed this process, logout and try recording a new show.

---

### Post by tshannon on 2007-02-22
Thanks for all your help.

Fenian's suggestion is what fixed it for me.

---

### Post by thelaughingman on 2007-03-01
What is the 'm-a' command?  I can't find it with 'which', do I have to install it with apt-get?

---

### Post by superm1 on 2007-03-01
m-a is the same as module-assistant

```
sudo apt-get install module-assistant
```

---

### Post by thelaughingman on 2007-03-01
Thank you, superm1.  I was having the same problems as tshannon.
My lirc is still messed up, but ill fix that later.

---

### Post by bhamail on 2007-03-06
Bam! Fenian's suggestion fixed it for me too. Thanks!

---

