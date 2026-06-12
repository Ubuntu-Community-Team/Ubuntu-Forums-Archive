---
title: "Controlling a Samba User"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by kid1000002000 on 2011-10-02
Hello world. I host a server on a home network and have a folder I want to control access to. My understanding is that I can make a new samba user, with a password, to limit access to any particular share.

Here is where my question comes. To make this samba user, it is tied to making a user on the server itself. I REALLY don't want the user to have access to the server; to be able to have an option to login from the server's monitor, or to even have a "Home" drive. All I want is a "guest account" that is passworded, a folder users can access using samba. I do not want them to have ANY OTHER access to the server.

I am concerned that creating a "samba user" will not meet my goals. Thank you for helping me.

---

### Post by kid1000002000 on 2011-10-06
bump

---

### Post by Dangertux on 2011-10-06
You can use the following command to add a user with no home directory and no shell access.

```

sudo useradd -g usersgroup -d /dev/null -s /dev/null user

```

Hope that helps.

---

