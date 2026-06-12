---
title: "slow internet in ubuntu 11.10"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by Smurf1979 on 2012-02-19
Hi my internet is really slow both in wifi and with cable, but in windows it is fine, can anyone help?

---

### Post by roelforg on 2012-02-20
I'm gonna quote the onofficial guide of stuff to include when asking for help regarding network (PM me when you've got more questions, i never check up on threads so i advise the pm option).

[quote user="The Onofficial Guide Of Stuff To Include When Asking For Help On The Ubuntu Forums (Chapter Network/Internet issues Sub-section No/Slow Internet)"]
===== THE ONOFFICIAL GUIDE OF STUFF TO INCLUDE WHEN ASKING FOR HELP ON THE UBUNTU FORUMS =====

==== Networking ====

== No/Slow Internet
The output of (run from root console (sudo bash)):
```

ifconfig -a
cat /etc/network/interfaces
uname -a
cat /etc/resolv.conf
lshw -C network #this can take a while
# ... Add More As Needed Or Possible ...

```
[/quote]

It's generally better to give too much info than not enough.

---

