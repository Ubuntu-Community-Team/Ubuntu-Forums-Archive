---
title: "ssh network only one direction"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by ajgreeny on 2010-05-25
I have a laptop with ubuntu 9.10 and a desktop with ubuntu 10.04.  The laptop is connected with wireless and the desktop by cable, no problems there.

Both machines have dchp IP addresses, which I know are correct when I try to connect the machines using openssh-server and openssh-client installed on both computers.

Today my desktop has an IP of 192.168.0.2 and the laptop 192.168.0.8.  I can connect from desktop to laptop using the menu item Places ->Connect to server ->and entering ssh in the top box and *username*@192.168.0.8 in the servername box, enter password for the laptop, and connected, no problem.

However, for some reason I can not do the same in the opposite direction, I just get the error message, ```
Cannot display location "sftp:// blah-blah@192.168.0.2/"
Connection refused by server
```

Anyone got any clues about this, and why it is only a one way connection.

---

### Post by Iowan on 2010-05-25
Probably a moot point - and not at all related:
You try an "SSH" and get an "SFTP" error?
Have you tried SSH from terminal?

---

### Post by ajgreeny on 2010-05-26
> **Iowan said:**
> Probably a moot point - and not at all related:
You try an "SSH" and get an "SFTP" error?
Have you tried SSH from terminal?
I hadn't, but have now just done so.  I have never used ssh in terminal so it is possible that I am not doing things quite right as far as the command is concerned, but again from my desktop I can get into the laptop with a simple ```
ssh username@192.168.0.8
``` but I can not go in the opposite drrection and get **connection refused by server**.

What on earth is going on here?  It must surely be something very simple.

---

### Post by puppywhacker on 2010-05-26
SSH uses a client and a server and to me it sounds like you have installed an sshserver on your laptop, but no server on your desktop.

You can in a terminal install it with
```
sudo apt-get install openssh-server
```


P.S. Note that also firewalls result in "connection refused by server", you should not block port tcp/22

---

### Post by lavinog on 2010-05-26
> **ajgreeny said:**
> I hadn't, but have now just done so.  I have never used ssh in terminal so it is possible that I am not doing things quite right as far as the command is concerned, but again from my desktop I can get into the laptop with a simple ```
ssh username@192.168.0.8
``` but I can not go in the opposite drrection and get **connection refused by server**.

What on earth is going on here?  It must surely be something very simple.

```

ssh -l username ipaddress

```

you can leave off the -l username if your username is the same.

I have noticed in the past that if the host key changes on the server, the client will not be able to connect with nautilus until the offending key is removed from .ssh/known_hosts.  In the past the only the command line ssh gave a message about the issue...I don't know if they fixed this in Lucid yet.

---

### Post by ajgreeny on 2010-05-26
OK, all get ready to call me a blithering idiot!

I said that I had **openssh-client** and **openssh-server** on both machines, because I remembered installing them, or at least the missing server to the desktop machine.

What I forgot was that I had installed openssh server to another install of lucid that I use to test things (such as ssh) on that desktop machine, and had not installed it to the main install that I use as my working OS.  Thanks to puppywhacker for giving me the clue about where to look.

All is now working just as I wanted it to, so thanks all round to those who tried to help.  I really must remember to check the obvious in future, and not start asking questions before I have properly checked, and double checked, and then checked again.

Thanks again for trying to help me.
Blithering idiot.

---

### Post by Iowan on 2010-05-26
> **ajgreeny said:**
> OK, all get ready to call me a blithering idiot!
I don't think so - I've seen some of your other posts.  I think you just wanted to see if we were awake.  It's nice to see a problem *solved* occasionally...

---

