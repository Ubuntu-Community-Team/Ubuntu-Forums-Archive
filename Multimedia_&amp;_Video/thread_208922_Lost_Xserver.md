---
title: "Lost Xserver"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by tajreed on 2006-07-04
I had a failed video card. Switched cards and now when I reboot and attempt to reconfigure the xserver (dpkg-reconfigure xserver-org) I asm informed that the Xserver is not installed. I've been using Dapper for 6 months and never a problem. Any thoughts? Do I have to reinstall?

---

### Post by mlind on 2006-07-04
try 
```

sudo dpkg-reconfigure xserver-**xorg**

```

---

### Post by tajreed on 2006-07-04
Did that. Received response that X server was not installed.

---

### Post by mlind on 2006-07-04
[QUOTE=tajreed]Did that. Received response that X server was not installed.[/QUOTE]

If you're using Ubuntu, make sure that you have ubuntu-desktop package installed.
Could you post the full error message part here?

---

### Post by tajreed on 2006-07-04
I'll check the error messages. But as I've mentioned I have using Ubuntu Dapper for 6 months with no problems. This started when I switched video cards.

---

### Post by tajreed on 2006-07-04
After dpkg-reconfigure xserver.org I get:
"Package "xserver.org" is not installed and no info is available"

---

### Post by mlind on 2006-07-04
[QUOTE=tajreed]After dpkg-reconfigure xserver.org I get:
"Package "xserver.org" is not installed and no info is available"[/QUOTE]

This might sound stupid, but are you sure you're writing that command correctly?
It's xserver-xorg not xserver.org

Could you post the full terminal output, which includes the command you invoke?

---

### Post by tajreed on 2006-07-04
You were right. I was the stupid one. Using the wrong command. I reconfigured and all is well.
Thanks for your help and patience.

---

