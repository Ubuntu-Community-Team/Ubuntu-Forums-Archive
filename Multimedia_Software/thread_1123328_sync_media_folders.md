---
title: "sync media folders"
date: 2009-04-12
forum: Multimedia Software
---

### Post by bruno9779 on 2009-04-12
I need to write a script in rsync to back up my media files.

i need it to sync (import **AND** export all changes) the folders : /home/bruno/Music and /media/Lacie/Music

I have been using the following code, from a previous thread:

```
rsync -vurt --progress --delete /home/bruno/Music /media/Lacie/Music

```

but I am not sure it does what I want.

After this i would need to do the same with a laptop on the same lan (import and export all changes)
My attempts so far show that rsync doesn't support samba shares (am i right?)

Any help would be appreciated

---

### Post by bruno9779 on 2009-04-12
Bump

People watches this, but no one replies...
Let me know if my explanation isn't in any way clear

---

### Post by bruno9779 on 2009-04-12
I have been looking this up on the man page of rsync and I came up with this:

```

#!/bin/sh

#push files
rsync -vurt --progress /home/bruno/Music /media/Lacie/Music
#pull files
rsync -vurt --progress /media/Lacie/Music /home/bruno/Music
```

I would need someone to overlook this and possibly tell me if it is fine, or if there is a single command way of doing this

and I still cannot make it work over samba shares

---

