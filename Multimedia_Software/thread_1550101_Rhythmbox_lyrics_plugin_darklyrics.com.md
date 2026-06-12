---
title: "Rhythmbox lyrics plugin: darklyrics.com"
date: 2010-08-10
forum: Multimedia Software
---

### Post by JonasDK on 2010-08-10
Hello everyone

I listen to metal a lot using Rhythmbox, but the lyrics plugin can't find any lyrics very often. There should be a way to add the website [www.darklyrics.com]("http://www.darklyrics.com") to the lyrics plugin. I found this link: [http://www.mail-archive.com/rhythmbox-devel@gnome.org/msg04858.html](http://www.mail-archive.com/rhythmbox-devel@gnome.org/msg04858.html), but I don't know how to work this out... My Rhythmbox has version 0.12.8

Can anyone help me with this please?
Thanks,
Jonas

---

### Post by JonasDK on 2010-08-13
Does anyone know please?
There should be a folder where I can edit the songlyrics plugin.

Thanks,
Jonas

---

### Post by monikgtr on 2010-08-23
> **JonasDK said:**
> Does anyone know please?
There should be a folder where I can edit the songlyrics plugin.

Thanks,
Jonas

I think this is the folder 
```
/usr/lib/rhythmbox/plugins/lyrics

```

I've got about five different files with the title "lyrics" but I'm not sure about wich one is the one, so, when I check on them, I'll let you know if I could change the search engine to darklyrics.

---

### Post by JonasDK on 2010-08-23
Thanks, I'll check later on today! :)

---

### Post by JonasDK on 2010-08-23
Seems like DarkLyrics needs its own .py and .pyc file and should be implemented in the LyricsSites.py-file, which seems to be the general file where all the sites go.

There is an attachment at that bug-report:
[http://bugzilla-attachments.gnome.org/attachment.cgi?id=162256](http://bugzilla-attachments.gnome.org/attachment.cgi?id=162256)

Don't know where that should go though. Is that the Python code for the DarkLyrics.py-file?

Thanks,
Jonas

---

### Post by monikgtr on 2010-08-24
I figured it out, you have to go to Gconf (alt+F2 gconf-editor) and there you navigate to apps -> rhythmbox -> plugins -> lyrics -> engines

Double click on engines and add darlyrics.com

---

### Post by JonasDK on 2010-08-27
> **monikgtr said:**
> I figured it out, you have to go to Gconf (alt+F2 gconf-editor) and there you navigate to apps -> rhythmbox -> plugins -> lyrics -> engines

Double click on engines and add darlyrics.com

When I do that, that 'engines'-string resets itself when I open Rhythmbox or reboot. Should there appear a darklyrics.com checkbox when I go to Plugins -> Song Lyrics in Rhythmbox too? Because it doesn't.

Thanks!

---

### Post by Disident on 2010-12-08
Hello!
I got Rhythmbox with DarkLyrics by default with installation, but anyway Rhythmbox can't find any lyrics. Not from DarkLyrics (some metal) nor even some very popular thing (like The Beatles etc.). What can be the problem?
(It's not connection problem, Last.fm works fine).

---

