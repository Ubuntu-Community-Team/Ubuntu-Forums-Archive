---
title: "HP laptop with the MCP67M Nvidia chipset + Virtualbox [FIXED]"
date: 2008-02-21
forum: Multimedia &amp; Video
---

### Post by SuperMike on 2008-02-21
I was running 7.10 Gutsy in a VM on Windows Vista, and no matter what tricks I pulled, I couldn't get the nVidia MCP67M chipset on the HP laptop to work. I couldn't only take it as far as 1024x768 and not the 1280x800 that it was capable of.

Then one day I was in the Virtualbox menus and I saw how it had some sort of add-on it could install inside the VM for Linux. So, I ran it and it popped a window into Ubuntu from /media/cdrom0. So, I ran the *.run file in there and restarted the VM. Lo and behold it went to 1280x768 mode. So, I edited the /etc/X11/xorg.conf file and notice it stuck "virtualbox" as the driver instead of "nv", "nvidia", or "vesa". So, I edited the file and made it say 1280x800, then restarted the VM, and sure enough it went into 1280x800 mode just fine.

---

