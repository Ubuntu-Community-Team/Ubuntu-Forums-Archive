---
title: "Internet radio requires text/html decoder plugin"
date: 2008-06-01
forum: Multimedia Software
---

### Post by Ertai88 on 2008-06-01
I'm running Xubuntu 8.04 with Rhythmbox 0.11.5. I'm having problems using internet radio - some require a html/text decoder plugin, others text/uri-list. I have no clue what these mean. Regular music off my hard drive works fine. What packages do I need to install to get radio working?

Thanks,
-Ertai88

---

### Post by wolfen69 on 2008-06-01
which internet radio are you trying to listen too?

---

### Post by Ertai88 on 2008-06-01
Ah ok, the station that needed the text/html had the wrong address - it was pointing to a YouTube video xD

The stations needing text/uri-list are the defaults that come with Rhythmbox - CBC Radio 1, etc.

---

### Post by Ertai88 on 2008-06-03
I don't know if this actually did something, but for future reference,  installing libgnomevfs2-extra seems to have done something. Its also supposed to be a dependency for Rhythmbox.

---

### Post by quack on 2008-07-31
Excellent - many thanks.

I was getting this error on a fresh install of Xubuntu 8.04 trying to play internet radio in Rhythmbox. Found this thread through a google search.

Installing libgnomevfs2-extra fixed it for me.

---

### Post by unix1adm on 2009-01-07
I have this same issue on a new install. I do have this fileset installed.
libgnomevfs2-extra But I still get the error txt/htmp converter needed.

I am trying to go to wwww.937mikefm.com

---

### Post by mike-g2 on 2009-03-04
I'm having the same problem with a std. hardy install.  Anyone have any ideas?  Is it that the CBC stations listed are wrong?

Look forward to any suggestions.


Mike

---

### Post by mike-g2 on 2009-03-04
To reply to my own reply.

It does seem to be a problem with the urls.

I found the following discussion and links from it useful.

[ first thread]("http://ubuntuforums.org/showthread.php?t=1064584&highlight=decoder+plugin+rhythmbox") and [second thread]("http://ubuntuforums.org/showthread.php?t=1071128")

---

### Post by vietvet72 on 2009-04-08
After std Xubuntu Hardy install, Rhythmbox was not playing internet radio. Also got error message saying I needed Magnatune etc plugins. Going directly to a website, I could hear the radio that way. Following the above suggestion to install libgnomevfs2-extra, I installed. This worked perfectly. Rhythmbox now plays and I can also see the Magnatune etc logos. 

Thanks guy!

---

### Post by FeTTo on 2009-12-23
same problem....problem was URL..dont copy link location..go to properties and take that link..problem solved..i go through shoutcast.com

---

