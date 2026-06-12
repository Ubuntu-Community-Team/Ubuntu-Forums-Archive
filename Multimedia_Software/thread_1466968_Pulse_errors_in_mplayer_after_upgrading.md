---
title: "Pulse errors in mplayer after upgrading"
date: 2010-04-30
forum: Multimedia Software
---

### Post by eyelessfade on 2010-04-30
After upgrading to 10.04 I get the following pulse error in mplayer before it starts.
```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket         
mplayer: No such file or directory
```

Not a biggie since I get both sound and video, but it takes a bit longer to start the file then before.

Also Kde tells me that the sound card "pulse audio" is no longer connected although pulse seem to live just fine.

---

### Post by xzero1 on 2010-04-30
I think this is normal, seems mplayer is checking for bluetooth audio service. At least that's my guess.

---

### Post by eyelessfade on 2010-05-01
hm I guess some one need that, but I should think it's pulses job to patch the sound to the bluetooth. oh well..

---

