---
title: "ssh transfer!!"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Deicider on 2009-12-15
ok,i managed to established connection server-client through terminal ,i can access the server through the client pc,but i dont know how to Copy files from the server to the client or vice versa.
What commands do i use to transfer files from one to another?

---

### Post by s3MA00RRNY on 2009-12-15
You have to have an FTP server set up on your computer that's only localhost accessible. Then you need to set a few options in your sshd config files.

---

### Post by s3MA00RRNY on 2009-12-15
SSH stands for Secure SHell. Once you log in, it functions exactly like the computer you are logged in to. That's why there's no file transfer.

---

### Post by callan79 on 2009-12-16
> **Deicider said:**
> ok,i managed to established connection server-client through terminal ,i can access the server through the client pc,but i dont know how to Copy files from the server to the client or vice versa.
What commands do i use to transfer files from one to another?


Hi Deicider,

Like pcdude2143 said, once you have an SSH connection to the server, you're actually controlling the server ... SSH isn't really a file sharing protocol.

However, you can use SSH to copy one file at a time ...

If you're sitting on the client machine, in terminal, and you want to grab a copy of photo.jpg which is on the server, you could do this :

Let's assume your username on the SERVER is fred and your password is 1234, and the server's IP is 192.168.1.1. The file is in fred's home folder...

Let's also assume the username on the CLIENT is sally, and you want to save the file into sally's home folder...

```

scp fred:1234@192.168.1.1/home/fred/photo.jpg /home/sally/

```

This is handy, but really only good for one file at a time.

If you want the ability to manage multiple files etc, you could use the CONNECT TO SERVER option on the Ubuntu PLACES menu. This will give you access to the other machine's file system. Or you could set up FTP/Samba file sharing on the server ...

Cheers
Callan

---

