---
title: "network manager upgrade"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by kellyrt on 2009-04-12
OK I'm a totally new using Ubuntu, what I'm wanting to do is upgrade the my network manager app 0.6.6 to 0.7.0.100 I'm lost and need help with this?  where do I start?

Thanks

Kelly

---

### Post by cariboo on 2009-04-12
If you are runniong Intrepid v.8.10 the version of network manager youo are looking for is in the repositories. It should be installed as an update.

Jim

---

### Post by kellyrt on 2009-04-12
I'm running 8.04 on a dell mini 12 I have download and unpacked the software, but when I goto terminal and type ./configure this is what I get back  "~/NetworkManager-0.7.0.100$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details."


I'm lost this is my first Linux machine where do I go from here?

Thanks

---

### Post by diedo on 2009-04-12
you need a c and C++ compiler 


```
apt-get install  gcc g++ 
```

---

### Post by tom56 on 2009-04-12
You don't need to do that. Go to System->Administartion->Update Manager, any updates you need to install will be listed there. What is it you need from the new version?

---

### Post by kellyrt on 2009-04-12
The new version will recognize my pantech um175 usb air card. When I go to the update manager is says everything is up to date.

---

### Post by tom56 on 2009-04-12
If you need it that bad then the best thing to do is upgrade to 8.10

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by kellyrt on 2009-04-13
I'm told I can't update to 8.10 this is a video driver issue with the dell mini 12.  Any other Ideas?

Thanks

Kelly

---

