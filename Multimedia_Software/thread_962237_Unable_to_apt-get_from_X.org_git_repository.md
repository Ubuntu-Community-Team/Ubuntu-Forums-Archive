---
title: "Unable to apt-get from X.org git repository"
date: 2008-10-29
forum: Multimedia Software
---

### Post by suncoolsu on 2008-10-29
The Intel driver for X.org is available from the public X.org git repository: 
```

git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel

```

when I type this, I get this error
```

$ bash  git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel: No such file or directory


```

I guess its because git repository is not added? 

Can some one suggest how to fix this problem?
Otherwise is there a way around to download these drivers? I need them to install driver for my Intel GMA X3100. I am unable to switch to resoltuion greater then 800x600, I know my monitor has a better resolution than this but somehow cannot do that.

Thanks

---

### Post by ucastrobr on 2012-09-04
First, instaled git:
```
sudo apt-get install git-core git-gui git-doc
```

After code is git clone + git://...........:
Example:

```
git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
```

Sorry, for time of the answer.

Site
[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

---

### Post by cariboo on 2012-09-04
This is a 4 year old thread, things have changed quite a bit since it was created. The op of the thread hasn't been back for almost 2 years. Thread closed.

---

