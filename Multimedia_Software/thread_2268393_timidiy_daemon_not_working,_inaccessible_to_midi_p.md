---
title: "timidiy daemon not working, inaccessible to midi players"
date: 2015-03-08
forum: Multimedia Software
---

### Post by kelt65 on 2015-03-08
I'm posting this in case anyone else has this problem. Unless you're a member of the audio group, no program you run will be able to access the timidity daemon, and will not even see it in it's list of devices. Unfortunatly, "audio" is not one of the default groups a new user is in! 

Add yourself to the audio group:

```


sudo usermod -a -G audio $USER 
# and in case you haven't :
sudo apt-get install timidity timidity-daemon

```

Log out and log back in (yes, you have to), and your programs should be able to see the devices created by the timidity daemon. Of couse, you will also need the package "timidity-daemon"

---

