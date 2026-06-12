---
title: "[SOLVED]The following packages have unmet dependencies:"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by Akacheebe on 2013-03-21
This is a recent install of 12.04 with Mate 1.4 desktop.  I've been trying for an hour to get ubuntu to share two partitions on a hard drive that are in this computer that contain Windows NTFS partitions but not having much luck.  I used NTFS Config to get them to auto mount at boot but I'm not able to enable sharing on either partition??  

So I checked in Ubuntu Software Center and Samba doesn't seem to be installed on my system so I tried to install it but I get an error stating that my system has some unmet dependencies?  Well, I've done the update, upgrade then tried to install from the Terminal but get the following error:

```
The following packages have unmet dependencies:
 samba : Depends: libwbclient0 (= 2:3.6.3-2ubuntu2.1) but 2:3.6.3-2ubuntu2.3 is to be installed
         Recommends: tdb-tools but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I even installed Synaptic Package manager and uninstalled Samba there only to get that same error when I try to reinstall via Ubuntu Software Center or Synaptic??

Any help for an old guy with a Samba share problem?

Thanks

---

### Post by Hadaka on 2013-03-22
Hi, I have zero experience with fixing
broken held packages, but, this link
may help you....
[http://ubuntuforums.org/showthread.php?t=2113213](http://ubuntuforums.org/showthread.php?t=2113213)
good luck

---

### Post by paulie-m on 2013-03-22
[https://help.ubuntu.com/community/SynapticHowto#How_to_fix_broken_packages](https://help.ubuntu.com/community/SynapticHowto#How_to_fix_broken_packages)

Try this link. It might help.

---

### Post by Akacheebe on 2013-03-22
Well, this is embarrassing to say the least.  I have good news and bad news.  Good news is I fixed it.  Bad news is I really can't be sure how??  The problem did seem to be centered around this line in the first post I made though.

```
samba : Depends: libwbclient0 (= 2:3.6.3-2ubuntu2.1) but 2:3.6.3-2ubuntu2.3 is to be installed
```

Which showed that one version was actually installed and another needed to be installed but couldn't.  When it was all said and done, version 2:3.6.3-2ubuntu2.4 is what's in it now??  

Two things I did was to enable "Conical Partners" in the sources and then install "Samba-Common" from Synaptics, which did install some other files along with that one.  After that I went to terminal and did an update, 
upgrade then I was able to install Samba from the Ubuntu Software Center.

Configured Samba sharing on those NTFS partitions and now there is joy in Muddville!  

Thanks for the help fellas as I did get some useful info from the links.

---

### Post by Hadaka on 2013-03-22
Great ! glad it worked out for you.
please mark this thread SOLVED
thanks.

---

