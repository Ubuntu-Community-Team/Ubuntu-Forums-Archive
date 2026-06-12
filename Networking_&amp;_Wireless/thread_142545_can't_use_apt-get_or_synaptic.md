---
title: "can't use apt-get or synaptic"
date: 2006-03-10
forum: Networking &amp; Wireless
---

### Post by melquiades on 2006-03-10
guys, 
         let me start my saying that I'm an absolute linux newbie. i tried using synaptic
package manager to get some packages. here's the log on my failed attemp in starting synaptic.

<snip>

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)

</snip>

same thing happens with apt-get. please help.

Thanks in advance,
melquiades

---

### Post by Klejs on 2006-03-10
Is the machines internet connection working?

---

### Post by melquiades on 2006-03-10
I composed this message using my ubuntu installation, so synaptic and apt-get
fails while I'm online ( dialup ).

---

### Post by bluevoodoo1 on 2006-03-10
Did you change your sources.list file recently?

perhaps running...

sudo apt-get update

from the terminal might fix things.

---

### Post by melquiades on 2006-03-11
'sudo apt-get update' worked like magic. Thanks a bunch.

---

### Post by bluevoodoo1 on 2006-03-11
Great!

---

