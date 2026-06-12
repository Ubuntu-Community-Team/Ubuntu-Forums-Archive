---
title: "[SOLVED] VLC can't play DVDs, even with everything installed"
date: 2008-12-06
forum: Multimedia Software
---

### Post by MockY on 2008-12-06
I installed the following:

libdvdread3 (and ran /usr/share/doc/libdvdread3/install-css.sh)
ubuntu-restricted-extras
w32codecs
libdvdcss2

I still can't play DVDs. VLC outputs the following:
```

libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: Unable to find map file '/home/mocky/.dvdnav/PTE0NNW1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
```

I clearly don't have something installed that I should. But what?

---

### Post by khelben1979 on 2008-12-06
It sounds that you lack the libdvdnav library. Try installing this.

I would also recommend that you start up the Kaffeine player within the KDE enviroment. It usually gives some type of output the first time the program is started and this can also give an indication of what is missing which also would affect the VLC player.

---

### Post by MockY on 2008-12-06
I have 4.1.2 already installed, but I went ahead and installed libdvdnav-dbg and its dependencies, but no luck. Still the same output.
I'm running Gnome, so no KDE apps are installed - nor will there ever be since it tends to make the system very unstable (though this is completely besides the point).

---

### Post by khelben1979 on 2008-12-06
Maybe [this guide]("http://tldp.org/HOWTO/html_single/DVD-Playback-HOWTO/") can help you?

---

### Post by MockY on 2008-12-06
Thanks for your help, but a reboot was all it took. I have never had to restart my computer after installing the codecs before. So I will definitely note this down for future reference.

---

### Post by C. Wizard on 2008-12-06
What version of VLC are you using? It isn't necessary to install codecs with the more recent releases of VLC as it is now self contained.

---

### Post by MockY on 2008-12-06
> **C. Wizard said:**
> What version of VLC are you using? It isn't necessary to install codecs with the more recent releases of VLC as it is now self contained.

0.9.4 - The version that's in the repos for Ibex

---

### Post by tech0007 on 2008-12-06
Try this link for a fix:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

