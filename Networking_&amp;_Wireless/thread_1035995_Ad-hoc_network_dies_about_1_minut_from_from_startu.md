---
title: "Ad-hoc network dies about 1 minut from from startup"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by ChrisBookwood on 2009-01-10
Hi,

I have create an Ad-hoc network on my laptop, and have set up my Eee and iPod to use it, and it works create when it works.
The thing is... It only works for about 1 minut at a time. When I boot up the computer, it works, but then it just stops working. I have been in iwconfig, and noticed that when it works, ssid on my wifi card is 'CBnet', but when it stops working, nothing is defined as ssid.

Now, I'm no expert, and because of that, I ran in to different things while setting up the ad-hoc network, such as the computer wont let me change ssid, channel and other things on my wifi card from the terminal. I have to define it in /etc/network/interfaces to make it take effect - I don't know if that have something to do about it?

My guess is, that after start up, some app loads up and changes the ssid on the wifi card, I just can't figure out which.


Regards,
ChrisBookwood

---

### Post by ChrisBookwood on 2009-01-10
Anybody?

---

### Post by ChrisBookwood on 2009-01-10
There must be somebody to lead me on the way!

---

### Post by dadozgb on 2009-01-10
Check your system logs /var/log ie syslog to see what kind of errors do you get.

---

### Post by ChrisBookwood on 2009-01-10
> **dadozgb said:**
> Check your system logs /var/log ie syslog to see what kind of errors do you get.

I have no idea what to look for in there -.-

---

### Post by dadozgb on 2009-01-10
try dhclient line. Look from the bottom up.

---

### Post by ChrisBookwood on 2009-01-11
I have unmarked Network Manager in my Sessions to make sure it doesn't interfeer, but it didn't really help anything. I will keep it off though, since it's not needed.
The ssid on the wifi card is set to 'CBnet' in /etc/network/interfaces, as you can see below, but if I look in iwconfig, as you also can see below, its undefined, and I'm pretty sure thats why I can't surfe the internet via my ad-hoc network. I have tried to ping my my wifi card *(192.168.1.1)*, but it just says the host is unreachable.

Just to make it clear, both my iPod Touch and Eee says I'm connected to the ad-hoc network all the time, I do not get disconnected, when the ssid disappears I just can't go on the internet.

Here's my /etc/network/interfaces: [http://paste2.org/p/128131](http://paste2.org/p/128131)
ifconfig: [http://paste2.org/p/128133](http://paste2.org/p/128133)
iwconfig: [http://paste2.org/p/128134](http://paste2.org/p/128134)
route -n: [http://paste2.org/p/128135](http://paste2.org/p/128135)

---

### Post by lswb on 2009-01-11
You are on the right track with disabling Network Manager. My experience (with hardy, not sure if intrepid is the same) is that NM does not like ad-hoc networks and interferes with using them.

When you disable NM from your session menu you are actually only disabling the applet the provides the little icon you see on the panel. The actual Network Manager part is still running. In hardy NM can be completley disabled with these commands in a terminal:
```

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop

```

and to restart NM use the same commands replacing "stop" with "start"

In intrepid NM can be stopped/started like this:

```

sudo /etc/init.d/NetworkManager stop

```

I have put these commands in a script named "netman" on my path so I don't have to retype them all the time. 

```

#!/bin/bash

[ "0" != "$UID" ] && ( echo "Must run as root!" ) && exit

/etc/dbus-1/event.d/25NetworkManager $@
/etc/dbus-1/event.d/26NetworkManagerDispatcher $@


```

Then I can stop or start Network Manager with "sudo netman stop" and "sudo netman start"

---

### Post by ChrisBookwood on 2009-01-11
I have created the same command for me now, but I will have to run it after every start up, right? Wouldn't it be smarter to actually stop NetworkManager from starting at all, instead of just closing it after it has started?

**UPDATE**
I've just created another script which first runs* /etc/init.d/networking restart* and then the netman command, and whenever I run that script ( netrestart ), it seems my ad-hoc network works for severel minuts. I will try to see if I can find a way to make it work all the time.

---

### Post by lswb on 2009-01-11
> **ChrisBookwood said:**
> I have created the same command for me now, but I will have to run it after every start up, right? Wouldn't it be smarter to actually stop NetworkManager from starting at all, instead of just closing it after it has started?
...

I only use my ad-hoc network occasionally so I have not tried to stop NM from running at boot. If you don't want NM to start automatically (You are running hardy, correct?) one way to do so would be to chmod the /etc/dbus.1/Network.... scripts so they are not executable. Then if you did want to start NM later, you could run the scripts by calling them with bash or sh first, i.e, your command line would be
```

sh /etc/dbus-1/event.d/25NetworkManager stop

```I haven't tested that but it should work. In intrepid you can just remove
 /intrepid/etc/rc2.d/S28NetworkManager

There are alternatives to NetworkManager. Many people have good results using wicd. You need to add a nonstandard repository to install it, you can search for details on this forum. I don't know how it handles ad-hoc networks but IIRC it does work with your /etc/network/interfaces file a lot better than NetworkManager does. I always liked the wifi-radar app when I was using dapper. You can do all your network configuration with /etc/network/interfaces too, but that makes connecting to public wifi & hotspots a headache.

---

### Post by ChrisBookwood on 2009-01-11
I'm not sure how I will do it, but for the next couple of days, I will have to do with just running the script at start up, which isn't any hassle to be honest. Later I'll likely make a more permanent solution, but for now, it will do:)

---

