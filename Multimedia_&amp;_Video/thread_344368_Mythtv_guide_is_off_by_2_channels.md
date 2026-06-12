---
title: "Mythtv guide is off by 2 channels"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by Das Oracle on 2007-01-22
I just finished my mythtv installation with zap2it and all the guide channels are off by 2 in mythtv. I have already checked my channels in zap2it and they are fine. any suggestions on howto fix?

---

### Post by majoridiot on 2007-01-22
try scanning the channels again in mythtv-setup and run mythfilldatabase again.  make sure
your backend is not running when you make the changes-

```
sudo killall mythbackend
```

and then when the changes are made, start it back up and fill it-

```
mythbackend &      (press return again for a prompt)
mythfilldatabase
```

---

### Post by Das Oracle on 2007-01-23
why I start mythbackend or /etc/init.d/myth-backend i get this error:

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

---

### Post by majoridiot on 2007-01-23
start the backend as described above instead of the method you are trying.

---

### Post by Das Oracle on 2007-01-23
thanks, that has fixed it. My channels are all happy except quality is rough from channel to channel and i read that i have to finetune them and mythweb is an easy way to do that. The other problem is have is that when I am in the guide and i try to watch something from the guide the computer locks up and i have to do a hard reboot.

---

### Post by Das Oracle on 2007-01-23
ok, fixed that issue and it the only problem I have left has to do with the audio being ahead of the video. I know it is a setting somewhere because when I play with tvtime the av is in sync but in mythtv the video is behind by the same amount and does not grow. does anyone know where this option is found or how it can be fixed?

---

### Post by majoridiot on 2007-01-24
i'm away from my box, but i'm pretty sure the setting you are looking for is in the frontend
setup, either under "general" or "playback"

glad you are getting things straighened.  you can also fine-tune the channels via phpmyadmin,
if you have thatr installed.  there are instructions here:

[http://ubuntuforums.org/showthread.php?t=334151&highlight=mythtv+one+channel+error](http://ubuntuforums.org/showthread.php?t=334151&highlight=mythtv+one+channel+error)

---

