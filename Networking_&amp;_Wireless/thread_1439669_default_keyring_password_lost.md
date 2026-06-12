---
title: "default keyring password lost"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by mooz123 on 2010-03-26
Hi,

This thread is not a question, but a solution. 

I had set up a new wireless connection, and had to fill in the password every time. Moreover, a new window opened with this message: The application 'NetworkManager Applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked. 
The only thing that worked was to click deny, because I didn't know the password.

There are a lot of threads on the forums with similar situations, but none of the offered solutions worked for me. I suspect they are all a little bit different problems, so I try to specify the situation where I think my 'solution' is applicable:

-you have used the keyring manager before
-the login password you used then is different from the one you use now
-you cannot remember what password it was
-important: you have no passwords stored in your keyring that you cannot replace (obviously, it is not working, so the risk is small)

What worked for me is:
Applications>Accessories>Passwords and encryption keys
Passwords tab
Select entry: 'Passwords login' (you can click on the triangle to see if there is anything worthwile in it)
Edit>Delete

Restart and you have to enter the password once more, but now it is in the keyring that unlocks automatically when you login

I hope this helps someone!
Mark

---

### Post by texpat on 2010-05-03
> **mooz123 said:**
> 
I hope this helps someone!
Mark

Yep, just as it started to become a major headache. Cheers, mate!

---

### Post by n4pgw on 2010-09-04
over a year later, but it helped me :)

---

### Post by SyFo on 2010-11-24
Just wanted to say this worked for me too.  How ever I found it under System>Preferences>Passwords and encryption keys

Might be that I'm using Ubuntu 10.10

Once again, thanks for this posting.

---

### Post by wsalopek on 2012-04-09
[B][I]What worked for me is:
Applications>Accessories>Passwords and encryption keys
Passwords tab
Select entry: 'Passwords login' (you can click on the triangle to see if there is anything worthwile in it)
Edit>Delete[/I][/B]

Above, re the line:  "select entry; Passwords login"

Mine is BLANK....I have nothing there to select...the entire box is blank...I have rebooted, etc etc.

Any ideas?

Thanks...(I'm a ubuntu newbie)

---

