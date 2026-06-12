---
title: "Rhythmbox searches for non-existant plugins."
date: 2009-05-18
forum: Multimedia Software
---

### Post by nosushi4you on 2009-05-18
Everytime I play a song in rhythmbox, it asks me to search for a application/smil decoder. It can't find any, so I have to close the box out. This happens *every time*. Is there any way to disable searching for plugins? This only happened once I updated to 9.04.

---

### Post by nosushi4you on 2009-05-18
EDIT: Nevermind. I figured it out. Turns out rhythmbox couldn't read some playlist file I had in my music folder from Windows. I deleted it; problem gone! :)

---

### Post by mafrica on 2009-05-28
Is there another solution to this?  I'm having the same issues,  and it's not overly practical to delete anything that isn't music.   

Is it rhythmnbox or gstreamer that pops up these messages?

---

### Post by fallingleaf on 2009-06-04
Workaround is to uncheck "Watch my library for new files" in the Music tab in prefs, but this is not ideal because I *want* to watch for new files :)

Anyone know another solution?

---

### Post by SPARTAN-118 on 2009-06-10
I have the same problem. I don't like how in iTunes, you have to continuously add your files, so why would I do that in Rythmbox?

BTW, does anyone know why, when I installed Amarock from the Add/Remove Applications, it is even *less featured* than in kubuntu? There isn't even a Visualiser in that thing!

---

### Post by Yellow Pasque on 2009-06-10
Keep your media in a separate folder from non-media stuff? Another person suggested sending the annoying popup window to a workspace that's not being used.

---

### Post by fallingleaf on 2009-06-10
I hear that Banshee is going to be the new default player in Ubuntu and that Rythmbox is not being actively developed anymore.  I'm thinking of switching.

---

### Post by Yellow Pasque on 2009-06-10
Do you have a source on that?
Rhythmbox is still being developed AFAICT: [http://mail.gnome.org/archives/rhythmbox-devel/index.html](http://mail.gnome.org/archives/rhythmbox-devel/index.html)

---

### Post by fallingleaf on 2009-06-11
Actually I got that a little wrong.  They are considering switching to Banshee, but it probably won't happen in Karmic.  This I heard on the Linux Outlaws [podcast]("http://linuxoutlaws.com/podcast/ogg/95") (around 22:30) which gave a reference in the show notes to [http://www2.apebox.org/wordpress/linux/105/](http://www2.apebox.org/wordpress/linux/105/)

What they said on the podcast is that the Rythmbox maintainer has said he will stop active development.  Researching this got me to the Rhythmbox dev mailing list archives which turned up interesting things, including mention of the problem we're discussing on this thread, which is supposed to be getting fixed: [http://mail.gnome.org/archives/rhythmbox-devel/2009-May/msg00034.html](http://mail.gnome.org/archives/rhythmbox-devel/2009-May/msg00034.html)

Anyway, the relevant items I found regarding development stopping are [this one,]("http://http://mail.gnome.org/archives/rhythmbox-devel/2009-February/msg00029.html") which looks kind of bad, and [this later clarification,]("http://mail.gnome.org/archives/rhythmbox-devel/2009-March/msg00042.html") which looks a little less bad.

---

### Post by mafrica on 2009-06-11
Unless you click yes to the "search for plugin" dialog,  Rhythmbox stops scaning your watch dir.  

 As for banshee,  I like it,  but Rhythmbox is way faster with larger libraries,  which is why I use it. 

I've searched high and low for any options to alter,  either using gconf-editor  or in ~/.gstreamer.010/    but there isn't really
anything that seems to adjust this behaviour.   I think there
is a recently released gstreamer,  not sure if that would help..

---

