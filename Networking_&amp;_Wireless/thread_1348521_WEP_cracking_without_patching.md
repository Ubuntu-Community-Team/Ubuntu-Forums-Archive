---
title: "WEP cracking without patching"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by j_thatch on 2009-12-07
Last night I successfully was able to crack my own WEP key using backtrack 4 (I know this is no big deal).  Afterwords  I thought to myself, I should try it on 9.10.  Without patching my 4965 wireless driver, or any fancy steps I was able to crack my own WEP.  Did anyone else know this was possible on ubuntu without patching your driver?

---

### Post by wilee-nilee on 2009-12-07
> **j_thatch said:**
> Last night I successfully was able to crack my own WEP key using backtrack 4 (I know this is no big deal).  Afterwords  I thought to myself, I should try it on 9.10.  Without patching my 4965 wireless driver, or any fancy steps I was able to crack my own WEP.  Did anyone else know this was possible on ubuntu without patching your driver?

Fro what I heard cracking a wep is quite easy never tried it though. A wpa can be cracked as well to with a brute force if a weak password is used, never tried it though.

---

### Post by j_thatch on 2009-12-07
I 100% agree. It takes like 3 mins to crack it haha.  I just thought it was interesting that you could do it on 9.10 with a built in wireless chip with ease.

---

### Post by ram130 on 2009-12-17
What are the steps u used? and is their no GUI program available for it?

---

### Post by Grenage on 2009-12-17
WEP can be cracked in minutes; it's a a completely worthless encryption.  For proof and pen-testing, look at Aircrack-ng.  Guides are avail online.

---

### Post by JBAlaska on 2009-12-17
The reason you cracked it on your own WEP connection without a patched driver, is beacuse it was being accessed... and you did not need to do packet injection.

On a Idle WEP AP, it can take hours without packet injection to get the key.

---

### Post by realzippy on 2009-12-17
> **ram130 said:**
> What are the steps u used? and is their no GUI program available for it?

GUI?
SpoonWEP and SpoonWEP2.....
check out Nubuntu....

[http://en.wikipedia.org/wiki/NUbuntu](http://en.wikipedia.org/wiki/NUbuntu)

---

### Post by criser80 on 2010-01-05
For a nice GUI, check this out:
[http://forum.aircrack-ng.org/index.php?topic=6329.msg32945#msg32945]("http://forum.aircrack-ng.org/index.php?topic=6329.msg32945#msg32945")

---

### Post by ram130 on 2010-01-06
> **realzippy said:**
> GUI?
SpoonWEP and SpoonWEP2.....
check out Nubuntu....

[http://en.wikipedia.org/wiki/NUbuntu](http://en.wikipedia.org/wiki/NUbuntu)
> **criser80 said:**
> For a nice GUI, check this out:
[http://forum.aircrack-ng.org/index.php?topic=6329.msg32945#msg32945]("http://forum.aircrack-ng.org/index.php?topic=6329.msg32945#msg32945")



Sweet!! thanks. I gonna try them later on.. the aircrack looks like it got future possible and legal issues soon lol :)

---

