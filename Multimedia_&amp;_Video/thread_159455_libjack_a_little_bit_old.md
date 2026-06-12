---
title: "libjack a little bit old"
date: 2006-04-12
forum: Multimedia &amp; Video
---

### Post by wip on 2006-04-12
hi all,

after trying in the past years red hat (planetccrma), gentoo, debian, demudi... i finally found a good distribution because of the good wiki on how to setup a vanilla kernel with preemptive patch! very happy. but, the version of jack in ubuntu is a little bit old : libjack0.80.0-0 version 0.99.0-2ubuntu1. since august 2005 version 0.100.0 is available. how can i installed it???

thanks!
pat

---

### Post by dolson on 2006-04-13
Ubuntu's releases are frozen once they are released. It would be messy for you to upgrade JACK, because then you will have to rebuild or upgrade every app that uses it.

Ubuntu Dapper has JACK 0.100.0, so you can either hold out until June 1st or upgrade to Dapper now. Be warned that Dapper is still being polished up, and there are many bugs in the process of being fixed.

That said, I have been running Dapper for several months with no major issues, and have been trying to contribute with bug reports and fixes where I can.

---

### Post by wip on 2006-04-13
i see... also ardour is a little old too. but i guess for ardour i can compile it from source cause no other package depend on it? hum... not sure at all...

---

### Post by dolson on 2006-04-13
If you want to constantly use the latest versions of all software, then Ubuntu is not the distro for you.

For one thing, once a release is out, it only receives security fixes.

For another, it follows debian for the most part, which means that you will only have software (at least things in universe) as new as debian has.

I'd suggest you either try Dapper, which still won't solve your perpetual upgrade desires, or debian Sid, which still might not have the latest everything, or Gentoo, which is a waste of time compiling all the time, in my opinion, or LFS, which is the same as Gentoo but you get 100% control over everything.

---

