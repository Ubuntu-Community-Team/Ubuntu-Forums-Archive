---
title: "Missing top and bottom bars"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Yumi on 2011-03-31
I am back on the classical Theme. Was working ok. But this morning the top and bottom bars are not there. Updated today to what I believe is Beta1 but no change.

Any advice on how to get the bars back? Was using clearlooks.

Michael

---

### Post by cariboo on 2011-03-31
I had the same thing a couple of days ago doing iso testing. try:

```
killall gnome-panel
```

If that doesn't work just ry:

```
gnome-panel
```

---

### Post by Yumi on 2011-03-31
I drop  to the promt (CTRL + ALT + F2) and insert the commands. Result:

> killall gnome-panel
gnome-panel: no process found

> gnome-panel
(gnome-panel:1727): GTK-Warning **: cannot open display

The absents of the bars happened before occasionally, but restarting the system helped. This time not. Desktop backgroun is there, Ubuntu is running, Desktop icons are visible and working.

Program windows are also without top and bottom bars. Unable to close them.

Michael

---

### Post by cariboo on 2011-04-01
Do they work in the Classic Desktop with no effects?

---

### Post by Yumi on 2011-04-01
I assume you mean program windows? I can click on a musik icon on the desktop and the player opens. Its playing but the window has no top bar.

---

### Post by Yumi on 2011-04-01
They are back again! I remembered that I used Software-Centre to remove Compiz yesterday as I do not use Unity. I reinstalled it and now my bars are back!. 

I did not know that compiz is required for the classical desktop!

Michael

---

