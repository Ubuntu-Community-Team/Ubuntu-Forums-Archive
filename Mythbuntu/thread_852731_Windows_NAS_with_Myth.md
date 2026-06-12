---
title: "Windows NAS with Myth"
date: 2008-07-07
forum: Mythbuntu
---

### Post by timcee42 on 2008-07-07
Bit of help!!! Been searching but haven't found much to help.
have a window Xp nas that has about 2tb of Crap that i want to play through my new mythbuntu box (got rid of vista, my god it sucks)
Having an issue getting the shares to work/stay.
i have mounted the shares and at one point could see them all but they seem to of dropped off.
Now i cannot see anything although the mounts are still there, just empty.
Any ideas. I am a beginner so go easy, although i am a windows engineer (why, Linux is way better).

Any help would be great.

---

### Post by nasha on 2008-07-07
You need to place the mount locations in your fstab (/etc/fstab) so that everytime you turn on your PC the locations are mounted.

This is the command you should be using to mount your directories with
```
sudo mount -t smbfs -o username=me,password=mypassword //192.168.100.2/icons ~/iconsXp
```

---

### Post by spokenword on 2008-07-07
word how grand i had a question and it was all right here lol kudos guy

[http://spokenword.pubwebhost.com]("http://spokenword.pubwebhost.com")

---

### Post by timcee42 on 2008-07-13
> **nasha said:**
> You need to place the mount locations in your fstab (/etc/fstab) so that everytime you turn on your PC the locations are mounted.

This is the command you should be using to mount your directories with
```
sudo mount -t smbfs -o username=me,password=mypassword //192.168.100.2/icons ~/iconsXp
```

Cheers this worked....

I am now living the dream....

---

