---
title: "changing channel program"
date: 2010-10-20
forum: Mythbuntu
---

### Post by vancheese on 2010-10-20
Dear nice people,

I've written a custom python channel changing IR program which takes care of my slightly unusual sky sat setup. The command works from a linux commandline and used to work from a karmic mythbuntu box. However on a fresh Lucid install with all the patches the program does not work and spits out this error

```

Traceback (most recent call last):
  File "/usr/local/bin/changechan.py", line 14, in <module>
    fullchannel = sys.argv[1]
IndexError: list index out of range

```

This means that the python script(see below) is not getting the channel number passed to it correctly. Any suggestions why this may be happening as the "standard bash" script  doesn't seems to work too but just doesn't exist with an error

My code
```
#!/usr/bin/env python2.6

import sys, os, time

def change_channel(list):
   """Activates the remote"""
   for step in list:
#    print("irsend --device=/dev/lircd SEND_ONCE SKY %s" %step)
    os.system("irsend --device=/dev/lircd SEND_ONCE SKY %s" %step)
    time.sleep(0.4)

fullchannel = sys.argv[1]
if fullchannel.startswith("x"):
    steps = []
#moves cursor down
    for x in range(0, int(fullchannel[1:])):
        steps.append("cursor-down")
    full_ir = ["Services", 7]+ steps + [ "select" ]
#    print full_ir
    change_channel(full_ir)
else:
    change_channel(fullchannel)
    os.system("irsend --device=/dev/lircd SEND_ONCE SKY BACKUP")
```

"Standard Bash"
```
#!/bin/sh
REMOTE_NAME=SKY
for digit in $(echo $1 | sed -e 's/./& /g'); do
  irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
  sleep 0.4 # note, you may have to tweak the interdigit delay up a bit
done
irsend --device=/dev/lircd1 SEND_ONCE $REMOTE_NAME BACKUP
exit 0
```

thanks for any help
Andy

---

