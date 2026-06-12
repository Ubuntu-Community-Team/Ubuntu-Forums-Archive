---
title: "installing Nvidia Linux drivers"
date: 2009-06-17
forum: Multimedia Software
---

### Post by raymondvillain on 2009-06-17
Trying to get GEForce 8400 GS nvidia graphics card to work.

I downloaded NVIDIA-Linux-x86-185.18.14-pkg1.run from the nvidia web site.  When I try to install it, I get a message "You appear to be running an X server; please exit X before Installing..."

How does one exit X?  I am clueless.

---

### Post by overdrank on 2009-06-17
> **raymondvillain said:**
> Trying to get GEForce 8400 GS nvidia graphics card to work.

I downloaded NVIDIA-Linux-x86-185.18.14-pkg1.run from the nvidia web site.  When I try to install it, I get a message "You appear to be running an X server; please exit X before Installing..."

How does one exit X?  I am clueless.

Hi and you will need to stop x 
```
sudo /etc/init.d/gdm stop
```

---

### Post by raymondvillain on 2009-06-17
Well, overdrank, your command

sudo /etc/init.d/gdm stop

really stopped everything.  I couldn't figure out what to do with the results, though.  I didn't even have a cursor.

When I type (in a terminal window)

sudo sh NVIDIA-Linux-x86-185.18-pkg1.run

I get a message box that says

ERROR: You appear to be running an X server; please exit X before installing.

Could you briefly explain what to do?  I mean, if I use your first suggestion, I don't have a command prompt at which to type the instructions.  There must be a way around all of this.  I'm pretty green with command line stuff.

Thanks for your suggestions.

---

### Post by overdrank on 2009-06-17
Yea sorry for being brief. Using the ctrl, alt, F1 keys this will bring you the command line and log in. Then ```
sudo /etc/init.d/gdm stop
``` Before you run the nvidia file you will need to cd change directory to where you downloaded the file. If it is on your desktop the ```
cd ~/Desktop
```

then run the sh nvidia driver. ```
sudo sh NVIDIA-Linux-x86_64-185.19-pkg2.run
``` make sure it is your name of file.
To get back to the desktop you can just change the stop part of the command to start. :)
Also you may see a error to install build-essential first.
New thread [here]("http://ubuntuforums.org/showthread.php?p=7478788#post7478788")

---

