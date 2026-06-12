---
title: "x11vnc authentication issues"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by jaychamp on 2009-10-10
When I try to log in using the UltraVNC viewer from a Windows box and the -rfbauth option with x11vnc I receive an authentication failed error.  The password is 5 characters and the path is correct.  If I select the DSMPlugin in the VNC viewer I don't receive an error but the screen doesn't load.  However if I use the -passwd option w/x11vnc it works fine.  Am I doing something wrong?

The command I'm using to start the server is: x11vnc -rfbauth /noted/location/of/stored/password/

---

### Post by jaychamp on 2009-10-10
Just tried with other VNC viewers and get the same error

---

### Post by krunge on 2009-10-11
> When I try to log in using the UltraVNC viewer from a Windows box and the -rfbauth option with x11vnc I receive an authentication failed error.  The password is 5 characters and the path is correct.  However if I use the -passwd option w/x11vnc it works fine.  Am I doing something wrong?

How did you create the rfbauth password file?  With vncpasswd(1)?  Or "x11vnc -storepasswd /path/to/file"?  Or something else?  Note that you can't simply place an ascii password into the -rfbauth file (but you can use -passwdfile for that.)

The development version of x11vnc 0.9.9 has a "-showrfbauth" option to display the password contained in an rfbauth file. This let's you verify it contains the password you think it does.

However I think you should you first retry with a fresh rfbauth file:
```

x11vnc -storepasswd ~/test.pw       [Type in a password when prompted]

x11vnc -rfbauth ~/test.pw ...

```
> 
The command I'm using to start the server is: x11vnc -rfbauth /noted/location/of/stored/password/
You don't really mean a "/" at the end, right?

> 
If I select the DSMPlugin in the VNC viewer I don't receive an error but the screen doesn't load.

x11vnc doesn't support the UltraVNC DSM Plugin (it almost does, but UltraVNC botched their implementation.)

---

### Post by jaychamp on 2009-10-13
It just a permissions thing.  :)

I guess it's because I created it using sudo

---

### Post by krunge on 2009-10-13
> **jaychamp said:**
> It just a permissions thing.  :)

I guess it's because I created it using sudo
Ah, I see.  So your problem is solved?

---

