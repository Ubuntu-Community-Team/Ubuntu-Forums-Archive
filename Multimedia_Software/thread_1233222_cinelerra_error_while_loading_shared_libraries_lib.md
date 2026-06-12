---
title: "cinelerra: error while loading shared libraries: libfaad.so.0"
date: 2009-08-06
forum: Multimedia Software
---

### Post by bobnutfield on 2009-08-06
Hello Everyone,

This should be easy to fix, but for the life of me I cannot figure out why it is looking for this lib and not finding it as it is installed, but is listed like this:

> bob@bob-laptop:~$ whereis libfaad.so.0
libfaad.so: /usr/lib/libfaad.so.2 /usr/lib/libfaad.so


Anyone know how to solve this?  In the Arch forums it was suggested that a symlink be created.  I used to use Cinelerra quite a lot in previous versions and never had an issue.

Any thoughts appreciated

Bob

---

### Post by mobrien118 on 2010-04-04
> **bobnutfield said:**
> Hello Everyone,

This should be easy to fix, but for the life of me I cannot figure out why it is looking for this lib and not finding it as it is installed, but is listed like this:

Bob

Me too, after Lucid upgrade, trying to run Boxee.

???

---

### Post by kelvin spratt on 2010-04-04
[COLOR=Red]In the Arch forums it is not suggested that a symlink be created[/COLOR].

---

### Post by mobrien118 on 2010-04-04
> **kelvin spratt said:**
> [COLOR=Red]In the Arch forums it is not suggested that a symlink be created[/COLOR].

A symlink to which one, and from where?

I get this:

```
mobrien@living-room:~$ /opt/boxee/run-boxee-desktop
/opt/boxee/Boxee: error while loading shared libraries: libfaad.so.0: cannot ope                                                                                            n shared object file: No such file or directory
/opt/boxee/run-boxee-desktop: 38: /opt/boxee/give_me_my_mouse_back: not found
mobrien@living-room:~$ whereis libfaad.so.0
libfaad.so: /usr/lib/libfaad.so.2 /usr/lib/libfaad.so /usr/lib64/libfaad.so.2 /usr/lib64/libfaad.so
```

---

