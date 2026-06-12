---
title: "restart Tangerine Media server after resume"
date: 2012-01-19
forum: Multimedia Software
---

### Post by frogotronic on 2012-01-19
Hi,

Tangerine doesn't play well with suspend/resume.  It is unavailable on resume - I have to use killall tangerine and then restart it.

Is there a way to do this via a script for suspend/resume?

Where would I put the script?

Thanks,
CH

---

### Post by frogotronic on 2012-03-16
Problem solved.  Need to unload and reload across suspend and resume.

Take from this Thread: [http://ubuntuforums.org/showpost.php?p=9155208&postcount=3](http://ubuntuforums.org/showpost.php?p=9155208&postcount=3)

So...for Tangerine do this:

```
cd /etc/pm/sleep.d
sudo touch 10_tangerine
sudo chmod 0755 10_tangerine
sudo gedit 10_tangerine
```

Then put this in the file:

```
#!/bin/bash
#Code from http://ubuntuforums.org/showthread.php?t=1387211

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    rfkill block tangerine
    ;;
    thaw|resume)
    rfkill unblock tangerine
    ;;
    *)
    ;;
esac

exit
```

Save and exit.

You should be good to go...:guitar:

- CH

---

