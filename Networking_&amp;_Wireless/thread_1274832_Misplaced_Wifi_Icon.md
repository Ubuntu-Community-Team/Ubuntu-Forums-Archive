---
title: "Misplaced Wifi Icon"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by Ron-Alain on 2009-09-25
Hi everyone.
 
First of all, before I installed Ubuntu on my laptop, I read problems the Wifi, this is strange because as soon as Ubuntu installed my wifi connected automatically, and I was able to use, just one short problem.
 
Next to the power button, next to the time and date, and the top right, my Wifi icon was there, where I was able to select which Wifi network to connect to, settings, etc., but yesterday, being a complete idiot, I accidentally removed it from the panel, now I can't find it again.
 
Is there anyway of finding it again and loading it back on my panel?
 
I will deeply appreciate your assistance!
Kind regards,
Ron-Alain.

---

### Post by t0mppa on 2009-09-25
Yes, most cards work out of the box, but a few WiFi cards are quite troublesome, especially for first time Linux users.

If you removed the whole Notification Area (with the clock, Network Manager, Bluetooth and sound control by default) from the panel, you can just right click the top panel and choose *Add to Panel...* and then *Notification Area*.

If you just closed down Network Manager, you can get it back up and running by pressing Alt + F2, typing in *nm-applet* and clicking *Run*.

---

### Post by Ron-Alain on 2009-09-25
Hi, thanks for your reply.
 
I've got the notification area, everything is there except for the network manager. I ran nm-applet and nothing happened, I found it by using 'search for files' and found the executable file, but if I run that it also doesn't do anything. I really need this to work, as I need to use my mother's computer since my laptop can't connect.
 
I deeply appreciate any assistance that can be given to me.
 
Thanks, kind regards,
Ron-Alain.

---

### Post by Ron-Alain on 2009-09-26
Can someone please help me! :confused:

---

### Post by nothingspecial on 2009-09-28
If you`ve lost network manager and can't get a wireless signal, you`ll have to do it the command line way.

```
sudo ifconfig wlan0 up
```

```
sudo iwconfig wlan0 essid *[COLOR="Red"]yournetworkname[/COLOR]*
```
```

sudo iwconfig wlan0 key *[COLOR="Red"]yourwirelesskey[/COLOR]*
```
```

sudo dhclient
```

Then ```
sudo apt-get update && sudo apt-get install wicd
```

wicd is an alternative network manager that I find alot better than gnome-network-manager.

Now, just that pesky graphics card.

---

### Post by nothingspecial on 2009-09-28
If you have a look at those commands above you`ll notice all but the last one has wlan0 in it.

This is usually your wireless interface, but not 100% of the time. Before you do all that type iwconfig to see if it is.

If not substitute wlan0 for whatever your wireless interface is.

---

### Post by Hobbsilla on 2009-10-01
I sorta have this problem. I decided to add a new user on my computer so I and my roommate could have our own separate home directories. On mine (the one that has been the only ubuntu home directory until a few days ago) the nm-applet displays but on my roommates login she is connected to the wireless network but she doesn't get the GUI interface of nm-applet. I tried reinstalling the nm-applet. I don't want to switch over to WICD because I've had problems with that and gnome nm is good enough for me. 
Is anyone able to help get the nm-applet to show rather than just switching to a new alternative?

---

