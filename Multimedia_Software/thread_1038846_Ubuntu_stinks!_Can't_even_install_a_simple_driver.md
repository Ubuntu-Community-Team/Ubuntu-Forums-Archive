---
title: "Ubuntu stinks! Can't even install a simple driver"
date: 2009-01-14
forum: Multimedia Software
---

### Post by ogivol on 2009-01-14
I've worked for no joke, hours, trying to install a simple nvidia driver.

Believe me I've tried every method in the books, 
[SIZE="1"]**[SIZE="3"]please don't respond with the following:[/SIZE]**[/SIZE]

1. Hardware drivers
2. Envy/Envyng
3. Manual Install
4. Use an older/legacy driver
5. Tweaking Xorg*

*number 5 might have some fixes in it, although heres the issue:

I get the simple error "Failed to initialize Nvidia graphics device"
It's just that nondescript. I have no idea what fixes might lie out there but I could attach a my Xorg, or if someone has a working config they could post for 180.22 (Nvidia driver for 8.10) I'd gladly accept it. 

[B]
Other than that please explain to me why an OS which I've found so helpful in the past fails to install simple proprietary software[/B]

Thanks for the help and hopefully I won't just give up entirely....

---

### Post by steve8track on 2009-01-14
What do the details say when gdm crashes?  Usually for me, if there is a module update or kernel update, my nvidia driver crashes saying that the files report varying versions of the driver.  This is because I didn't use the driver Ubuntu provided me with, but installed from the nvidia site.  With each update, I have to reinstall the driver.

With all you have tried, I wonder if it could be hardware failure...

So when you install the drivers, did you uninstall the ubuntu drivers?  Logging in with the vesa drivers if you need to do something like uncheck the Restricted Drivers checkmark and use Synaptic to see what you may need to uninstall that says nvidia on it.

Also, just in case you haven't, don't forget to disable gdm while installing the nvidia drivers.

One tty1, for example:
```

sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-xxxxx.run --update
sudo /etc/init.d/gdm restart

```

Sorry if any of this is the same as the stuff you have tried.  Alernatively, have you tried the legacy drivers?  It won't even let you log in or view GDM?  Where is this error message?  In that blue screen after gdm crashes?

I hope this helps,

Steve

---

### Post by Macr237 on 2009-01-14
I have a NVIDIA 9600 GT M in my laptop and this is how I did it.
Boot Ubuntu
at the login screen select ctrl+alt+f4
Log into root
type ```
sudo /etc/init.d/gdm stop
```
Then I change directories to where the driver was located
then in my case I typed ```
sh NVIDIA-Linux-x86-180.17-pkg1.run
```
Once it had done that I then typed ```
sudo /etc/init.d/gdm start
```
Then I rebooted the computer and logged into the Ubuntu and now have shading and all the other features of the Beta driver from NVIDIA.

---

### Post by eye208 on 2009-01-14
> **ogivol said:**
> **[SIZE="3"]please don't respond with the following:[/SIZE]**

1. Hardware drivers
2. Envy/Envyng
3. Manual Install
4. Use an older/legacy driver
5. Tweaking Xorg*
6. Restricted Drivers Manager

---

