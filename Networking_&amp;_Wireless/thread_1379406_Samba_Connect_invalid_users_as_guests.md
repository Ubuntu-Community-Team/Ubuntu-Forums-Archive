---
title: "Samba: Connect invalid users as guests?"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by dummptyhummpty on 2010-01-12
I'm not sure if this is even possible and I've tired searching, but I can't seem to figure it out. I have a few shares setup in Samba. I want them to prompt for a username and password. If an invalid user/pass is entered I want the user to be authenticated as a guest.

I've tried the following:

guest account = nobody
map to guest = bad user
security = user

This prompts the user for user/pass, but if they enter anything invalid, it just keeps prompting.

adding public = yes (or guest = ok). Doesn't prompt and just connects every one as guest.

Let me know if you need to see more of my smb.conf file.

---

### Post by Morbius1 on 2010-01-12
You're going to have to pass that by me one more time, real slow like.

If you use guest = ok, everyone including your Aunt Tilly will have access.

But what you want is to require authentication and when authentication fails you grant them access as guests. The net result is that everyone including your Aunt Tilly will have access.

I'm missing some subtlety about your requirements.

---

### Post by dummptyhummpty on 2010-01-12
> **Morbius1 said:**
> You're going to have to pass that by me one more time, real slow like.

If you use guest = ok, everyone including your Aunt Tilly will have access.

But what you want is to require authentication and when authentication fails you grant them access as guests. The net result is that everyone including your Aunt Tilly will have access.

I'm missing some subtlety about your requirements.

Yes. I want the guest users to have read only access, while authenticated users should have read/write access. I've set the correct permissions on the directories and I have "write list = @users". The users group contains the users on the system who will be logging in and who I want to have read/write access. Sorry for not mentioning this before, I got distracted and hit submit before double checking.

---

### Post by Morbius1 on 2010-01-12
What happens when you create the share as read only but include the write list:

[share]
path = /path/to/share
guest ok = yes
read only = yes
write list = @users

This does not work?

---

### Post by dummptyhummpty on 2010-01-12
> **Morbius1 said:**
> What happens when you create the share as read only but include the write list:

[share]
path = /path/to/share
guest ok = yes
read only = yes
write list = @users

This does not work?

I won't be home for about 30mins, but I think when I tired that I was no longer prompted for user/pass and thus was given only read access. I'll try it again to confirm.

---

### Post by dummptyhummpty on 2010-01-12
> **Morbius1 said:**
> What happens when you create the share as read only but include the write list:

[share]
path = /path/to/share
guest ok = yes
read only = yes
write list = @users

This does not work?

Nope, didn't work. It never prompts for username/password and the share is mounted read only.

---

### Post by dummptyhummpty on 2010-01-14
Anyone else have any ideas?

---

