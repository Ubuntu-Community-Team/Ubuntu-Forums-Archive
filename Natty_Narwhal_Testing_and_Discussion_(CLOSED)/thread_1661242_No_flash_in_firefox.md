---
title: "No flash in firefox"
date: 2011-01-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sworddragon on 2011-01-06
If I install flashplugin-nonfree I don't see the plugin in firefox. I have already deleted the ~/.mozilla folder and created a new profile but this hasn't changed anything. Copying the official preview 3 release from flash "square" in ~/.mozilla/plugins work. But I have some problems with this version and want to try out an older one. Maybe it's because I'm using the 64 bit version of Ubuntu.

---

### Post by Harry33 on 2011-01-06
> **Sworddragon said:**
> If I install flashplugin-nonfree I don't see the plugin in firefox. I have already deleted the ~/.mozilla folder and created a new profile but this hasn't changed anything. Copying the official preview 3 release from flash "square" in ~/.mozilla/plugins work. But I have some problems with this version and want to try out an older one. Maybe it's because I'm using the 64 bit version of Ubuntu.

Installing flashplugin-nonfree or directly flashplugin-installer also installs ia32-libs and nspluginwrapper. This is because this flashplugin is for 32-bit architectures.

Adobe's "Square" is of 64-bit architecture. That one must be installed manually (before that all other flashplugins must be purged).
It (libflashplayer.so) can be installed (for firefox) into one of these folders:
  .mozilla/plugins/  (for single user)
or
/usr/lib/mozilla/plugins/   (for system wide).

---

### Post by jfernyhough on 2011-01-06
Use the sevenmachines Flash PPA:

[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

Works perfectly.

---

### Post by Sworddragon on 2011-01-06
Curious is that I could install and use flashplugin-nonfree on Ubuntu maverick 64 bit. Maybe it has even something to do with the natty firefox package.

---

### Post by jfernyhough on 2011-01-06
Not really. It uses nspluginwrapper to wrap 32-bit plugins to work on 64-bit browsers. That's usually what causes the problems.

---

### Post by wilee-nilee on 2011-01-06
> **Sworddragon said:**
> Curious is that I could install and use flashplugin-nonfree on Ubuntu maverick 64 bit. Maybe it has even something to do with the natty firefox package.

If you install the ubuntu-restricted-extras you will have flash.

In the terminal run sudo apt-get install ubuntu-restricted-extras

This is also in synaptic as well.
[ATTACH]180307[/ATTACH]

---

### Post by jfernyhough on 2011-01-06
> **wilee-nilee said:**
> If you install the ubuntu-restricted-extras you will have flash.This is a metapackage that installs (among other things) flashplugin-installer, which is the new name for flashplugin-nonfree (which is the transitional package for flashplugin-installer).

In short, it has the same net effect with regards to Flash. :)

---

### Post by wilee-nilee on 2011-01-06
> **jfernyhough said:**
> This is a metapackage that installs (among other things) flashplugin-installer, which is the new name for flashplugin-nonfree (which is the transitional package for flashplugin-installer).

In short, it has the same net effect with regards to Flash. :)

Exactly and has the codecs of gstreamer and other good stuff needed.:)

---

### Post by Sworddragon on 2011-01-06
> **jfernyhough said:**
> Not really. It uses nspluginwrapper to wrap 32-bit plugins to work on 64-bit browsers. That's usually what causes the problems.

I have never thought about wrapping. I thought the flashplugin was maybe deassemblied and recompiled with 64 bit.


> **wilee-nilee said:**
> If you install the ubuntu-restricted-extras you will have flash.

This hasn't changed anything.

---

### Post by efflandt on 2011-01-06
I have had issues since at least Maverick (and Natty) with flashplugin-installer on 64-bit systems with nvidea (although, it seems to work fine with legacy ATI and Intel with default video drivers).  But I never really noticed when it happened (maybe just flash ads), except from logs indicating that something like npviewer.bin crashed due to libflashplayer.so segfaulting.  So I have been using real 64-bit flash without any problems (except a temporary glitch in Firefox in the middle of some libs being updated weeks ago).

But if you have multiple flash versions (and/or gnash), that could result in issues.  I typically install ubuntu-restricted-extras, then uninstall flashplugin-installer, then drop real 64-bit flash into /usr/lib/mozilla/plugins.  Both Firefox and Chromium automatically find it there, but if you use Hulu Desktop, you have to tell ~/.huludesktop where it is:

```
[flash]
flash_location = /usr/lib/mozilla/plugins/libflashplayer.so
```Although, you do not need that to view Hulu from Firefox (I have not installed 64-bit Hulu Desktop in Natty yet).

---

### Post by lidex on 2011-01-07
Or...use flash-aid:
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) 
if you use firefox.
> Remove conflicting flash plugins from Ubuntu Linux systems, install the appropriate version according to system architecture and apply some tweaks to improve performance and fix common issues.

---

### Post by Sworddragon on 2011-03-21
The problem isn't solved with this. It looks like a bug or something else. I will explain it with an example again:

I have purged firefox and deleted $HOME/.mozilla. After this I installed firefox and flashplugin-nonfree. Theoretically the flash plugin should now be loaded automatically in firefox. But after I'm starting firefox there is no flash plugin.

I have tried this some weeks ago with a 32 bit version of ubuntu and all was working fine. It just doesn't work on my 64 bit ubuntu so this is maybe the problem.

---

### Post by beew on 2011-03-21
Actually flash is already installed for Natty if during installation you choose the option of installing extra packages or something like that. To update (or install it in case it is not) flash the best way is to use the flash-aid plugin from firefox. It works on natty too.

---

### Post by Sworddragon on 2011-03-30
I could finally solve this problem. The command "nspluginwrapper -i /usr/lib/flashplugin-installer/libflashplayer.so" was needed to make the flash plugin available for firefox without a workaround.

---

