---
title: "Sound problem (ubuntu 11.04)"
date: 2011-05-19
forum: Multimedia Software
---

### Post by prohp on 2011-05-19
Hi,
I'm using Ubuntu 11.04 and PulseAudio.

when i open terminal and run 'speaker-test' as regular user, i can't hear any sound, but when i run it as root the sound works.

i checked syslog for errors but can't find anything.

in alsamixer it set to maximum & unmute.

How can i solve this problem?

---

### Post by prohp on 2011-05-31
Any ideas, please?

---

### Post by prshah on 2011-05-31
> **prohp said:**
> when i open terminal and run 'speaker-test' as regular user, i can't hear any sound, but when i run it as root the sound works.

Is your user a member of the "audio" and/or "pulse" group? If your user is a newly created user, and does not have admin rights, then te* needs to be a member of pulse or audio to use audio devices. 

You can check by opening the terminal(Applications-Accessories-Terminal) and giving the command```
groups
``` If audio or pulse is not listed, please add the "audio" group to your user, eg```
sudo adduser *user* audio
``` (Replace *user* as appropriate).

The user will have to logout/login (or reboot) for changes to take effect.

Please post back if this is not working.

(*) te = gender neutral pronoun, see [I suggest te]("http://ubuntuforums.org/showpost.php?p=10869035&postcount=24")

---

