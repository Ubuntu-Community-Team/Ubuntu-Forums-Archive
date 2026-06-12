---
title: "Installing LIRC Ubuntu 15.04"
date: 2015-05-13
forum: Multimedia Software
---

### Post by Mac Tzu on 2015-05-13
Hey User,

I setup just setup a new media pc Woot !
 but :( I am having LIRC issues.

install no prob 
services load in systemd 
remote setup and irw sees remote commands no prob 
but remote doesn't work with Vlc and kodi 
then I run 
```

dpkg reconfigure lirc 

```
the it works perfectly 
 the next time I boot it stops working, if I run dpkg it works again 

what is going on ?
what dpkg doing ?

---

### Post by dino99 on 2015-05-13
it might be a kodi issue with systemd
sadly the wiki is a bit old; but who knows maybe you'll find an idea ;)  [https://help.ubuntu.com/community/LIRC](https://help.ubuntu.com/community/LIRC)

glancing at the 'Fedora' part can help too  [https://www.mythtv.org/wiki/LIRC](https://www.mythtv.org/wiki/LIRC)

---

### Post by Mac Tzu on 2015-05-14
dino99, 

Hey man thank you for you comments.  :( both of those links are old.  I have had a look at package and sent of question to the maintainers.  But I am still open to suggestions and ideas

---

