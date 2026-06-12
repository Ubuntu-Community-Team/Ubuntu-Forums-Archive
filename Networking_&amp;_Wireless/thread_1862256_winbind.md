---
title: "winbind"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by rmlrml on 2011-10-16
Hey, newbie question.  well, not exactly new but i'm still clueless.  I tried to find the answer to this but I can't find anything definitive.  I was trying to speed up my boot time.  Right now I can see in bum boot-up manager that i have winbind as a service.  I have looked it up and i see that it's some kind of samba whatever used to connect to windows machines.  i don't do any kind of networking or server anything.  i just have a personal laptop.  the most connecting i do is to my landlord's wireless router and to the wireless router at work.  is that something i need winbind/samba for or can i disable/remove it?

thanks

---

### Post by capscrew on 2011-10-16
> **rmlrml said:**
> Hey, newbie question.  well, not exactly new but i'm still clueless.  I tried to find the answer to this but I can't find anything definitive.  I was trying to speed up my boot time.  Right now I can see in bum boot-up manager that i have winbind as a service.  I have looked it up and i see that it's some kind of samba whatever used to connect to windows machines.  i don't do any kind of networking or server anything.  i just have a personal laptop.  the most connecting i do is to my landlord's wireless router and to the wireless router at work.  is that something i need winbind/samba for or can i disable/remove it?

thanks

If you are not using Samba you can safely remove Winbind.  Winbind is usually installed when you explicitly install it.  I wonder how it got installed.

Just to make sure if it really is installed can you post the output of ```
pgrep -l win
```

This will show the *winbindd *service if it indeed is running.

You can remove Winbind through Synaptics (search term winbind) or you can remove it from the command line like this```
sudo apt-get purge winbind
```

---

### Post by rmlrml on 2011-10-17
Thanks!  Yes pgrep showed it was running and i see in synaptic that it's installed.  I have no idea why, could have been a careless selection i made in synaptic at some point??  samba isn't installed, but winbind is.  Thanks for your help!

---

