---
title: "Network disabled after suspend/hibernate in ubunutu 13.04"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by ianheggie on 2013-05-10
The problem I had was that wired connection works after a cold boot, but not after a suspend or hibernate.

The network driver (alx) has a known issue, but the fixes presented elsewhere did not work, although removing and readding the alx module manually ffixes the problem. Thanks go to [http://ubuntuforums.org/showthread.php?t=2128766](http://ubuntuforums.org/showthread.php?t=2128766) for the initial idea.

Environment: Ubuntu 13.04 unity desktop on a Toshiba P870 with SSD

Workaround: Removing and then adding the alx module back with a few seconds delay. One second is sufficient for my Core i7 system booting from SSD, but I expect that to vary. I left the remove module command in for when the system is being suspended, although it isn't nessisary for my system.

If someone can come up with a neater solution, I would be interested, but this got me going.

```

#!/bin/sh

# Fix Toshiba P870 "network disabled after suspend" issue.
# Problem in atheros network driver (alx for eth0).

case $1 in
     suspend|suspend_hybrid|hibernate)
        modprobe -r alx
        ;;
     resume|thaw)
        (
            sleep 2
            modprobe -r alx
            modprobe alx
        ) &
        ;;
esac


```

---

### Post by matt_symes on 2013-05-10
Hi

Try this. An idea from one of chili555's posts.

Copy and paste this into a terminal.

```
echo 'SUSPEND_MODULES="alx"' | sudo tee /etc/pm/config.d/config
```

Disable your old script (maybe use chmod -x .....).

Reboot and then suspend/hibernate.

Kind regards

---

### Post by ianheggie on 2013-05-11
Hi Matt,

Thanks for the suggestion, but that does not fix the problem, nor does installing the hibernate package and using its unload/reload mechanism. I also tried the following in case SUSPEND_MODULES was already set
> 
echo 'SUSPEND_MODULES="$SUSPEND_MODULES alx"' | sudo tee /etc/pm/config.d/config


For some reason, on my system at least, both the > sleep 2 and the > modprobe -r alx is required before the > modprobe alx. (To be precise sleep 1 works on my system but even though I have an SSD I wanted that extra second - commenting out the sleep causes the network to fail to initialise at next suspend or hibernate).

Ian

---

### Post by matt_symes on 2013-05-11
Hi

You have a good work around so all's good :D.

I have used the technique you are using in the past, but i have never had to *modprobe -r *after coming out of suspend, so that's a bit odd.

However if it works... :guitar:

Kind regards

---

