---
title: "Followed NetworkManager tut, doesn't work..."
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by Termight on 2006-06-04
At least, not completely.  nm-applet, NetworkManager and NetworkManagerD come up just fine, but they need to be killed and then restarted with sudo before anything will work.  Then they work just fine, in fact I'm posting using my wireless card right now!  This feels like a permissions problem to me, as if they might be starting without privs for the network card.  The tut I followed is [here]("http://www.ubuntuforums.org/showthread.php?t=125150").  I'm a bit of newbie, so there's probably an easy solution but I can't find it :rolleyes:

---

### Post by bswilson on 2006-06-04
Based on the tutorial, you have a directory called **~/wpa**, right?  I believe you should check those permissions first thing.  What do they show?

```
ls -alF ~/wpa
```

The above command should tell you what the permissions are.  Assuming you don't have the right permissions, you might need to modify them to something more.

```
chmod o+rwx ~/wga
```

I'm assuming that you didn't create the **~/wpa** folder as *root* or with *sudo.*  The above command gives the owner (you) read, write, and execute permissions for that folder.

---

### Post by marcw on 2006-06-04
[QUOTE=bswilson]
```
chmod o+rwx ~/wga
```

I'm assuming that you didn't create the **~/wpa** folder as *root* or with *sudo.*  The above command gives the owner (you) read, write, and execute permissions for that folder.[/QUOTE]

Almost.  "o" in your example above actually stands for "others".  For owner, the correct letter would be "u".

---

### Post by bswilson on 2006-06-05
**Ack!**  Yes, that's my bad.  *USER,* owner, group.  :-)

---

### Post by Termight on 2006-06-05
Permissions before 

```
chmod u+rwx : drwxr-xr-x 5 greg greg  4096 2006-06-04 16:40 wpa
```

and everything inside the folder has the same permissions from the looks of things.  Should I still be running chmod o+rwx?  I've narrowed it down to NetworkManager.  That's the only program that has to be killed and restarted for it to work.

---

