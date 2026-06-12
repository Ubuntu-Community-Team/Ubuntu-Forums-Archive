---
title: "Move mythtv backend/frontend server"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by BillDozer on 2008-02-26
Hi,

I soon have to move my mythtv frontend/backend machine to another location and this will result in a new IP-address for the system. I remember that I read somewhere there are some steps to follow, but I cannot seem to find them anymore (not even with my friend google).

Is there anyone who knows what I have to do? I recall that there should run a script to update the database with the new location.

I am running mythtv on ubuntu 7.04.

Thanks in advance.

---

### Post by .nedberg on 2008-02-26
Run mythtv-setup, in General enter the new IP of your backend (two places if it is master backend) and save the configuration and exit.

You might have to restart your backend now. (sudo /etc/init.d/mythtv-backend restart)

When you start your frontend you will be asked for the new IP. I think you can use localhost here if it is the same machine.

---

