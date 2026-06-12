---
title: "Can't remove flashplugin-nonfree"
date: 2009-12-11
forum: Multimedia Software
---

### Post by Sig Nuka on 2009-12-11
In the terminal, putting in **sudo dpkg -l | grep flash** gives me this:

```
ii  adobe-flashplugin   10.0.42.34-2karmic1   Adobe Flash Player plugin version 10
ic  flashplugin-nonfree   9.0.124.0ubuntu2   Adobe Flash Player plugin installer

```

But putting in **sudo apt-get remove flashplugin-nonfree** gives me this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libdns50 libnss3-dev libnspr4-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

What do I do now? (I have a feeling I should've put this in the Absolute Beginner Talk section, so apologies if it's an obvious solution)

---

### Post by fancypiper on 2009-12-11
sudo apt-get autoremove should clean out the unneeded stuff.

If you type:
```
about:plugins
```
in the address bar of Firefox, flash shouldn't be in the list.

---

### Post by Sig Nuka on 2009-12-11
Thing is, both Firefox and Opera work just fine with Flash - it's Epiphany and the Chrome beta that are having problems seeing the newer Flash version.

Also, autoremove didn't remove flashplugin-nonfree. *sigh*

---

### Post by efflandt on 2009-12-12
Synaptic **flashplugin-nonfree** says: "This package is a transitional package that can safely be removed after you installed flashplugin-installer."  So maybe you need to fix, or remove and reinstall **flashplugin-installer** (which was installed if you installed restricted-extras).

However, if you are running 64-bit Linux, you could remove that and manually install 64-bit flash (instead of Ubuntu 32-bit flash with wrapper) [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)  If you have older 64-bit cpu lacking lahf_lm instruction and that crashes your browser, the flash sticky in 64-bit forum points to a fix for that (illegal instruction).  I had to do that for my earlier version of Athlon64 3200+ from 2004.

---

### Post by Sig Nuka on 2009-12-12
> **efflandt said:**
> Synaptic **flashplugin-nonfree** says: "This package is a transitional package that can safely be removed after you installed flashplugin-installer."  So maybe you need to fix, or remove and reinstall **flashplugin-installer** (which was installed if you installed restricted-extras).
Problem: It's not installed, and if I select it for installation in Synaptic Package Manager it says that I need to uninstall adobe-flashplugin (which would be pointless since that's what I want to keep).

> However, if you are running 64-bit Linux...
Nope, 32-bit. :(

Thing is, flashplugin-nonfree isn't listed as installed either, yet it still comes up in the terminal and both Chrome and Epiphany use it (rendering both browsers almost useless since both crash with any site that has flash). **Edit:** Wait, just Chrome crashes (and just that specific tab). Epiphany just doesn't display it at all if I scroll at all (no sound obviously). **Edit2:** Well, spoke too soon - Epiphany just crashed. I guess Epiphany just takes longer. :(

This is starting to get very frustrating. :cry:

---

### Post by Sig Nuka on 2009-12-13
Bumping for a solution. :(

---

### Post by Sig Nuka on 2009-12-14
Just tried **sudo apt-get remove --purge flashplugin-nonfree**, but it gives the same response as last time. And **sudo dpkg -l | grep flash** still gives me this:

```
ii  adobe-flashplugin     10.0.42.34-2karmic1   Adobe Flash Player plugin version 10
ic  flashplugin-nonfree   9.0.124.0ubuntu2      Adobe Flash Player plugin installer
```

Why is it that flashplugin-nonfree is completely uninstalled yet still able to function as if it hasn't been uninstalled at all? And is there any way at all to remove it, or will I have to give up and uninstall Epiphany and Chrome since they're both useless at this point? :cry:

---

### Post by Sig Nuka on 2009-12-15
Bumping again. Apologies if I'm bumping too much, but I have a feeling this has an easy solution that I'm missing. Please? :cry:

---

### Post by Yellow Pasque on 2009-12-16
I'm guessing there are residual config files left for the flashplugin-nonfree package:
```
sudo dpkg -P flashplugin-nonfree
```

---

### Post by fancypiper on 2009-12-16
Also, try this: run **locate libflashplayer.so**
then, **sudo rm <files found above>**

---

### Post by Sig Nuka on 2009-12-16
> **Temüjin said:**
> I'm guessing there are residual config files left for the flashplugin-nonfree package:
```
sudo dpkg -P flashplugin-nonfree
```

Well, this *seems* to work (not detected using the terminal anymore), except for the fact that both Epiphany and Chrome STILL see the old version. Any way I can fix that, or would I have to *gulp* purge both browsers and reinstall them (which I'd like to avoid as much as possible)? :(

---

### Post by Yellow Pasque on 2009-12-16
Search for files with 'libflash*' on your system. You probably have an old version hanging around that isn't associated with a package.

---

### Post by Sig Nuka on 2009-12-16
> **Temüjin said:**
> Search for files with 'libflash*' on your system. You probably have an old version hanging around that isn't associated with a package.

Found two:

/usr/lib/openoffice/basis-link/program/libflashli.so
/usr/lib/adobe-flashplugin/libflashplayer.so

...

Wait, I just found out what's going on. Opera is using flashplugin-alternative.so (which I never thought to check). As for Firefox... *checks* I, uh, have no idea (though I'm assuming the same). ^^;

So, is it safe for me to just remove libflashplayer.so, or would it break Flash updates?

---

### Post by Sig Nuka on 2009-12-17
Bump, as I have NO idea what to do anymore. :(

---

### Post by fancypiper on 2009-12-18
Have you removed the files you found? Have you restarted the browser?

```
sudo rm /usr/lib/openoffice/basis-link/program/libflashli.so
sudo rm /usr/lib/adobe-flashplugin/libflashplayer.so
```

---

### Post by fancypiper on 2009-12-18
What's going on? Triple post!

---

### Post by fancypiper on 2009-12-18
Double post

---

### Post by bkmfs on 2009-12-18
You are probably gonna have to open the Synaptic, type in flash player in the 'quick search' and remove everything that has the words "flash player" in it.  

That is what I had to do when my flash player stopped working.  My next step was to reinstall 'adobe-flashplugin' and that straightened everything out for me but that may not be your next step (depending on what you are doing).

---

### Post by Sig Nuka on 2009-12-18
> **fancypiper said:**
> Have you removed the files you found? Have you restarted the browser?

```
sudo rm /usr/lib/openoffice/basis-link/program/libflashli.so
sudo rm /usr/lib/adobe-flashplugin/libflashplayer.so
```

I actually marked adobe-flashplugin for complete removal first (easier to do, easier to reinstall later). Browsers still saw the old Flash. Then I fired up the terminal. Here's what I tried:

```
siggy@siggy-laptop:~$ locate libflash
/home/siggy/.mozilla/plugins/libflashplayer.so
/home/siggy/.opera/cache/temporary_download/libflashsupport_1.0~2219-2_i386.deb
/usr/lib/openoffice/basis3.1/program/libflashli.so
```

"What? An extra plugin location I missed? Lets remove that and see what happens."

```
siggy@siggy-laptop:~$ sudo rm /home/siggy/.mozilla/plugins/libflashplayer.so
```

*fires up Epiphany, goes to [this page](http://www.adobe.com/software/flash/about/)*

Flash was uninstalled! So I reinstalled adobe-flashplugin, restarted Epiphany, and went to the site again.

```
You have version
10,0,42,34 installed
```

[IMG]http://skipall.com/7rs.jpg[/IMG]

Many thanks to everyone in this thread! :mrgreen:

---

### Post by crazyedy on 2010-08-23
Here is the fix for this issue.

dpkg -r --force-remove-reinstreq flashplugin-nonfree

---

### Post by Barney on 2012-10-26
above solution didn't work->

dpkg: error processing flashplugin-nonfree (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree

---

