---
title: "How do I get nautilus/gnome to use kaffeine and not totem"
date: 2008-05-18
forum: Multimedia Software
---

### Post by xanas3712 on 2008-05-18
I don't like totem, at all.  Xine, gstreamer, whatever it's using it's just not a great app IMO.  Kaffeine has always been good for me for removable media.  I used to be able to (in previous ubuntu versions) setup the system to make it use kaffeine, but this doesn't work in Hardy for some odd reason. The file management preferences only has 3 options, and the "movie player" option is of course totem.  The "preferred applications" menu apparently is good for nothing, because it doesn't do anything when I set kaffeine up in the text box on that one.  gconf-editor doesn't seem to let me do anything with this and I'm really at a loss at this point.  The properties when I right click the drive show only that the dvd is a "folder" type, so nothing I add reflects like "movie player" even though many programs could act as a potential replacement.

What do I do in hardy to get this to work the way that I want?

---

### Post by xanas3712 on 2008-05-18
To answer my own question, what you have to do is go to /etc/gnome/defaults.list and change the video-dvd setting to kde/kaffeine-iso.desktop  This will allow you to choose kaffeine on the file management preferences menu.  I was using just kaffeine previously per advice, then I noticed that it was in a subfolder so I tried this and it worked as expected, except it was opening the vob.  I was going to edit the kaffeine.desktop when I noticed kaffeine-iso.  That option worked exactly as expected.

---

