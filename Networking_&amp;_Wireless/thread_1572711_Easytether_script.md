---
title: "Easytether script"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by wildman4god on 2010-09-11
For those of you who don't know, easytether is an app for android phones that allows you to tether it to a computer via usb without root, now it requires a client on the pc to make the connection and while they support ubuntu, the program is cli and a little tedious to startup and requires the terminal to remain open, so in another thread they made the two scripts (the connection process requires the first terminal remain open so a second is needed for the next step) I managed to combined them into one script that doesn't need an open terminal and can request your password via gksu (that little box that pops open when ever you do an administrative task) and it can be ran as autorun from the root directory of your phone's sd card so it auto connects upon plugin it in to your computer. There are a couple of issues with it though, first since it doesn't open a terminal there is no way to invoke the disconnect command before you unplug the phone, second (and this relates to the first) I would like to use zenity to give it a simple gui but as of now I don't know how to use it, I am trying to learn but if anyone wants to jump in and help then by all means.

also this requires the easytether drivers to be installed:
[http://www.mobile-stream.com/easytether/drivers.html](http://www.mobile-stream.com/easytether/drivers.html)

---

### Post by gzarkadas on 2010-09-11
I don't have such a device, so I won't be able to dig through this. However, a first attempt could be to show a graphical terminal with dhclient progress; zenity is not appropriate here because you are not in control of the dhclient output. 

```

#!/bin/bash
easytether connect
gksu -- gnome-terminal --title='EasyTether' --command="dhclient easytether0"

```

This will probably need some modification for KDE, but I don't use it to know the equivalent.

---

### Post by wildman4god on 2010-09-11
well actually it think the extra code should go on the first command as that is the one you close the connection from, the second command only needs to run one and then you can close the terminal, but I get your point and thanks for the feed back, also if I am having issues getting it to run as an autorun from the root of my phone even though auto run prompt detects it and gives me the option to run it, it doesn't always run. but runs fine everytime from the desktop, is there away to configure the script to run when the device is automatically connected. I'm not that good with terminal and this is my first attempt at a script.

edit: I just found that the command to disconnect the easytether client (ctrl+c) actually had the same effect of closing the terminal window, and even with it running in the background without a terminal (like my script does) just unplugging the phone doesn't cause any issues, so controlling it is a non-issue, so now I just need help with the auto run.

---

### Post by gzarkadas on 2010-09-11
You may need to write a udev rule to make this reliable. There is a nice tutorial on the subject in [this thread]("http://ubuntuforums.org/showthread.php?t=168221"). You could also make the rule to run programs on connect/disconnect, per [this guide]("http://reactivated.net/writing_udev_rules.html#external-run") (linked from the tutorial thread). Unfortunately, missing the device I cannot experiment with this, but if you manage to make something that is at least semi-functional we could then shape it better.

---

### Post by Limon160 on 2010-10-23
I just put the second line in a new x term like this, hope it helps

#!/bin/sh
#easytether launcher
xterm -e easytether connect
gksu -- gnome-terminal --title='EasyTether' --command="dhclient easytether0"

---

### Post by Limon160 on 2010-10-23
I forgot the " & " on the first line, Along with some explanation.

The first command line is is locking the terminal, so I'm pushing it into another terminal, the "&" allows this terminal to continue to the next line of code. It will ask for you password, the the first terminal will close, leaving the second terminal as long as the connection is up.

This probable isn't the best way, but I am pretty new to linux, and it does work. with a shortcut on the desktop, It looks nice and clean too.

#!/bin/sh
#easytether launcher
xterm -e easytether connect &
gksu -- gnome-terminal --title='EasyTether' --command="dhclient easytether0"

---

### Post by TruckerDJ on 2011-04-07
Any ideas, suggestions on how to remove the easytether drivers from Ubuntu? I am no longer interested in the program and would really like to just get the USB mass storage mode back.

Thanks DJ

---

### Post by gzarkadas on 2011-04-07
> **TruckerDJ said:**
> Any ideas, suggestions on how to remove the easytether drivers from Ubuntu? I am no longer interested in the program and would really like to just get the USB mass storage mode back.

Thanks DJ

Since it was installed as a .deb file, from what I can see in their site, it is just as easy as doing a ```
sudo apt-get purge easytether
``` inside a terminal window.

If this does not work for any reason, then you can manually remove the package files. Below are the commands to remove the files that an [Ubuntu 10.4+ i386 easytether package]("http://www.mobile-stream.com/beta/easytether_0.7.1-3_i386.deb") would install in a system: 
(**NOTE:** If you go by that way, you must verify that the contents of the installed version of the package are the same with the ones shown below, before proceeding to rm.)

```
sudo rm /lib/udev/rules.d/65-easytether.rules
sudo rm /usr/bin/easytether
sudo rm -R /usr/share/doc/easytether/
```

---

### Post by yankeevader on 2012-08-12
Was a fix found to make this run automatically?
Mine has a network manager so the "dhclient easytether0" in a new terminal is not needed.
However I get an error that it cant find the program to run when I plug the phone in and hit ok when the box pops up that says
"This medium contains software intended to be automatically started. Would you like to run it?"
I would really like to be able to get it working properly. any help would be greatly appreciated.
Thanks

---

