---
title: "Memory leak in nm-applet"
date: 2010-12-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jmmL on 2010-12-04
I thought I'd post here to get this bug some more exposure and see who it affects. The bug is: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/684599](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/684599)

After about 3 hours of uptime nm-applet is using 160MB of RAM on my machine. Don't forget to mark yourself if it affects you.

---

### Post by MacUntu on 2010-12-04
Possibly a dupe of [https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/682786](https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/682786)

---

### Post by scradock on 2010-12-04
> **jmmL said:**
> I thought I'd post here to get this bug some more exposure and see who it affects. The bug is: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/684599](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/684599)

After about 3 hours of uptime nm-applet is using 160MB of RAM on my machine. Don't forget to mark yourself if it affects you.
Yes, I see the same - watching in System Monitor | Processes shows that nm-applet uses steadily more memory as time goes on. I've confirmed your bug - if it gets marked as a dup of the other one we can confirm that one.....

---

### Post by Quackers on 2010-12-04
203MB on mine at the moment - 6 hours uptime

---

### Post by kyleabaker on 2010-12-04
I noticed this earlier as well. Adding my "me too" to the bug now..

---

### Post by ronacc on 2010-12-04
I fired up system monitor right after boot and nm-applet started out at 6.8 MB and has been adding .1 mb about every 10>15 sec  networkmanager itself is stable at 4.7 MB .

---

### Post by Yes_It's_Me on 2010-12-05
It was using about 1.5GB for me a few times the last couple of days. Like I would go to sleep, wake up and my RAM is full, my swap is starting to fill up and my computer hardly works because everything is going through swap. And the cuprit according to conky? nm-applet.

---

### Post by Quackers on 2010-12-05
Oh dear. nm applet is back up to 187MB again. I'll have to reboot soon.

---

### Post by Red_Steve on 2010-12-05
I too can confirm this memory leak.

---

### Post by efflandt on 2010-12-05
Unity mostly works fine for me, other then the RAM munching nm-applet, and broken Untity icons on resume from suspend.

I don't see nm-applet in System Monitor if I log into a "Failsafe" session.  If I log into "Classic", all the upper right and lower panel applets crash, and restarting them brings back the lower panel applets, but no applets at all in upper right.  Even though nm-applet is not displaying anything, and shows a little round icon with a fuse in System Monitor because it bombed out, it keeps growing (from somewhat smaller starting number).

---

### Post by Quackers on 2010-12-11
Recent updates seem to have fixed this annoyance.
nm-applet was using 4.2MB at startup and now it's using 4.2MB - 6 hours later!
Happy again :-)
Thank you fixers!

---

### Post by efflandt on 2010-12-11
In 15 hours my nm-applet has grown from about 3.9 MB to 10.3 MB (even though it always appears to be "Sleeping").  So the gusher has slowed to a drip, but still leaks a little for me.

---

### Post by Quackers on 2010-12-11
Hmm, mine's still at 4.2MB even now.

---

### Post by ronacc on 2010-12-11
I can't tell if my memory leak has been fixed or not , it seems to be but I can't keep nm-applet running long enough to tell :D , it segfaults randomly or if it don't segfault randomly disconnects seems to be associated with something that acceses the net and then finishes , update with synaptic and when the update finishes nm-applet dies ,check email nm-applet dies , browse and its ok ????? .

---

### Post by dino99 on 2010-12-11
memory leaks is not a new thing on my end: after suspecting the kernel, then some apps, i finally conclude that each time java was to blame (the first app in system-monitor eating the memory is ipblock because it hugely use jar), so i've reported this problem with the backtrace to Oracle).

On the other hand, when this memory leak become scary (up to 95 %) and then the system freeze, i dont understand why the swap is not used higher than 5 %. Is it the same for you ? ( i've digg around that and tweaked the 'swapiness' but no luck)

---

### Post by Yes_It's_Me on 2010-12-11
When in doubt, blame Java. That's always been my saying.

---

### Post by pressureman on 2010-12-12
The memory leak in nm-applet is resolved for me.

```

nm-applet[3405]: segfault at 38 ip 000000000042dd4e sp 00007fff2e386390 error 4 in nm-applet[400000+62000]

```

Hey... if it can't load, it can't leak memory, right? ;-)

---

### Post by gnomeuser on 2010-12-12
> **pressureman said:**
> The memory leak in nm-applet is resolved for me.

```

nm-applet[3405]: segfault at 38 ip 000000000042dd4e sp 00007fff2e386390 error 4 in nm-applet[400000+62000]

```

Hey... if it can't load, it can't leak memory, right? ;-)

That at least is true

---

### Post by ronacc on 2010-12-12
issue seems resolved for me , managed to keep nm-applet running for 7 hrs and no mem increase over that time .

---

### Post by Quackers on 2010-12-12
Mine's been running for 24 hours now and it's only gone from 4.2MB to 4.9MB - looks promising :-)

---

### Post by pressureman on 2010-12-12
> **Quackers said:**
> Mine's been running for 24 hours now and it's only gone from 4.2MB to 4.9MB - looks promising :-)

A slow memory leak is still a memory leak. It will just take longer for your computer to fall over.

---

### Post by Quackers on 2010-12-12
It's still at 4.9MB
That's much better than it was. It would have crashed by now with the old leak :-)

---

### Post by knarf on 2010-12-15
> **ronacc said:**
> I can't tell if my memory leak has been fixed or not , it seems to be but I can't keep nm-applet running long enough to tell :D , it segfaults randomly or if it don't segfault randomly disconnects seems to be associated with something that acceses the net and then finishes , update with synaptic and when the update finishes nm-applet dies ,check email nm-applet dies , browse and its ok ????? .
Same here, nm-applet has bitten the dust after a bunch of updates which also took out gtk (by leaving a stale cache file in the gnome icons directory) and made it impossible to log in through gdm or lightdm. Before that it was hogging memory so I quite like not having it running at the moment... iwconfig and dhclient work fine as well.

What about the nmcli command? Has anyone ever gotten that to work? Theoretically 'nmcli con up id <name_of_network>' (or 'uuid <uuid_of_network>') should bring up a connection but in reality it doesn't do squat:

```
nmcli con up uuid 71285010-4123-1708-4c24-bc34ac6578c2
Active connection state: activating
Active connection path: /org/freedesktop/NetworkManager/ActiveConnection/0
  [COLOR=Red]<<<A LONG, LONG WAIT....>>>[/COLOR]
** (process:14894): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager/ActiveConnection/0: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


state: unknown
Error: Connection activation failed.
```It would make a good replacement for nm-applet if it worked. Alas, it does not.

---

### Post by zika on 2010-12-15
Can You, hmm, just, use nm-connection-editor...?
nmcli works fine here...```
:~$ sudo nmcli con up id Auto\ eth0
Active connection state: activating
Active connection path: /org/freedesktop/NetworkManager/ActiveConnection/2
state: activated
Connection activated
``````
:~$ sudo nmcli con up id Wired\ connection\ 1
Active connection state: activated
Active connection path: /org/freedesktop/NetworkManager/ActiveConnection/3
```
Thank You for making me try this...

---

### Post by ronacc on 2010-12-15
nm-connection editor might solve the problem but would not fix the issue, such a basic default part of the system MUST be rock stable . Thinking that my problem with nm-applet randomly segfaulting and acting generally flaky was because my install was a left over and much abused maverick , then upgraded at repo open I wiped it and did a reinstall with yesterdays daily, /home and all . The problem got worse nm-applet was starting reliably and connecting but all the rest of the indicator area applets were crashing on startup , when I reloaded them nm-applet would segfault and have to be restarted from cli .After a late day update the last 2 restarts have been normal ( nothing crashing and connecting on startup) so this may finally be fixed .

---

### Post by pressureman on 2010-12-15
I'm using cnetworkmanager in the meantime, since nm-applet won't even start without segfaulting (this is on a fresh install too).

```

cnetworkmanager -C my_ssid --wpa-pass=my_password

```

---

