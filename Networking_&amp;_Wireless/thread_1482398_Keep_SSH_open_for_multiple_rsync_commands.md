---
title: "Keep SSH open for multiple rsync commands"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by GammaQuantum on 2010-05-13
Hello,

I use a bash script to copy the files of my desktop computer (iMac, Mac OS X 10.5) onto my NetBook (Asus Eee, Ubuntu 10.04 NetBook).

Since I only had trouble with SMB and AFP I use SSH now for my rsync. This works perfectly, the only downside is that it asks me for my iMac password for every of the four rsync commands. This is not very nice.

Can I somehow make one SSH session and run four rsync commands?

This scipt is run from my Eee:

```
#!/bin/sh
#
#Paths
quelle="me@192.168.0.1:/Users/me"
ziel="$HOME"
#
#Synchronisation
/usr/bin/rsync -avE --delete --exclude-from exclude.txt --max-size=100M $quelle/Code/ $ziel/Code/
printf '\a' ; printf '\a' ; printf '\a'
/usr/bin/rsync -avE --delete --exclude-from exclude.txt --max-size=100M $quelle/Documents/ $ziel/Dokumente/
printf '\a' ; printf '\a' ; printf '\a'
/usr/bin/rsync -avE --delete --exclude-from exclude.txt --max-size=100M "$quelle/Music/iTunes/iTunes\ Music/" $ziel/Musik/
printf '\a' ; printf '\a' ; printf '\a'
/usr/bin/rsync -avE --delete --exclude-from exclude.txt --max-size=100M $quelle/Pictures/ $ziel/Bilder/

```

Thanks!

Gamma Quantum

---

