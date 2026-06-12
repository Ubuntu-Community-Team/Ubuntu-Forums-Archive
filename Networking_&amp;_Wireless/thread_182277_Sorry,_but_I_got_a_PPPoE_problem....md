---
title: "Sorry, but I got a PPPoE problem..."
date: 2006-05-25
forum: Networking &amp; Wireless
---

### Post by pitzi on 2006-05-25
I tried looking up the forum for a solution, but I didn't find my exact problem.
If there is one, the excuse me for the redundent post.

After my first configuring with the pppoeconf, all was well. pon and poff are working
fine.

Point is that after logging out, restarting or anything of the such I must use the "sudo pppoeconf" command all over again so that the connection will stay stable.

I read in some post that the whole "Save Sessions" could do the trick, but as far as I figured it means that little checkbox on the top of the "logout" window. no?

Anyway, I will appreciate any help in the subject.

---

### Post by Darkling on 2006-05-26
Ive just had the same problem, and while I DO have a fix, Its almost definitely not the ideal.
The problem is that the password is not saved when you configure the connection. I solved this temporarilly by adding a password field to the dsl-provider file.
Obviously this is less than ideal since your password is stored as plain text in the file.

---

