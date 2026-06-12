---
title: "Connect to Server problem"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by Z.K. on 2011-04-17
In Gnome Places->Connect To Server dialog, I am having problem using the Custom Location Service Type.  I enter in the URI as

```

smb://username:password@ipaddress/share_name

```

I get an pop up error message that says:

> 
Cannot Connect To Server.  You must enter a name for the server.


Which would be fine if there was actually a place for me to enter the name which there is not.  What am I doing wrong.  This is the first time I have tried using the Connect To Server dialog.  Normally I just use a script I wrote to mount my share in a folder on my local drive as some programs cannot access the mounted network folder.  In a browser all I have to do is:

```

smb://ipaddress/share_name

```

I tried using Windows Shares, but that did not work either.  It does work if I click on network and access the share that way, but some programs like firefox and a few others that I want to save a file to my network drive do not show the network unless the share is mounted in a folder.  So, I wrote a script:

```

#!/bin/sh

#mount ext storage drive
mount -t cifs //192.168.0.2/files -o username="username",password="password" /mnt/files

```

This works and I can use this, but it would be handy if I could just use the Connect To Server dialog.

:confused:

---

### Post by Leppie on 2011-04-17
what happens if you use
```
//ipaddress/share_name
```
in the custom location address bar?

---

### Post by Z.K. on 2011-04-17
> **Leppie said:**
> what happens if you use
```
//ipaddress/share_name
```
in the custom location address bar?

Same thing.  By custom location address bar I assume you mean "Location (URI):" since that is the only textbox available.

---

### Post by Leppie on 2011-04-17
yeah, that's what i meant.
sorry, don't have a samba server to connect to at the moment...

---

