---
title: "How do I access my Samba/storage server?"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by grs on 2009-02-06
I've got a Samba server set up on a machine running Clarkconnect (based on Red Hat). I can access the Samba share fine from Windows and Mac based PC, accessing it from my Ubuntu PC doesn't seem to be working. If I go to Places/Network then Windows Network/MSHome I can see the  Clarkconnect server and I can even see the folders that are in the Samba shares but I can't open them, it just says unable to mount location.

I also have Samba on the Ubuntu PC, is there a GUI for Samba in Ubuntu?

---

### Post by geoglitch on 2009-02-06
I was having the same trouble.  Seemed that nautilus wasn't getting the right server name to put in the address by using the workgroup name.  I got it working by putting
```
smb://servername
```
in the address bar of nautilus rather than clicking through the Network options.  If the nautilus address bar isn't visible, there's a toggle button beside the folder path list that toggles between button and text-based locations.  You could also try using smbclient to check the server as
```
smbclient -L servername
```

---

### Post by grs on 2009-02-06
Sorry I don't think I was clear.

I can access the server itself and I can see the shared folders (TV, Films, Files) but if I try to open them I get the mount error.
Normally on Windows or Mac I would be asked for a usename and password before I could even get into the server, Ubuntu doesn't ask for any username or password.

The username and password I have set up on the Samba server are the same as what I use on the Ubuntu PC.

When I type in smbclient -L servername I get all the info on the server which is correct.

---

### Post by geoglitch on 2009-02-06
Sorry, I think I read the original post wrong.
If you log into the samba server using
```
smbclient servername
```
can you browse throught the folders and see files that are in them (not just see the shared folders but their contents)?

Also, are the usernames the same as the samba server on your windows/mac boots?  The absence of a login prompt might mean that the samba connection assumes your username and password (just guessing; I'm working through samba connection issues too).

Have you tried using the Connect to Server... dialog under the Places menu?

---

### Post by grs on 2009-02-06
> **geoglitch said:**
> Sorry, I think I read the original post wrong.
If you log into the samba server using
```
smbclient servername
```
can you browse throught the folders and see files that are in them (not just see the shared folders but their contents)?


The command 
```
smbclient -L servername
```
only displays info on the Samba shares - it does give details for the Home directory for my username. Therefore it is linking to my username, I know this because the Samba server has other user on it with Homes directories.

In Nautilus I can only see the first layer folders but no files or sub-directories. I can see TV, Films, Files, and GRS (my Home directory) but not there contents.

> 
Also, are the usernames the same as the samba server on your windows/mac boots?  The absence of a login prompt might mean that the samba connection assumes your username and password (just guessing; I'm working through samba connection issues too).


The username on the Windows PC is the same, the Mac is my brothers and as far as he know's there is no username setup, the Mac asks for login details when he tries to access the Samba server.

> 
Have you tried using the Connect to Server... dialog under the Places menu?

I'm too sure how to use that Connect to Server function.

---

### Post by geoglitch on 2009-02-06
The -L parameter sent to smbclient just lists the available shares
I think I got the arguments wrong on my last post.  If I do
```
smbclient //servername/share -U username
```
I get dropped into a samba shell that looks like
```
smb: \>
```where I can issue shell commands and browse the system.  Does this work?

As far as the Connect to Server dialog goes:
Select Windows Share under Service type
enter your Server name, and fill in the share name

Hope this helps.

---

### Post by grs on 2009-02-06
I'll have to look at it later when I get a chance, but I was hoping I would able to browse through a GUI rather than command line.

---

### Post by geoglitch on 2009-02-06
The GUI should work if the command line works (guess it's just a question of figuring out what the browser is assuming that is incorrect).  I see the smbclient as just another method to check things out with as I haven't used it to do anything but to make sure my samba server is working.

---

### Post by grs on 2009-02-14
I've managed to access the Samba shares - the problem was with the share settings I had some conflicting settings. I can get to the shares by going to the Places menu. However if I open an application I can't seem to access the network when I try to open a file, when I start the PC I have to open my places and manually load the shares onto the desktop, I thought I would be able to just browse the network to open a file from an application.

---

