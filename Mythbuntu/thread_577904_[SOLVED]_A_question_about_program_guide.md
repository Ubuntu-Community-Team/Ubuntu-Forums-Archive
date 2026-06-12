---
title: "[SOLVED] A question about program guide"
date: 2007-10-16
forum: Mythbuntu
---

### Post by HenrikAn on 2007-10-16
It's probably just me being stupid, but anyway...
I am thinking about a new mythbuntu install on my media computer, but since it is in "production" and I can't afford too much downtime I'm trying to sort out all my questions now.

As far as I can see mythbuntu doesn't come with xmltv. How am I getting my program guide data? (I still have an analog signal. I guess the EIT option would work if I had digital channels?)

Am I missing something or do I have to add xmltv to the install?

---

### Post by superm1 on 2007-10-16
minor bug in the RC prevented it from being installed during the installer.  

As of next week's release, it's been resolved.  

If you want to install xmltv though via the rc, you will just have to do it after the install is done.  Not very difficult or anything.

Just a matter of opening up synaptic and searching for xmltv or 

```
sudo apt-get install xmltv
```

---

### Post by HenrikAn on 2007-10-17
Ahh, okey. Thanks!
I just wanted to make sure I didn't miss some new smart and simple way of managing the program guide.

---

