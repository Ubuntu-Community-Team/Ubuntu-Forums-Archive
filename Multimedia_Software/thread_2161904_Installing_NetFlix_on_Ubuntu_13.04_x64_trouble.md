---
title: "Installing NetFlix on Ubuntu 13.04 x64 trouble"
date: 2013-07-12
forum: Multimedia Software
---

### Post by minhgi on 2013-07-12
Hi all,

I am having issue with installing netflix on Ubuntu.  Search high and low for the solution, but no luck. I was able to get the PPA and install the netflix desktop, but launching it would get the stuck at "performing local install" for hours.  So I try to launch it in the terminal command and these are the errors I see.

sudo netflix-desktop
cmp: /home/minhgi/.wine-browser/wine-browser.sha256sums: No such file or directory
fixme:urlmon:DownloadBSC_OnProgress Unsupported status 3
fixme:wininet:InternetLockRequestFile STUB
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:urlmon:DownloadBSC_OnProgress Unsupported status 3
fixme:wininet:InternetLockRequestFile STUB
fixme:storage:create_storagefile Storage share mode not implemented.
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: cannot open shared object file: No such file or directory
wine: configuration in '/home/minhgi/.wine-browser' has been updated.
fixme:console:CONSOLE_DefaultHandler Terminating process 40 on event 0
fixme:console:CONSOLE_DefaultHandler Terminating process 14 on event 0





Any help would be appreciated.

---

