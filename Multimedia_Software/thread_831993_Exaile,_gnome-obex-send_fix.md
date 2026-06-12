---
title: "Exaile, gnome-obex-send fix"
date: 2008-06-17
forum: Multimedia Software
---

### Post by holr on 2008-06-17
I have upgraded to hardy heron and tried using my current fave music player, Exaile, to send files via bluetooth to my phone, only to find that it wouldn't work as gnome-obex-send doesn't exist anymore (superseded by bluetooth-sendto).

So if you want a quick exaile fix:
Close exaile.
```

rm ~/.exaile/plugins/bluetooth.pyc
gedit ~/.exaile/plugins/bluetooth.py

```
Do a Search and replace from "gnome-obex-send" to "bluetooth-sendto" then save. It worked for me, and I could send tunes to my phone again via a nice gui!

Of course, it helps if you have bluetooth-sendto already installed ;-)

---

### Post by atlas95 on 2008-07-30
Thanks for this tweak !!

---

### Post by lapalorky on 2009-04-27
I did:

```
sudo ln -s /usr/bin/bluetooth-sendto /usr/bin/gnome-obex-send
```

The above method didn't work for me, the plugin disapeared when deleting that .pyc file.

---

