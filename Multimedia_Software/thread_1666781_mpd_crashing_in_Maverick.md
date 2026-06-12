---
title: "mpd crashing in Maverick"
date: 2011-01-14
forum: Multimedia Software
---

### Post by karthikophobia on 2011-01-14
Hi 
I've been using mpd for over an year.
Today I noticed that it keeps crashing after about 95% playback regardless of the song I play. When I checked the log file, I found this:
```

mpd: /build/buildd/mpd-0.16.1+git20110110.24d51b9/./src/decoder_thread.c:65: decoder_command_finished_locked: Assertion `dc->command != DECODE_COMMAND_NONE' failed.

```

Kindly help. Thanks in advance.

---

### Post by samfuzz on 2011-01-14
[http://musicpd.org/mantis/view.php?id=3149](http://musicpd.org/mantis/view.php?id=3149)


wait for the fix

---

### Post by karthikophobia on 2011-01-14
Thanks. I thought there was something wrong with just my installation.

---

### Post by erniejunior on 2011-01-14
I have this issue too. Is there no workaround for this? Because it makes mpd useless for me! I am using 0.16. Would downgrading to 0.15 help?

---

### Post by erniejunior on 2011-01-14
#Doublepost

---

### Post by erniejunior on 2011-01-14
#Doublepost

---

### Post by erniejunior on 2011-01-14
#Doublepost

---

### Post by erniejunior on 2011-01-14
#Doublepost
Maybe some bored admin will delete all these doubleposts

---

### Post by erniejunior on 2011-01-14
#Doublepost

---

### Post by Brianetta on 2011-01-15
If you are using [http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu](http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu) to get a bleeding edge mpd server, and *haven't* run apt-get autoremove, then the following command will roll mpd back to the version before this broken one, without requiring any download:
```
sudo dpkg -i /var/cache/apt/archives/mpd_0.16+git20101211.c7f5a87-0ubuntu1~ripps1~lucid_i386.deb
```

If you're using the regular repository, then in /var/cache/apt/archives there should be a .deb for whichever mpd server packages you've had installed; just use dpkg -i to install the one that looks like it's the one before your current one.

After that, just be careful not to let apt update mpd until it's been fixed.

---

### Post by Brianetta on 2011-01-15
If you are using [http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu](http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu) to get a bleeding edge mpd server, and *haven't* run apt-get autoremove, then the following command will roll mpd back to the version before this broken one, without requiring any download:
```
sudo dpkg -i /var/cache/apt/archives/mpd_0.16+git20101211.c7f5a87-0ubuntu1~ripps1~lucid_i386.deb
```If you're using the regular repository, then in /var/cache/apt/archives there should be a .deb for whichever mpd server packages you've had installed; just use dpkg -i to install the one that looks like it's the one before your current one.

After that, just be careful not to let apt update mpd until it's been fixed.

---

### Post by erniejunior on 2011-01-15
I had this issue too with version 0.17 of mpd. It made this version of mpd useless for me:-|
But a downgrade to version 0.15 (the Ubuntu default) solved the issue for me. Unfortunately this version has no auto update:-k

#Kind of doublepost again because I thought it did not work yesterday

---

### Post by samfuzz on 2011-01-17
it 's solved now 
and the ppa is up to date
[http://musicpd.org/mantis/view.php?id=3148](http://musicpd.org/mantis/view.php?id=3148)

---

### Post by samfuzz on 2011-01-17
it 's solved now 
and the ppa is up to date
[http://musicpd.org/mantis/view.php?id=3148](http://musicpd.org/mantis/view.php?id=3148)

---

### Post by samfuzz on 2011-01-17
it 's solved now 
and the ppa is up to date
[http://musicpd.org/mantis/view.php?id=3148](http://musicpd.org/mantis/view.php?id=3148)

---

### Post by samfuzz on 2011-01-17
it 's solved now 
and the ppa is up to date
[http://musicpd.org/mantis/view.php?id=3148](http://musicpd.org/mantis/view.php?id=3148)

---

### Post by karthikophobia on 2011-01-18
Yeah I upgraded last night.
thanks everyone

---

