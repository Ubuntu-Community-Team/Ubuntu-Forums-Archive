---
title: "How to get Dual screens Gutsy ATI proprietory drivers"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by JulesBl on 2008-01-18
Hi

Managed to get my dual screen setup going under gutsy with an ati x1300 card and the proprietory drivers.

Have a look here for loads of advice
[http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)
and here for gutsy specific stuff
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Additional_configure_with_aticonfig_tool](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Additional_configure_with_aticonfig_tool)

1. Ensure you have the fglrx ati proprietory drivers installed and configured using the restricted drivers manager.

2. Make sure you have aticonfig installed

3. backup your xorg.conf file to keep your current config
sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.backup

4. Issue these two commands
sudo aticonfig --initial=dual-head --screen-layout=right
sudo aticonfig --dtop=horizontal --overlay-on=1

5. Restart your machine

and voila you should have both screens working.

The only problem I have is the the screen on the vga cable looks a little washed out, the greys are far too pale.
aticonfig --query-monitor
Comes back with
  Connected monitors: crt1, tmds1
  Enabled monitors: crt1, tmds1
which seems a little strange as the monitors are identical Samsung 930bf

Jules

---

