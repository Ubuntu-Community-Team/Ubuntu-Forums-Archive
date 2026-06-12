---
title: "WICD, no wifi in Ubuntu, wifi works in Arch Linux, triple boot laptop"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by Dtfa on 2010-02-22
Hello all,

My System has atheros AR5001 WIFI. In Linux, the MADWIFI'S ath5k drives internet connectivity via WICD. My system triple boots Vista, Ubuntu & Arch Linux. WIFI works in Vista (vista is OEM) & ARch Linux. To enable WIFI in Linux, I followed this [thread:  ]("http://wiki.archlinux.org/index.php/Wicd")
In short: The following works in &quot;Arch Linux&quot; with the Gnome Desktop and Gnome login manager.
# /etc/rc.d/network stop
# /etc/rc.d/dhcdbd stop
# /etc/rc.d/networkmanager stop

# nano /etc/rc.conf

Blacklist via prefixing with a ! 
INTERFACES=(!eth0 !wlan0)

Blacklist via via prefixing with a ! and add the bolded
DAEMONS=(syslog-ng **dbus** !network !dhcdbd !networkmanager **wicd** ...)

# gpasswd -a USERNAME network

# /etc/rc.d/hal start

log out login restart twice shutdown once then all is golden.

How on earth am I supposed to make the system work in Ubuntu.
>
[B] Note: In Ubuntu I use Fluxbox, don't know if that matters. Although sometimes I session switch back to Gnome
>
[/B] I've been through 25 forum pages and a lot of google. Apparently, according to Google, WICD works great, wont install, is difficult to use with VPN or it wont auto-start. It would seem that I am the only person with my particular problem.
I've been at a standstill with this :confused: ](*,) F#$-- M$#%^7u 
Help would be appreciated and** thanks** in advance.
Postscript:

---

### Post by Dtfa on 2010-02-23
Bump

---

### Post by 2hot6ft2 on 2010-02-23
From what I've read there are a pair of brackets "[]" in one of the config files for wicd that needs to be deleted.

I tried it and it wouldn't work for me so I went back to network-manager. That was before hearing about the brackets.

EDIT: Here it is:
> **jruberto said:**
> You'll probably need to sudo edit the config file as it is a system config file.

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

If you aren't familiar with the console text editors, nano is probably the "easiest", at least the help is on the screen when you run it.  go out to a console and
```
 sudo nano /etc/wicd/wired-settings.conf
```find a line that is just 
```
 []
```and delete it. If there isn't a line that looks like that, then that isn't the problem, and i'm sorry.  Best of luck.
From this thread:

[Internet Stopped Working (Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1407885")

---

### Post by Dtfa on 2010-02-24
> **2hot6ft2 said:**
> From what I've read there are a pair of brackets "[]" in one of the config files for wicd that needs to be deleted.

I tried it and it wouldn't work for me so I went back to network-manager. That was before hearing about the brackets.

EDIT: Here it is:

From this thread:

[Internet Stopped Working (Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1407885")

[COLOR=Red]Perhaps it's unrelated, but after applying the above, I lost WICD in Fluxbox. Restoring from the backup copy of the WICD.conf file did noy resolve the issue.[/COLOR]
You' re correct about NANO. I never use vi not evern when I edit my visudo file. I do not remember, nor do I want to remember the name of the other text editor. Of course Gedit & Kedit are awesome!
A sincere thanks for the effort. However, there was no such line. I did view the WICD wireless config file for the first time, and it's blank. 
>
I now believe that this the problem. Do you or does anyone know of good documentation for the configuration of WICD wireless,conf file.

---

