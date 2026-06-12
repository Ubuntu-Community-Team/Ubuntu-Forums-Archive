---
title: "No network devices available, nm-applet, nm-tool"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by akoskm on 2010-10-12
Hi!
Yesterday upgraded from 10.04 to 10.10, however while I'm connected to the internet - sometimes... the network-manager-gnome applet says that there are no network devices available.
By right clicking, the Enable networking is grayed out.
Some of my configuration files:
**/etc/network/interfaces**
```

auto lo
iface lo inet loopback

```
**/etc/NetworkManager/nm-system-settings.conf**
```

# This file is installed into /etc/NetworkManager, and is loaded by
# NetworkManager by default.  To override, specify: '--config file'
# during NM startup.  This can be done by appending to DAEMON_OPTS in
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```
**Output of nm-tool**
```

** (process:2466): WARNING **: _nm_object_get_property: Error getting 'WirelessHardwareEnabled' for /org/freedesktop/NetworkManager: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (process:2466): WARNING **: _nm_object_get_property: Error getting 'WwanHardwareEnabled' for /org/freedesktop/NetworkManager: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (process:2466): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



NetworkManager Tool


** (process:2466): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


State: unknown


** (process:2466): WARNING **: error: could not connect to NetworkManager

```
**Output of nm-applet**:
```

** (nm-applet:2505): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

```.
Yes, D-Bus is running, output of **ps axuw | grep dbus**
```

102        922  0.0  0.1   3392  1660 ?        Ss   17:26   0:00 dbus-daemon --system --fork
gdm       1472  0.0  0.0   3460   560 ?        S    17:26   0:00 /usr/bin/dbus-launch --exit-with-session
akoskm    1725  0.0  0.0   3352   204 ?        Ss   17:26   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
akoskm    1728  0.0  0.0   3460   556 ?        S    17:26   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
akoskm    1729  0.0  0.2   4708  2132 ?        Ss   17:26   0:01 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
akoskm    2508  0.0  0.0   4016   740 pts/0    S+   18:24   0:00 grep dbus

```
I can also post the output if lshw -C network , ifconfig, iwconfig, but my devices are fully functioning, and currently are in use!

Any help greatly appreciated.

---

### Post by akoskm on 2010-10-12
Problem solved.
IMHO there is a bug in package management system.
connman grabbed every time the d-bus management from network-manager, that was the reason for those error messages above.
The only thing you need to do is to remove connman:
```

sudo aptitude remove connman

```.
They should be marked as conflicted packages in the package management system.

---

### Post by akoskm on 2010-10-12
If somebody is affected you can subscribe here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/659460]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/659460").

---

### Post by castironpants on 2010-10-12
You totally saved my butt! Thanks a million!

---

### Post by akoskm on 2010-10-12
> **castironpants said:**
> You totally saved my butt! Thanks a million!

I'm glad that helped.
The bug is with low priority but at least it's confirmed, it will affect many people.

---

### Post by Iowan on 2010-10-12
Glad you found a solution (and posted bug report). Perhaps you could mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others find it. :)

---

### Post by akoskm on 2010-10-13
> **Iowan said:**
> Glad you found a solution (and posted bug report). Perhaps you could mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others find it. :)

Yeah, of course I always forget... thank you for warning.

---

### Post by jurialmunkey on 2010-10-17
> **akoskm said:**
> Problem solved.
IMHO there is a bug in package management system.
connman grabbed every time the d-bus management from network-manager, that was the reason for those error messages above.
The only thing you need to do is to remove connman:
```

sudo aptitude remove connman

```.
They should be marked as conflicted packages in the package management system.

OH GOD!!! THANKS!!!

This was a complete lifesaver. It should be added that a reboot is also needed. 

[RANT]
Now I just have to figure out why I can't get my wallpaper to display. Should have just stuck with the LTS. Every single update since 8.04 has been painful and broken something utterly essential (either network, sound or display). I think I'll wait till the 3 or 4 month mark before I upgrade to a non-LTS version again. I wish there was a simple way to rollback to the LTS. 

I'm getting tempted to jump ship back to Windows because this sort of thing is worse than a BSOD (And trust me, that is something extremely painful to admit... And I don't even want to think about what I'll have to deal with from my Apple loving friends - If I ever hear "just buy a mac" again, I swear I'm going to punch someone). 
[/RANT]

So yeah, thank you! and thank god for this community. Because I do so love the beautiful Lynx this Warty Warthog has evolved into despite how many times it has bitten me on the way. :)

---

### Post by sts2001 on 2010-10-27
You saved my day. 
I was googling this for several hours without success. Now your fix worked.
You are my personal hero of the week. Really. 
Thank you very much.

---

### Post by fdiaztrias on 2010-11-01
> **akoskm said:**
> Problem solved.
IMHO there is a bug in package management system.
connman grabbed every time the d-bus management from network-manager, that was the reason for those error messages above.
The only thing you need to do is to remove connman:
```

sudo aptitude remove connman

```.
They should be marked as conflicted packages in the package management system.

That one saved my day!!!

Thanks a lot!

---

### Post by beadrifle on 2010-11-08
Fixed. Thanks a lot!

---

### Post by TheGreggles on 2010-11-29
Legend! :o) I've spent a good couple of hours trying to figure out why my nm-applet was showing my network card as not being avail... Thank you SOOOOOO much! You diamonds! :o)

---

### Post by myr|deadman on 2010-12-02
You are a hero!
I've searched two days, debuged the network-manager. And then this was the answer.
Thank you so much!

---

### Post by djwazza on 2010-12-08
You guys are a lifesaver... well system saver anyway!  I was getting very despondent with 10.10 and now a life of sunlit Ubuntu uplands beckons again...

---

### Post by mulayhafid on 2010-12-25
Thank you 
but i get this when i wrote 
SUDO APTITUDE REMOVE CONNMAN

sudo:aptitude :command not found

please help .

---

### Post by mitchlhannah on 2011-01-01
Removing connman worked for me as well.

---

### Post by Beowolf64 on 2011-03-06
Ditto. Killed **connman** and life is good again.

---

### Post by sankeert on 2011-10-26
hey connman isnt the case with me but I am facing the same problem. Could you  please suggest any way out?
I am using a dell xps 15z and I am afraid if it is a driver problem

---

