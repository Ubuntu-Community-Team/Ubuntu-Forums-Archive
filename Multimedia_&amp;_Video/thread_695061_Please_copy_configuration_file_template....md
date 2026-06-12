---
title: "Please copy configuration file template..."
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by Ikith on 2008-02-12
I'm having a lot of trouble with the ati fglrx. I installed it per the wiki guide ([http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)) and whenever I do sudo aticonfig --initial it says
"Warning: Could not find configuration file"
"Please copy configuration file template to /etc/X11"

I looked through the guide and found no fix for this. Please help me out :-(!

---

### Post by zazery on 2008-02-12
That means your xorg.conf file is missing and you need to create it. You can do this by reconfiguring xserver-xorg package.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Ikith on 2008-02-12
I have done everything to get this work... I did what you said and rebuilt xorg.conf and now when I aticonfig --initial it goes through and same with the Xv thing and it comes up as Mesa project! UGH!

---

