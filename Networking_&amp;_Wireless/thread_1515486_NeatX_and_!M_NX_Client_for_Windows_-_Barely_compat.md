---
title: "NeatX and !M NX Client for Windows - Barely compatible?"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by Redsandro on 2010-06-22
I have installed **NeatX** on Ubuntu Lucid 10.04.
[SIZE="1"][http://help.ubuntu.com/community/FreeNX]("http://help.ubuntu.com/community/FreeNX")[/SIZE]

And I use the No Machine Windows client to connect.
[SIZE="1"][http://www.nomachine.com/select-package-client.php]("http://www.nomachine.com/select-package-client.php")[/SIZE]

On first glance it is superior to **FreeNX** because it does incorporate theme and style into the remote session.

On longer usage it gets more and more trouble connecting. Basic commands like RestoreSession and Terminate do not work, but get the same reply.
Either
```
NX> 500 Internal error
NX> 999 Bye.
Sessions still open, not unmounting
NX> 280 Exiting on signal: 15
```
or 
```
NX> 105 Terminate --sessionid="d1fba7b43a654634790532b7cf56b4e1"
NX> 503 Error: undefined command: 'terminate'
NX> 105 NX> 280 Exiting on signal: 15

```

I can create a new session but I cannot ever ever ever terminate it even after a reboot.

What's going on? Is Ubuntu relying on Alpha stage software here?

[IMG]http://stuff.rednet.nl/rommel/trash/nxserver.png[/IMG]

---

### Post by doas777 on 2010-06-22
I've gotten a few of those as well. it happens once everytime i reboot the server, so i think it's on the neatx side. 
I just wrote a script called nxclean to delete the existing session file. it should have been deleted once the session was completed and cleaned up, but I rebooted too quickly (I always close my nx session, ssh in, and issue a reboot command.) if I try to nx in and fail, I just ssh in, and run nxclean. then it connects fine. 

if you check your log file viewer, you will be able to find the location of the sessions cache (sry, I don;t recall the path off the top of my head.) then just delete the contents of the the 'sessions' dir (but don't delete 'sessions' itself; that will give you a diff error).

let me know if you find out anything more on this issue. I haven't really dug into it, as my server remains booted for months at a time, so nbd to me.

---

### Post by Redsandro on 2010-06-22
Thank you, next time I get this I will try to empty the dirs you described and see if I can back in again.

The problem for me is that I create a shortcut on the desktop, and when it is in that list of leftover sessions, I cannot use the same shortcut anymore and I need to use the wizard to create a new session. There's a good chance it's fixed with your solution.

---

### Post by Redsandro on 2010-07-18
I just had to do it again, and there are a lot of session dirs. I haven't tried deleting them all to see what error I get (since you mentioned), 'cause I'd rather play on the safe side at the moment.

So just to provide a quick trick to empty but not remove all session dirs as well as the path for future reference, here it is:

> 
**$** sudo rm -r /var/lib/neatx/sessions/*/*


Extra-quick from the desktop?
Press **ALT**+**F2** (run) and type:

```

gnome-terminal -x sudo rm -r /var/lib/neatx/sessions/*/*

```

---

### Post by P J on 2011-01-21
I put an entry in cron to delete the sessions on reboot. This has made things a lot easier, after reboot I no longer have to ssh in first to delete the sessions before I start a new one.

Be root, with 'sudo bash' or whatever you use, then crontab -e
Put a new line:

```
@reboot rm -r /var/lib/neatx/sessions/*

```
save, quit, reboot and retry...

---

