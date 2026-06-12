---
title: "can not see apple trailer"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by parvez on 2008-03-19
hi 
I am using Ubuntu 7.10 32bit on Intel Duel Core 3 GHz. I have firefox and mozilla-mplayer. But when I watch any trailer from apple web site, I can only hear the sound no video. I need to mention that I have symbolic links of all mplayer codecs  from my home folder .mozilla/plugins to /usr/lib/mozilla/plugins/. Any can help me why I can not see apple trailers. Thanks in advanced

---

### Post by wolfen69 on 2008-03-19
this works for me:
```
sudo apt-get remove --purge totem-mozilla
```
for good measure, and extra codecs:
```
sudo apt-get install vlc
```
totem mozilla can conflict with mplayer.

---

### Post by parvez on 2008-03-20
Hi 
Thanks for your reply, but it did not work. I don't have totem-mozilla. I have just install vcl. But it is still the same problem. No vedio only sound

---

### Post by wolfen69 on 2008-03-20
do you have flash installed?

---

### Post by parvez on 2008-03-20
Are you talking about Macromedia flash. I am not sure about flash player. How can I check?

---

### Post by parvez on 2008-03-20
Hi 
I have jus install flash player from Adobe site but it still does not work.

---

