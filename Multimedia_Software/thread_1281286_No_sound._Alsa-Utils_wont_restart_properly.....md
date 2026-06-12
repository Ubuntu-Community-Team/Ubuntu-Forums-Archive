---
title: "No sound. Alsa-Utils wont restart properly...."
date: 2009-10-03
forum: Multimedia Software
---

### Post by djwkd on 2009-10-03
Hello everyone (again),
Im running the beta version of Ubuntu 9.10, and i dont have any sound. This has been going on for about 3 days now. Someone suggested that i restart pulse-audio. Still no sound. So they told me to restart alsa-utils....
```
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially
Available commands:
  scontrols       show all mixer simple controls
  scontents	  show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> [command]
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially


```
:(

But OVER AND OVER AGAIN.Like an infinite loop, except it ends after about 10/15/20 seconds.
Can anyone help?

---

### Post by djwkd on 2009-10-03
Also, i did file an error report, but when i looked the next day, it was gone...Im assuming it was something already filed, but i couldnt find it.

---

### Post by djwkd on 2009-10-10
Never mind, i think i'll just reinstall ubuntu 9.04.

---

