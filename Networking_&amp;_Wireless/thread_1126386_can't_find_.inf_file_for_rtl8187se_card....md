---
title: "can't find .inf file for rtl8187se card..."
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by hg87099 on 2009-04-15
I installed ubuntu 8.10 yesterday as a dual-boot with xp on an msi wind u100 which has a realtek 8187se card installed.  The card works find on the xp side, but is not recognized by ubuntu.  I installed the ndiswrapper files from the ubuntu cd, and tried to copy the drivers that xp is using.  However, the only file that xp identifies as my wireless card driver is a .sys.  I can't find any .inf file to give to ndiswrapper.  I've tried looking for drivers online and downloaded the .exe package from realtek, but it seems to only have .sys also.  Any ideas?

---

### Post by puppywhacker on 2009-04-15
I think using the ndiswrapper should be avoided as much as possible, windows drivers where just not ment to run in linux.

For the wired nic I use the drivers from Realtek. The r8169 drivers are generic enough to also work on the RTL8101. download them [HERE]("http://122.146.118.42/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110S-32/RTL8110SB(L)/RTL8169SB(L)/RTL8169SC(L)%3Cbr%3ERTL8169")

For the RTL8187SE wireless chip I used the these preliminary drivers [rtl8187se_linux_26.1023.0928.2008.tar.gz]("http://launchpadlibrarian.net/18533836/rtl8187se_linux_26.1023.0928.2008.tar.gz")

Those drivers will be included in linux kernel 2.6.29 so until ubuntu updates the kernel you better compile them yourself.


MMH, on second though, you might also just download them already prepackaged here ...
[http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html]("http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html")

---

