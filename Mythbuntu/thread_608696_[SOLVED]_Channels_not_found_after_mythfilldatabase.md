---
title: "[SOLVED] Channels not found after mythfilldatabase"
date: 2007-11-10
forum: Mythbuntu
---

### Post by jackliddlephysics on 2007-11-10
Hi I've just installed mythbuntu here in Germany.  Mythbuntu scanned for an found all the channels without any problem.  During the install I selected "no grabber".

Generating the xmltv data elsewhere I then update the database with

```
mythfilldatabase --update --no-delete --file 1 -1 tvprogramm.xml
```

then I restart the backend with (not sure if this is necessary)

```
/etc/init.d/mythbackend restart
```

Starting the front again, the front end fails to see any channel names or data in the programme guide.

Any idea what I'm doing wrong?

Thanks

Jack Liddle

---

### Post by jackliddlephysics on 2007-11-10
OK I submitted the post a little too soon.

Each channel has to be associated with an XMLTV id, either through the backend configuration or with```
 mythfilldatabase --manual
``` I know these ids but I don't know which channel is associated with each one.  I have more than 30 channels, so don't want to do it by trial and error.

The channel ranges are called by mythtv

21-26
E5-E12
E21-E26
S21-S25,S35
SE10-SE20
SE4-SE9

Anyone know of list xmlids associated with these channels?  This is for Germany.

---

### Post by jackliddlephysics on 2007-11-10
OK i will just go through the channels slowly and write down which channel is which.

Apologies for carrying out my internal monologue in public like this.

---

