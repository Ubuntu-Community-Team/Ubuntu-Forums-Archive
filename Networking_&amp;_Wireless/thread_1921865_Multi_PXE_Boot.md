---
title: "Multi PXE Boot"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by Woogi on 2012-02-07
So I have the following Setup

Ubuntu 10.04 Running Virtual Box Hosting:
     -Debian box acting as a PXE Server
     -Non OS PXE Boot Testing box (used for testing my PXE boot, as        it is quicker to load)


So I currently have UBCD booting just fine with the PXE Server and syslinux. It boots to a custom vesamenu.c32 from there, I can load the UBCD menu. What I could like to do, is have a few different options in my vesamenu. Say BartPE, or any other number of tools/OS install CD's.

I found this guide for booting BartPE

XXXX://wiki.contribs.org/PXE_booting_to_BARTPE

and it looks good, but I dont see a why to boot it using SYSlinux...any ideas?

---

