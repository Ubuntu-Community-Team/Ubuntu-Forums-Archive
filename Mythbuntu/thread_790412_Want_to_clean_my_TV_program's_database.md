---
title: "Want to clean my TV program's database"
date: 2008-05-11
forum: Mythbuntu
---

### Post by NarsilAnduril on 2008-05-11
Hi,

I need to load an xmltv file bypassing grabber, so I did a

mythfilldatabase --file 0 /.../tvguide.xml

But my sourceid is not 0 but 1 ...

First I had to delete all "unassigned" channels created by mythfilldatabase -> done

But now, when selecting a show to record, I get every program twice, one assigned to the existing channel, and anothe assigned to no channel ...

Big mess !

How could I clean this ?

Thanks for your your help

Diego

---

### Post by KillerKiwi on 2008-05-11
Clear the program table in mysql and start again... or just wait a couple of days ;)

```
mysql -u mythtv -p xxxxx mythconverg
mysql> delete from program;
mysql> quit
```

I usually use mythweb for editing channels it has a nice easy ui

---

### Post by NarsilAnduril on 2008-05-12
delete from program did it, thanks KK.

Diego

---

