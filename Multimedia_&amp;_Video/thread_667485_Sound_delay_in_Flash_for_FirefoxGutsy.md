---
title: "Sound delay in Flash for Firefox/Gutsy"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by shendric on 2008-01-14
I have seen a lot about delayed sound in Flash, and I used to have that problem when I used Dapper.  However, during a recent fresh install of Gutsy, I'm back to that delay in the sound when watching movies in Flash.  Should this still be a problem for Gutsy, and if so, is there a workaround so that my Flash player in Firefox is back to how it was on Dapper?

---

### Post by kostkon on 2008-01-14
> **shendric said:**
> I have seen a lot about delayed sound in Flash, and I used to have that problem when I used Dapper.  However, during a recent fresh install of Gutsy, I'm back to that delay in the sound when watching movies in Flash.  Should this still be a problem for Gutsy, and if so, is there a workaround so that my Flash player in Firefox is back to how it was on Dapper?

This used to be a shortcoming of F*lash Player 7 for Linux* (or older). I think the *Dapper* repositories offer you *Flash 7*, that's why you had this problem (although you could get version 9 if you had enabled the *dapper-backports* repository).

Normally, in *Gutsy* you should have *Flash 9*. You can check which version you have by opening *Firefox* and giving
```
about:plugins
```
 in the address bar.

---

### Post by wolfen69 on 2008-01-14
here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

---

### Post by shendric on 2008-01-14
Hey guys, thanks for the responses.  Here's the version I have: 9.0 r115.  I also tried downloading the package that wolfen69 recommended, but that's the same version i had, it looks like, and I still have the problem.

---

### Post by anderskitson on 2008-01-14
I had the same problem, I actually had flash working, then did an update and it was terrible, tried gnash it sucked, but this fixed it for me [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by shendric on 2008-01-14
I appreciate the response, anderskitson, but the thing is that the downloaded package on that thread is the same as that from wolfen69, which still gives me the sound delay.  At least, package manager thinks its the same.

---

