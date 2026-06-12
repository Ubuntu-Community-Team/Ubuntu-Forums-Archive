---
title: "ugly fonts in firefox"
date: 2010-08-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Jordanwb on 2010-08-19
See the text in Firefox. Through the terminal I installed firefox-3.5, firefox-kde-support and firefox-branding. I haven't used Kubuntu since 8.04 so I'm out of the loop when it comes to KDE.

Oh god that image is ugly. Give me a minute to upload it to a better image host.

[http://img685.imageshack.us/img685/1001/snapshot1w.png]("http://img685.imageshack.us/img685/1001/snapshot1w.png")

---

### Post by kahumba on 2010-08-19
This works for me:
```

cd /etc/fonts/
sudo mv conf.d/10-hinting-slight.conf .
sudo ln -s conf.avail/10-hinting-slight.conf conf.d/
sudo mv conf.d/10-hinting.conf .
sudo ln -s conf.avail/10-hinting.conf conf.d/
sudo dpkg-reconfigure fontconfig

```I don't remember if rebooting is needed.

Solution taken from:
[http://ubuntuforums.org/showthread.php?p=7094387](http://ubuntuforums.org/showthread.php?p=7094387)

---

### Post by Jordanwb on 2010-08-19
That fixed it thanks. Now I gotta fix KDE's case of Alzheimers because it keeps forgetting my monitor setup. I know its not because of nouveau.

---

