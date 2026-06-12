---
title: "how to run multiple sound apps conurrently"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by scottbporter on 2008-02-17
How do you get multiple sound apps to run. With the OS that must not be named, I can start multliple apps, media player, you tube videos, etc to run concurrently. With Ubuntu, if I am running XMMS playing a streamed feed then try to check my phone messages or run a you tube vid or news vid I get message saying sound device is already in use. I then have to close XMMS to run another sound app. It really is frustrating. Any suggestions?

---

### Post by linuxwizard on 2008-02-17
Look on this page for > Getting more than one application to use the soundcard at the same time

[https://help.ubuntu.com/community/SoundTroubleshooting#head-882ddc981673f44656e4f791858e9a586a007705](https://help.ubuntu.com/community/SoundTroubleshooting#head-882ddc981673f44656e4f791858e9a586a007705)

---

### Post by scottbporter on 2008-02-18
Thanks for the info, but I still can't get it to work. I have alsa. Do I need Jack?

---

### Post by scottbporter on 2008-02-18
I get it now. Each app has to have the same default audio driver. One must go into each app and set the default audio to ALSA. Simple.

---

