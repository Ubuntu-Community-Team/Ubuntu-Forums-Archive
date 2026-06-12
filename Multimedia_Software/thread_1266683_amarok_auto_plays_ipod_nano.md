---
title: "amarok auto plays ipod nano"
date: 2009-09-14
forum: Multimedia Software
---

### Post by solarbike on 2009-09-14
I'm running amarok from Ubuntu Intrepid. When I plugin my iPod nano 4G into my box (for charging), amarok immediately starts playing songs from the nano.  Is there a way to turn that off?

---

### Post by lduperval on 2009-09-14
Go to System > Preferences > Removable Drives and Media and change it there.

L

---

### Post by solarbike on 2009-09-15
I see cam, vid cam, web cam, PDA, printer, scaner... but no iPod type device.

---

### Post by mc4man on 2009-09-15
If your using nautilus, which seems likely, (though the thread tag is kde) then the setting is in file management -> media -> music player.

For what ever reason ubuntu dev's have decided you shouldn't know of file management, so it's a hidden menu item in System -> Preferences.

Two of the many ways

To enable, go in terminal, and enable file management in preferences
```
alacarte
```

to access directly, also in a terminal
```
nautilus-file-management-properties
```

Have a look around, several useful setting

---

### Post by solarbike on 2009-09-15
> **mc4man said:**
> 
```
nautilus-file-management-properties
```

That did the trick, just disable the option under media tab

To gain access using GUI, open nautilus (open any folder), go to edit -> preference.

---

