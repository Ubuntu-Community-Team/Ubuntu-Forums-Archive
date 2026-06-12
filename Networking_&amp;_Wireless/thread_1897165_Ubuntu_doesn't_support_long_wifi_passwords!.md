---
title: "Ubuntu doesn't support long wifi passwords?!"
date: 2011-12-18
forum: Networking &amp; Wireless
---

### Post by 2BE4E27E1A77D1 on 2011-12-18
I just installed a fresh copy of ubuntu-11.10-desktop-i386 and tried to connect to my wifi but when I paste the 63 characters long password in Wireless Network Authentication, it gets cut off somewhere in the middle, and can't click Connect. 

doesn't Ubuntu support long passwords?! :confused:

---

### Post by praseodym on 2011-12-18
Did you copy/paste the key from windows with the windows notepad choosing CTRL+A for "mark all"? Only mark the key itself! Linux does not use the "Byte-order-mark" like windows texteditors, this mark is interpreted as sign. Linux systems consequently use the system encoding.

---

### Post by 2BE4E27E1A77D1 on 2011-12-19
the copy/paste is fine, I tried pasting in a new document in gedit and all the 63 characters are there but the problem is I can't even type anything in **Key:** after the 26th character cut off.

---

### Post by haqking on 2011-12-19
> **2BE4E27E1A77D1 said:**
> the copy/paste is fine, I tried pasting in a new document in gedit and all the 63 characters are there but the problem is I can't even type anything in **Key:** after the 26th character cut off.

are you choosing the right encryption, if you are using WEP 128 then it is 26 chrs HEx.

make sure you have chosen WPA/WPA2 etc for longer characters

---

