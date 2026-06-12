---
title: "wireless not detected?"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by RjBanker18 on 2006-02-24
Hi, i think i posted in the wrong forum....im new here lol.  Well anyway, my wireless card is not detected, my freind had me type in iwconfig and it didnt show up.  then he decided that the restricted-modules in the repository should be installed, so im stuck there.

i need to install the linux restricted-module 10-686 for my wireless card(linksys wpc55ag with atheroschipset) to work. when i go to the repository and click to install it, it gives me this...

linux-restricted-modules-2.6.12-10-686:
Depends: nvidia-kernel-common but it is not installable

can someone please help me?(im new to linux)
Thanks

---

### Post by JoshHendo on 2006-02-24
What brand/model is your wireless card?

---

### Post by RjBanker18 on 2006-02-24
its a linksys wpc55ag (atheros chipset)

---

### Post by ltmon on 2006-02-24
I think your friend is right, the madwifi driver (which iirc is used for atheros chipsets) is in the linux-restricted-modules package.

I think you can't install the nvidia driver because you haven't enabled the extra repositories that a whole lot of extra packages are in.

Follow the guide to adding the universe and multiverse repositories in this document: [https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu](https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu)

and then try again.

L.

---

### Post by RjBanker18 on 2006-02-24
Hey thanks, ill give it a try and report back in!

---

### Post by RjBanker18 on 2006-02-24
Well it still displayed that error message from above and after following the repository tutorial and reloading, it displayed this.....

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)

Any clue as to whats going on? I still have the same problem, i can't download the restricted -10 686 module.

**EDIT**
Ok i added the other repositories for ubuntu and after that i got these errors...
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) Sub-process bzip2 returned an error code (2)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:) Sub-process gzip returned an error code (1)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:) 416 Unknown
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:) Sub-process gzip returned an error code (1)
AND THEN this...
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
Sorry for all the text and stuff...hopefully someone can help me with this and getting my problem above solved.
Thanks again.

---

