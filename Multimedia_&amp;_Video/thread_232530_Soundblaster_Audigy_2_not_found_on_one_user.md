---
title: "Soundblaster Audigy 2 not found on one user"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by spikedupback529 on 2006-08-08
Hi, I randomly recieved an error saying that fsck (the automatic scanning utility to make sure the drives are working properly, from my understanding) failed. I ran it manually, and fsck found multiple errors. I deleted all the problems, and the system started normally. On my user, the sound doesn't work. Ubuntu states that no sound card is installed. However, on the login menu and on other users, the sound card works fine. How would I get Ubuntu to recognize the sound card on my user?

Thanks,
Dale

---

### Post by mlind on 2006-08-09
Is that user on **audio** group ?

---

### Post by spikedupback529 on 2006-08-09
How would I check to see?

---

### Post by mlind on 2006-08-09
> **spikedupback529 said:**
> How would I check to see?

```

cat /etc/group | grep audio

```
Or login as that user, open a terminal and type **groups**.


You can add user to certain group using
```

sudo adduser *user* *group*

```

---

