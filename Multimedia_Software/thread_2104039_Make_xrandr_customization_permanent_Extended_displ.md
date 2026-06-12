---
title: "Make xrandr customization permanent? Extended display not dual."
date: 2013-01-11
forum: Multimedia Software
---

### Post by abisdad on 2013-01-11
Hi, 

FYI people! :-)

I had the problem of wanting an extended display on my new LXDE box, (not a dual clone), found the correct command, but couldn't make it permanent.

The correct command was:

    xrandr --output VGA-0 --right-of DVI-0

Found some pointers here:
[http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent/240168#240168]("http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent/240168#240168")
but all these methods seemed too hard/not the right way to do it.



I eventually found this: [http://www.sudo-juice.com/change-lxde-screen-resolution-ubuntu-lubuntu/]("http://www.sudo-juice.com/change-lxde-screen-resolution-ubuntu-lubuntu/")

that worked a treat, but used gedit instead, so from the command line:

    sudo gedit /etc/xdg/lxsession/LXDE/autostart

then in gedit added the line at the end of autostart file with an @ symbol at the start:

    @xrandr --output VGA-0 --right-of DVI-0

Hope that helps and thank you to sudo-juice.

Rob.

PS Note the double "-" in the xrandr command "--" (didn't show up too clearly on my screen).

---

