---
title: "wireless takes long to establish after resume"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by Trebaruna on 2009-08-28
My resume appears to work fine. However, after I punch in my password it just takes too long before my wireless connection comes back up. For some time no networks show up in the pop-up menu; as soon as they do ConnectionManager does attempt and succeed to start a connection. So, it seems that for some reason it either takes long to scan, or it takes long before one is started.
It takes between 35 and 45 seconds between pressing the power button and NM beginning to establish a connection.

Is there something I can do about this? Is this a fundamental limitation of the hardware? Can the driver be tweaked?

If anyone has any insight I'd be glad to read it.

---

### Post by kerry_s on 2009-08-28
are you suspending the wireless driver module?
have you right clicked the icon-> edit connections, check "available to all users", make sure all the settings are right. there's a "remember authentication" i think if you check that you won't have to type the password. also on mine the connection icon is just slow, it shows that it's trying to connect, but i can go ahead & open my browser & it is connected already, i'll see that "your connected" pop up while i'm already browsing.

press-> **alt+f2**
**gksudo gedit /etc/pm/config.d/config**

put:
**SUSPEND_MODULES="your-driver"**

---

### Post by Trebaruna on 2009-08-28
Thanks for your reply kerry.

What I meant by my password was the locked screen after I resume my machine. I'd quite like to keep it that way. The secret for the connection is setup fine, too.
Adding the configfile and the parameter does seem to have rather reduced the time it takes to build a connection. Cool!

...why aren't network modules automatically suspended..?

Anyway, thanks again for the help :)

---

