---
title: "3G Modem, Change Idle Timeout?"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by foresthill on 2010-10-16
I'm running a Virgin Mobile 3G USB modem in 10.10, and have had no problems setting it up. Kudos devs, for the easy set-up.

One problem I do have is that the modem times out when idle for 10 minutes or so, and after it disconnects, it won't dial out and I have to unplug the device and then replug it in to get it to respond.

So anyone know how to adjust the timeout? I would like to set it for "0" (no idle timeout at all) but am not sure where the option is. Thanks in advance.

---

### Post by costre on 2010-10-22
I have pretty much the same problem with a Huawei E182E modem. I can't say I'm sure the idle time is causing the modem to disconnect, but it seems plausible since it never happens when I'm active online.
I too have to unplug the modem and plug it back in to make it respond and connect again.

Any suggestions would be awesome

Also, I'm running Kubuntu 10.10 (I couldn't get gnome-panels to behave)

---

### Post by foresthill on 2010-10-22
I believe Network Manager controls 3G connections, so it should just be a simple matter of editing the config file to stop the modem from disconnecting when idle. 

I know that if you use wvdial to connect with a modem. and you want to get rid of the idle timeout you just add this line to the wvdial.conf file:

Idle Seconds=0

I'm assuming that Network Manager should be fairly similar.

---

### Post by costre on 2010-11-01
Well, it's not hanging up because of idle time, that's for sure. The connection, or rather modem functionality, simply dies.

Having to unplug the modem to get it to dial up again is strange, it seems like the system suddenly chooses to ignore the device for some reason.

It's getting quite annoying, and any further tips on this are appreciated!

---

### Post by foresthill on 2010-11-01
Well, for me it only occurs when I walk away from the computer for 5 minutes or so. When I come back, my connection has been terminated, and the Network Manager icon becomes non-responsive. The only way I can reconnect is to unplug the modem and plug it in again and wait 30 seconds or so for the device to "flip".

I'm just afraid that all this plugging and unplugging going to wear out either my USB port or the USB connector on the modem, or both.

As far as solutions go, I have been searching the net for the past few days, and this is about all I can come up with:

[http://wiki.ubuntuforums.org/showthread.php?p=9839990](http://wiki.ubuntuforums.org/showthread.php?p=9839990)

Not sure if it even applies, but I intend to try out this solution the next time I'm in Windows.

---

### Post by costre on 2010-11-01
I'm thinking it has to do with the computer turning into powersave mode.
I'm going to try to turn off every power saving option imaginable and see what that does.

I'll be back this afternoon and see if it helped.

---

### Post by costre on 2010-11-03
OK, it seems to be some kind of bus overload / interrupt thing-or-another.
The USB modem stayed connected the whole day, easily 20 hours plus.
Then I performed some heavy tasks on a USB hard drive, and it disconnected without warning. The connection was not idle either.

I will continue to experiment ... suggestions are welcome :)

EDIT:

I am now maxing out the bandwidth of the modem, aswell as performing heavy duty tasks to and from the USB hard drive, and everything is working.
The only difference is that I changed the port of the modem to the right hand side of the laptop, keeping the hard drive on one of the left hand side USB ports.
Solution or coincidence? Who knows? :)

---

### Post by foresthill on 2010-11-03
I looked in Windows and found no options to control which types of towers the modem uses. So no luck there.

I can't believe that no one else is having this problem except us two. 

It happens on both my laptops and on my desktop. It's not the worst problem to deal with, but it can get a little annoying.

---

### Post by masque7 on 2010-11-06
I also have this problem on Ubuntu 10.04 with a ZTE MF636. -- reported via lsusb -- when the device is actually a ZTE MF627. It does seem like it disconnects when it's idle, but I'm not so sure. If that were the case it doesn't seem to be directed by time, it differs too much for that. 

I had a Huawei E220 modem prior to this, and I don't recall that being a problem. With the ZTE model back on 9.10 I had to find a [USB switcher](http://reprap.org/wiki/Main_Page) that would allow it to be recognised as a 3g modem, not a storage device. However since 10.04 I believe the model I'm using is supported out of the box.

---

### Post by bmf0354 on 2011-01-09
Did anyone here solve this issue?  I'm having a very similar issue.  Using a Novatel usb760 (CMDA) 3g modem in Ubuntu 10.10.  When I'm actively using the pc the 3g connection is fine.  When I let the pc sit idle for ~5 minutes modem-manager closes the connection and I too have to unplug/plug the usb modem for it to be recognized and the connection re-established. 

I'll try to turn up the modem-manager logging to see if that provides any additional info.

Thanks,
Brian

---

### Post by foresthill on 2012-03-14
Updates seem to have fixed this problem, at least in version 10.10. Which update, I don't know, but I just got home from work and noticed that my Virgin Mobile 3G modem stayed connected for approximately 7 hours while I was gone.

---

