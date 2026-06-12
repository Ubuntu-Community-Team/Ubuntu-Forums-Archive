---
title: "install libdvdcss2 libdvdread4 libdvdnav4 10.10 ubuntu"
date: 2010-10-28
forum: Multimedia Software
---

### Post by toffuuu on 2010-10-28
i am having a problem with installing [B]sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4    i already have vlc, and most of the things needed for all the other audio/video stuff    here is the out put for this whole command that i get..  

" sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss2' has no installation candidate "


any help would be greatly appreciated..
[/B]

---

### Post by mc4man on 2010-10-28
Run this - should take care of (libdvdnav is a recommend of libdvdread, should be installed if not already

```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```

Also never hurts to install basic gstreamer plugins

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

---

### Post by toffuuu on 2010-10-28
> **mc4man said:**
> Run this - should take care of (libdvdnav is a recommend of libdvdread, should be installed if not already

```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```Also never hurts to install basic gstreamer plugins

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

thanks mc4man   this worked perfectly however very useful for others tho since i already had the gstreamers stuff installed...

---

### Post by rhapa on 2011-01-22
> **mc4man said:**
> Run this - should take care of (libdvdnav is a recommend of libdvdread, should be installed if not already

```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```

Also never hurts to install basic gstreamer plugins

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```


Hey man, thanks a lot. You actually set me free of a lot of headaches. Thank you.

---

### Post by comandgedit on 2011-08-24
libdvdcss2 installed perfectly! Thanks Powder.

---

### Post by mpw on 2011-11-06
Hello,

does anyone know, if there's an easy possibility to access the dvd via network, for example with sshfs?

I have only one optical drive in my house, it's in my headless server, which runs 10.10 server. I can mount the dvd via ssh. But if I then mount that folder via sshfs from another PC, I can't play the DVD.

Is there any chance to use libdvdcss2 over network? Or do I have to rip it and then watch it from hdd?

Bye
MPW

---

### Post by PsychicNut on 2011-11-06
Hi there toffuuu,
Thanks for the advice. I just tried it on my fresh install of Oneric and it worked after a restart.
Beautiful!
Thanks again!
:)
Psychic

---

