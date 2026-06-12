---
title: "Ubuntu Flash Help"
date: 2008-12-24
forum: Multimedia Software
---

### Post by lulio on 2008-12-24
So, there's this great step-by-step instruction-ish place here: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)
but after the Package Installer comes up, by Status it says "Error: Dependency is not satisfiable: libcairo2" and I have *no* idea what to do now. It won't even let me click the "Install Package" button. :confused:

---

### Post by cariboo on 2008-12-24
You can install the flash plugin directly from the repositories:

```
sudo apt-get install flashplugin-nonfree
```

Or better yet install the ubuntu-restricted-extras meta package, and get most of the plugins you need to play most audio/video files.

Jim

---

