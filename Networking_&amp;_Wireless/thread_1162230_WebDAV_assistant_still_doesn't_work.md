---
title: "WebDAV assistant still doesn't work"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by Cubytus on 2009-05-17
Hi to all, 

this topic is to try to know why does the server connection assistant still doesn't work in Ubuntu 9.04. The problem was already there in 8.04, and probably before that.

Example:

I do "File>Connect to server"
Here I select Secure WebDAV, enter the adress [www.webdepot.umontreal.ca/Usagers/p0123456](www.webdepot.umontreal.ca/Usagers/p0123456), nothing in"Port", nothing in "Folder", then I put p0123456 as user name. I then click "Connect", enter the password, and it readily displays:


"Erreur : DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Sélectionnez un autre visionneur et essayez à nouveau."

Same goes when I put the "/Usagers/p0123456" in "Folder" after removing it from "Server".

However, when I enter davs://www.webdepot.umontreal.ca/Usagers/p0123456 in the adress bar in Nautilus, there's no problem connecting.

Other problem while connected to this server, usually in Mac OS X Finder, I get the remaining space available, but not in Nautilus. 

Does anyone knows why are there still these problems with WebDAV in Ubuntu?

---

