---
title: "Update Maverik problem"
date: 2010-08-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by joelw135 on 2010-08-19
I ran update manager and it hangs at "Setting up Firefox". I then opened terminal and tried "sudo dpkg --configure -a" same lockup. What should I do as i can't complete the update?

---

### Post by kansasnoob on 2010-08-19
You might try "sudo apt-get clean" first and then once again try "sudo dpkg --configure -a". You should then check for updates again after that.

If that doesn't work post the output of:

```
aptitude show firefox
```

---

### Post by joelw135 on 2010-08-19
> **kansasnoob said:**
> You might try "sudo apt-get clean" first and then once again try "sudo dpkg --configure -a". You should then check for updates again after that.

If that doesn't work post the output of:

```
aptitude show firefox
```

UPDATE- It fixed itself I don't know how.

The sudo apt-get clean and sudo dpkg --configure -a no luck below is the results of aptitude show firefox
joel@joel-desktop:~$ aptitude show firefox
Package: firefox                         
State: partially configured
Automatically installed: no
Version: 3.6.9~hg20100817r34537+nobinonly-0ubuntu1~umd2
Priority: optional
Section: web
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Uncompressed Size: 30.5M
Depends: fontconfig, psmisc, lsb-release, debianutils (>= 1.16), libasound2 (>
         1.0.22), libatk1.0-0 (>= 1.29.3), libc6 (>= 2.11), libcairo2 (>=
         1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78),
         libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.3.5), libgcc1 (>=
         1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.21.6), libglib2.0-0 (>= 2.24.0),
         libgtk2.0-0 (>= 2.18.0), libnspr4-0d (>= 4.7.3-0ubuntu1~), libnss3-1d
         (>= 3.12.6), libpango1.0-0 (>= 1.14.0), libstartup-notification0 (>=
         0.10), libstdc++6 (>= 4.1.1), libx11-6, libxext6, libxrender1, libxt6,
         zlib1g (>= 1:1.1.4), firefox-branding | abrowser-branding
Recommends: ubufox
Suggests: firefox-gnome-support (=
          3.6.9~hg20100817r34537+nobinonly-0ubuntu1~umd2), kmozillahelper (>=
          0.6), latex-xft-fonts, libthai0
Provides: iceweasel, www-browser
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface, enhanced
 security features including protection from online identity theft, and
 integrated search let you get the most out of the web.

joel@joel-desktop:~$

---

### Post by xebian on 2010-08-19
> **joelw135 said:**
> UPDATE- It fixed itself I don't know how.

The sudo apt-get clean and sudo dpkg --configure -a no luck below is the results of aptitude show firefox
joel@joel-desktop:~$ aptitude show firefox
Package: firefox                         
State: partially configured
Automatically installed: no
Version: 3.6.9~hg20100817r34537+nobinonly-0ubuntu1~umd2
Priority: optional
Section: web
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Uncompressed Size: 30.5M
Depends: fontconfig, psmisc, lsb-release, debianutils (>= 1.16), libasound2 (>
         1.0.22), libatk1.0-0 (>= 1.29.3), libc6 (>= 2.11), libcairo2 (>=
         1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78),
         libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.3.5), libgcc1 (>=
         1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.21.6), libglib2.0-0 (>= 2.24.0),
         libgtk2.0-0 (>= 2.18.0), libnspr4-0d (>= 4.7.3-0ubuntu1~), libnss3-1d
         (>= 3.12.6), libpango1.0-0 (>= 1.14.0), libstartup-notification0 (>=
         0.10), libstdc++6 (>= 4.1.1), libx11-6, libxext6, libxrender1, libxt6,
         zlib1g (>= 1:1.1.4), firefox-branding | abrowser-branding
Recommends: ubufox
Suggests: firefox-gnome-support (=
          3.6.9~hg20100817r34537+nobinonly-0ubuntu1~umd2), kmozillahelper (>=
          0.6), latex-xft-fonts, libthai0
Provides: iceweasel, www-browser
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface, enhanced
 security features including protection from online identity theft, and
 integrated search let you get the most out of the web.

joel@joel-desktop:~$

Your Firefox is not the Maverick version/repo.

---

### Post by mgsfan on 2010-08-19
I have that as well and can't seem to fix it..

---

### Post by VinDSL on 2010-08-19
I had the same problem, this morning.

I'm running the Firefox 3.6.9pre release.

After doing all the conventional things, I renamed:

```
/usr/lib/firefox-3.6.9pre   -->>  /usr/lib/firefox-3.6.9pre.orig
```

Then, I reinstalled Firefox 3.6.9pre using Synaptic.

When I opened Firefox, everything was there - no harm, no foul. 

And afterwards, I could continue with the updates.

I know this sounds rather ghetto, but I was running out of options, going the 'normal' route.  LoL!

I spent hours on this problem, and it's the ONLY thing that worked.  Go figure!

---

### Post by VinDSL on 2010-08-19
> **xebian said:**
> Your Firefox is not the Maverick version/repo.This might have caused the problem.

While I was doing forensics via Aptitude-GTK, the dialog box would say "Waiting for user input...".

Of course, the only user input you could give it was:

```
$ sudo killall aptitude-gtk
```

Dittos for apt-get, synaptic, et cetera.

It was a real corker!  :D

---

