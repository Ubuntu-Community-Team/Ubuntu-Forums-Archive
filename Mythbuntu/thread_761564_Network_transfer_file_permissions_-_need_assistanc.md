---
title: "Network transfer file permissions - need assistance"
date: 2008-04-21
forum: Mythbuntu
---

### Post by kyfehr on 2008-04-21
Hello All,

I have searched the forum but can't seem to find exactly what I need here. 

I have a network share setup fine. I can access the videos, music and recordings folders fine, however, my problem is sending the files to the myth machine.

When they transfer to the myth machine, I need to physically go to the machine and change the file permissions to allow it to stream through mythweb. 

This is what is happening:

When I transfer the file over the network these are the permission settings that get set

owner: mythtv
access: read and write
group: mythtv
access: read and write
others: none

What I need it to be is
owner: mythtv
access: read and write
group: mythtv
access: read and write
**others: read and write**

How do I set it up to set the "others" permission to read and write automagically.

Thanks in advance for anything.

---

### Post by txcrackers on 2008-04-22
What kind of "network share" is it? I can think of at least 5 different varieties off the top of my head...

---

### Post by kyfehr on 2008-04-22
Sorry.. Thought I had written the type in... it is a samba share

---

### Post by txcrackers on 2008-04-22
Got this from the SAMBA manual. I don't have SAMBA running anywhere, but a quick look on [http://samba.org](http://samba.org) revealed:
```
force create mode = 0666
```

---

