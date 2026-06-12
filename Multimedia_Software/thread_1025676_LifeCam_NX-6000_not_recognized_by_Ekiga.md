---
title: "LifeCam NX-6000 not recognized by Ekiga"
date: 2008-12-30
forum: Multimedia Software
---

### Post by Pine Cone on 2008-12-30
I have an up-to-date Hardy box. The LifeCam is functional and interacts with luvcview in terminal window without issue. When I use the ekiga config assistant the lifecam is tested and recognized. Later, when I go into the Edit > Preferences  page nothing is stored and it can't be detected. Any ideas?

---

### Post by ace214 on 2009-03-16
I'm having the same problem and am about to file a bug.

I think it's a problem that the camera is named with the [SIZE="4"]®[/SIZE] symbol and ekiga has an issue with it. It happens when I try to use it as an audio input device too.

Try running ekiga from the terminal and let me know if you get the following as an error when you try to set it as the video and/or audio device in the preferences.

> (ekiga:4971): GConf-CRITICAL **: gconf_engine_set_string: assertion `g_utf8_validate (val, -1, NULL)' failed


---

### Post by mixmadmen on 2009-08-18
Just thought I'd say I have the same issue. And now that you mention it, I did also notice that all of the details in terminal showed that character, but was not displayed properly. It does seem like that might have to do with it.

Running hardy. Let me know if you guys would like any more info from me to help with this. *shrug* cari at mixmadmen dot com

---

