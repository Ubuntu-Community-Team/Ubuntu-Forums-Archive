---
title: "Lost my remote control settings, please help"
date: 2010-05-11
forum: Mythbuntu
---

### Post by Naoi on 2010-05-11
I was having trouble with my remote control today and decided to try resetting it in the Mythbuntu control center.

I didn't realize that unchecking the 'enable remote control' box under the 'infrared devices menu' would completely erase the settings.  

I am kicking myself for not writing down what I had in the 'remote', 'driver module', 'configuration' and 'device' boxes.  There was some version of lirc in one of them.

I last worked on this over 2 years ago and I spent many hours getting my remote to work and absolutely dread figuring it out all over again.

Is there a way to restore the Mythbuntu control center settings for the infrared device?

The files must be there, searching hasn't given me any clear idea where the settings are stored.  

I am running Mythbuntu for Ubuntu 8.04.

Any help would be greatly appreciated!

---

### Post by iponeverything on 2010-05-11
look in

/etc/lirc

---

### Post by OffAxis on 2010-05-14
There have been LOTS of updates since 8.04 to everything.
Remote control configurations have been added to, usb drivers have been updated, modules have been added or removed... so the hoops that you had to jump through to get your remote working in 8.04 may not be necessary in 10.04. 
If there's not a specific reason you're avoiding upgrading, it might be worth a shot (or at least a LiveCD demo run on a remote frontend). If you do take the plunge, remember to backup your database and recordings. If 8.04 is running myth .22 :
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

Even upgrading to an older 9.04 or 9.10 may help.

The hardware config is
**/etc/lirc/hardware.conf**

The lirc config is
**/etc/lirc/lircd.conf**

> There was some version of lirc in one of them.

For what it's worth, to get the lirc version just type
```

lircd -v
```

and if that doesn't do it for you;
What kind of remote do you have?
What kind of receiver do you have?

---

