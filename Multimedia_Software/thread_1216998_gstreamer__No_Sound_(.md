---
title: "gstreamer :: No Sound :("
date: 2009-07-18
forum: Multimedia Software
---

### Post by indranama on 2009-07-18
I was cleaning my apt cache this morning, and after that Totem only shows video, but no sound. I've installed totem-xine and it played sounds well. My belowed app, Songbird, which uses only gstreamer does not play audio.

Is there a way to repair gstreamer ? (I've tried reinstalling some gstreamer packages at Synaptic, but it didn't solve. May be I didn't reinstall the faulty package)

Its very helpfull if anyone can help me in this issue.
Thanks.

---

### Post by kostkon on 2009-07-19
Do you mean that you did a
```
sudo apt-get autoremove
```
?

If that's what you did, then you could check the *dpkg.log* log file to see what packages were removed.

You can access it easily using the *System Log* (*System &#8594; Adminstration &#8594; System Log*) utility. If it's not listed there already, you can add it by selecting *File &#8594; Open*. It resides in */var/log*.

Or in the terminal, give, for example:
```
gedit /var/log/dpkg.log
```

---

### Post by indranama on 2009-07-19
Honestly speaking, I was so foolish and all I did was run the Ubucleaner script.([I got it from UbuntuGeek]("http://www.ubuntugeek.com/ubucleaner-simple-bash-script-to-keep-your-ubuntu-system-clean.html"))

it says it only removes cached files, however it seems it had wiped out my gstreamer. :(

---

