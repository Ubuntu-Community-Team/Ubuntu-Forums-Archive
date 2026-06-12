---
title: "Everything requiring sound needs to be ran as root"
date: 2010-03-30
forum: Multimedia Software
---

### Post by Guyon on 2010-03-30
Just did a fresh install of Ubuntu 9.10 Minimal, and the sound works flawlessly, but everything sound related requires sudo to work correctly. Alsamixer, aplay, all need sudo. Due to this I get no sound anywhere unless I use root privileges. 

Thanks in advance. :D

---

### Post by Guyon on 2010-03-30
Anyone?

---

### Post by Guyon on 2010-03-30
Bump.. quite sure the answer is simple, I just don't know where to look. :(

---

### Post by lidex on 2010-03-30
In your menu go to "System>Administration>Users and Groups".
Click on "Manage Groups". Make sure your user is a member of the audio, cdrom and all pulse groups. Logout/login

---

### Post by Guyon on 2010-03-30
> **lidex said:**
> In your menu go to "System>Administration>Users and Groups".
Click on "Manage Groups". Make sure your user is a member of the audio, cdrom and all pulse groups. Logout/login
I'm a member of all three. I still have sound issues. :(

---

### Post by lidex on 2010-03-31
> I'm a member of all three. I still have sound issues. 
Did you logout?

You'll want to belong to all these groups:
> adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

Also look at post #4 here:
[http://ubuntuforums.org/showthread.php?t=411038]("http://ubuntuforums.org/showthread.php?t=411038")

---

### Post by lidex on 2010-03-31
What is the output of this command:
```
ls -l /dev/audio*
```

---

### Post by Guyon on 2010-03-31
I think I am a member of all of those groups except scanner, which I don't need. And I have logged out.

> **lidex said:**
> What is the output of this command:
```
ls -l /dev/audio*
```
```
crw-rw----+ 1 root audio 14, 4 2010-03-29 22:22 /dev/audio

```

fgrep -ie 'audio' /etc/group returns
```
audio:x:29:pulse
```
according to this: [http://ubuntuforums.org/showpost.php?p=2557784&postcount=7](http://ubuntuforums.org/showpost.php?p=2557784&postcount=7), that is incorrect. 
Thanks for the help so far. :D

---

### Post by lidex on 2010-03-31
Are you a member of pulse-access also? Try this and reboot this time:
```
sudo usermod -a -G audio YOURUSERNAMEHERE
```

---

### Post by Guyon on 2010-03-31
> **lidex said:**
> Are you a member of pulse-access also? Try this and reboot this time:
```
sudo usermod -a -G audio YOURUSERNAMEHERE
```

Aha, that worked perfectly. I'm using openbox was using terminal instead of going to Users and Groups and thought I had it all figured out. Guess not!

Thanks again so much! :D

---

