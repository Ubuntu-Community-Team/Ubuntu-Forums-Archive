---
title: "[SOLVED] YouTube videos crash Firefox 3.0.1"
date: 2008-09-01
forum: Multimedia Software
---

### Post by dldeskins on 2008-09-01
Within the past week, I have experienced problems with YouTube videos crashing Firefox 3.0.1 (shuts down).  I have problems with other videos (CNN, etc).  I can download them with youtube-dl and play them in Totem, otherwise they crash Firefox.

Has anyone else had these problems?

Thanks

---

### Post by nicedude on 2008-09-01
You should install adobe flashplayer 10 as it solved all my flash problems ( flash format is what you tube and many others use ). It is not in the medibuntu repositories yet ( they have ver 9 ) but you can find a hardy deb package via google or look in the forums here for "install flash 10" as I have seen some guides etc on how to do it and a link to the deb package.


Hope that helps and goodluck

---

### Post by gjoellee on 2008-09-01
[http://kshoster.net/?c=downloads_deb](http://kshoster.net/?c=downloads_deb)

---

### Post by dldeskins on 2008-09-01
OK... I installed v10, but it STILL crashes Firefox.  Keep in mind that NOTHING else crashes Firefox, I can play videos from every other site.  

I have disabled all other add-ons and extensions with no luck. Any other suggestions?

---

### Post by Masoris on 2008-09-01
> **dldeskins said:**
> OK... I installed v10, but it STILL crashes Firefox.  Keep in mind that NOTHING else crashes Firefox, I can play videos from every other site.  

I have disabled all other add-ons and extensions with no luck. Any other suggestions?

Check your flash version again. Newest one is v10 rc which was released on 11th August 2008.
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by dldeskins on 2008-09-01
Masoris,

I had installed v10 from the deb that gjoellee suggested.  When I checked synaptic, it said v10 but the browser plugin said v9.XXX.  So I uninstalled.

When I followed the link and downloaded the tar.gz.  I started installing, but was stuck on the path... the default did not work.  What path should i use?

Thanks,

---

### Post by cariboo on 2008-09-01
To really find which plugin you got installed in Firefox's address bar type:

```
about:plugins
```

It says I have this version installed:

```
Shockwave Flash 10.0.0 d525
```

I still get crashes on occasion, but in my case it opens another window and closing that crashes firefox

Jim

---

### Post by cariboo on 2008-09-01
To really find which plugin you got installed in Firefox's address bar type:

```
about:plugins
```

It says I have this version installed:

```
Shockwave Flash 10.0.0 d525
```

I still get crashes on occasion, but in my case it opens another window and closing that crashes firefox. It is a bug in the flash plugin

Jim

---

### Post by dldeskins on 2008-09-02
> **cariboo907 said:**
> To really find which plugin you got installed in Firefox's address bar type:

```
about:plugins
```

It says I have this version installed:

```
Shockwave Flash 10.0.0 d525
```

I still get crashes on occasion, but in my case it opens another window and closing that crashes firefox. It is a bug in the flash plugin

Jim

Jim, Thanks for the info... I got the new version installed (both were installed) **BUT that was not the problem**.

The real problem was my hosts file.  I use it (like a lot of other people) to block bad web sites.  The one that I use is from [http://www.mvps.org/winhelp2002/](http://www.mvps.org/winhelp2002/) .  Evedently, YouTube is now using one or two of these sites (richmedia.yimg.com? ts.richmedia.yimg.com?).  I commented the two lines out, now the videos will play.

Again, thanks for all the help guys,

Don

---

### Post by bizghetto2 on 2008-09-15
Ok so I took the advice that you gave but now when I try to watch videos from youtube they play for the first 2 seconds and then stop......... always for the first 2 seconds nothing further???

YAY!!!!!!!!!!!!! thank you thank the lord everything works!!

---

