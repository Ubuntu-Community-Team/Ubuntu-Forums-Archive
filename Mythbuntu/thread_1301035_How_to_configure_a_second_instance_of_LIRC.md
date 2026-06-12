---
title: "How to configure a second instance of LIRC?"
date: 2009-10-25
forum: Mythbuntu
---

### Post by Lorenzo1985 on 2009-10-25
Hiya

Has anyone got any idea how to configure a second instance of LIRC.

I have one of the dodgy Cyberlink remotes that shows up as Two devices. This means xbmc etc only work with the buttons on one of the devices.  I followed some slightly vague instructions on lirc.org and worked out that I can connect two instances together as follows.

```
/usr/sbin/lircd --output=/var/run/lirc/lircd --driver=devinput --device=/dev/input/event5 --pidfile=/var/run/lirc/lircd1.pid --listen=8765
/usr/sbin/lircd --output=/var/run/lirc/lircd --driver=devinput --device=/dev/input/event6 --connect=localhost 8765
```

This works great, however I've no idea how to configure a second instance of lirc and make it start at startup etc.

Anyone got any ideas?

---

### Post by Lorenzo1985 on 2009-10-26
I found this in a submit to bazaar for lirc from superm:
>   - Update init script to have the ability to spawn multiple lirc processes.

And also this blueprint that is marked as implemented: [https://blueprints.launchpad.net/mythbuntu/+spec/lirc-multiple-devices](https://blueprints.launchpad.net/mythbuntu/+spec/lirc-multiple-devices)

This would suggest this is possible but how?

---

