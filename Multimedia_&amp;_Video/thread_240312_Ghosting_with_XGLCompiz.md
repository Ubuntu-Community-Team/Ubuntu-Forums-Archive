---
title: "Ghosting with XGL/Compiz"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by lethallogic on 2006-08-20
Hello,

I recently setup XGL/Compiz on my ubuntu Dapper and evrything works great and looks really good. Except that I have ghost images of the window decorations for windows I have already closed! I am sure there is a setting somewhere that gets rid of that, was just wondering if someone could help me out. I have been tweaking the options to no avail for a long time now.

I have an nvidia card, and all plugins seem to work except "water" which I really don't care about, just want the ghost windows to go.

Attaching a scrrenshot to explain better than I. If this is not the right forum for this, could someone please point me to the right place to ask this question?

Thanks.

---

### Post by ubuntu_demon on 2006-08-22
I moved your thread to the video & sound section.

---

### Post by playmesumch00ns on 2006-08-24
I get the exact same problem. I tried posting on the compiz forums, but got no reply there either.

I'd be very interested to know if someone has a solution!

---

### Post by lethallogic on 2006-08-28
[Play...] I switched off the state and trailfocus plugins and the problem seems to have diminished considerably. Could you try that and confirm that the same applies for you?

Thanks.

---

### Post by playmesumch00ns on 2006-08-29
Hi, I found mention of minimize being a possible cause somewhere. Turning minimize off indeed fixed the problem for me.

On closer investigation I found that reducing the speed of the minimize effect also stopped the ghost windows appearing.

---

### Post by kgolden on 2006-09-01
I'm seeing this as well, but only for "popup windows" from a java-based XML editor (OxygenXML).  Slowing down minimize created ghosting effects for other windows.  Removing trailfocus solved the problem but since I *like* trailfocus, I excluded "com-install4j-runtime-Launcher" for trailfocus (WM_CLASS).  If you can't fix the problem, fix the symtoms, eh?  ;)

---

### Post by lethallogic on 2006-09-02
Slowing down minimize and with all other plugins on, I am not having this problem anymore. Full XGL/Compiz sans any discomfort. :-)

[kgolden's] solutions seems to be very good for ghosting effects due to a particular application.

[play] Could you also update the query you started in the Compiz forums so that in case the developers are looking at this issue they have an idea as to what worked for us?

Thanks all,
Lethal

---

### Post by kgolden on 2006-09-03
Looks like there's something between my setup and Java pop-ups since I'm also seeing issues with Yahoo Games popups (WM_CLASS=sun-plugin-navig-motif-Plugin)

Dunno if this is something about my setup or an issue between sun-java5 and AMD64 but it's nice (for certain values of nice) to see a pattern emerge.

---

