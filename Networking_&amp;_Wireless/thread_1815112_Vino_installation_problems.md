---
title: "Vino installation problems"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by linuxwonder on 2011-07-30
Hi All:

Has anyone been able to successfully install vino 3.1.1 from the vino-3.1.1.tar.gz distribution? I begin with the configure script and cannot seem to get past the following error:

[I][B]checking for glib-genmarshal script... configure: error: glib-genmarshal not listed in glib-2.0 pkg-config file
[/B] [/I]
I have ubuntu 10.04

Thanks

---

### Post by chili555 on 2011-07-31
You will need to install libglib-2.0-dev. Other packages may need to be installed after that. Post back if you get stuck.

Edit: I got all the way through ./configure by installing a few extra packages. Here is the relevant part of my log.

---

### Post by linuxwonder on 2011-07-31
Thanks chili555! I made it a little farther but now I get this

configure: error: Package requirements (glib-2.0 >= 2.17.0 gio-unix-2.0 gtk+-x11-3.0 >= 3.0.0      ) were not met:

No package 'gtk+-x11-3.0' found

I noticed the gtk+... stuff in you log. My question now is this. What generated the log. I have tried to search for this package using the synaptic package manager but to no avail.

Thanks

---

### Post by chili555 on 2011-07-31
> What generated the log.It is a snipped copy of my /var/log/apt/history.log. It shows the packages I installed and the dependencies Synaptic installed to get all the way to the end of ./configure. Assuming you are running Natty, install everything mentioned in the log and you'll be all set. In many cases, if you select one package in Synaptic, all the dependencies will be proposed as well.

You don't need to worry about the full description; e.g. to install x11proto-resource-dev-1.1.1-1, you only need to look for and select x11proto-resource-dev, or, in a terminal:```
sudo apt-get install x11proto-resource-dev
```In many cases, when compiling these things, configure complains that you don't have a library or package installed when it really wants the development tools or -dev package.

As fun as compiling from source is, is the vino that's in the Ubuntu repositories not working as expected?

---

