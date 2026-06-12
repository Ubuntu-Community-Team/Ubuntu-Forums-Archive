---
title: "Evolution keeps asking for password to one account"
date: 2010-07-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-07-30
I have 4 email accounts setup in evolution and they have been working fine up until today.
Now evo keeps on asking me for the password for one of them and won't accept it, says my username or password is wrong.

I have double checked the account settings and everything is fine and I have also tried logging into the provider from a web browser and it accepts it with no problems.

The thing is, 3 of my 4 accounts are with the same provider and it is accepting the others fine.

---

### Post by ronacc on 2010-07-30
try removing and re adding the account , I've typo-ed a password more than once and its hard to tell from asterisks .

---

### Post by x-shaney-x on 2010-07-30
Definitely the right password, typed it in very carefully well over a dozen times now.
It had the password stored and was working fine.

I have tried removing and re-adding the account, tried restoring evo from a previous backup, tried moving the main evo folder and started from scratch and again all the other accounts are working except this one.

Signed in from a web browser several times throughout the day and signed in every time without issue.
Has evolution been updated at all in the past couple of days?  I don't remember.

---

### Post by philinux on 2010-07-30
> **x-shaney-x said:**
> 
Has evolution been updated at all in the past couple of days?  I don't remember.

Have a look at /var/log/apt/term.log

---

### Post by x-shaney-x on 2010-07-30
I never remember where to look.
It hasn't been updated at all recently so can't imagine what the problem is.

---

### Post by x-shaney-x on 2010-07-31
<sigh> 2 days and still having this problem but I've noticed it's also in lucid.

Still able to login via web browser every time.  Still no problems with other accounts via the same provider and I have now gone to the trouble of trying thunderbird and that has no problems with any account.

---

