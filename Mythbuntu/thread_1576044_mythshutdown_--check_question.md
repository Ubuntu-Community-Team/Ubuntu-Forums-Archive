---
title: "mythshutdown --check question"
date: 2010-09-16
forum: Mythbuntu
---

### Post by jonnybignote on 2010-09-16
Hi all
this is as much a basic bash question as it is a myth thing

at the end of my daily cron jobs, (4am) I'm performing a reboot. 

currently it does this regardless of machine status

I'd like to run it with a loop that will query mythshutdown --check and proceed to reboot only if there is no recording or other myth activity.

Apologies for my very basic scripting knowledge as I'm sure this is very rudimentary, but here is what I have...

```
#!/bin/sh
while    
mythshutdown --check
do
sleep 10
done
sudo reboot
```

Currently the script is working in reverse so I think I either need to specify the return value or approach in another way.

Any help greatly appreciated

Thanks

---

### Post by Neon Dusk on 2010-09-16
Think you just need to change your 'while' to an 'until'

(in bash a 0 indicates a successful return - mythshutdown --check will return 0 when it's ok to shutdown)

---

### Post by alien878 on 2010-09-17
This is from my script.  It's perl, but you can probably figure it out:
```
while (($status=system("/usr/bin/mythshutdown -s")/256) != 0) {
        sleep(20);
}
```If you want to know the return codes, run mythshutdown -h.

---

