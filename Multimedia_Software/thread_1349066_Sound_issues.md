---
title: "Sound issues"
date: 2009-12-07
forum: Multimedia Software
---

### Post by Rockanium on 2009-12-07
When i turn my computer on i get the login sound, but i have no sound what so ever in youtube, im using 9.10

---

### Post by quixote on 2009-12-08
After login, once the desktop is loaded, do you have at least system sounds then?  If you go to System -> Preferences -> Sound, there are buttons to test whether sound is produced.  Do any of those work?  If other sounds work, but youtube doesn't, then it's a problem with the flash plugin probably.  Let us know a bit more what your situation is, and then it'll be easier to help.

---

### Post by petru.marginean on 2009-12-08
I have similar issues with the sound in Ubuntu 9.10
Right after restart the sound is working; after awhile the sound stops working.

The way I solve it is to run the following commands (that I've compiled in a script):

```
$> cat bin/sound.sh                                           [~]
#!/bin/bash

sudo /etc/init.d/alsa-utils stop
rm -fr .pulse*
sudo alsa force-reload
sudo /etc/init.d/alsa-utils start

```

I hope this helps,
Petru

---

