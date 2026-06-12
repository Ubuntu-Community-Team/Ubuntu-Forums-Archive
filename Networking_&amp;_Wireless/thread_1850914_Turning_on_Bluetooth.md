---
title: "Turning on Bluetooth"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by SoFl W on 2011-09-27
I have bluetooth disabled in my startup applications, I don't have a bluetooth adapter on this computer.  I have purchased an adapter for another machine but would like to know if there is an easy way to turn on bluetooth without adding it to startup applications and logging out or restarting. 

When and if I plug in the adapter to this machine I just want to start/stop the program and not permanently change the startup list.
Is the command "[COLOR=Blue]sudo /etc/init.d/bluetooth start[/COLOR]" or is it going to be more complicated?  (I don't have the adapter with me at the moment, I was hoping it would be a simple turn-on/turn-off" command.

---

### Post by khelben1979 on 2011-09-28
Have you tried the [Bluetooth Applet]("http://library.gnome.org/users/gnome-bluetooth/stable/gnome-bluetooth-applet.html.en")? You can easily turn it off or on from there.

---

### Post by SoFl W on 2011-09-29
Thank you for responding.  The other day I discovered I had removed the Bluetooth menu option from the system preferences main menu. (no wonder I couldn't remember where I saw it) 
I finally had the chance to install the bluetooth device and it work perfectly with no problems once I turned the bluetooth menu option back on.

It also worked with my virtualbox XP machine, after I turned on both "unknown device" and the broadcom adapter.

In case someone else is looking the **IOGEAR GBU421 bluetooth adapter** works with no fuss in Ubuntu 10.4.3 (64) and just a little bit of fuss within a windowsXP virtual machine.

---

### Post by wildman4god on 2011-12-04
I can't get this adapter working, I turned it off when I was running windows 7, I wiped windows and installed ubuntu and while lsusb sees it, it won't turn on, the adapter doesn't even light up. Any tips?

---

