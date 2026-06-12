---
title: "Make hciconfig changes permanent."
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by eldaria on 2011-10-06
Hello.

I have installed Hands Free Console to enable me to use my computer as a bluetooth headset for my mobilephone.
[http://nohands.sourceforge.net/](http://nohands.sourceforge.net/)

However every time I start hfconsole after a reboot it gives me an error:

```
net.sf.nohands.hfpd.Error.BtScoConfigError: Unsuitable SCO MTU values 64:0 detected
To fix this, run, as superuser, "hciconfig hci0 scomtu 64:8"

```

I'm trying to make this change permanent so I can have the program autostart.
But where do I make this modification, is there a configuration file or do I need to add it to a startup script?

---

### Post by chili555 on 2011-10-06
I think all this is telling you is to open a terminal and run:```
sudo su
hciconfig hci0 scomtu 64:8
exit
```DISCLAIMER: I know nothing about hci and little about bluetooth. I only know how to abuse the terminal!

---

### Post by eldaria on 2011-10-06
Oh, my appologies, I guess I did not make it clear.
I already do the command every time I reboot, what I need is a permanent solution. :-)

I guess I will end up putting it in one of the startup scripts, I was just hoping there was a config file somewhere. :-)

---

### Post by chili555 on 2011-10-06
There may be a config file somewhere; I don't know. You might drop it into /etc/rc.local above exit 0.

---

