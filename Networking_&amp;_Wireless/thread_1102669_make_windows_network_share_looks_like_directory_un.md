---
title: "make windows network share looks like directory under root"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by mxnerd on 2009-03-21
I'm a newbie to linux and Ubuntu 8 desktop and I want to run  windows programs accross the network using WINE Windows emulation.

The Windows programs are stored on Windows 2003 server "srv" in folder level1

in this folder there is a main menu program that will call other sub-system program under other sub-folders.  The programs does not require any installation, it can be run directly.

The directory structure look like this
```
\level1\sysname\menu.exe
               \sys1\sys1.exe
               \sys2\sys2.exe
               \sysn\sysn.exe
               \sysdata\*.dat
               \sysconfig\config.ini
```

and I shared level1 folder over the network.  

I have confirmed that the program ran fine if I copy the whole \sysname folder onto Ubuntu root directory.

The problem with this system is each exe file looks for absolute directory sysname under the root, so when ran over network, the directory must looks like the level1 folder is not there.  So just connected to the share, with a bookmark or not, when you ran the program, the exe files complain they can't find \sysname\sysconfig\config.ini file.

My question is, how can I make or mount a remote windows share folder under the Ubuntu root directory so these exe files can run correctly?

Thanks!!

---

