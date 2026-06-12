---
title: "Where does Ubuntu maps the automatic smb folders?"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by MewRS on 2011-01-17
Hi people!

I swear that I searched everywhere for this...

Here's the question: When accessing a smb folder using Run App (Alt + F2) and typing smb://192.168.1.10/data/ Ubuntu creates a shortcut at Places. I'm using this way because it was very hard to map via smb.conf.

So... I was trying to access this via Terminal, but I just have no clue where it's mapped!

May you guys help me out?

Thank you very much!

---

### Post by MewRS on 2011-01-18
Nobody?

---

### Post by redmk2 on 2011-01-18
> **MewRS said:**
> Hi people!

I swear that I searched everywhere for this...

Here's the question: When accessing a smb folder using Run App (Alt + F2) and typing smb://192.168.1.10/data/ Ubuntu creates a shortcut at Places. I'm using this way because it was very hard to map via smb.conf.

So... I was trying to access this via Terminal, but I just have no clue where it's mapped!

May you guys help me out?

Thank you very much!

If you used Nautilus to share the folder then the *usershares *are defined at **/var/lib/samba/usershares**. All of the "Usershare" information is at /var/lib/samba.

---

### Post by Boondoklife on 2011-01-18
I think you are looking for ~/.gvfs

---

### Post by MewRS on 2011-01-24
> **Boondoklife said:**
> I think you are looking for ~/.gvfs

Yeah!!! That's it!

Thank you very very much!

---

