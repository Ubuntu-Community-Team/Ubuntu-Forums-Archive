---
title: "Another amarok mp3 problem"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by apoorvkhurasia on 2007-06-11
I am using kubuntu 6.06 LTS and amarok is using xine engine (there is no other engine). Now when I try to play mp3 files amarok does not play it and submits the track to last.fm and says playlist finished (without playing even a single bit of the track).

I know this problem has been discussed several times but when I tried to install
```

sudo apt-get install libxine-extracodecs

```
(with all the repos in my repos list as uncommented) it says
```

apoorv@oracle:~$ sudo apt-get install libxine-extracodecs
Password:
Reading package lists... Done
Building dependency tree... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate

```

Does somebody know how to get past this? I have already installed libmad0 and gstreamer0.8-mad.

Thanks for any help in advance.

---

### Post by apoorvkhurasia on 2007-06-12
i am posting this so that it is again at the top and more people can look at it.

---

