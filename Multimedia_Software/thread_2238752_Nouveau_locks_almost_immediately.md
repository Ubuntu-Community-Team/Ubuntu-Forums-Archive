---
title: "Nouveau locks almost immediately"
date: 2014-08-09
forum: Multimedia Software
---

### Post by Yippee38 on 2014-08-09
I just installed Ubuntu 14.04.1 LTS.  I've got an NVIDIA 7300 LE video card in this machine.  It boots to the default desktop, but withing moments (less than a minute) it stops responding.  The very first time, the screen went to terminal mode and there was a message about GPU locked and something about nouveau.

Is there a way I can boot the system to terminal and switch the drivers out to NVIDIA drivers?

---

### Post by kc1di on 2014-08-09
from the menu at boot you should see an entry ubuntu advanced. select it and the select recovery. 

it will take you to a page - select network first and allow it to finsh setting you a connection , when it done selet root , it will take you to a root terminal.
When you get there do the following:

```
apt-get update
``` 
Then
```
apt-get install nvidia-173
```

reboot see it that works.

---

### Post by Yippee38 on 2014-08-09
I don't get a boot menu.  It goes straight to desktop.

---

### Post by kc1di on 2014-08-09
try hitting the tab key when it just starts to boot.

---

### Post by Yippee38 on 2014-08-09
That didn't work at first.  I had to play around with it for a while, but I finally got that menu.  Did what you recommended.  When I rebooted, it just hangs at the Ubuntu screen.  The dots fill in, but then that's it.

Any suggestions?

---

### Post by kc1di on 2014-08-10
ok lets try this then,
do the same thing only install ```
 apt-get install nvidia-current
```

see if that makes a difference.

---

### Post by Yippee38 on 2014-08-10
> **kc1di said:**
> ok lets try this then,
do the same thing only install ```
 apt-get install nvidia-current
```

see if that makes a difference.

Well, it got me past the Ubuntu splash screen, but then it just went to a black screen.  <sigh>

---

### Post by kc1di on 2014-08-10
Sorry that particualar card seems to be a bear to get going on 14.04 
lots of reports of problems going back a few years.  
I'm sure someone must have had success but I'm out of Ideas at the moment. 
maybe some else will chime in on this one. 

there was one report here but it's quite old now that you could force unity to show 
see [this blog]("http://askubuntu.com/questions/38853/is-the-nvidia-geforce-7300-le-blacklisted").

---

### Post by Yippee38 on 2014-08-10
Yeah.  That was the problem.  I put an old 8800 GTS in and it worked fine.  Of course, I had to re-install Ubuntu because UEFI stopped seeing my hard drive as a UEFI device.  Have I mentioned that I hate UEFI?  ;)

Thank you for your help!

---

### Post by kc1di on 2014-08-10
your welcome , glad you got it going. :)

---

