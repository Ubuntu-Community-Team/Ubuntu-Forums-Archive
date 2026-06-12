---
title: "Removing proprietary multimedia codecs: What and How"
date: 2014-03-01
forum: Multimedia Software
---

### Post by saved2serve on 2014-03-01
Hi, I know this is an odd request, but I would like to know the names and perhaps the locations of  all proprietary multimedia codecs. I   have tried many different Linux distros, and  sometimes want to  place them  (like the lightweight  LXDE desktop) on older PCs to give away. However, i also want to be legal, and most  Linux flavors include   proprietary multimedia codecs, which i  understand in the US requires  licenses (and thus Flurendo sells them),  so i would like to simply remove the proprietary ones, i could find them. 

I know Linux Mint offers a version that does not have them by default,  and it seems Fedora ands OpenSuse does not either, and am not sure about any others,  but i  would like to be able to use  any distro and just remove the proprietary codecs.

And i also know i understand  that this is a  issue of debate, but from what i read at least some are illegal, and even W/8 no longer  ships with the ability to play DVD's unless you buy the Media Center.

Thanks in advance for any help.

---

### Post by monkeybrain20122 on 2014-03-01
There is no proprietary codecs in *buntu unless you install them (*buntu-restricted-extras) Debian, Fedora also don't come with condecs. LXLE does come with codecs (the long term supported version of lubuntu 12.04 but it is made by a third party that is not connected to Canonical or lubuntu)

I don't know how you actually go about "sometimes want to   place them  (like the lightweight  LXDE desktop) on older PCs to give  away" Unless you are some large scale distributor I won't worry about it, it is not like the FBI is going drag you away screaming and kicking just because you give out an old laptop that plays mp3 and dvd out of the box and have vlc preinstalled.  :)

**Edited**: I occasionally give out old laptops with lubuntu on it and I make sure that all the good stuffs are installed lest the recipients think that I give them crap and ask someone else to replace the os with (unlicensed) Windows XP :)

---

### Post by ibjsb4 on 2014-03-01
None of the Buntu's come with proprietary codecs installed.

It has to be added with one of the restricted extras package.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by saved2serve on 2014-03-01
> **monkeybrain20122 said:**
> There is no proprietary codecs in *buntu unless you install them (*buntu-restricted-extras) Debian, Fedora also don't come with condecs. LXLE does come with codecs (the long term supported version of lubuntu 12.04 but it is made by a third party that is not connected to Canonical or lubuntu)

I don't know how you actually go about "sometimes want to   place them  (like the lightweight  LXDE desktop) on older PCs to give  away" Unless you are some large scale distributor I won't worry about it, it is not like the FBI is going drag you away screaming and kicking just because you give out an old laptop that plays mp3 and dvd out of the box and have vlc preinstalled.  :)

**Edited**: I occasionally give out old laptops with lubuntu on it and I make sure that all the good stuffs are installed lest the recipients think that I give them crap and ask someone else to replace the os with (unlicensed) Windows XP :)

Thanks. But i am looking for a lightweight  version that is meant for a system having 512mb or less. I did install Fedora LXDE on one, but it is too basic, besides Yum being unable to work after the first day. 

But i would just like a list of the codecs at issue, but no one seems to know so far.  This is the second forum i asked.

---

### Post by saved2serve on 2014-03-01
> **ibjsb4 said:**
> None of the Buntu's come with proprietary codecs installed.

It has to be added with one of the restricted extras package.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


But the lightweight ones like Lubuntu and Peppermint or XFCE or LXDE versions seem to have them.

Be back tomorrow PM. Thanks

---

### Post by monkeybrain20122 on 2014-03-01
Lubuntu doesn't have them unless you install them (LXLE does have them as noted) Debian is very light weight if you choose a light desktop.

But like I say, big deal. What is the point of installing lubuntu only to have your recipients slapping pirated Windows xp on top since they think Linux is crap because it can't play any media? It is self defeating and for no valid reason IMO. :)

---

### Post by andrew.46 on 2014-03-02
> **saved2serve said:**
> But i would just like a list of the codecs at issue, but no one seems to know so far.  This is the second forum i asked.

There is a set of codecs that Medibuntu used to package which are perhaps the ones that you mean? These can be placed manually either in */usr/lib/codecs *or */usr/local/lib/codecs *but these are of diminishing use these days as MPlayer / FFmpeg are increasingly covering most of the bases. The page is here:

[http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/)

Bear in mind the only useful ones are the 32bit ones. If you crack open one of these (perhaps [this one]("http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20110131.tar.bz2")) you will get your list...

---

### Post by saved2serve on 2014-03-02
> **monkeybrain20122 said:**
> Lubuntu doesn't have them unless you install them (LXLE does have them as noted) Debian is very light weight if you choose a light desktop.

But like I say, big deal. What is the point of installing lubuntu only to have your recipients slapping pirated Windows xp on top since they think Linux is crap because it can't play any media? It is self defeating and for no valid reason IMO. :)

Thanks. I am installing Lubuntu now. This is for someone who only uses the laptop for email and light surfing, while i also want to use Linux for myself. If they want to add multimedia after then that is up to them. Canonical sells them for that reason.

---

### Post by saved2serve on 2014-03-02
> **andrew.46 said:**
> There is a set of codecs that Medibuntu used to package which are perhaps the ones that you mean? These can be placed manually either in */usr/lib/codecs *or */usr/local/lib/codecs *but these are of diminishing use these days as MPlayer / FFmpeg are increasingly covering most of the bases. The page is here:

[http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/)

Bear in mind the only useful ones are the 32bit ones. If you crack open one of these (perhaps [this one]("http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20110131.tar.bz2")) you will get your list...

Thanks, I did unzip it and can see quite a few, but which I assume are both proprietary ones and free ones.

---

### Post by Yellow Pasque on 2014-03-03
> **saved2serve said:**
> But i would just like a list of the codecs at issue, but no one seems to know so far.  This is the second forum i asked.

That's because you're asking the wrong question... The best way to make sure you're not including proprietary codecs is not to install them in the first place (disablilng multiverse repo would be a step in the that direction). Once you start installing them, the horse is out of the barn.
Example: You install gstreamer-plugins-ugly, which pulls in mp3 codecs and such. Now, to get rid of that stuff, you can't just remove the gstreamer-ugly package; you also have to track down the dependencies.

EDIT: I guess someone could give you an exhaustive list, but it would be very tedious/time-consuming. Don't hold your breath. ;)

---

