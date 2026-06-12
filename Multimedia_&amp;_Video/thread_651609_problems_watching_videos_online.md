---
title: "problems watching videos online"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by youthgonewild23 on 2007-12-27
I've been having a problem watching videos through my web browser. I use Ubuntu Linux with Firefox and have already installed the Flash plugin. I went to myspace and youtube to watch videos but they don't work. I don't understand. I uninstalled the plugin and re-installed it but it still doesn't work. Does anybody know what else I need to do to watch movies in a web browser? It is really annoying me. Thanks, in advance.

---

### Post by linuxwizard on 2007-12-28
Do you have all the codecs installed ?

[https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca](https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca)

---

### Post by glennliwanag on 2007-12-30
are you using the newest ubuntu distro? i tried installing the flashplugin-nonfree and after restarting firefox i got youtube video running.

---

### Post by Seisen on 2007-12-30
Make sure that the flashplugin is installing because it sounds like its not installing correctly.

---

### Post by youthgonewild23 on 2008-01-02
> **glennliwanag said:**
> are you using the newest ubuntu distro? i tried installing the flashplugin-nonfree and after restarting firefox i got youtube video running.


I'm using the newest Ubuntu and also installed the flashplugin-nonfree, restarted it, and it still doesn't play. Actually youtube videos do work but myspace videos don't.

---

### Post by youthgonewild23 on 2008-01-02
> **linuxwizard said:**
> Do you have all the codecs installed ?

[https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca](https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca)

I went to the website and it told me to install the ubuntu rstricted formats through the Synaptic package manager. I also have the flash plugin nonfree installed. Still,only certain websites work, even after rebooting the computer. Youtube works fine but myspace videos still  don't work.

---

### Post by chewearn on 2008-01-02
Unfortunately, the is no fix at the moment, except to manually install/compile your own:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890)

---

### Post by fparri on 2008-01-02
Or you can download  and install my backport from hardy:

[http://rapidshare.com/files/80562619/flashplugin-nonfree_9.0.115.0ubuntu2_7.10prevu1_i386.deb.html](http://rapidshare.com/files/80562619/flashplugin-nonfree_9.0.115.0ubuntu2_7.10prevu1_i386.deb.html)

---

### Post by KommoKaze on 2008-01-02
hello...  i'm no linux hacker, but this worked for me.  i would suggest that you go to "tools" then "add-ons" in firefox.  disable the "ubuntu firefox extension."  go back to youtube, and let it install flash as usual.  flash should now work.  then, you can go back and re-enable the ubuntu extension.  i hope this helps.  it works for me evertime i do a fresh install.  perhaps, there is a sticky somewhere that covers this in the forums.  if not, there may need to be.

---

### Post by yipeskop on 2008-01-02
if you are using 64-bit Ubuntu then I suggest getting 32-bit firefox instead, thats what worked for me.

---

