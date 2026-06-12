---
title: "XMLTV - Australia Not Listed?"
date: 2008-03-18
forum: Mythbuntu
---

### Post by nasha on 2008-03-18
Hey Guys,
Just installing another backend for a friend and ive hit a glitch during the mythtv-setup.

When selecting video sources, it provides no option for Australia..?

Can anybody tell my why its not there (same install CD i used for my setup), and most importantly how i can overcome it?

Any help would be greatly appreciated!
Nasha

---

### Post by laga on 2008-03-18
You need to install a XMLTV grabber for Australia.Iit'll have to support the 'baseline' capability at least, and probably 'manualconfig'. (see [http://www.xmltv.org/wiki/xmltvcapabilities.html](http://www.xmltv.org/wiki/xmltvcapabilities.html))

If you can't find a grabber which supports those capabilities then you can still resort to using mythfilldatabase --file.

---

### Post by nasha on 2008-03-18
Ive downloaded a tv_grab_au, put it in /usr/bin and run:
```
 tv_grab_au --configure --configfile ~/.mythtv/FTA-Oz.xmltv
```
I then need to put my channels into that xml file, as well as my username and password, and everything should work?

---

### Post by jbman on 2008-03-19
follow the guide on this site
[http://www.ozmyth.com/](http://www.ozmyth.com/)

---

### Post by nasha on 2008-03-19
jman: Thats what ive used everytime in the past... But if you look at the screen shots, its selecting Australia in the listing grabber box... It isnt there for me... Thats my problem

---

### Post by kombipom on 2008-03-20
This isn't an answer to your problem but something that you should be be aware of.  tv_grab_au_reg (as suggested on the ozmyth site) is going to stop working in a few days ( 31/3/08 ) with the community data from oztivo  I still haven't found an alternative that works yet.  I found one called tv_grab_oztivo but it fails to run, crashing out when trying to create a config file.  Have any of you found a way around this?

---

### Post by nasha on 2008-03-20
Here's the alternative: Shepherd
Im trying it out now

```
http://svn.whuffy.com/index.fcgi/wiki/
```

---

### Post by callagga on 2008-05-20
I seem to be getting a blank screen at this URL (i.e. for shepherd).  Is the site down?

---

### Post by parsim on 2008-05-27
That URL is wrong. Try the main page: [http://svn.whuffy.com/]("http://svn.whuffy.com/")

---

