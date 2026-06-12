---
title: "problem with firefox and flash"
date: 2008-06-10
forum: Multimedia Software
---

### Post by seth556 on 2008-06-10
I'm having a problem running flash with firefox. I can watch stuff like youtube videos but when I click on a different video it starts to load and then firefox closes without warning. It's been happening a lot and is getting very annoying. How can I fix this?

---

### Post by seth556 on 2008-06-10
bump. this is getting annoying.

---

### Post by spudicus on 2008-06-10
The problem I'm having is 8.04 is when i go to youtube it asks to install the plugin.  I check the box and install it only to find it ask again once I've reload firefox.  I tried to uninstall and install it from the package manager but firefox still does not see it. How did you get it to work at all?  :)

---

### Post by muadnu on 2008-06-10
> **spudicus said:**
> The problem I'm having is 8.04 is when i go to youtube it asks to install the plugin.  I check the box and install it only to find it ask again once I've reload firefox.  I tried to uninstall and install it from the package manager but firefox still does not see it. How did you get it to work at all?  :)

Try running the following on a terminal:

```
sudo apt-get install flashplugin-nonfree 
```

---

### Post by smlefo on 2008-06-10
I get the same problem as the original poster.  It's a segfault, but I don't know any more than that.  It happened somewhat rarely with Firefox 3 Beta, but now that Firefox 3 has been released, it's happening much more frequently.

Here's my console:

```
(firefox:16148): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:16148): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:16148): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:16148): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:16148): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:16148): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

```

EDIT: Another grab from my console... an interesting note (and possibly a strange fix?) is that when I have two firefox's open, it doesn't seem to crash.  So maybe some people can try opening two firefox's (by typing firefox in the console twice), and seeing how that works for them.

```
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault
```

---

### Post by smlefo on 2008-06-10
I refined my fix (that I don't understand why it works).

Start up two instances of firefox.  I do it by opening a firefox by clicking the button in GNOME, and starting a second by typing the command firefox in the terminal.  In the first firefox, load a YouTube page and hope that it doesn't crash.  Now pause the video, and browse with the second firefox.  No YouTube pages will crash.

I assume this is because the first firefox is somehow keeping flash in memory, so that it isn't de-allocated, and re-allocated, which causes the crash.

Keep in mind I am just playing around, and this is what I found.  Obviously this is not a great fix... but it does get the job done for now.

Let me know if this works for anyone else - it works perfect for me.

~Sean

---

### Post by Paradoxfox93 on 2008-06-11
Works for me as well.  This was getting to be a real pain, but this is a nice cheap fix till the get it sorted out.  I'm having this problem on firefox 2 but i'm reading that it's a known issue in 3.  Souns like we might be using this workaround for a minute...

---

### Post by taiwanfires on 2008-06-15
I was having the same problem until I downloaded flash10 from the adobe site.  

labs.adobe.com/downloads/flashplayer10.html

---

### Post by Mako Eyes on 2008-06-16
> **taiwanfires said:**
> I was having the same problem until I downloaded flash10 from the adobe site.  

labs.adobe.com/downloads/flashplayer10.html

Wow.. that's funny. I was having the problem until I *removed* Flash 10b and reinstalled version 9.

What's up with that?

---

