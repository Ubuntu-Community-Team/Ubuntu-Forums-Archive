---
title: "&quot;Could not save the monitor configuration&quot;"
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by humphreybc on 2010-09-05
After a recent update a day or two ago, I can no longer save my dual monitor configuration when using two monitors on Maverick.

I've got a Toshiba Satellite 15.4" laptop with an HDMI port, a Dell 24" LCD plugged into the HDMI port.

My graphics card is an ATI Radeon HD2600 and I'm using the stock open source radeon driver that's on Maverick.

Terminal output:

```
benjamin@benjamin-laptop:~$ gnome-display-properties

(gnome-display-properties:16864): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:16864): Gtk-WARNING **: No object called:

** (gnome-display-properties:16864): CRITICAL **: gnome_rr_config_save_to_file: assertion `error == NULL || *error == NULL' failed
```

It wouldn't matter so much if the two monitors where the same size, [but because they're not]("http://www.flickr.com/photos/humphreybc/4442107247/"), I get an awesome 15cm difference in height between them which means when I move the mouse cursor between them, it jumps up or down half of the screen.

I opened up a [bug.]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/631217") Anyone have any ideas on how to fix this?

[IMG]http://launchpadlibrarian.net/55039786/display.png[/IMG]

---

### Post by DeadSuperHero on 2010-09-06
Did an upgrade of a xorg package break it? This seems to be stemming from some kind of driver or xorg error. Did the Radeon driver support multiple monitors before?

Edit: on the other hand, the "could not create configuration" error could have something to do with the permissions of the conf app, or the file itself.

---

### Post by humphreybc on 2010-09-06
I'm not sure, there was about 200mb of updates.

The driver worked with my multiple monitors absolutely perfectly before.

I think you might be correct with configuration permissions, I'd check but I don't know what file it's trying to write to.

---

### Post by realzippy on 2010-09-06
*I don't know what file it's trying to write to.*


it used to be **~/.config/monitors.xml**
but maybe it changed in maverick...

---

### Post by pheitman on 2010-09-06
I'm having the same problem. Editing .config/monitors.xml by hand doesn't help - the file gets overwritten upon startup and the Preferences -> Monitors applet doesn't seem to read it. Editing the file and then opening the applet shows the old orientation, not the new one.

---

### Post by Funnnny on 2010-09-06
With the recent update, xorg or any of if package didn't have any update, the gconf package was updated, and the problem is here

---

### Post by laborg on 2010-09-07
I've troubled by the same:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/630545](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/630545)

I hope they fix it soon...

---

### Post by teachop on 2010-09-07
This situation happened to my Sony laptop, which was installed fresh last with Alpha 3, and updated from there.  When I wiped it with the released beta, allowing updates from there, this particular problem was gone.

---

### Post by MacUntu on 2010-09-07
Try to recompile gnome-desktop without the patch 100_load_desired_settings.patch - maybe some update broke it.

---

### Post by cowanh00 on 2010-09-08
By running 

```
sudo gedit ~/.config/monitors.xml
```

I changed the the Width and Height to the correct values and changed Primary to yes, logged out and logged back in and my resolution has returned to normal!

---

### Post by pheitman on 2010-09-08
I edited .config/monitors.xml, changed the x offsets for the two monitors so that the correct monitor was at 0 and the other monitor had x set to the width of the left monitor. That fixed me up!

---

### Post by Funnnny on 2010-09-08
If you just want to change the resolution, use the command 

DISPLAY=:0 xrandr -s 1366x768

---

