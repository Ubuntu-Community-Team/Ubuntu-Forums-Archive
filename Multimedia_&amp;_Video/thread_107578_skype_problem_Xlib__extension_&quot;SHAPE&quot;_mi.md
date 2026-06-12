---
title: "skype problem Xlib:  extension &quot;SHAPE&quot; missing on display &quot;:0.0&quot;.
Xlib:  extension &quot;S"
date: 2005-12-23
forum: Multimedia &amp; Video
---

### Post by jamaas on 2005-12-23
I'm using Breezy on a dell d410 notebook and skype worked fine until recently ... went away so I reinstalled and now I get this error  message.

Xlib:  extension "SHAPE" missing on display ":0.0".
Xlib:  extension "SHAPE" missing on display ":0.0".
Xlib:  extension "SHAPE" missing on display ":0.0".


Sorry, I know this is an old one but I've dug around and not found anything, point me in the right direction!

Thanks

Jim

---

### Post by N8K99 on 2005-12-23
pretty sure that if you look at the wiki.ubuntu.com/Skype and use the easy method that is listed then things should work out for you. 

just to be sure.

add the following to you /etc/apt/sources.list

deb [http://www.paul.sladen.org/debian](http://www.paul.sladen.org/debian) all skype

then apt-get update

apt-get install skype

This got Skype onto my computer and runs it. Now I haven't had any luck with people hearing me when I try to talk to them. It may be that OSS is not doing the trick that it is uspposed to tdo for me. I was hoping to find some answers to this.

---

