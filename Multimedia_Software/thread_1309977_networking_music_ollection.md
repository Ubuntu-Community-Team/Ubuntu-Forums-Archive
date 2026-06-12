---
title: "networking music ollection"
date: 2009-11-01
forum: Multimedia Software
---

### Post by scruffz on 2009-11-01
hey i have a dell inspiron 9200 with some decent specs that i just received i was wondering if i could wirelessly have a music and media database on my one ubuntu pc with a tb of music and movies if so what applications would the server pc have to run

---

### Post by Glucklich on 2009-11-01
> **scruffz said:**
> hey i have a dell inspiron 9200 with some decent specs that i just received i was wondering if i could wirelessly have a music and media database on my one ubuntu pc with a tb of music and movies if so what applications would the server pc have to run

By "a tb" you mean 'a Terabyte'?

If so, the answer is no. The limit is 2Gb on the free account. You get 50Gb if you pay 10$ a month.

Edit: Nevermind. My apologies, I though you were asking about Ubuntu One.

---

### Post by unamanic on 2009-11-01
> **scruffz said:**
> hey i have a dell inspiron 9200 with some decent specs that i just received i was wondering if i could wirelessly have a music and media database on my one ubuntu pc with a tb of music and movies if so what applications would the server pc have to run

There are several methods to share data from one machine (server) to clients.  I use NFS as the traditional Unix way of doing things.  But Ubuntu has samba integrarted.  Just rt click on the folder you want to share in Nautilus and hit sharing options, then enable (It may ask to install software at this point, and to log off an back in to configure sharing.).

Next on the Client side just navigate there using Places -> Network.

---

### Post by scruffz on 2009-11-01
i tried that and its not visable under network places on the laptop

---

### Post by unamanic on 2009-11-01
You said wirelessly, make sure you can dont have something like AP Isolation turned on, and can ping back and forth.

I'll see if I can't do an NFS tutorial this evening, but in the mean time you can:
```

sudo aptitude install openssh-server

```

and use Places->Connect to server (connection type ssh).  You'll endup using more bandwidth over ssh, but it's encrypted.

---

### Post by unamanic on 2009-11-01
Please take a look at [http://unamanic.witt-family.net/2009/11/nfs-mounts/](http://unamanic.witt-family.net/2009/11/nfs-mounts/) and see if servers your file share needs.

---

