---
title: "unity not working with glew 1.5.7 version"
date: 2011-02-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by marijus on 2011-02-01
todays update to libglew1.5-1.5.7 and libglewmx1.5-1.5.7 broke unity for me (Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)).

workaround downgrade this two packages to version 1.5.2

bugreport: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/711401](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/711401)

---

### Post by mc4man on 2011-02-01
You'd want to hold off on those updates (libglew1 and libglewmx1) till you see a new unity and most likely libnux* updates
(not confined to intel

---

### Post by jim11 on 2011-02-01
How would one go about downgrading these packages?

---

### Post by Harry33 on 2011-02-01
> **jim11 said:**
> How would one go about downgrading these packages?

Like this:
Go to launchpad,
[https://launchpad.net/ubuntu/+source/glew/1.5.2-0ubuntu1](https://launchpad.net/ubuntu/+source/glew/1.5.2-0ubuntu1)
select your architecture (32- or 64-bit),
download the packages you want to downgrade, also all upgraded dependencies.
Then in terminal, go to the folder where you downloaded them to and run
```
sudo dpkg -i package1.deb package2.deb ...

```

---

### Post by coffeecat on 2011-02-01
> **Harry33 said:**
> Like this:
Go to launchpad,
[https://launchpad.net/ubuntu/+source/glew/1.5.2-0ubuntu1](https://launchpad.net/ubuntu/+source/glew/1.5.2-0ubuntu1)
select your architecture (32- or 64-bit),
download the packages you want to downgrade, also all upgraded dependencies.
Then in terminal, go to the folder where you downloaded them to and run
```
sudo dpkg -i package1.deb package2.deb ...

```

Yes, but where do you download them from? I can't find libglew or libglewmx where they ought to be here:

[http://archive.ubuntu.com/ubuntu/pool/main/libg/](http://archive.ubuntu.com/ubuntu/pool/main/libg/)

**EDIT**: Don't worry, I've found it. libglew is filed under G. But, of course! :rolleyes:

[http://archive.ubuntu.com/ubuntu/pool/main/g/glew/](http://archive.ubuntu.com/ubuntu/pool/main/g/glew/)

**EDIT2**: Yup. That works nicely with an ATI card and the open source driver. Thanks. In fact I didn't need to download any dependencies; they were already in situ.

---

### Post by webme on 2011-02-01
Libglew 1.5.7 has been renamed to 1.5.2.1 and is available now as an update (they say that 1.5.7 will be post-alpha 2 fixed). Unity is working again.

---

### Post by coffeecat on 2011-02-02
> **Harry33 said:**
> Like this:
Go to launchpad,
[https://launchpad.net/ubuntu/+source/glew/1.5.2-0ubuntu1](https://launchpad.net/ubuntu/+source/glew/1.5.2-0ubuntu1)

> **coffeecat said:**
> Yes, but where do you download them from? I  can't find libglew or libglewmx where they ought to be here:

[http://archive.ubuntu.com/ubuntu/pool/main/libg/](http://archive.ubuntu.com/ubuntu/pool/main/libg/)

**EDIT**: Don't worry, I've found it. libglew is filed under G.

[http://archive.ubuntu.com/ubuntu/pool/main/g/glew/](http://archive.ubuntu.com/ubuntu/pool/main/g/glew/)

I  must be losing my marbles! I was sure Harry33's link resolved to the  bug report yesterday, not to a page where you could download the  packages I was looking for. Or perhaps I was suffering from Unity  withdrawal syndrome. Sorry, folks. :frown:

> **webme said:**
> Libglew 1.5.7 has been renamed to 1.5.2.1 and is available now as an update (they say that 1.5.7 will be post-alpha 2 fixed). Unity is working again.

Yes, I see there's a package being offered called libglew1.5_1.5.7.is.1.5.2-1ubuntu1_amd64.deb, but if that's simply libglew1.5-1.5.7 in disguise, isn't that simply going to break Unity again? Or do I need to buy some more marbles? :|

---

### Post by tjeremiah on 2011-02-02
> **coffeecat said:**
> I  must be losing my marbles! I was sure Harry33's link resolved to the  bug report yesterday, not to a page where you could download the  packages I was looking for. Or perhaps I was suffering from Unity  withdrawal syndrome. Sorry, folks. :frown:



Yes, I see there's a package being offered called libglew1.5_1.5.7.is.1.5.2-1ubuntu1_amd64.deb, but if that's simply libglew1.5-1.5.7 in disguise, isn't that simply going to break Unity again? Or do I need to buy some more marbles? :|

I updated last night and all was well.

---

### Post by coffeecat on 2011-02-02
> **tjeremiah said:**
> I updated last night and all was well.

Confirmed here. I've just updated from libglew and libglewmx version 1.5.2 to "1.5.7.is.1.5.2" and Unity is fine. I can see what they're doing now. I misread the  "1.5.7.is.1.5.2" name to be the 1.5.7 package renamed, but it must be the 1.5.2 package renamed, which allows people to upgrade from 1.5.2 or the broken 1.5.7.

---

### Post by Harry33 on 2011-02-02
> **coffeecat said:**
> 
...
Yes, I see there's a package being offered called libglew1.5_1.5.7.is.1.5.2-1ubuntu1_amd64.deb, but if that's simply libglew1.5-1.5.7 in disguise, isn't that simply going to break Unity again? Or do I need to buy some more marbles? :|

libglew1.5_1.5.7.is.1.5.2-1ubuntu1
means the following:
- its version number is higher than that of the previous version to ease the update process (update manager, synaptic, apt-get ...)
- it is really the same as version 1.5.2
- updating to this version is basically the same as downgrading to version 1.5.2

---

