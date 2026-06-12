---
title: "Problem With Sound"
date: 2016-04-12
forum: Multimedia Software
---

### Post by shane_faulkinbury2 on 2016-04-12
I'm having a problem with sound on my Ubuntu Mate 15.10 laptop.  The laptop has sound, but using Spotify and Clementine hasn't been working for three days now.  I update my laptop everyday before opening any programs using the "sudo apt-get update" command.  I have no idea what the problem could be.  The laptop is only 5 months old.  Attached are some screenshots of the sound settings.

---

### Post by v3.xx on 2016-04-14
Your first screenshot shows you using 'Analog Stero Duplex' and the second shows you using HDMI.  Could that be it?

Also updating is just half of the process.  This need to be followed with and upgrade.

```
sudo apt-get dist-upgrade
```

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by shane_faulkinbury2 on 2016-04-14
Well the upgrade didn't fix anything so I guess I'm going to go ahead and do a reinstall.  It sucks though that I have to reinstall all my programs and move all my documents, downloads, pictures, music, and videos back over, but I can't stand to go without my music for another week!  I also think waiting for 16.04 to come out next week will not help anything either.  :icon_frown:

---

### Post by v3.xx on 2016-04-14
Are you using analog or digital stereo?

---

### Post by shane_faulkinbury2 on 2016-04-14
I tried them both!

---

### Post by v3.xx on 2016-04-14
Is alsa showing the right sound card (F6)?

```
alsamixer
```

Edit

You can also try a reinstall

[http://ubuntuforums.org/showthread.php?t=2280056&p=13294117#post13294117](http://ubuntuforums.org/showthread.php?t=2280056&p=13294117#post13294117)

---

### Post by shane_faulkinbury2 on 2016-04-15
Well I did a reinstall and everything is working now!  This exactly why I backup everything twice!  :D

---

