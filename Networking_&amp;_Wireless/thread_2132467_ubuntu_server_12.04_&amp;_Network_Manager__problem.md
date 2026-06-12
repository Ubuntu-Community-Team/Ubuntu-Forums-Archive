---
title: "ubuntu server 12.04 &amp; Network Manager  problem with privileges"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by navoye on 2013-04-04
hello,
I use Ubuntu 12.04.2 LTS with openbox and lightdm

I installed and run network manager but when i try to connect to wifi i get error

```
** (nm-applet:1453): WARRNING **: Failed to add/activate connection: (32) Insufficent privileges.
```

I can run network manager with sudo and connect but its uncomfortable.

Could You please tell me how to add needed privileges to my user to manage networks?

I tried with network manager wiki and google, but i'm a newbie in linux and i wasnt able to do this.

---

### Post by Irihapeti on 2013-04-04
Right-click on the nm-applet icon in the taskbar, edit the wireless connection and save. Untick the "make available to all users" box before saving. If you're the only human user on the system, that should be OK.

If you do want to make it available to all users, you'll need to run nm-applet with sudo first.

Once the settings are saved, there's no need to run it with sudo. At least, that's been my experience.

---

### Post by navoye on 2013-04-05
maybe i'm wrong, but i cant imagne that i have tray application and i cant just click on ssid of my network, it ask my about key and just connect and store

---

### Post by Irihapeti on 2013-04-05
You have openbox and nm-applet, is that correct? Did you also install the Tint2 taskbar?

---

### Post by navoye on 2013-04-05
yes, thats right - openbox, tint2, nm-applet - i think problem is with permision of my user to add/change network settings but i dont know how to add them

---

### Post by Irihapeti on 2013-04-05
If the nm-applet is showing in the system tray, you should be able to right-click on it and choose "edit connections". 
The trick I use is to unselect the "Available to all users" option when editing the settings. Then it lets me save. I'm the only user on my system, so it doesn't matter.

---

### Post by navoye on 2013-04-05
yes, that trick working - but i want to know how to do this normally, without a trick - how to walk true the door, not how to get behind them

---

### Post by Irihapeti on 2013-04-05
I tried this to get a configuration which is available to all users:

```
sudo killall nm-applet

sudo nm-applet &
```

Delete any configurations that are already there, and create a new one, and save.

Reboot.

Once you've done that, you'll need to do the same thing again if you want to change the password.

I agree that this is a bit clunky. I think the real problem is that we're using network-manager-gnome outside of its natural setting, and so things don't work quite as easily as they would in a gnome desktop.

I'm going to be offline for some hours now, so if this doesn't work, maybe someone else will have some ideas.

---

### Post by navoye on 2013-04-05
thank You very much, will check it and wait, maybe some know how to do it without trick

---

