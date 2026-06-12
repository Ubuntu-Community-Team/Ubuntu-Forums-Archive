---
title: "Kaffeine does not work without ALSA; what to do?"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by Saoshyant on 2007-08-08
Saluton,

I installed OSS, which kicked out ALSA.  foobar2000 and Amarok are OK with the changes, it was easy to configure them to use OSS.  But not Kaffeine.  Kaffeine's crashing because Xine can't find ALSA.

So, the question is, how do I set Xine to use OSS?

---

### Post by Saoshyant on 2007-08-08
The answer was given to me by a 4front forum member.  You may find it [here](http://4front-tech.com/forum/viewtopic.php?p=6000#6000).  Very useful to get all applications that depended on or where looking for ALSA working back again, including KMix.

It's possible apriori's reply may be purged in the future, so for the record I'll post it here.

[QUOTE="apriori"]Make sure that the output of aplay -l looks like this:

```
aplay: device_list:204: no soundcards found...
```

If you got some OSS devices listed instead, the ALSA emulation is running and causes any application that currently tries to use ALSA to hang or to simply fail. To prevent the OSS startup script from using the ALSA emulation, do the following:

```
rm /usr/lib/libasound.so.2
ln -s /usr/lib/libasound.so.2.0.0 /usr/lib/libasound.so.2
```[/QUOTE]

---

