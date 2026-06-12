---
title: "Access remote computer via gui?"
date: 2013-07-12
forum: Networking &amp; Wireless
---

### Post by t0p on 2013-07-12
A few years ago (Gnome 2 I think) I was able to access my shell account on a remote computer via the 'Places' tab.  Now, with 12.04, it seems the only way to do this is via the Remmina Remote Desktop Client.  Unfortunately, I don't know all the info the program asks for.  But I know the url of the remote computer, the protocol I want (ssh/sftp), my login name on the remote computer and the password.  So I plug all that into Remmina and hit 'Connect', it asks for the password, which I type in correctly, there's a pause, then connection fails (error message says 'SSH password authentication failed: Access denied. Authentication that can continue: publickey,password,keyboard-interactive,hostbased'.

I can ssh/sftp to the remote computer via terminal, but I like dragging and dropping files from one computer to the other rather than typing in the terminal commands.  If I can access the remote computer via terminal using just login name and password, why can't I with Remmina?  How can I resolve this issue? The remote computer is running NetBSD if that's of any importance, I'm using Ubuntu 12.04.

---

### Post by steeldriver on 2013-07-12
You should be able to connect to a remote ssh/sftp via Nautilus in 12.04 by going to the File --> 'Connect to server' menu and entering your server info + credentials - that should be exactly equivalent to the way you used to do it

Alternatively, if the remote system is running an X session of some kind you may be able to run a command line ssh session with the -X (X forwarding) switch and then start an instance of whatever filemanager is on the remote system, which will then display on your local desktop

Remmina probably should work as well but it's overkill for running a plain terminal based SSH session and won't run an actual remote desktop unless a remote desktop server (VNC, RDP) is listening at the other end

---

### Post by t0p on 2013-07-16
I opened a Nautilus window by typing into terminal

```
gksudo nautilus
```

then hit **File > Server** and got this error notification:

```
Can't load the supported server method list.  Please check your gvfs installation.
```

Unfortunately, I don't know how to check my gvfs installation (dunno what my "gvfs installation" *is*).

Can someone help please?

Cheers.

---

### Post by steeldriver on 2013-07-16
Do you really need to run nautilus as root (with gksudo?) - that error will go away if you run it as a normal user, I think

---

### Post by t0p on 2013-07-16
After posting that last one, I thought I'd try the oldie but goldie [Google Is My Friend]("https://ihatehate.wordpress.com/2010/04/08/how-to-search-the-internet-3-how-to-actually-use-a-search-engine/") approach.  So I googled for the error message "Can't load the supported server method list.  Please check your gvfs installation".  It quickly led to an Ubuntuforums.org thread [here]("http://ubuntuforums.org/showthread.php?t=1898963").  I got  all excited (yes, I need to get a life, anybody got one going spare?) but soon found that my problem does not stem from not having gvfs-backends installed - apt-get told me "gvfs-backends is already the newest version".  So, I still await a saviour...  :(

---

### Post by t0p on 2013-07-16
> **steeldriver said:**
> Do you really need to run nautilus as root (with gksudo?) - that error will go away if you run it as a normal user, I think

steeldriver you are my (ssh/sftp-related) saviour.  I have no idea at all why I thought I needed to run Nautilus as root.  Using as normal user is just fine.

Thank you so much for saving me from sftp command-line rage.

---

### Post by steeldriver on 2013-07-16
You're welcome - actually I can imagine situations where it *would* be useful to connect to a remote server from a root nautilus session, so I'd like to know *why *it doesn't work - fwiw I found a thread here that suggests it's a samba config issue, however I haven't tested the suggested solution:

[http://ubuntuforums.org/showthread.php?t=1960477&p=11853894#post11853894](http://ubuntuforums.org/showthread.php?t=1960477&p=11853894#post11853894)

---

