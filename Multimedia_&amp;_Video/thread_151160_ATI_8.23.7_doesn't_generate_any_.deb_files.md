---
title: "ATI 8.23.7 doesn't generate any *.deb files"
date: 2006-03-27
forum: Multimedia &amp; Video
---

### Post by outofsync on 2006-03-27
Hi,

I'm trying to run the ATI 8.23.7 installer as specified on the Wiki (I run it preceded by "fakeroot").

But, no *.deb packages are generated in the current directory.

Only a "*.changes" file is produced.

Also, an "usr/share/fglrx" directory is created in my home directory (sounds weird).

(I also tried to use "sudo" instead of "fakeroot", and then the "usr/share/fglrx" directory was created in the root (ie: "/") which looks more reasonable, although no *.deb packages where generated either)

When the installer asks for your Ubuntu version, I said either "breezy" or "5.10", and both of them failed.

What might be the cause for this problem?

---

### Post by outofsync on 2006-03-29
Finally, I found that *.deb packages were generated, but in the /tmp directory, so look there if you can't find them. It seems either the ATI installer is broken, or the rootless Ubuntu environment makes it behave in weird ways.

---

### Post by dicecca112 on 2006-03-29
I have never used fakeroot always sudo.  Follow this HowTo everytime and it works perfectly [Ubuntu Forums - View Single Post - HOW-TO: ATI fglrx driver latest version]("http://ubuntuforums.org/showpost.php?p=423584")

---

### Post by ThaRabbit on 2006-03-31
Are you sure the user trying to create the .deb files had writing rights to the folder ?

I used the very same wiki and driver revision and it gave me pefectly working *.deb files to work with.

---

