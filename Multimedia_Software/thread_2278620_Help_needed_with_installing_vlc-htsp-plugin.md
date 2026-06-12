---
title: "Help needed with installing vlc-htsp-plugin"
date: 2015-05-18
forum: Multimedia Software
---

### Post by srikesh2 on 2015-05-18
Could someone help me setup the tvheadend plugin for VLC in Ubuntu?

**Operating System**
OS: Ubuntu 14.04 LTS
Bit: 32-bit
Kernel: 3.16.0-37
VLC: 2.1.6 Rincewind

I downloaded the 'vlc-htsp-plugin' from [https://ci.btbn.de/job/vlc-htsp-plugin/](https://ci.btbn.de/job/vlc-htsp-plugin/).  The exact one I downloaded was from [https://ci.btbn.de/job/vlc-htsp-plugin/PLATFORM=linux_x86,label=linux/](https://ci.btbn.de/job/vlc-htsp-plugin/PLATFORM=linux_x86,label=linux/).

As per instructions I found on the web, I moved the file 'libhtsp_plugin.so' to /usr/lib/vlc/plugins/access and changed the rights with sudo chmod 644 (also tried with 777).  When I open VLC player and try to look for that plugin, I don't find it.  I am not sure what I am doing incorrectly to not get that plugin to show up in my VLC player.

Any help on this matter would be much appreciated.
Thanks.

---

### Post by dino99 on 2015-05-18
maybe these "instructions found on the web" does not apply to the actual ubuntu rules.
some other users comments  [https://tvheadend.org/boards/4/topics/8509](https://tvheadend.org/boards/4/topics/8509)

---

### Post by srikesh2 on 2015-05-19
> **dino99 said:**
> maybe these "instructions found on the web" does not apply to the actual ubuntu rules.
some other users comments  [https://tvheadend.org/boards/4/topics/8509](https://tvheadend.org/boards/4/topics/8509)

Thanks for trying to help but that link is for Windows operating system.  I am seeking help with installing the plugin on linux/ubuntu.

---

### Post by monkeybrain20122 on 2015-05-19
> **srikesh2 said:**
> Thanks for trying to help but that link is for Windows operating system.  I am seeking help with installing the plugin on linux/ubuntu.

If you actually read the comments there are instructions for installing on Linux from forum participants (basically move to  /usr/lib/vlc/plugins/ instead of  /usr/lib/vlc/plugins/access )

I don't know anything about this plugin and have no use for it. But as a guess it is possible that your vlc version is too old (current release is 2.2.1)

---

### Post by mc4man on 2015-05-19
start vlc from terminal as such, may report some info on the .so  - 
vlc -vv

---

