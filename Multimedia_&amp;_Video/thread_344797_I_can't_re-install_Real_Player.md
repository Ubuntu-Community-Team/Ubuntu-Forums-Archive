---
title: "I can't re-install Real Player"
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by Handssolow on 2007-01-23
Anyone else posted with this problem?
This afternoon I selected to download the 6 items showing in the Update Manager. After completion I selected to check again and a greyed-outRealPlayer update was showing but choosing install wasn't effective.

Next I choose to use sudo aptitude update and sudo aptitude dist-update. There's a message about a conflict with libc6 and Real Player. So I remove Realplayer expecting to be able to re-install but get this error using synaptic package manager-
realplay:
  Depends: libc6 (>=2.5-0ubuntu1) but 2.4-1ubuntu12.2 is to be installed 

I think libc6 was one of the items in the latest update. I am unable to use Automatix2 to install Realplayer without an error showing. I am unable to reinstall RealPlayer.

Suggestions?

---

### Post by david_2001 on 2007-01-23
A quick browse around [http://archive.canonical.com](http://archive.canonical.com) confirms what you write.  RealPlay has now been added to the Edgy repository and, according to packages.gz, does indeed depend on:> 
libatk1.0-0 (>= 1.12.1), **libc6 (>= 2.5-0ubuntu1)**, libgcc1 (>= 1:4.1.1-12), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.10.3), libpango1.0-0 (>= 1.14.5), libstdc++5 (>= 1:3.3.4-1), libx11-6, libxext6, libxv1
To be honest, I've uninstalled RealPlayer, primarily because the mozilla-mplayer plugin works much better with the RealPlayer video on the BBC's news website.  The Dapper realplay package will still install on Edgy, however.

---

### Post by hikaricore on 2007-01-23
I think a the package maintainers made a version typo or maybe we didn't get the new version of libc6 when we should have.  >.<

I ran:
```

sudo aptitude download realplay
sudo dpkg -i --force-all packagename.deb
sudo gedit /var/lib/dpkg/status

```
Searched for the realplay package, and finally changed the version of libc6 in the dependencies.

This isn't the easiest way to do it but it works.  Tho update manager will tell you repeatidly that the realplay packages is available again and that it's being held back.  This is the same version that you just downloaded so ignore it til this issue is resolved.

---

### Post by wh0rd on 2007-01-24
The problem was resolved by the latest libc6 update. Sorry about the post earlier, I pasted the wrong link.

---

### Post by Handssolow on 2007-01-24
The problem has been sorted now and I've been able to install the modified Real Player using synaptic. My thanks to the people concerned.

---

