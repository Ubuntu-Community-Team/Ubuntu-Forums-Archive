---
title: "Instaling Ceton InfiniTV USB drivers"
date: 2012-05-04
forum: Multimedia Software
---

### Post by b3orion on 2012-05-04
Hello helpful people,
I seem to be running into a problem when trying to install the InfiniTV USB drivers.
I downloaded all the .tar files, extracted and set off installing after reading the README file.
I type ```
./configure --prefix=/usr
``` as per readme, it starts to do its thing, then stops and tells me:
```
checking for LIBNL... no
configure: error: Package requirements (libnl-1) were not met:

No package 'libnl-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBNL_CFLAGS
and LIBNL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```I have used synaptic package manager to make sure LIBNL is installed, but the driver installation does not seem to notice that it is installed. The Driver install mentions something about adjusting ```
PKG_CONFIG_PATH
``` or setting environment variables, but i have no clue how to do that! Is there something I am missing or is LIBNL not installing correctly? I notice the driver install asks for ```
libnl-1
``` but Ubuntu installs ```
libnl1
``` without the hyphen. Could that be the issue?

So to sum it up, can someone help me install this driver by fixing the libnl-1problem?
Thanks for the help!

---

