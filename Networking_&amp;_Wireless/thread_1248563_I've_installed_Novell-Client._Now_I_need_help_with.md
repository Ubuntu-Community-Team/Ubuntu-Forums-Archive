---
title: "I've installed Novell-Client. Now I need help with Yast2!"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by Augsburg on 2009-08-24
Hello.

I'm trying to setup novell-client for Ubuntu so I can Authenticate against a netware server. I was able to successfully install novell-client by doing the following:

Installing novell-client in Ubuntu:

1) sudo apt-get install alien
2) sudo apt-get install rpm
3) sudo apt-get install libglitz-glx1
4) unarchive novell-client-2.0-suse10.2-i386.iso
5) cp ncl_install_Ubuntu.sh novell-client (this is a file I edited from the provided ncl_install.sh --attached)
6) cd novell-client
7) su root
8 ) bash ncl_install_Ubuntu.sh
After it completes, there will be a link under Applications > Other for Novell-client.
___________________________________

9) Novell-client config files are in the yast format (.ycp) and are located in the directory:
	/usr/share/YaST2/include/novell-client
10)install YaST2...

It is step 10 that I am having difficulties with, simply because YaST2 has a lot of dependencies, and all packages have to be installed separately via alien. Can anyone guide me to a solution or provide a solution they have discovered? Alternatives could be another way to configure novell-client (and the ycp documents) without YaST2.

Thanks a bunch!

---

### Post by Augsburg on 2009-08-24
bump. the install is on ubuntu using alien.

---

