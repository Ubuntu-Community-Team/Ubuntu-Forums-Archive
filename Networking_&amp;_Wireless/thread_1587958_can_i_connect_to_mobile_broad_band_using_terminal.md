---
title: "can i connect to mobile broad band using terminal ?"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by avengerxp on 2010-10-04
hi,

is there a command (set of) which i could use to connect my USB modem while in recovery mode?

what happened?
well, i tried installing Drivers for my ATI VGA and then uninstaled them (in order to install the edgers drivers). soon after the reboot i found out my key board n mouse is not recognized in GUI.

Solution=====

i found a little work around here 
> Good. That means that you do have keyboard in that mode & there are no
seriously misconfigured packages.
It's the 'netroot' menu selection & don't use 'sudo' in that mode as you
are in a root shell.
And while there, ensure that you have established a connection (ping
ubuntu.com), and then:
# ping ubuntu.com
[if this works, then proceed with the rest]
# apt-get update
# apt-get upgrade
# apt-get install -f
# dpkg # cd /etc/X11
# ls -al xorg.*
Now take a look at the newest xorg.conf and compare against the previous:
# cat xorg.conf |more
# cat |more
Pay attention to any sections with keyboard or mouse.
While Goh's recommendation is good/correct, sometimes it's worth just
moving the xorg.conf out of the way (10.04 default is no xorg.conf). So
you might try:
[backup the existing xorg.conf first]
# cp /etc/X11/xorg.conf /etc/X11/xorg.conf-old
[now let's remove the xorg.conf]
# rm /etc/X11/xorg.conf
Now you can exit and try booting:
# reboot now
If removing the xorg.conf works, you can leave as is. If not, you can go
back to netroot (Recovery mode) and put the old one back:
# cp /etc/X11/xorg.conf-old /etc/X11/xorg.conf
# reboot now

but to use it i need to connect to the internet. i have a USB huwawi e1550.

can i connect it to the internet while am in recovery mode??

thanks in advance

---

### Post by realzippy on 2010-10-04
Try
```
pon dsl-provider
```

---

### Post by avengerxp on 2010-10-05
no it isn't working.. my version is 10.04.1 LTS. it said it cannot find a " ppa " folder path.

any options ???

and also i tried the other commands " removing the xorg, but it says theres no such file or folder...

can any one help me with this plz

---

