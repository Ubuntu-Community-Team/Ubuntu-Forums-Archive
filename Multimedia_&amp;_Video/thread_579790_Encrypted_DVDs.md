---
title: "Encrypted DVDs"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by Cirrocco on 2007-10-18
so it's day 1 of Gutsy and I have nothing that will play and encrypted DVD.

I think we need a couple things:

1) what applications, librarys, codecs, and repos you need to play a rented movie.

2) a how to set it up so it works guide.

3) some distinction as to what the difference is between gstreamer and xine and which goes best with Ubuntu.

4) a how to remove all the crap to installed to make it work - but it failed anyway

---

### Post by scrooge_74 on 2007-10-18
[https://help.ubuntu.com/community/RestrictedFormats#head-72bdc20d068d618fa98aa7d4477a8b56e4a8255a](https://help.ubuntu.com/community/RestrictedFormats#head-72bdc20d068d618fa98aa7d4477a8b56e4a8255a)

---

### Post by Cirrocco on 2007-10-19
Thanks, Scrooge.

those steps helped me and now it's working.

I still find it unfortunate that these basic requirements aren't bundle together into a single check box in the add-remove applications section of Ubuntu.

---

### Post by scrooge_74 on 2007-10-19
There are suppose to be in the restricted drivers section under Admin.  Remember is not legal in all countries to use this kind of codecs and libraries. 

 At least on the new release this is suppose to be easier to do. I won't be going near it since I like the philosofy of if it ain't broken just tweak it.

I am not a fan of running the latest distro, I'm kind of old fashion :)

---

### Post by tommcd on 2007-10-20
> **Cirrocco said:**
> Thanks, Scrooge.

those steps helped me and now it's working.

I still find it unfortunate that these basic requirements aren't bundle together into a single check box in the add-remove applications section of Ubuntu.

In gutsy you can just install "ubuntu-restricted-extras" using synaptic or apt-get. Then get the w32 codecs and libdvdcss2 from medibuntu:
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by scrooge_74 on 2007-10-20
in other words they made a package to install all the other packages.

---

### Post by tommcd on 2007-10-21
> **scrooge_74 said:**
> in other words they made a package to install all the other packages.

Pretty much. The ubuntu-restricted-extras installs flash, java, all the gstreamer stuff and most of the other codecs. I just needed to get the w32 codecs and the libdvd* stuff from medibuntu. Make sure you add the universe and multiverse repos to  your sources.list or by checking them in synaptic.

---

