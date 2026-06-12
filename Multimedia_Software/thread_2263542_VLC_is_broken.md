---
title: "VLC is broken"
date: 2015-02-01
forum: Multimedia Software
---

### Post by CrackedP0t on 2015-02-01
When I open vlc, it says
```

[0000000001ee60e8] core audio output error: option equalizer-preamp does not exist
[0000000001ee60e8] core audio output error: option equalizer-bands does not exist
[0000000001ee60e8] core audio output error: option equalizer-preset does not exist
[0000000001eebfa8] core interface error: no suitable interface module
[0000000001eb8118] core libvlc error: interface "hotkeys,none" initialization failed
[0000000001eecdf8] core interface error: no suitable interface module
[0000000001eb8118] core libvlc error: interface "dbus,none" initialization failed
[0000000001eb8118] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

```

When I try to open a file, it says:
```

[0000000001eecdf8] qt4 interface error: Unable to load extensions module
[00007f3e0800a398] core input error: open of `file://<file>' failed
[0000000001f336e8] core playlist error: could not export playlist

```

This happens with every file I try, leading me to suspect that its media playing libraries are broken.

I've tried purging and reinstalling with apt and running "make uninstall" with the source and reinstalling via apt again, but it never works.

---

### Post by andrew.46 on 2015-02-01
Perhaps try:

```

vlc --reset-config

```

Bear in mind that this will remove any special customisations and options that you have specified for vlc and replace with defaul 'as new' options...

---

### Post by CrackedP0t on 2015-02-01
> **andrew.46 said:**
> Perhaps try:

```

vlc --reset-config

```

Bear in mind that this will remove any special customisations and options that you have specified for vlc and replace with defaul 'as new' options...

No, still not working.

---

### Post by mc4man on 2015-02-02
> **CrackedP0t said:**
> 
I've tried purging and reinstalling with apt and running "make uninstall" with the source and reinstalling via apt again, but it never works.
I would suggest you remove all of vlc, starting with any installed packages. This will do that - 
```
sudo apt-get purge vlc-data
```
Then check that nothing releated to vlc  is installed to /usr/local/*, in particular /usr/local/bin, /usr/local/lib, /usr/local/share
If found then get rid of all.

After cleaning up your mess - 
```
sudo apt-get update && sudo apt-get install vlc
```

---

