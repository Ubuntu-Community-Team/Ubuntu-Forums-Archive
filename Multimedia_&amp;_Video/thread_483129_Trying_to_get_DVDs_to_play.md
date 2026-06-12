---
title: "Trying to get DVDs to play"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by deathspell on 2007-06-24
I tried the instructions given in the following link

[http://ubuntuforums.org/showthread.php?t=413625](http://ubuntuforums.org/showthread.php?t=413625)```


wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

The above command gave me an error saying "gpg: no valid OpenPGP data found." so I didn't continue with it. What went wrong? What do I need to do?

---

### Post by mig5 on 2007-06-24
Do the commands in this order:

```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

(each line is a command, the '|' doesn't mean a new line)

Source: [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by deathspell on 2007-06-24
Okay, I did that, and got this...

         
Fetched 24.6kB in 22s (1071B/s)                                                
Reading package lists... Done
W: Duplicate sources.list entry [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/at.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

How do I fix that? Should I have not edited the souces.list file?

---

### Post by deathspell on 2007-06-24
Assuming that it was normal, I'm doing the update and install the codecs.. Hopefully it should play my DVDs after that :)

---

### Post by deathspell on 2007-06-24
DVDs are now playing fine. Thanks!

---

### Post by mig5 on 2007-06-24
> **deathspell said:**
> Okay, I did that, and got this...

         
Fetched 24.6kB in 22s (1071B/s)                                                
Reading package lists... Done
W: Duplicate sources.list entry [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/at.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

How do I fix that? Should I have not edited the souces.list file?

I'm guessing that you got that message because you had already attempted to add the repository, or maybe its because the medibuntu repository has packages that overlap with the ones in the other repositories (like ffmpeg and codecs).  Glad to hear that you got it working anyway.

---

