---
title: "nm-applet invisible (no icon)"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by mp035 on 2011-06-11
Hello All,

I have xubuntu installed on an asus eee pc r101d.  Everything except the wifi switch (Fn-F2) was working.  Whilst at an airport waiting to get on a plane, I decided to manually switch off the wifi radio from the command line by using 
```

sudo echo -n 0 >> /sys/class/rfkill/rfkill0/state

```

The wifi radio switched off and the nm-applet icon disappeared.

Interestingly the /sys/class/rfkill directory had 4 subdirectories originally (rfkill0 rfkill1 rfkill2 rfkill3) but immediately after issuing the above command, rfkill0 disappeared.

After rebooting the netbook, the Fn-f2 radio switch now works, there are only 3 rfkill subdirectories (rfkill0 rfkill1 rfkill2) and the nm-applet is present in the notification area (I know this because I can click the empty space) but it does not have an icon, it is, I guess, invisible.

Does any one know how to re-set the icons for nm-applet on xubuntu?

---

### Post by mp035 on 2011-06-13
Bump...... Anyone?
Cheers.

---

### Post by Toz on 2011-06-13
What does: ```
rfkill list
```return?

---

### Post by mp035 on 2011-06-14
Hi Toz,

Thanks for the reply.

```

mp035@eeepc:~$ rfkill list
0: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: eeepc-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
mp035@eeepc:~$ 

```

Any clues there?

Cheers,
Mark.

---

### Post by Toz on 2011-06-14
Hmmm, looks okay. Did you change icon themes? It's possible the new icon theme doesn't have a corresponding icon.

You can also try restarting network manager and nm-applet: ```
killall nm-applet
sudo service network-manager restart
nm-applet & 
```

This will force nm-applet to update the icon.

---

### Post by mp035 on 2011-06-15
Thanks Toz.

No theme change, ever.  Still running the stock xubuntu 11.04 theme.

I restarted the nm-applet one more time using your commands verbatim.

No luck :(

Any thing else you can think of?

---

### Post by Toz on 2011-06-15
Lets see if its generating any errors. In a terminal window, can you run these commands and post back the results:
```
cat ~/.xsession-errors | grep -i nm-applet
cat ~/.xsession-errors.old | grep -i nm-applet
```

You can also try removing the notification applet from the panel and then re-adding it.

And, is NetworkManager running?```
sudo service network-manager status
```

---

### Post by mp035 on 2011-06-15
Thanks for all of your help Toz.

I think this may be a bug in xfce or nm-applet.
After doing a complete reinstall, the icon was back.  After re-applying my xfce setttings which I backed up from ~/.config/xfce4, the icon disappeared again.

After some fiddling around, I found that if I had the notification area in an horizontal panel the icon was visible, but if I had it in a vertical panel it would disappear.

I ran your commands regardless, in case you can glean from them which package I should be reporting the bug in.
```

mark@eeepc:~$ cat ~/.xsession-errors | grep -i nm-applet
** (nm-applet:2678): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2678): DEBUG: foo_client_state_changed_cb
** (nm-applet:2678): DEBUG: foo_client_state_changed_cb
mark@eeepc:~$ cat ~/.xsession-errors.old | grep -i nm-applet
** (nm-applet:2183): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2183): DEBUG: foo_client_state_changed_cb
** (nm-applet:2183): DEBUG: foo_client_state_changed_cb
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
mark@eeepc:~$ sudo service network-manager status
[sudo] password for mark: 
network-manager start/running, process 708
mark@eeepc:~$ 

```

---

### Post by Toz on 2011-06-15
It appears that this is a known bug and was fixed in 0.2.0-0ubuntu4.1

See: [https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/787977]("https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/787977")

What version do you have:```
apt-cache policy xfce4-indicator-plugin
```

---

### Post by itagomo on 2011-07-13
**[http://ubuntuforums.org/showthread.php?t=628814](http://ubuntuforums.org/showthread.php?t=628814)**

a workaround from this post says that you just need to add notification area to the panel to show NetworkManager

right click Panel
select Add new Items
choose Notification Area
and a pop up will appear for you to check the box for Networkmanager Applet
just press OK then

---

### Post by nm_geo on 2011-07-13
What do you get if you run this? 

```
cat /sys/class/rfkill/rfkill0/state
```

1(=on)  on my box
2 (=off) on my box

Don't know for sure but yours might be null... after the sudo echo

I have no idea why that would make the nm-applet vanish...

---

### Post by plaa on 2011-08-16
Hi,

I'm having the same issue.  Neither the network manager nor bluetooth applet are showing up in the notification area after I upgraded to 11.04.  I have a single horizontal panel with the notification area on it (it contains the volume and battery indicators).

It is running correctly and I get notifications when it attaches to a WLAN (one that I had defined prior to upgrading).  Restarting the applet and/or network-manager service does not help.

When signing in, I say for a fraction of a second the bluetooth applet flashing in the panel, but not the nm-applet - might have been too brief though.

Here's my output from xsession-errors:

> 
$ grep nm .xsession-errors
** (nm-applet:4649): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:4649): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:4649): DEBUG: old state indicates that this was not a disconnect 0
(xfce4-indicator-plugin:4667): Indicator-Application-DEBUG: Building new application entry: :1.33  with icon: nm-no-connection at position 1
** (nm-applet:4649): DEBUG: foo_client_state_changed_cb
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
** (nm-applet:4649): DEBUG: foo_client_state_changed_cb
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
** (nm-applet:4649): WARNING **: _nm_object_get_property: Error getting 'RsnFlags' for /org/freedesktop/NetworkManager/AccessPoint/26: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(nm-applet:4649): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_y >= 0 && dest_y + dest_height <= dest->height' failed
(xfce4-indicator-plugin:4667): Indicator-Application-DEBUG: Building new application entry: :1.85  with icon: nm-no-connection at position 1


Should I report a new bug?

Thanks.

---

### Post by plaa on 2011-08-16
Hi,

A bit more info:  When I reboot my machine and log in, the notification area does not appear in the panel at all.  It is running though:

> $ ps waux|grep xfce4-indicator
sampo     1565  1.7  0.7 145252 16320 ?        Sl   07:45   0:04 /usr/lib/xfce4-indicator-plugin/xfce4/panel-plugins/xfce4-indicator-plugin  28 25165889 indicator Indicator Plugin An indicator of something that needs your attention on the desktop

When I manually add it to the panel it shows only the volume and battery indicators.

I've attached my .xsession-errors after reboot and login, there's quite a bit of stuff related to the indicator, bluetooth and network manager.

---

### Post by ppqq on 2012-06-09
Go to panel preferences and edit Notification area, check that icon size =16px as below the nm-applet icon vanishes!  

update to xfce 4.10 fixes it I think.

[upgrade xfce 4.10]("https://sites.google.com/site/debianinstallnotes/tutorial/xfce/xfce-4-10")

---

### Post by ppqq on 2012-07-06
also (on such an old thread) check panel size -for me with xfce has to be >18px to show nm applet, icons >16px
any smaller panel and u get pixbuf crash

---

### Post by wildmanne39 on 2012-07-07
Old thread closed.

---

