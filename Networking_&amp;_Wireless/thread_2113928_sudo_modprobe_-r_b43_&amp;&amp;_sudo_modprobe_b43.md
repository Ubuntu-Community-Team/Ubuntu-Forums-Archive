---
title: "sudo modprobe -r b43 &amp;&amp; sudo modprobe b43"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by KegHead on 2013-02-08
Hi!

This gets me temp wifi:
sudo modprobe -r b43 && sudo modprobe b43

How do I make it perm?

Thanks in advance.

KegHead

---

### Post by Hadaka on 2013-02-08
Here ya go..

```
sudo su
echo b43 >> /etc/modules
exit
```

---

### Post by KegHead on 2013-02-08
hi!

i'll try!

---

### Post by KegHead on 2013-02-08
Hi!

It worked!

Thank you very much. (my wife is happy too!)

KegHead

---

### Post by bkratz on 2013-02-08
I guess you can ignore my posting in your other thread!  Congratulations on getting it done!

---

