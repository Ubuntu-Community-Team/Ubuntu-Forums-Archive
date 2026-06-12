---
title: "Songbird 1.2 &amp; emesene-crazy"
date: 2009-07-02
forum: Multimedia Software
---

### Post by monikgtr on 2009-07-02
A few weeks ago, I installed Songbird 1.2. It is really really a lot better than the previous version :P But, I found out that most plugins weren't updated yet. To fix that, download the latest version of the plugin, open the .xpi with archive manager (I'm running Ubuntu, don't know what is the name of the app that does that in other distros), open install.rdf and change one of the last lines so that it reads:
```
em:maxVersion="1.2.0"
```

Do this at your own risk!


And now, what I considered most important, is to get the *currentsong* plugin working. Note: I'm running emesene-crazy. This is what I did:
```

1. Go to addons.songbirdnest.com and look for DBusBird, download the latest version

2. Open the .xpi with archive manager

3. Open the file "install.rdf" with gedit, change one of the last lines that says "em:maxVersion>1.1.1" and change it to "em:maxVersion>1.2.0". Save. A window will prompt, click on update.

4. After the update, close both gedit and archive manager. Drag the updated .xpi to your songbird addon's list, install and restart.

5. Download [http://rapidshare.com/files/153886509/songbird_emesene.tar.gz.html]("http://rapidshare.com/files/153886509/songbird_emesene.tar.gz.html") and extract, copy the files inside the folder to /usr/share/python-support/emesene/plugins_base/currentSong/

6. Restart emesene, and configure the current song plugin :P 
```


I hope this will work for someone else as well! :)

---

### Post by o_z on 2009-07-03
It really works! I'm using Jaunty, Songbird 1.2 and emesene crazy and it works...


thank you for the post.. =D>

---

### Post by monikgtr on 2009-07-20
I'm now running LinuxMint 7 and this works too! :D

---

### Post by vikrant_me on 2009-08-05
I tired a lot of things, none of them worked eventually i just installed the  livetweeter plug-in for songbird, just install it from within songbird by going to the plug-in tab and search for it there.

---

### Post by Akedz on 2009-08-06
tried this in arch, works like a charm. except the directory changes from 
/usr/share/python-support/emesene/plugins_base/currentSong/  to   /usr/share/emesene/plugins_base/currentSong.

---

### Post by monikgtr on 2009-08-16
I re-installed Mint Gloria today, and odd.. but the directory has changed to the last one you referred. :O

> **Akedz said:**
> tried this in arch, works like a charm. except the directory changes from 
/usr/share/python-support/emesene/plugins_base/currentSong/  to   /usr/share/emesene/plugins_base/currentSong.


**Edit:**
The reason why the directory had changed was because I forgot to install emesene crazy and just installed emesene 1.0 from the repos. Didn't notice untill I couldn't find some features xD

---

