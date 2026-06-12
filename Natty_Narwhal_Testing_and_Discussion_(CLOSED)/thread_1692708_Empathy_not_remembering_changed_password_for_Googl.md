---
title: "Empathy not remembering changed password for Google Talk"
date: 2011-02-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dearingj on 2011-02-21
I've been using Empathy to chat with friends on Google Talk for some time. The other day I switched on Google's new 2-factor authentication, and created an application-specific password for Empathy. Empathy happily accepted the new password and logged into my account. The problem is, whenever I reboot my computer the saved password gets reset to what it used to be.

I've checked the permissions on the files in ~/.config/Empathy - I have read & write permissions on every one.

Any suggestions?

---

### Post by dearingj on 2011-02-22
Solved this problem by:
1) Closing Empathy
2) Opening up "Passwords and Encryption Keys", a.k.a. Seahorse
3) Deleting the stored passwords for my Gtalk account. For some reason there were two entries, one of which had the current password and the other had the old password. Neither was editable; I could only view and delete them.
4) Closing Seahorse and reopening Empathy
5) Entering the new password in Empathy when asked

---

