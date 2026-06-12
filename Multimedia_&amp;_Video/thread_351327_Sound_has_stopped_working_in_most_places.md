---
title: "Sound has stopped working in most places"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by DjKritical on 2007-02-01
Hey there :D 

I'm having some troubles with sound in gnome,

**Here is what's happening:**

The volume control applet has a small red cross next to it and gives me the following error

> No volume control GStreamer plugins and/or devices found.

Any application in gnome which tries to play sounds fails miserably (All videos crash instantly with various error messages in every media player I've tried)

I do hear the drum beats when GDM starts

**Here's what has happened before my sound stopped working**

Recently my main user account stopped working, in an effort to try to get it to work again I have reinstalled GDM (drastic measures) with no success.

In the end I removed the main account and added a new user account.

I have setup my new account with the permissions to use audio through the 'Users and Groups' section of administration.

**Here's what I have tried**

I've tried apt-get install gstreamer* which installed about 30 gstreamer plugins
I've setup my new user with permissions for Audio
I've searched google for ages =)

So...

Any help would be greatly appreciated,

Cheers :)

---

### Post by DjKritical on 2007-02-04
* bump *

---

### Post by DjKritical on 2007-02-06
bump?

---

### Post by DoktorNo on 2007-02-08
Some users on box could have no permission to play sound. Check the /etc/group file, and add (if needed) users to 'sound' group.

---

### Post by DjKritical on 2007-02-08
Yep, I've checked the permissions for the user,

any other ideas? :(

---

