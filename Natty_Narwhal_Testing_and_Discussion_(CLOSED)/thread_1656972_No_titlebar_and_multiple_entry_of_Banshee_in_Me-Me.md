---
title: "No titlebar and multiple entry of Banshee in Me-Menu"
date: 2010-12-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-12-31
Hi,

I have been using gnome-classic for sometime, besides, i have to reload gnome-applets at start, i do not have titlebar in any of the windows.

I have multiple instances of Banshee in me-menu. For some reason when i click volume applet i can't take screenshot.

Thanks.

---

### Post by lidex on 2011-01-02
As for the banshee entries, have a look at:
```
~/.cache/indicators/sound/familiar-players-db.keyfile
```
You may need to edit that.
Are you logging into ubuntu-classic desktop?

---

### Post by donniezazen on 2011-01-02
> **lidex said:**
> As for the banshee entries, have a look at:
```
~/.cache/indicators/sound/familiar-players-db.keyfile
```
You may need to edit that.
Are you logging into ubuntu-classic desktop?

There is no such file. I can't get drop down menus and right click in Unity lately so i am back to ubuntu classic. But i have this problem both in Unity and classic. I have multiple entires several software in usr/share/applications.

---

### Post by lidex on 2011-01-02
> **soham_1207 said:**
>  I have multiple entires several software in usr/share/applications.

That may not be unusual behavior, I have that also although I don't have banshee installed. Doesn't mean they are the same. The .desktop files show in nautilus by the name within the file. You can see the difference by opening gedit and dragging the files into it from nautilus. If they are exactly the same, then delete one.

EDIT:You may be experiencing this bug also:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/690461](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/690461)

---

### Post by mc4man on 2011-01-02
> I have multiple entires several software in usr/share/applications.
There doesn't seem to be anything unusual there, you should have multiple entries in some cases.
Ex. - synaptic
One is synaptic.desktop, the other is synaptic-kde.desktop, both have the same display name - "synaptic".
Remote desktop Viewer - 
one is vinagre.desktop, the other vinagre-file.desktop. (same display name

---

