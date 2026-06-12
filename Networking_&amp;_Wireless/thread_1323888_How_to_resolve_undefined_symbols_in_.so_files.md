---
title: "How to resolve undefined symbols in .so files"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by lubod on 2009-11-12
This post might seem kind of backwards, but I'm posting a solution to my problem found online elsewhere (google groups for debian) that worked for me, mainly as a reference for other with similar conundrums. My searching for this was long and aside from the URL given below quite frustrating :-(

My system: Karmic amd64 with all current updates as of 12 Nov, 2009.

My problem: After various (perhaps ill-advised?) gyrations to update Network Manager to a version newer than in the repositories, I ended up with nm-applet unable to start because of "undefined symbols". Apparently, these attempts (with checkinstall used to build source from a tarball) had left a shared object (.so) nm-applet uses in /usr/local, which was taking precedence over the built in system one!

Solution:

How to resolve undefined symbols in .so files

[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/a593453a09a99d0a](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/a593453a09a99d0a)

in short:

run misbehaving program in terminal, e.g. nm-applet (to see error output)

$ nm-applet
nm-applet: symbol lookup error: /usr/lib/libnm-glib.so.2: undefined symbol: nm_ip6_address_unref

ldd /usr/bin/nm-applet|grep /usr/local

this is to check which (if any) of the .so files nm-applet depends on is currently loaded from /usr/local, i.e. if it is using files from a homemade install compiled from source instead of the default ones provided by the distribution

if found:

sudo mv file_shown_above file_shown_above.OLD (or if you want to delete irreversably, instead of rename, substitute rm in place of mv)

retest with ldd command above or by re-running misbehaving program :-)

---

