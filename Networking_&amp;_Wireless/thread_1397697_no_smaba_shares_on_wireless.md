---
title: "no smaba shares on wireless"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by Hogosha on 2010-02-03
Samba works fine over ethernet but over wireless i get nothing, i cannot even browse to smb://stargazer/ manually.

smbtree gives me this:

failed negprot: ERRnomem
failed negprot: ERRnomem

---

### Post by ant2ne on 2010-02-03
I got to ask... are you certain you are on the same network. My wife would always complain "I can't get to my share!!" and I'd sigh and ask her "Are you on the correct wireless network?" To which she would say "Well, no."

Can you ping the samba server by name? Goto the samba server and gets its IP, then ping by IP.

---

### Post by Hogosha on 2010-02-04
well, i am sure i am on the same network but there is a new development. 

I can use samba all i want at work but even wired at home i cannot. I did recently reinstall but nothing should have changed from my previous set up.

this one really has me stumped

---

### Post by superprash2003 on 2010-02-04
you didnt answer the question on whether you can ping by ip or name?

---

### Post by Hogosha on 2010-02-04
i can ping ip but not name

---

### Post by ant2ne on 2010-02-04
and can you connect to the samba share by IP?

---

### Post by Hogosha on 2010-02-04
not at all.

I just rewrote my smb.conf file while i was at work so i will try it again when i get home.

---

### Post by Hogosha on 2010-02-04
it seems that if the machine is XP it will show up in my network list, if it is Vista i can get to it but not see it in the list, if it is 7 i cannot access it at all

---

### Post by eggiot on 2010-02-05
Have you looked [here]("http://ubuntuforums.org/showthread.php?t=1169149")?

---

