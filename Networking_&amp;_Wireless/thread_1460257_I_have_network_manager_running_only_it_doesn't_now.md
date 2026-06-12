---
title: "I have network manager running only it doesn't now!"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by myjess on 2010-04-22
I had network manager running on my netbook karma install, but when I installed VNC as another display, logged into that other display and accidentally clicked on not to run network manager on startup cause there is already one running, it screwed up the network manager auto startup on my normal netbook display.

I tried adding it back into auto start in settings but that has not worked.

As always, thanks for any help you can give me getting this to auto start again on login, without deleting my kde cache(cos it is setup the way I want it).

---

### Post by Iowan on 2010-04-22
I'm not familiar with the Netbook version, but...
Is Network Manager checked in System>Preferences>Startup Applications?

---

### Post by myjess on 2010-04-23
> **Iowan said:**
> I'm not familiar with the Netbook version, but...
Is Network Manager checked in System>Preferences>Startup Applications?

I don't have System/Preferences/Startup I'm afraid.

---

### Post by iponeverything on 2010-04-23
open a terminal and run:

```

nm-applet&
disown %1
exit

```

or you can remove and re-add the notification area.

---

