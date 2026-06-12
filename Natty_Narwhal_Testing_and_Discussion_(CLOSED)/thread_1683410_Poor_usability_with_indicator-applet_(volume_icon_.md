---
title: "Poor usability with indicator-applet (volume icon lost issue)"
date: 2011-02-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by syltty on 2011-02-07
This is just stupid.  

New user decides to remove envelope icon from indicator tray --> POOF!!! --> You just lost your volume icon. 

"Add to panel" dialog fails to find anything when searched with text:volume. Of course new user should know, that you have to add Indicator Applet to get the volume icon back ](*,)

There are too many threads about lost volume icon because of this problem. I think this really should be fixed in Natty. :confused:

---

### Post by Framli on 2011-02-07
I don't think that behavior will change, as Ubuntu is moving away from gnome-panel. But the problem will be solved, as there won't be any GUI to remove the envelope icon from "Unity-panel".

---

### Post by cariboo on 2011-02-07
The envelope icon isn't only for mail, it is multi-functional. in my case it works as a notification for xchat when someone pings we.

---

### Post by Mr. Picklesworth on 2011-02-07
I filed a bug report on this a while ago. It probably won't be fixed at this point…
[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/519553](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/519553)

That this is an issue is really a weakness in the panel's design, filed away here:
[https://bugzilla.gnome.org/show_bug.cgi?id=616244](https://bugzilla.gnome.org/show_bug.cgi?id=616244)

The real problem is that Gnome Panel is nasty and XFCE's panel is much better. I'm glad that it's finally being dropped, and I bet it will be completely forgotten in a few years :b

---

### Post by seeker5528 on 2011-02-07
> **Mr. Picklesworth said:**
> The real problem is that Gnome Panel is nasty and XFCE's panel is much better.

How is it a fault in panel design that......

[list]A: The indicator applet only gives you the option to remove the entire applet and not individual indicators?[/list]

[list]B: Indicators sometime behave in quirky ways?[/list]

Is there an indicator applet for the XFCE panel that works better?

> I'm glad that it's finally being dropped, and I bet it will be completely forgotten in a few years :b

Apparently someone forgot to inform the maintainers. :p 

[http://live.gnome.org/RoadMap](http://live.gnome.org/RoadMap)

[http://live.gnome.org/GnomePanel/Future](http://live.gnome.org/GnomePanel/Future)

Later, Seeker

---

