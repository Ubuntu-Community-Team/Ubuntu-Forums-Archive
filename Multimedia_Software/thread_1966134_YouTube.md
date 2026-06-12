---
title: "YouTube?"
date: 2012-04-26
forum: Multimedia Software
---

### Post by inspiredbylasers on 2012-04-26
Has anyone else run into any issues with YouTube? Despite having all necessary drivers installed, YouTube doesn't even grant me a loading error- rather, it presents an entirely-black screen. Any ideas?

Best,
Y.

---

### Post by ExSuSEusr on 2012-04-27
DO you have flash installed?

---

### Post by IWantFroyo on 2012-04-27
```
sudo apt-get install flashplugin-installer
```Retry.

Or you could install Google Chrome. I hear Flash is now supported as an add-on.

```
sudo apt-get install chromium-browser
```

You'll have to track the plugin down on the webstore, however.

---

### Post by inspiredbylasers on 2012-04-28
Updating Flash made the difference (was not automatically updated after my non-clean install of final vs. Beta LTS)

Thanks!

-Y.

---

