---
title: "amapche + amarok"
date: 2008-07-20
forum: Multimedia Software
---

### Post by dexter.deepak on 2008-07-20
i have just installed ampache out of curiosity, and am learning to use it efficiently.on watching the wiki page for ampache, there seems to be a connection between amarok and ampache ...but i can understand what has amarok to do with ampache ??
i am also having one more stupid doubt..whether ampache uses my browser's plugins..or the decoders in my operating system ??

---

### Post by TDragon on 2008-08-22
> **dexter.deepak said:**
> i have just installed ampache out of curiosity, and am learning to use it efficiently.on watching the wiki page for ampache, there seems to be a connection between amarok and ampache ...but i can understand what has amarok to do with ampache ??
i am also having one more stupid doubt..whether ampache uses my browser's plugins..or the decoders in my operating system ??

Amarok is a music player/manager like iTunes. It stores your library info within a SQL database. Upon installing and running Amarok for the first time, you are prompted to choose a SQL sever and configure it for Amarok. Choices include, sqllite, mysql, etc. Most people choose to go with MySQL.

Now, I haven't set up Ampache yet, but I would assume that you could have them share the same database.



Hopefully someone will pipe up and give some input on using the two programs in tandem.




Also, since Ampache runs on a websever that can be accessed anywhere. Since the player is web-based, I am pretty sure that the decoding takes place at the system-level on the clients machine (via codecs). So, if you are playing it on the same PC that it is serving on, that PC is decoding. If you are accessing it somewhere else, laptop, etc, that machine is doing the decoding.

---

