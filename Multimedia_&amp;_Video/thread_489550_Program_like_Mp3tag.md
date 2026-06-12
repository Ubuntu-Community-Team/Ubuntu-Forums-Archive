---
title: "Program like Mp3tag"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by alexv305 on 2007-07-01
I used a program called Mp3tag for Windows and I liked it. I was wondering if there was a similar program for Ubuntu. I tried the EasyTag program but it doesnt have a sorting feature to sort by date modified. I was wondering if anyone knows about a better program or what you would recommend.

Thanks

---

### Post by Matt Yun on 2007-07-01
Konqueror (the default KDE file manager/browser/kitchen sink) can display metadata, including id3 tags, and allow you to sort by metadata.  However, you can't edit the metadata directly.

If you need to do batch id3 tag operations (eg. mass tagging, mass file renaming), try  [Audio Tag Tool]("http://pwp.netcabo.pt/paol/tagtool/") (apt-get install tagtool), or [Kid3]("http://kid3.sourceforge.net/") (apt-get install kid3)

I've tried all of the popular music collection software like Rhythmbox, Banshee, Amarok, JuK, etc.  For me, I prefer a combination of Konqueror and Audio Tag Tool.

---

### Post by itsdaveperdue on 2007-07-11
Do you recommend one for the command line?  The ones I've seen don't allow you to tag a genre with "Podcast" since it's not an official genre.

---

### Post by stchman on 2007-07-11
> **alexv305 said:**
> I used a program called Mp3tag for Windows and I liked it. I was wondering if there was a similar program for Ubuntu. I tried the EasyTag program but it doesnt have a sorting feature to sort by date modified. I was wondering if anyone knows about a better program or what you would recommend.

Thanks

Ubuntu has a program called tagtool:

sudo apt-get -y install tagtool

This will allow you to edit the ID3 tags of OGG and MP3 files using a nice GUI.

---

