---
title: "ubuntu icecast startup"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by Ravensound on 2008-04-16
I've tried running the ubuntu icecast server and have two queries:

Is there a simple way to prevent it auto-starting on boot up?

Is it possible to source via winamp 1.8.2b with an encrypted password, as the source won't connect and this seems to be the most likely reason.  How is the makepassword algo supposed to work?

Regards

---

### Post by davidshere on 2008-04-16
Preventing starting at startup:
```
sudo update-rc.d -f icecast2 remove
```

and to put it back:
```
 sudo update-rc.d -f icecast2 defaults
```

Not sure on the winamp problem.  I use ices2 to source.

---

### Post by Ravensound on 2008-04-16
Thanks for the start key.  I run shoutcast already so thought I could add an output to test the icecast from the winamp source but it doesn't appear to support encrypted passwords.

---

