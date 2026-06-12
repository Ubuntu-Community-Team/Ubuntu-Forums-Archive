---
title: "How to enable/disable wireless from command line"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by lunatico on 2009-08-20
Hello,

I use network manager and it's beautiful. There is one thing I would like to do from command line (so that I can script it later).

To enable and disable wireless.

So if you right-click network manager there is a 'Enable Wireless' option that you tick or untick to achive this.

How can I do that exact same thing from command line?

Thanks!

---

### Post by slakkie on 2009-08-20
I just do ifdown wlan0, but then again, I don't use network manager.

---

### Post by lunatico on 2009-08-20
> **slakkie said:**
> I just do ifdown wlan0, but then again, I don't use network manager.

Yeah I tried that but:
~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured

I want to keep using network manager, that's why I want to kinda' emulate ticking and unticking that option.

---

### Post by lunatico on 2009-08-20
Found it!

I went into Network Manager site and it says NM uses dbus and hal to do their stuff... so I asked in their mailing list and got the answer.

Here it is:

To disable wireless:

```
dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:false
```

To enable wireless:

```
dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:true
```

Note that this is just to get the same effect as doing right-click Network Manager and tick/untick 'Enable Wireless'.

---

### Post by Brandon Williams on 2009-08-20
Yes ... that works for Jaunty and (hopefully) beyond. However, it is not a great idea to "depend" on this, because it may not be a stable API. The method changed between the intrepid and jaunty versions of the network manager, for example. They seem to have the idea that people don't do this sort of thing, and so they don't publish clear details when they change it.

---

### Post by lunatico on 2009-08-20
> **Brandon Williams said:**
> Yes ... that works for Jaunty and (hopefully) beyond. However, it is not a great idea to "depend" on this, because it may not be a stable API. The method changed between the intrepid and jaunty versions of the network manager, for example. They seem to have the idea that people don't do this sort of thing, and so they don't publish clear details when they change it.

I see you point. I guess if they break it I'll ask again on their mailing list, they are helpful enough anyway.

---

### Post by VvWolverinevV on 2011-09-02
This doesn't seem to work in 11.04.  Anyone know if/how the API has changed?

---

### Post by Circa Lucid on 2011-09-08
nmcli nm wifi off

Though the menu for nm_applet still will have wireless checked, the wireless does shut off.

Using

dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Get string:&#8221;org.freedesktop.NetworkManager&#8221; string:&#8221;WirelessEnabled&#8221;

came back with an error that org.freedesktop.NetworkManager is not a service. It's not listed in 

ls /usr/share/dbus-1/services/

so I'm thinking NetworkManager moved away from dbus.

---

### Post by VvWolverinevV on 2011-09-08
Thanks, Circa.  A couple of questions:
[LIST=1]
[*]Where are you getting this information?
[*]It's weird that the NM menu doesn't reflect the state of the WiFi interface properly.  Is there another way to verify the state?
[/LIST]

---

### Post by praseodym on 2011-09-08
Please show:

```
rfkill list
```

---

