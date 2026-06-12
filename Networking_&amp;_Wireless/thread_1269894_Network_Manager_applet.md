---
title: "Network Manager applet"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by gdonwallace on 2009-09-18
When I booted up 9.04 this morning, the Network Manager Applet was not running.  I updated to the latest Alpha (6), hoping that it would fix the problem, but it still persists.

When I try to launch nm-applet from terminal, I get the following errors:

** (nm-applet:2644): WARNING **: <WARN>  request_name(): Could not acquire the session service as it is already taken.  Return: 3

** (nm-applet:2644): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

Not sure what they mean.  Anyone have any ideas how I can fix this and get nm-applet running.

thanks.

Also, I have tried uninstalling / reinstalling Network Manager

---

### Post by speedwell68 on 2009-09-19
You could just ditch nm-applet i favour of WICD.  It is in the jaunty repos.

```
sudo apt-get install wicd
```

---

### Post by gdonwallace on 2009-09-19
Thanks for the help, that worked fine.

I think I'll be using wicd instead of network manager.

---

### Post by GeorgeVita on 2009-09-19
> **gdonwallace said:**
> ...When I try to launch nm-applet from terminal, I get the following errors:
** (nm-applet:2644): WARNING **: <WARN>  request_name(): Could not acquire the session service as it is already taken.  Return: 3
** (nm-applet:2644): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

This is because nm-applet is running!
You can see all running processes with: ps -A
Or use a 'filter' to see applets: **ps -A | grep -i applet**

Probably you just deleted 'Notification area' from top panel, so add it:
- right click on top panel, "Add to Panel..."
- click on Notification Area
- Add, close

Regards,
George

---

### Post by gdonwallace on 2009-09-21
I didn't notice that before.

Notification had been removed from the panel.  

I am having some problem this morning getting connected to a hidden wireless network.  I don't seem to have anywhere that I can input the name of the network.  I'm going back to Network-Manager and see if I can get connected with that.

thanks for the help.

---

### Post by LukonLinux on 2009-11-26
I had a sinilar problem and tried everything on these forums.  Then I installed wicd which did not work, but when I reinstalled network manager, everything was fixed.  It's weird, because I had tried uninstalling and reinstalling NetworkManager more than once.  Some flag must've gotten reset when I installed wicd.  Happily, it all works fine now...

---

### Post by alecwk on 2010-06-05
> **GeorgeVita said:**
> This is because nm-applet is running!
You can see all running processes with: ps -A
Or use a 'filter' to see applets: **ps -A | grep -i applet**

Probably you just deleted 'Notification area' from top panel, so add it:
- right click on top panel, "Add to Panel..."
- click on Notification Area
- Add, close

Regards,
George

The above solved my problem. Came across add notification area earlier but never knew that this it the one to add back the connection manager. Why named Notification area?

---

### Post by benjabean1 on 2011-04-07
It actually isn't called Notification Area. It's just that the Notification Area is what allows nm-applet to be seen by the user. Also, this fixed my problem too. I somehow confused 'Notification Area' and 'Indicator Applet.' ;)  Weird, that there are two standard programs for the same purpose. :confused:

---

### Post by Z.K. on 2011-04-07
The Network Manager applet frequently disappears for whatever reason if you do not have a Ethernet cable plugged in or you are using the interfaces file to manage your Ethernet connections and not network manager.  My solution is to always allow network manager to manage eth0.  If you have a secondary interface like I do you can put it in interfaces with a static address for a dhcp server.  Dealing with wireless though seems to cause the problem as well unless you have it always connect.

I am not saying that someone might not accidentally remove the icon, but in a lot of cases it is network manager itself that does it.  It would be nice if the icon would stay there regardless if there are any active interfaces or not.  It would also be nice if network manager would actually monitor the interfaces file as a secondary source.  It has cause me a lot of headaches.

---

