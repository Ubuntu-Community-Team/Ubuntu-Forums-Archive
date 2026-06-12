---
title: "Newbie's quick and dirty methods for connecting to a University WebDAV shared drive"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by Jaunty_Joe on 2010-09-29
Hello all!  I asked for help on my university's forum in connecting to the WebDAV drives, as needed for a class.  I got one response from a cat that gave me two sets of instructions, quick and easy.  The first method is for 10.04 - 

GUI
1. Places -> Connect to Server (Make sure you've got the correct service type and server, username/pword etc...)

The second is:
Command Line
1. $ sudo apt-get install cadaver
2. $ cadaver (url)

This is one of my first posts, so please forgive any faux pas' I just committed!  Also, if this is all common knowledge and I am just an idiot, please just disregard instead of flaming me.  I was so happy it worked like butter, I  just had to share for any other n00bs out there like me. Thanks :D

---

### Post by grahammechanical on 2010-09-30
I too am new. This is a self-help forum. If new people like us did not either ask questions or try to provide answers then this forum would become slow and small. And we do have a code of conduct and moderators that are on the watch.

Regards

---

### Post by Greg_Brown on 2010-10-27
Hi!  I have the same requirements.  I've been able to connect to my college's webdav using your first instructions, but something odd happens.

ODT files, the file type for OpenOffice, are "not found."  I can't download them or copy them or open them.  The icons don't look like ODT files look locally; the symbol suggests they are perceived as binary files only.  Other file types work OK. 

Have you worked with *.odt files?  How'd it go?  Thanks!

G

---

### Post by SeijiSensei on 2010-10-27
Might be a case-sensitivity problem.  Perhaps they end in .ODT?

Kubuntu users can enter a webdav://server URL in the address bar of Dolphin or Konqueror to accomplish this task.  I don't know if that's supported in GNOME myself.

---

