---
title: "Newbie Mythbuntu questions"
date: 2007-12-15
forum: Mythbuntu
---

### Post by dbk723 on 2007-12-15
Hi!  I am totally new to Ubuntu, although I have been reading articles on it for a while now.  I have been trying to put together an HTPC system - so far I have been able to get the 7.10 build of Ubuntu Studio up and running, and added several applications to it with Synaptic. And that's about as far as I've got.

I have an ISO image of Mythbuntu 7.10, and I'd like to install it over my current configuration.  Can I boot from the Mythbuntu disk and auto-install it without overwriting my current configuration?

I am planning to make this HTPC using a Hauppauge PVR-500 and an old ATI HDTV Wonder for the tuners.  Has anyone tried this and got it to work for them yet?

---

### Post by jlp_engineer on 2008-09-19
> **dbk723 said:**
> Hi!  I am totally new to Ubuntu, although I have been reading articles on it for a while now.  I have been trying to put together an HTPC system - so far I have been able to get the 7.10 build of Ubuntu Studio up and running, and added several applications to it with Synaptic. And that's about as far as I've got.

I have an ISO image of Mythbuntu 7.10, and I'd like to install it over my current configuration.  Can I boot from the Mythbuntu disk and auto-install it without overwriting my current configuration?

I am planning to make this HTPC using a Hauppauge PVR-500 and an old ATI HDTV Wonder for the tuners.  Has anyone tried this and got it to work for them yet?


I believe the Mythbuntu CD is used to install Myth with a minimal Ubuntu environment on an empty system.  I do not know if the ISO install CD can be used to install Myth on an existing system.  I believe  you must use "apt-get" for that.  Try the following commands when you bring up a terminal window:

sudo apt-get update
sudo apt-get install mythtv

As for the PVR-500, it will be recognized by the kernel without any additional drivers or configuration file changes.  With the ATi HDTV Wonder, things are a little more complicated.  Try looking at the following threads:

[http://ubuntuforums.org/showthread.p...light=ati+hdtv](http://ubuntuforums.org/showthread.p...light=ati+hdtv)

[http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder](http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder)

These links were given to me by 'blackoper' who gives a lot of good advice around here.  It would be wrong to give you the links without giving credit where credit is due.  I also have an ATi HDTV Wonder and I am trying to get it to work.  I hope to be able to post my SUCCESS story soon. :)

Regards...

---

