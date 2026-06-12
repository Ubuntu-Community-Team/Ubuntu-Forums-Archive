---
title: "Flash Doesn't Like Non-Flash Stuff"
date: 2008-10-08
forum: Multimedia Software
---

### Post by Unanimated on 2008-10-08
When I go to a site that displays a flash banner on its home screen, then has HTML-based selections at the top (for example, Dell.com) I can't see the selections. To see what I'm talking about, go to dell.com, and mouse over Home, Office, and whatever else they have. For me, the Flash video covers up most of the options. Here's a screenshot.

---

### Post by directhex on 2008-10-08
Fixed by Flash 10.

---

### Post by Jabz.biz on 2008-10-08
hmm...I also have my troubles with flash. How do I get that update? How can I upgrade to flash 10?

---

### Post by minky311 on 2008-10-08
The First thing you should do is open up synaptic package manager system->administration->synaptic package manager and search for flash player non free and uninstall it. Also search for libflashsupport and uninstall it if you have it. It is no longer needed in flash player 10.

Go here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) scroll down to the bottom and download the plugin for linux in tar.gz format.Save it to the desktop. Right click it and select extract here.

Next Open up a terminal applications->accessories->terminal and do the following one at a time.
```
cd Desktop
cd install_flash_player_10_linux
./flashplayer-installer

```

Then press enter to install. Make sure any browsers you have open are closed.

---

### Post by Unanimated on 2008-10-11
When I installed Flash 10 the first time, it crashed my Firefox a lot, so I reverted back to Flash 9. Is Flash 10 fully released now?

---

### Post by minky311 on 2008-10-11
No it isn't but it seems to be a lot more stable than flash 9 on my install and I thought it might end up being the same for you.
If it does seem to crash a lot then just continue to use flash 9.

---

