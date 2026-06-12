---
title: "Feisty: how do I uninstall ivtv driver to upgrade?"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by scram69 on 2007-09-27
2-3 times a week, mythbackend.log fills up with "ivtv driver not responding", while /var/log/messages fills up with ivtv DMA errors.  This causes my machine to completely lock up - no ssh, no ctl-alt-del, no response to anything other than the reset button.

I would very much like to update the ivtv driver version - I have 0.10.1 that came with Feisty, kernel version 2.6.20-16.  The only problem is I have not been able to un-install the current driver.  The Ubuntu package manager allows un-installation of something called "ivtv-utils", but after removing that, the ivtv 0.10.1 driver still loads.

Unfortunately, neither the howto at ivtvdriver.org, or help.ubuntu.com discuss un-installation.  I'm guessing I need to go and manually delete some files from the morass in /lib/modules/ , but I have no idea which ones.  I would appreciate any insight...

Also, it was suggested on the ivtv-users list that the specific DMA error fixes are in the v4l-dvb repository at linuxtv.org.  While the ivtv driver downloads had installation instructions, the downloads from [http://www.linuxtv.org/hg/](http://www.linuxtv.org/hg/) do not.  Any suggestions?

---

