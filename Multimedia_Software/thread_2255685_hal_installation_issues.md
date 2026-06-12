---
title: "hal installation issues"
date: 2014-12-06
forum: Multimedia Software
---

### Post by spam-h6i on 2014-12-06
I know hal is deprecated and I shouldn't even be trying to install it, but everything seems to be telling me it's the only way to solve my 4oD woes.

I've tried
```

sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update
sudo apt-get install hal
```
but that just seems to give me a wall of errors:
```

Setting up icedtea-netx:amd64 (1.5.1-1ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/javaws doesn't exist
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        dpkg: error processing package icedtea-netx:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of icedtea-7-plugin:amd64:
 icedtea-7-plugin:amd64 depends on icedtea-netx (= 1.5.1-1ubuntu1); however:
  Package icedtea-netx:amd64 is not configured yet.


dpkg: error processing package icedtea-7-plugin:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-plugin:
 icedtea-plugin depends on icedtea-7-plugin; however:
  Package icedtea-7-plugin:amd64 is not configured yet.


dpkg: error processing package icedtea-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 icedtea-netx:amd64
 icedtea-7-plugin:amd64
 icedtea-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Hoping that it had perhaps worked anyway, I soldiered on, but alas, my 4oD tribulations continue. It doesn't seem to be a Flash issue or anything, since iPlayer, Netflix, etc. all work fine.

What's going on and how do I fix it?

[Ubuntu 14.10, 64 bit]

(On an entirely unrelated note, signing up with my all-spam-from-websites-goes-here email address seems to have stuck me with the unfortunate username "spam-h6i", which I don't recall choosing. Is there a way to change it to something that makes my intentions sound less ill?)

---

### Post by bashiergui on 2014-12-07
The hal package depends on some old and probably depracated packages. You have the solution in your output from above. You have to find a way to install each of the dependencies that it complained about. This is called "dependency hell" for a reason. It sucks. Google each package and you'll probably find how to install it.

---

### Post by Yellow Pasque on 2014-12-08
I'm not even sure those errors have anything to do with hal. This seems to be the key error message causing the cascade of others:
```
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/javaws doesn't exist
```

---

### Post by sundarrajan-srgm on 2015-07-28
The mentioned solution worked for me  and i could able to install hal.

I was installing hal to make work 'aptoncd' in my ubuntu.

Thanks for sharing the ppa.

---

