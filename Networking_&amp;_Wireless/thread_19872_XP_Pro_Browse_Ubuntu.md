---
title: "XP Pro Browse Ubuntu"
date: 2005-03-14
forum: Networking &amp; Wireless
---

### Post by Gordon Freeman on 2005-03-14
Hi everyone,
                     I recently installed Ubuntu (my first Linux) and it is going well. I have it up and running on my network and can connect to my XP Pro machines fine (installed Samba). However when browsing from my XP machines, I can see the Ubuntu pc, but when i go to it it prompts for a username and password, and i can't make one work (local, remote, administrator). This seems strange because none of my other machines have a problem like that, and its only when browsing from Xp to Ubuntu.
                   Makes me think it's something i have to configure on the Ubuntu machine, like sharing a file etc. I set it to allow remote tcp connections etc, but still the same problem.
                   Can anyone help? Thanks in advance!

---

### Post by brousch on 2005-03-14
Did you add a user to samba? Samba does not automatically pick up your unix users, so you have to add one manually.

Assuming your login name is "gordon" and your password is "blah", use this command:

[FONT=Courier New]sudo /etc/samba/smbpasswd -a gordon[/FONT]

When it prompts for the password, type "blah" without the quotes.

Then when you try to connect to the share on the Ubuntu computer, use "gordon" and "blah" as the login and password.

---

