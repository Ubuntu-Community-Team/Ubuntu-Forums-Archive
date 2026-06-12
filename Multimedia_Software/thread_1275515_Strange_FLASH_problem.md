---
title: "Strange FLASH problem"
date: 2009-09-25
forum: Multimedia Software
---

### Post by Sukotto on 2009-09-25
Fresh install of Jaunty. I went to youtube and the system directed me to install plug ins to support the videos. Installed what was promted for me to install. Then I notice that the you tube videos looked a bit off. so I went to the Adobe website and dl'ed and installed FLASH and now when I go to youtube the videos are a bit strange looking, almost like there are 2 videos playing and giving a off shost effect sort of, hard to describe. and also on some pages with as I get a grey box wth a play sign? I am a little confused here.

---

### Post by Sukotto on 2009-09-26
Bump

---

### Post by karesz on 2009-09-26
It seems that you've installed swfdec or gnash or both. Uninstall them. (Synaptic-search-gnash, search-swfdec, then install flashplugin-nonfree . BTW, don't forget to enable the multiverse and restricted repositories.
Hope it helps. And don't think that adobe's flashplayer (the nonfree) will be as smooth as in windows. It's adobe's fault, that it isn't that fine in unix/unix-like systems...

---

### Post by Sukotto on 2009-09-27
Thanks! That fixed it!

---

