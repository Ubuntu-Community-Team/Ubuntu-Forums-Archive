---
title: "ssh -X errors"
date: 2010-10-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-10-09
I am getting errors when trying to open nautilus from 10.10 using ssh -X to manage my remote machine running 10.04, I will have to post the errors later this afternoon when I get my server reinstalled.

---

### Post by CharlesA on 2010-10-09
What sort of errors are you seeing?

This is what it says for me:

```
charles@lynx:~$ nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

Which looks.. normal, since nautilus file sharing isn't enabled by default.

Running gedit doesn't show any errors.

---

### Post by tad1073 on 2010-10-09
No, that is not it, When I am ssh -X'd into my 10.04 server and call nautilus it throws up a bunch of errors which I will have to post later when I get it reinstalled.

---

### Post by tad1073 on 2010-10-09
well, I reinstalled ubuntu server 10.04-1 and I am not getting the errors anymore, it just times out every now and then.

---

