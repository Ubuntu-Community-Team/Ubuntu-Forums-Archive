---
title: "Shuting down Windows from ubuntu"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by nunojpg on 2010-10-14
I'm trying to shutdown a Windows XP machine from Ubuntu.

```
nuno@sky9:~$ net rpc shutdown -U "Miguel" -I 192.168.1.66
Enter Miguel's password:

Shutdown of remote machine succeeded
nuno@sky9:~$ rpcclient -U Miguel -I 192.168.1.66 -c REG shutdownEnter Miguel's password: 
failed tcon_X with NT_STATUS_DUPLICATE_NAME
Cannot connect to server.  Error was NT_STATUS_DUPLICATE_NAME

```

Both of this commands fail. When I check windows logs, they look as if a "Guest" tried to shutdown the computer. Because of this, if I set the remote shutdown permissions to "Everyone" it works.
So the issue is: Why isn't it being logger in as "Miguel"?

Trying Terminal Server Client to 192.168.1.66 and User Miguel connects easily to the windows machine. So the account and password is correct.

Regards,
Nuno

---

