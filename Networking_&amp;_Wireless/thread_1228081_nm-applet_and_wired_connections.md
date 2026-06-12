---
title: "nm-applet and wired connections"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by buzzmandt on 2009-07-31
My mother has comcast cable internet w/ a surfboard modem.

nm-applet shows it's connected but can't browse the internet.
I connect my laptop and nm-applet shows connection but can't browse the internet.

Connected a desktop, nm-applet shows connection but can't browse the internet.

I connected a wireless router to it, and as long as we're connected through it (either wireless or wired into the router) it connects and works just fine, works very good in fact with all computers listed above.

Is this a nm-applet issue or is comcast somehow blocking linux from connecting?  (All three systems are hardy on the desktop, intrepid on moms laptop, and jaunty on my laptop at the time).

Or is this something that WICD could take care of?  (Going to try it when I get home, just wanted some user input on this as a suggestion)

Also has anyone else experienced this problem before?

---

### Post by dmizer on 2009-07-31
Could be that Comcast has keyed your access to the MAC address of the router. You may consider calling them to verify this. Is the surfboard modem a modem/router combination? If not, do you get an IP if you try this:
```
sudo dhclient eth0
```

Do you have local firewalls installed on any/all of the computers?

---

### Post by buzzmandt on 2009-07-31
> **dmizer said:**
> Could be that Comcast has keyed your access to the MAC address of the router. You may consider calling them to verify this. Is the surfboard modem a modem/router combination? If not, do you get an IP if you try this:
```
sudo dhclient eth0
```

Do you have local firewalls installed on any/all of the computers?

I'm on the road rtm, will try any suggestions when I'm back and visit mom (couple weeks).

as for firewalls, whatever default is in ubuntu.  Haven't installed any firewalls.
modem is modem only, not modem/router combination.  the router she's using is my standalone router, linksys if I remember right.

and I'm pretty sure they've not keyed it to the router.  Was having this problem before putting the router on it.  Putting the router on it was a last resort effort to getting it to work and it worked.  Now I'm trying to figure out if it's a nm-applet problem and why it worked when I put the router on it.

Main reason I've suddenly wondered if it was nm-applet causing the trouble is because of this post: [http://brainstorm.ubuntu.com/idea/20854/](http://brainstorm.ubuntu.com/idea/20854/)
> I know, out of experience, that GNOME's network manager does not like my wired connection. I know that KDE's network manager does not function with wired or wireless connections.

I know, however, that WICD likes both my connections.  

Hence my reasoning for asking if anyone else has had trouble with nm-applet on wired connections

---

