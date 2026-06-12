---
title: "Getting ath0 to run at boot using iwpriv"
date: 2006-03-20
forum: Networking &amp; Wireless
---

### Post by Clochard on 2006-03-20
I've been able to get my wireless card setup and working just fine, however my access point uses a shared key.  This means that I need to issue the following command to get things working:

```
sudo iwpriv ath0 authmode 2
```

This sets it up to use shared keys, and I can then issue sudo ifup ath0 and it acquires the DHCP address and we're off to the races.

However, my problem is that I need to do this everytime I boot the system.  Is there some way I can add this parameters to /etc/network/interfaces, or some other place such that this happens automatically everytime I boot?

I tried adding this command to /etc/rc.local but this doesn't work.  Is this some kind of module parameter that I need to mess with?

---

### Post by Clochard on 2006-03-22
I was able to get this working, and if anyone else has the same problem here is what I did:

Added a script to /etc/init.d called ath0_authmode

Script:
```

#!/bin/sh
iwpriv ath0 authmode 2

```

I then made sure it was executable

```

chmod a+x S39ath0_authmode

```

I created a soft link to this script in /etc/rcS.d called S39ath0_authomode

```

ln -s ../init.d/ath0_authomode S39ath0_authmode

```


Finally, I added the following line to /etc/network/interfaces

```

auto ath0

```

right above the ath0 section.

Note that I am making the script get run before networking is run (where ifup is run) by using the S39 prefix (networking is S40 on my box).

---

