---
title: "Proprietary Nvidia"
date: 2010-05-01
forum: Multimedia Software
---

### Post by Martin Marshalek on 2010-05-01
I am about to update to Lucid and I found out that it includes the Noveau driver for Nvidia cards. If I choose to install the proprietary driver through the "Hardware Drivers" window will I have to do the whole blacklisting thing with the modeprobe files or will it work correctly after installing from that window and rebooting?

---

### Post by cascade9 on 2010-05-01
AFAIK, installing the nVidia binary drivers disables the noveau driver. ;) 

You shouldnt have to blacklist anything. Well, unless you have intel and nVidia graphics cards installed..normally that only happens with laptops, but there are some desktops that wont let you disable the onboard (intel normally) video. In those cases you might have to blacklist the intel card.

---

### Post by Martin Marshalek on 2010-05-01
Oh okay, thanks. I wasn't sure because I had seen some guides involving blacklisting in lucid but I guess that was only for the Nvidia .run files. I also wasn't sure because I knew that you had to do that in Fedora 12. Thanks.

---

