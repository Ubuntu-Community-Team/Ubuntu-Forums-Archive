---
title: "help with network script on wifi connect"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by paradoxni on 2010-05-30
I have a NAS and am using autofs, which mounts the directories automatically once I navigate to /media/....

I wanted them mounted on startup, but due to a wireless connection not kicking in before fstab, I couldnt do this, instead I am trying to get it done with a simple script that traverses my mount directories causing autofs to kick in once wifi is up:

```
/etc/NetworkManager/dispatcher.d/nasbox.sh
```

```
IF=$1
STATUS=$2

if [ "$STATUS" = "up" ]; then
cd /media/nasbox/nasboxAlun
cd /media/nasbox/nasboxQmultimedia
cd /media/nasbox/nasboxApps
fi

```

Now this actually works if i disable wifi then re-enable it... my 3 directories get mounted and appear on desktop.. my problem is it does NOT work on first connection, wifi connects, but the shares do not appear/the script doesnt seem to run, unless I disable/re-enable wifi.

Any ideas?

---

