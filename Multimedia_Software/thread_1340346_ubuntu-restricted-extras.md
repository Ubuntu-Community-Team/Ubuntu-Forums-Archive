---
title: "ubuntu-restricted-extras"
date: 2009-11-28
forum: Multimedia Software
---

### Post by BobSongs on 2009-11-28
Karmic Koala is encountering an odd error as it attempts to download and install the ubuntu-restricted-extras package, both in the terminal as in Synaptic Package Manager. The error message says:
> **E: ttf-mscorefonts-installer: subprocess installed post-installation script returned error exit status 1**The console offers many:
> [B]Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'[/B]Every MS font fails to download. It is as if SourceForge shifted where they are located and it foils the installation of the restricted extras.

I imagine I can install the various components that make up this package, but I was wondering if anyone else was running into this difficulty.

---

### Post by Raffles10 on 2009-11-28
I installed ubuntu-retricted-extras on a new Karmic install yesterday, it took a while, in particular it took several attempts to find courier32 but it did eventually download and install. I think sometimes the sourceforge sites are just very slow and drop outs are frequent depending on the time of day. Persist and it should work, eventually.

---

### Post by BobSongs on 2009-12-01
It's always fun to resolve your own issues.

"DNS Resolve" seems much slower in Karmic. This is a known problem (that's why some websites seem to take an unusually long time to load).

The fix that worked for me (and pounding at repeated installs of **ttf-mscorefonts-installer** didn't work) is commented in bugs.launchpad.net by "Laurent". Here's the link and I'll quote the text for the readers.

The text Laurent removed is in bold red text.

Link: [https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/431217/comments/21](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/431217/comments/21)

> To me it seems a pb of DNS time out.
 I solved the [problem] with this workaround/dirty patch.
 In the file **/var/lib/****dpkg/info/****ttf-mscorefonts****-installer.****postinst** (coming with package first install),
I removed the DNS time out in watchdog  line 148 to get

 > if ! wget --continue --tries=1 [COLOR=Black]--connect-timeout=5 [/COLOR]--read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff ; then

  instead of

 > if ! wget --continue --tries=1 [COLOR=Green]**[COLOR=Red]--dns-timeout=10[/COLOR] **[COLOR=Black]--connect-timeout=5[/COLOR][/COLOR] --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff ; then

 But I can not tell you why it failed with this package and not with others.
So, essentially, remove **[COLOR=Red]--dns-timeout=10[/COLOR]** from the text.

---

