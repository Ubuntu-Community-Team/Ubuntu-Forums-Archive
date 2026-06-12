---
title: "NetworkManager is not running/disabled on boot? LXDE"
date: 2013-01-23
forum: Networking &amp; Wireless
---

### Post by aem0512 on 2013-01-23
I just did a minimal install of ubuntu 12.04 with lxde but I can't figure out how to get the NetworkManager working on boot. If I don't have ethernet connected at boot time (suppose I'd like to use wireless...) then I get "waiting for network configuration.." and it takes forever to boot. Then I find that I have to do:
sudo service network-manager restart 

in order to get it working.

I've got the correct box checked in desktop session settings and I've tried to add the program to ~/.config/autostart but nothing works. The applet in the system tray loads up just fine, but it just says it's not running/disabled.

How can I fix this?

Bingo, found the solution:
[http://ubuntuforums.org/showpost.php?p=11835741&postcount=448](http://ubuntuforums.org/showpost.php?p=11835741&postcount=448)

---

