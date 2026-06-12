---
title: "Samba Options"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by Oxwivi on 2010-10-18
How do I run Samba with a different option, specifically -D? Can I do it from the GUI (system-config-samba)?

Also, how do I ensure it runs and startup?

---

### Post by Oxwivi on 2010-10-19
<snip>
**Bump**

---

### Post by luvshines on 2010-10-19
See if this file helps:
/etc/init/smbd.conf

It has exec smbd -F in the end. Maybe -D will do the trick.
This file itself is the one which make Smdb an upstart job and defines the run-levels on which it should be running on system startup.

---

### Post by Oxwivi on 2010-10-19
On 10.10 Samba runs as a service, no longer from init.

---

### Post by Morbius1 on 2010-10-19
> **Oxwivi said:**
> On 10.10 Samba runs as a service, no longer from init.
It never ran from [COLOR=Blue]**init**[/COLOR], It ran from **[COLOR=Blue]init.d[/COLOR]**. It still does ( sort of ) only now there's a symlink there to show it's now controlled by upstart. 

Do as luvshines says and go to /etc/init/smbd.conf. What you will see this:
> description "SMB/CIFS File Server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

start on (local-filesystems and stopped rc)
stop on runlevel [!2345]

respawn

pre-start script
    RUN_MODE="daemons"

    [ -r /etc/default/samba ] && . /etc/default/samba

    [ "$RUN_MODE" = inetd ] && { stop; exit 0; }

    install -o root -g root -m 755 -d /var/run/samba
end script

**[COLOR=Blue]exec smbd -F[/COLOR]**
I have no idea if that will answer your question but I beleive that is what luvshines is referring to.

---

### Post by Oxwivi on 2010-10-19
I see, sorry I don't know too much about how it works, I was arrogant. I'll do as you say.

---

### Post by Oxwivi on 2010-10-19
Okay, it successfully runs in the option of my choice, thank you very much!

But my printer I'm sharing from Ubuntu doesn't show up on Windows even if the Ubuntu system is visible on network. Only after I run the Samba GUI, system-config-samba, the printer shows up. Any ideas?

---

### Post by Morbius1 on 2010-10-19
I had the same problem. It's caused by smbd starting before cups starts instead of the other way around like it should. As it turns out I inadvertently posted the solution I use above. That is not the default /etc/init/smbd.conf , it is is the workaround for your problem:
> description "SMB/CIFS File Server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

**[COLOR=Blue] start on (local-filesystems and stopped rc)[/COLOR]**
stop on runlevel [!2345]

respawn

pre-start script
    RUN_MODE="daemons"

    [ -r /etc/default/samba ] && . /etc/default/samba

    [ "$RUN_MODE" = inetd ] && { stop; exit 0; }

    install -o root -g root -m 755 -d /var/run/samba
end script
[COLOR=Black]
[/COLOR] [COLOR=Black]exec smbd -F[/COLOR]

---

### Post by Oxwivi on 2010-10-20
Banzai! Finally! Finally I can print freely (as long as the Ubuntu system is on)! Thank you - thank you very much! You have my utmost gratitude!

---

### Post by Oxwivi on 2010-10-20
By the way, can anyone tell me how to restart services? Obviously init.d et al doesn't work...

---

### Post by Morbius1 on 2010-10-20
```
sudo service smbd restart
```

As it turns out smbd is a tricky one.

If smbd is not running then "sudo service smbd restart" will fail.

To start it if it's not running: "sudo service smbd start"

If smbd is running and you want to restart it: "sudo service smbd restart"

---

### Post by Oxwivi on 2010-10-20
So Samba always runs at the root level?

---

