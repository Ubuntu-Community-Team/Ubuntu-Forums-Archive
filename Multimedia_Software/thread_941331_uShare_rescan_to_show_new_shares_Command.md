---
title: "uShare rescan to show new shares? Command??"
date: 2008-10-08
forum: Multimedia Software
---

### Post by taseedorf on 2008-10-08
I frequently download new content, however, it will not show up automatically on my XBOX in the uShare connection unless I reboot and run ushare -x -D again.  Is there a way I can restart the daemon and have it rescan?  I have all the necessary config settings in ushare.conf...so I don't need to type at terminal what location I want it to look for media in.

---

### Post by ilrudie on 2008-10-08
don't use the -D option on ushare.  Just run ```
ushare -x &
```

This way you can still lookup a PID with ```
ps -eaf | grep ushare
```
Then run ```
sudo kill <ushare's PID>
``` and then you can restart ushare.
Also I found that setting the xbox compatibility didn't work in the config file so I changed the init.d script for ushare to always use the -x flag.  that way i can just run ```
sudo /etc/init.d/ushare restart
``` to have it rescan.  Make a luncher icon that does this and you are set.

---

### Post by taseedorf on 2008-10-08
works great! wondering though, why not use -D and use & instead? do they do the same thing except one shows a pid and the other does not?

---

### Post by ilrudie on 2008-10-08
When I run ushare with a -D (--daemon) option I can no longer find it's PID later (ps -eaf | grep ushare) to kill it if I need to.   That's why I use the & instead if I'm running it manually from the command line.  Daemons get run from /etc/init.d generally.  I think the -D option may be broken because it should show up in the above command otherwise.

---

