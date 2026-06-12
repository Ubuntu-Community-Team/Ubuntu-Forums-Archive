---
title: "Mythbuntu Mover script"
date: 2010-10-13
forum: Multimedia Software
---

### Post by joshpond on 2010-10-13
Hi all,

Currently running mythbuntu 10 and I'm trying to write a script that will move the *.mpg recording onto my server when it has finished recording.

This is what I have so far:

1) System events, when finished recording: /var/lib/mythtv/mover.sh

2) mover.sh (chmod +x)
```

#!/bin/sh
#this is to move the files after recording locally
#to a unRaid box (reiserfs conflict)
sudo mount 192.168.1.1:/mnt/cache/  /mnt/pvr
sudo mv /var/lib/mythtv/recordings/*.mpg /mnt/pvr

```

3) sudo visudo
```

pvr All = NOPASSWD: /var/lib/mythtv/mover.sh

```

This is my first script and I don't know too much so go easy, but I'm not sure what I'm missing. 

When I bash mover.sh it seems to work, mythtv just doesn't run it.

Thanks Josh

---

