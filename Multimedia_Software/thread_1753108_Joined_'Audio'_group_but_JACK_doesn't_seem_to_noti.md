---
title: "Joined 'Audio' group but JACK doesn't seem to notice?"
date: 2011-05-08
forum: Multimedia Software
---

### Post by adamkristo on 2011-05-08
I'm having troubles setting up Ardour. 
Ardour couldn't start JACK - looked up various reasons and patched up as many holes as [https://help.ubuntu.com/community/UbuntuStudio/JackQuickStart](https://help.ubuntu.com/community/UbuntuStudio/JackQuickStart) and [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
recommended.   I'm now at a point where after I start JACK an error message states:

~JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
Your system has an audio group, but you are not a member of it.
Please add yourself to the audio group by executing (as root):
  usermod -a -G audio (null)
After applying these changes, please re-login in order for them to take effect.
You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!~
 
I've, seemingly, added myself to audio group (threw System> Administration> Users and Groups) and this message persists.

My goal was to get Ardour running to see if I liked it or not... 

If you have any suggestions it would be greatly appreciated.

This is my first post to the forum and I'm completely new to Linux so bare with me ;)

Thanks for your time.
Adam

---

### Post by backu on 2011-05-23
This may seem to be a moot point, but could you post the results of "cat /etc/security/limits.conf" and "groups username" (replacing username with your user name)

---

