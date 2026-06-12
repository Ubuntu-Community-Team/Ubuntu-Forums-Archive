---
title: "Configuring Ati X700 video card"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by coronaronin on 2006-06-03
Hey all,

First off I'd like to introduce myself as a new linux user, ive fiddled around with fedora and redhat, but now I am using ubuntu. Ive looked at alot of forums that have taught me alot but now I seem to be at an impass. I have a widescreen monitor that has max resolution of 1680 x 1050, and im trying to get it to that resolution as my monitor now is set for 1024x768 (I have a widescreen monitor so its kinda weird how it would want to put that resolution by defualt). When I try and set the display settings to 1680x1050, my monitor flashes and then my desktop looks all screwey, like it's a picasso painting of my original monitor. I have installed my ATI drivers, but the install guide said I needed to do some configuring, by following this step: "7.  Launch the Terminal Application/Window and run  /usr/X11R6/bin/aticonfig --initial to configure the driver." When I do so, both as regular user and as root, it says "no such file or directory."

After viewing these forums a bit I read a wiki on how to install this driver, found at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually)
but I do not know how to manually edit xorg.conf as I do not have access privlidges and I do not know how to log on as root. I have viewed the xorg.conf, and it has standard resolutions set and it has no mention of the resolutions my monitor should be at. I have set up a root password from the command line, but when I try and enter it from the login screen it says the administrator can't login from here. 

Can anyone give me some suggestions? It would be super helpful.

Thanks!!!!!

By the way, the ATI install guide is below in case I'm dumb and forgot to do something that makes it easy. 


[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.25.18-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.25.18-inst.html)

---

### Post by Lux Perpetua on 2006-06-03
[QUOTE=coronaronin]I have installed my ATI drivers, but the install guide said I needed to do some configuring, by following this step: "7.  Launch the Terminal Application/Window and run  /usr/X11R6/bin/aticonfig --initial to configure the driver." When I do so, both as regular user and as root, it says "no such file or directory."[/QUOTE]That probably means your fglrx installation didn't succeed. However, you don't need that driver if all you want to do is fix your resolution. To execute a single command as a superuser (root), you can use "sudo": [color=green]sudo aticonfig --initial[/color]. To execute a gnome application (like gedit) as root, you can use "gksudo": [color=green]gksudo gedit /etc/X11/xorg.conf[/color]. Finally, to *become* root, use the command [color=green]sudo su[/color]. I believe you can also fix your resolution by running [color=green]sudo dpkg-reconfigure xserver-xorg[/color].

---

### Post by coronaronin on 2006-06-06
hey, I followed those steps and redid my xorg config...but when I restarted my computer after it boots into ubuntu the screen goes black and nothing happens. It just stays black, I can't get to my login screen. 

All I did with the xorg config was follow the menu's and change my resolution to 1680x1050 at 75hz (which is the resolution this monitor should be at).

Now what should I do to get back to my operating system without reformatting and reinstalling the whole damn thing?

Thanks,

CR

---

### Post by titus1950 on 2006-06-06
If you reinstall,follow this guide for ubuntu Dapper ati drivers...

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually)
it is guided to Ubuntu.

---

