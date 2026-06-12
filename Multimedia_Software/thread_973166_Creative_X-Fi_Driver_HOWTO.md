---
title: "Creative X-Fi Driver HOWTO"
date: 2008-11-06
forum: Multimedia Software
---

### Post by PGHammer on 2008-11-06
Creative actually posted a *generic* Linux driver (32/64-bit) for the X-Fi series (both PCI and PCIe; according to Creative, it should also work for the external/notebook products).  My PCI-based XtremeGamer *does* work with the driver (and with minimal fiddling).  Here's the six-step method to get it running.

1.  First off, make sure you have your system up to date!  (This includes all the headers, kernel sources, and compilers; this is especially critical for the 8.x series.)
2.  Download the updated (6 November 2008) archive from [http://support.creative.com/downloads/download.aspx?nDownloadId=10792](http://support.creative.com/downloads/download.aspx?nDownloadId=10792).
3.  Extract to the preferred location (I chose the Documenents subsection of my /home folder) and start a terminal session; navigate to that same location, which should be /home/UserName/Documents/XFiDrv_Linux_Public_US_1.00).
4.  Type in the Terminal session (without the quotes) "sudo make"; when that completes, follow up with "sudo make install".
5.  UNfortunately, like the Windows drivers, Creative's volume start is invariably too high; turn the Volume in the mixer *down*!
6.  Once you have the volume turned down far enough, start configuring your applications to use the card.

---

### Post by Divide_Overflow on 2008-11-06
Nice catch and thanks for the how to!

I haven't had sound on my system in a while but this is working well so far on 8.10 x64.

---

