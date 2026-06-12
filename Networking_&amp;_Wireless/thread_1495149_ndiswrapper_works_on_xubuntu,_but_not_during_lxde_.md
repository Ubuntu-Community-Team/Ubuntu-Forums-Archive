---
title: "ndiswrapper works on xubuntu, but not during lxde sessions?"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by SlidingHorn on 2010-05-27
So I have a usb wireless adapter that I set up on my Xubuntu system, and it has been working great since.  The laptop that I have Xubuntu on is kind of a POS, so I wanted to try out LXDE to see how it would fare in terms of resource usage.  

When logged into an LXDE session, all of the ndiswrapper settings appear to be the same, but there are no networks listed and it doesn't connect.  Any idea what could be causing the difference?  

I'm not too bent about it, but it'd be nice to know what the problem might be.

---

### Post by SlidingHorn on 2010-05-27
Fixed the problem.  nm-applet isn't set to load with LXDE by default, so you have to change your autostart config:

```
sudo mousepad /etc/xdg/autostart/nm-applet.desktop
```
*I like mousepad for my text editor.  You can use gedit, nano or whatever else you prefer*

Once open, add the bold part below:

```
[Desktop Entry]
Name=Network Manager
Comment=Control your network connections
Icon=nm-device-wireless
Exec=nm-applet --sm-disable
Terminal=false
Type=Application
OnlyShowIn=GNOME;XFCE;**LXDE;**
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet
```

Thanks to [bchapman]("http://ubuntuforums.org/member.php?u=6884") & [keithpeter]("http://ubuntuforums.org/member.php?u=20948") for "finding" this fix.  May have been discussed prior, but I found the solution here: [http://ubuntuforums.org/showpost.php?p=7206414&postcount=3](http://ubuntuforums.org/showpost.php?p=7206414&postcount=3)

I found that it's not really necessary to copy the nm-applet.desktop from the /etc/xdg/autostart to your ~/.config/ directory...all you have to do is add the part I showed above to the main .desktop file.

Hope this helps anyone who's having the same issue!

---

### Post by Kixtosh on 2010-06-25
It may be even simpler than the solution you found. I just added the LXDE package to my Xubuntu install on an old Toshiba Portégé laptop, and once I switched to LXDE by logging off my session, and logging in with LXDE selected from the menu, I couldn't get the wireless to turn on. Nor could I find any network manager option in any of the menus. I'm using a Netgear PCMCIA wireless card, but it does not need any proprietary drivers or ndiswrapper to work, so here's how I fixed it:
 
1) Clicked on the LXDE icon on the bottom left, so that the menu pops up.
2) Selected "preferences" from that menu.
3) From the second menu list that pops up, clicked "Desktop Session Settings".
4) From the Automatically Started Applications tab, checked the box for Network Manager.
5) Rebooted, and voilà!
 
Initial impressions with LXDE are very positive.

---

