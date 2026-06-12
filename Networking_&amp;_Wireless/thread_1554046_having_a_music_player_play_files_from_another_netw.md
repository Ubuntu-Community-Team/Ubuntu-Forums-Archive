---
title: "having a music player play files from another networked computer?"
date: 2010-08-16
forum: Networking &amp; Wireless
---

### Post by princeofnam on 2010-08-16
i don't have much space on my individual computers, so i have to keep my music files on my laptop with most of everything else on my PC.  i want to have rhythmbox play music from my networked laptop, but i have a few issues.

for one, my laptop doesn't show up in Places --> Network

two, even if it did. i'm not exactly sure how i could get rhythmbox to do that.  would i have to use SSH? connect everytime?

---

### Post by shoppertrip on 2010-08-16
what's SSH? i was thinking if your music player supports bluetooth, that could be possible.

---

### Post by princeofnam on 2010-08-16
unfortunately it doesn't and neither does my desktop

---

### Post by sikander3786 on 2010-08-16
You don't need to use SSH for that.

What OS is your laptop running? If Windows then it will be simple file sharing, if Ubuntu, you'll have to  use [Samba]("https://help.ubuntu.com/community/SettingUpSamba").

Post back if any queries.

---

### Post by princeofnam on 2010-08-16
both pcs are using Ubuntu.  i thought samba was only necessary for ubuntu <--> windows networks?

---

### Post by princeofnam on 2010-08-17
wait i'm still confused. why do i need a program for cross-platform sharing between two ubuntu machines?

---

