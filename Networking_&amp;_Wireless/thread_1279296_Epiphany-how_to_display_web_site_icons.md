---
title: "Epiphany-how to display web site icons?"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by vickoxy on 2009-09-30
Hi,
i am testing now few web browsers and among them epiphany. Still have some problems with web site icons-only few of them are shown in adress and bookmark panel. Does anyone knows how to fix it?

Thanks

Linux Mint 7 (Ubuntu 9.04)
Epiphany 2.26.1

---

### Post by bapoumba on 2009-09-30
> **vickoxy said:**
> Hi,
i am testing now few web browsers and among them epiphany. Still have some problems with web site icons-only few of them are shown in adress and bookmark panel. Does anyone knows how to fix it?

Thanks

Linux Mint 7 (Ubuntu 9.04)
Epiphany 2.26.1
Try first to clear your cache, and reload a google page.
Then try use the favicon fallback extension.

---

### Post by vickoxy on 2009-09-30
> **bapoumba said:**
> Try first to clear your cache, and reload a google page.
Then try use the favicon fallback extension.

Thanks for suggestion-but i tried that, nothing.

I cleared cache in settings-history. Or should i clear something else? And i activated favicon falback...

---

### Post by vickoxy on 2009-09-30
Well i tried several times to clear cache but nothing.

One more question:

Is it possible to add to right mouse button google search (as in firefox)?

---

### Post by vickoxy on 2009-10-01
No one has similar problems?

---

### Post by vickoxy on 2009-10-01
bump

---

### Post by bapoumba on 2009-10-01
May be this bug ?
[https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/355755](https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/355755)

---

### Post by vickoxy on 2009-10-01
Probably-i left message there, but it seems they are very slow on fixing some problems there-i followed some bugs, but rarely found a solution.

Shame, because it seems that epiphany is faster than firefox and even opera (at least on my dell mini 9), and i like minimalistic design. 

But i miss icons on my personal bookmark bar /instead of text/ and right-mice-google search....

Hoping some one has solution for it.

Thanks!

---

### Post by bapoumba on 2009-10-01
Welcome :)
I did not say I'm using Epiphany and do/did not have this problem. I know I'm not helping..

---

### Post by vickoxy on 2009-10-01
> **bapoumba said:**
> Welcome :)
I did not say I'm using Epiphany and do/did not have this problem. I know I'm not helping..

Thanks for listening :popcorn:

---

### Post by vickoxy on 2009-10-03
I noticed that there is epiphany 2.28. out, but i could not install it. 

Does anyone here uses epiphany and could confirm me that this bug is not fixed /or in new version is fixed/?

I am just curious-it seems that epiphany is not so used, but i have a feeling that epiphany is little bit faster than the firefox or opera. Or it is just subjective opinion?

---

### Post by bapoumba on 2009-10-03
> **vickoxy said:**
> I noticed that there is epiphany 2.28. out, but i could not install it. 

Does anyone here uses epiphany and could confirm me that this bug is not fixed /or in new version is fixed/?

I am just curious-it seems that epiphany is not so used, but i have a feeling that epiphany is little bit faster than the firefox or opera. Or it is just subjective opinion?

Karmic Epiphany is 2.26.1
[http://packages.ubuntu.com/search?keywords=epiphany-browser&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=epiphany-browser&searchon=names&suite=all&section=all)

Unless there is a PPA (which I have not looked for, I'm using epiphany-webkit from another PPA) you will not be able to instll it from the repos.

Epiphany is faster here indeed.

---

### Post by vickoxy on 2009-10-03
> **bapoumba said:**
> Karmic Epiphany is 2.26.1
[http://packages.ubuntu.com/search?keywords=epiphany-browser&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=epiphany-browser&searchon=names&suite=all&section=all)

Unless there is a PPA (which I have not looked for, I'm using epiphany-webkit from another PPA) you will not be able to instll it from the repos.

Epiphany is faster here indeed.

I found epiphany 2.28 in PPA, but couldn´t install it.

Maybe one stupid question-what is epiphany-webkit? Someone somewhere told that his favicon problem was gone when he installed epiphany-webkit, but i didn´t found it in repos....,

---

### Post by bapoumba on 2009-10-03
[https://launchpad.net/~webkit-team/+archive/epiphany](https://launchpad.net/~webkit-team/+archive/epiphany)
[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)
Here are the PPA for webkit and epiphany-webkit

webkit is another engine (different from gecko) that next stable epiphany release will be using.

To install from a PPA, you need to add the ppa in the sources.list and update/upgrade.

---

### Post by vickoxy on 2009-10-03
Thanks-i know how to add to repos ppa´s. But what should i then install? epiphany-broser and epiphany-webkit together? Because, system want me to install gecko? Or both of them?

Is webkit faster than gecko? Because, gecko seems to me faster as firefox or opera...

Thanks

---

### Post by bapoumba on 2009-10-03
You should install epiphany-webkit.

---

