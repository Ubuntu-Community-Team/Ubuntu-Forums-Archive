---
title: "The Fix: for the &quot;failed to parse xorg.conf&quot; bug"
date: 2009-12-21
forum: Multimedia Software
---

### Post by cameronol on 2009-12-21
Hello, i was searching the internet to try and find a solution to my nvidia-settings problems and i found a neat little guide on
[http://awesomelinux.blogspot.com/](http://awesomelinux.blogspot.com/)

This is just a post for the community and i take no credit in making this AT ALL!, 
i only get credit for finding the article :)



Ubuntu 9.10 Karmic Nvidia-settings parse fail with xorg.conf
There is a bug in Ubuntu 9.10 Karmic with the default /etc/X11/xorg.conf involving Nvidia. If you try running 'kdesu nvidia-settings' or 'gksu nvidia-settings', then try to save with "Save to x confguration file" button, but receive the error:

    Failed to parse existing X config file '/etc/X11/xorg.conf'

I found the problem by running:

    sudo nvidia-settings 2>/dev/null

    VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
    Undefined Device "(null)" referenced by Screen "Default Screen".

    Erreur de segmentation

My default /etc/X11/xorg.conf looks like this:

    Section "Screen"
    Identifier "Default Screen"
    DefaultDepth 24
    EndSection

    Section "Module"
    Load "glx"
    EndSection

    Section "Device"
    Identifier "Default Device"
    Driver "nvidia"
    Option "NoLogo" "True"
    EndSection

To fix the problem, just remove the Section "Screen" part. The final version (before you edit it with the nvidia-settings program) should look like this:

    Section "Module"
    Load "glx"
    EndSection

    Section "Device"
    Identifier "Default Device"
    Driver "nvidia"
    Option "NoLogo" "True"
    EndSection

Posted by Sadarax  from [http://awesomelinux.blogspot.com/](http://awesomelinux.blogspot.com/)



Hope this works for most of you :),

Cameronol

Source: [http://awesomelinux.blogspot.com/2009/11/ubuntu-910-karmic-nvidia-settings-parse.html](http://awesomelinux.blogspot.com/2009/11/ubuntu-910-karmic-nvidia-settings-parse.html)
[and again, i take no credit for Sadarax's work, only for finding it]

---

### Post by cameronol on 2009-12-22
bump

---

### Post by Grannun on 2009-12-22
thank you so much, I was trying to figure this out.  This worked perfectly

---

### Post by Linuxforall on 2009-12-22
This bug only affects those who install the driver via the hardware applet. If you install the ncurses based binary driver from nvidia site, there are no issues like this with that.

Anyways to solve that error, after installing the driver and rebooting, all you do is in a terminal you type gksudo nvidia-xconfig this creates the xorg.conf file and to access and set nvidia driver type gksudo nvidia-settings 

You can then save to X if you need to set a different resolution and refresh rate.

---

### Post by foxxman on 2009-12-22
> **Linuxforall said:**
> This bug only affects those who install the driver via the hardware applet. If you install the ncurses based binary driver from nvidia site, there are no issues like this with that.

Anyways to solve that error, after installing the driver and rebooting, all you do is in a terminal you type gksudo nvidia-xconfig this creates the xorg.conf file and to access and set nvidia driver type gksudo nvidia-settings 

You can then save to X if you need to set a different resolution and refresh rate.


OHHH YOU ARE THE MAN!!!:guitar: never thought bout that.

---

