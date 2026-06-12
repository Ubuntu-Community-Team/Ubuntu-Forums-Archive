---
title: "Script to mount share only if online"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by Grone1985 on 2010-01-17
Hi, I'm trying to make this script that can check if the computer is online using

```
ping -c2 $HOST | grep 'received' | awk -F',' '{ print $2}' | awk '{ print $1}'
```

and then run

```
gvfs-mount smb://address
```

to mount the share. The idea is to have it check every five seconds or something until it finds the connection. I need help writing the script because I don't really know about programming. Any help is appreciated.

Cheers!

---

### Post by Grone1985 on 2010-01-18
Bump

---

### Post by leandromartinez98 on 2010-01-18
I guess your ping returns "received" if the host in online. Then it should be something like this (I didn't test it).

```

#!/bin/bash
i=1
while [ $i == 1 ] ; do
  sleep 5
  ping=`ping -c2 $HOST | grep 'received' | awk -F',' '{ print $2}' | awk '{ print $1}'`
  if [ $ping == "received" ]; do
    gvfs-mount smb://address
    i=2
  fi
done

```

---

### Post by littlepeon on 2010-01-18
hey there....
i have always posted my shell scripting questions here:

[http://www.unix.com/shell-programming-scripting/](http://www.unix.com/shell-programming-scripting/)

they have always been friendly/helpfull

hope this helps
-Peon

---

### Post by Grone1985 on 2010-01-19
Thanks for the answers but it's still not working... If I try to run the script on a terminal it closes right away. I don't know what the problem on the script could be. Thanks again!

---

### Post by Ahriman on 2010-01-19
You say it closes right away ... but is the computer online and did it run 'gvfs-mount smb://address'?

---

### Post by Grone1985 on 2010-01-19
> **Ahriman said:**
> You say it closes right away ... but is the computer online and did it run 'gvfs-mount smb://address'?

Yes, the computer is online and no it didn't run the command, or ata least it didn't work, and as the terminal closes right away I can't see any output so I don't know where is the problem

---

### Post by Ahriman on 2010-01-19
Try changing the mount command to something that will echo a word in the console, so you can tell if it's reaching that point or not.

If it says the word in the console, then the issue is with the mount. If it doesn't say the word, but closes the script straight away again, then it's something else.

---

### Post by Grone1985 on 2010-01-19
> **Ahriman said:**
> Try changing the mount command to something that will echo a word in the console, so you can tell if it's reaching that point or not.

If it says the word in the console, then the issue is with the mount. If it doesn't say the word, but closes the script straight away again, then it's something else.

Ok, so I tried what you suggested and it still closed right away, so the problem is in the first part of the script. Besides I know that the mount command works and therefore it shouldn't be the problem. BTW Thanks for the suggestion!

---

### Post by Grone1985 on 2010-01-19
Ok, I finally think I got it. Thanks to your suggestions and playing a little with the script I got this:

```
#!/bin/bash

NUM=0

while [ $NUM -ge 0 ]; do
  sleep 5
PING=`ping -c2 HOST | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }'`
    if [ $PING -eq 2 ]; then
      gvfs-mount "smb://address"
      exit
    fi

      let NUM=$NUM+1

done
```

It runs until it can mount the folder and then closes by itself! Thanks everyone!

---

