---
title: "Cann't write to windows share via places&gt;network"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by g2c on 2010-11-27
Hello,

Using places>networking

Tried to drag files from windows to ubunto: works ok
Tries to drag from ubunto to windows, getting 
there was an error copying the file to 
smb://<computer name>/<folder name>/
permission denied

Thanks in advance for your time

Ubuntu 10.04, Windows Vista home premium
Guy

---

### Post by Der Ritter on 2010-11-27
> **g2c said:**
> Hello,

Using places>networking

Tried to drag files from windows to ubunto: works ok
Tries to drag from ubunto to windows, getting 
there was an error copying the file to 
smb://<computer name>/<folder name>/
permission denied

Thanks in advance for your time

Ubuntu 10.04, Windows Vista home premium
Guy

This is a Windows problem and outside the scope of this forum, but I'll answer it anyway. It's likely that the Windows security settings are set incorrectly.

Look in the sharing settings for the folder under Windows. Make sure "Everyone" can read and write to the folder. Else, when you're connecting to the folder tell Ubuntu to log in as a user on the Windows box who has permission to write to the folder.

---

### Post by g2c on 2010-11-27
Well, I was not reporting a problem but simply calling for help and since it's about networking one must often face more than one machine.

In fact I wouldn't have bothered to play with samba via places>network as I ma satisfied with filezilla server on the Vista box and client on the Ubuntu one BUT, A friend to whom I recommended to use ubuntu has given up because he failed to create a mixed network and as I intend to go soon abroad visiting him I thought it'd be a good idea to practice this mixed OS networking. I am not an IT guy, just a user and was wandering if there was a tutorial; explaining just that: Seeing and manipulating windows files from a Ubuntu box and vice versa (at lesser priority) and without necessitating more understanding than the regular user has.

Thanks

Guy

---

### Post by dandnsmith on 2010-11-27
There are tutorials, which you can find via google queries.

As a rough rule, it is always easier to pull data than to push it, due to file protection. Like other OS, Windows has got progressively harder to use with networking - it is sometimes tricky to say what will work (for example, XP home and XP Pro are quite different, and then Vista once again changed the default group name for networking ...)

---

### Post by g2c on 2010-11-27
OK here is what I did

From Places>Network can only read.
Went to Places>Connect to a server>
Service type: Windows share
Server: <The name of the Windows box> the computer name as in computer properties
user name: <my user name on windows>
Share:<the shared folder on the Windows box>
Folder: left empty
Domain name: left empty
In the next password screen: the windows admin password

The folder will open in read/write/rename

---

### Post by g2c on 2010-11-27
Now would be nice to access from windows the ubuntu box, anyone has an idea?

---

