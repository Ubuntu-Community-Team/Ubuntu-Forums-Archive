---
title: "Install Adobe Flash Player for Opera web browser."
date: 2013-11-19
forum: Multimedia Software
---

### Post by ML7rcEx on 2013-11-19
I am running Ubuntu 13.10 and have started using the Opera web browser. But i am unable to watch itv, bbc iplayers (catch up tv). I am informed that i need to install Adobe Flash Player. So would anyone care to tell this old noob how i can install Adobe Flash Player please.

---

### Post by philinux on 2013-11-19
> **ML7rcEx said:**
> I am running Ubuntu 13.10 and have started using the Opera web browser. But i am unable to watch itv, bbc iplayers (catch up tv). I am informed that i need to install Adobe Flash Player. So would anyone care to tell this old noob how i can install Adobe Flash Player please.

Open the Software Center from the launcher on the left. In the search box type flash. It should appear at the top of the list. Click the install button.

---

### Post by ML7rcEx on 2013-11-19
Hi philinux
I have already got the Adobe Flash Player Plugin for Firefox installed but it still don't work?

---

### Post by Yellow Pasque on 2013-11-19
You probably need to create a symlink to the libflashplayer.so file. MNake sure you are in the opera plugin directory, which could be /usr/lib/opera/plugins or something else depending on how/where you installed opera.

```
cd <opera plugin directory>
sudo ln -s /usr/lib/flashplugin-installer/libflashplayer.so
```

---

