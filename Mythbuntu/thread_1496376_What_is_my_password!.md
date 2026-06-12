---
title: "What is my password?!"
date: 2010-05-29
forum: Mythbuntu
---

### Post by sinkyboy2000 on 2010-05-29
When in the frontend of Mythtv, when I select utilities/setup > setup, I'm asked for a password.  I've tried my root password and my mysql password (and no password) but none works.  Does anyone know a way of finding the password or changing it.

I don't remember being asked for it before when entering setup.

---

### Post by ian dobson on 2010-05-29
Hi,

Have a look at mysql.txt on your backend the file is usually in  /etc/mythtv/mysql.txt or in the home directly of your mythtv user.

a "locate mysql.txt " from the terminal prompt will list all files with the name mysql.txt 

Regards
Ian Dobson

---

### Post by matt06 on 2010-05-29
Are you talking about a setup PIN required to change any settings in Myth?

---

### Post by sinkyboy2000 on 2010-05-30
> **matt06 said:**
> Are you talking about a setup PIN required to change any settings in Myth?

Well don't I feel like an idiot!  Yes, it was the PIN.  It should say PIN rather than password.

Thanks so much.

---

### Post by matt06 on 2010-05-30
No problem!  Been there before myself.  Glad you got it worked out.

---

