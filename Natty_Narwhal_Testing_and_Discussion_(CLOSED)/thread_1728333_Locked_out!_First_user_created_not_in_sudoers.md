---
title: "Locked out! First user created not in sudoers"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Technosites on 2011-04-13
Hi :)

I recently installed a fresh copy of Ubuntu 11.04 Natty Beta on my server, via USB (unetbootin) using the main release CD iso.

I'm having a strange problem; when I installed I created a user (and password), but never - or at least can't remember, setting a root password. Now, I understand that the first user created should be added to the sudoers (and admin group?) by default right?

My problem is that I cannot sudo, I cannot provide the 'root' user password when asked, I cannot view or edit the sudoers file. So apart from booting into a livecd, napping the passwd hash file and trying to crack the root password, what can I do? I don't really want to format.

I thought I did a fairly straight forward default install, but unless ubuntu coders no longer want the user to have root access to their own system, I think something's gone wrong! I don't really want to have to format again :S

Thanks in advance!
-tech

---

### Post by cariboo on 2011-04-13
Is your user a member of the admin group? To check while running as the user, open a terminal and type:

```
groups
```

If the user isn't, start in recovery mode and type:

```
gpasswd -a <user_name> admin
```

---

### Post by Technosites on 2011-04-14
Hi :)

Thanks for the reply. Unfortunately it seems it is not a member of the admin group, and I can't run that command because you need root access to run it! I'm just gunna reformat if I can't get it working today :S

-tech

---

### Post by coffeecat on 2011-04-14
Could you not boot into recovery mode and add yourself to the admin group with usermod?

**EDIT**: Oops sorry. Just noticed that you installed the server version. Can you boot into recovery mode with that? You can boot into a root shell if you can.

---

