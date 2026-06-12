---
title: "Sharing folders"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by tom56 on 2009-04-12
Hi

I have shared a folder by logging in as me, right clicking the folder, clicking share and allowing guest access. This works fine :)

My girlfriend has an account on my computer, and when she is logged in the files aren't being shared. This means our housemate can't watch my shared videos when my girlfriend is on the computer, which is bad because she promised to make cookies if I shared Heroes with her :)

I know I could share the folder again from my girlfriend's user account, but I'd rather have it shared by all users, so that if another account was added to the computer, I wouldn't have to share the folder again from the new account too.

Any help appreciated, thanks
Tom

---

### Post by dmizer on 2009-04-12
You'll need to configure a samba server then. Please see the first link in my sig :)

---

### Post by tom56 on 2009-04-12
I think samba's already running since the folder is already accessible. Trouble is it only works when I'm logged in.

EDIT: Also, that tutorial looks damn complicated

---

### Post by dmizer on 2009-04-12
That tutorial is a bit complicated but if you follow it carefully you will have a working share that will be available no matter who is logged in.

Yes, samba is running on your machine, but it's only running in user space. If you want your samba share to be available no matter who's logged on, you have to create a samba server according to that howto.

If you have questions or need help, just ask! :)

---

