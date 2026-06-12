---
title: "media files not playing"
date: 2009-02-10
forum: Multimedia Software
---

### Post by vijay karthik on 2009-02-10
hi...
i get this error msg when i play any media files.."Failed to connect stream: Invalid argument"...
any suggestions to solve this pls..i had installed updates after which this prob has begun...(kinda weired..)prior to the updation it was working fine...

---

### Post by UbuntuNerd on 2009-02-10
try this go to System > Preference > Sound, try changing the settings that say "auto detect" to alsa and press test to see if it works.

---

### Post by vijay karthik on 2009-02-10
:( nope...same error ....

---

### Post by UbuntuNerd on 2009-02-10
also try the OSS option see if that works

---

### Post by vijay karthik on 2009-02-10
hard luck...its not working as well....when i play the media using amarok it says device busy...does that throw more light

---

### Post by whaevr on 2009-02-10
Have you tried removing the alsa packages and then reinstalling them?
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
then after that install them again:
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```

Then reboot.

---

### Post by vijay karthik on 2009-02-11
:) done....things going fine now :)..tnx to both of ya...

---

