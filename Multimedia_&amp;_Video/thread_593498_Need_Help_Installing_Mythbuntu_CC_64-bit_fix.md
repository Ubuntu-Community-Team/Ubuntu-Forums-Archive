---
title: "Need Help Installing Mythbuntu CC 64-bit fix"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by bper on 2007-10-27
Sorry but I have the problem where I can't run Mythbuntu CC on 64-bit Gutsy.

I found this fix in a post:

[http://ppa.launchpad.net/mythbuntu/ubuntu/pool/main/m/mythbuntu-control-centre/mythbuntu-control-centre_0.11-0ubuntu1~ppa1_all.deb](http://ppa.launchpad.net/mythbuntu/ubuntu/pool/main/m/mythbuntu-control-centre/mythbuntu-control-centre_0.11-0ubuntu1~ppa1_all.deb)

When I tried to install the fix I get the following error:

E: Couldn't find package mythbuntu-control-centre_0.11-0ubuntu1~ppa1_all.deb

The package is in the same directory in which I issue the sudo apt-get command.

What's the problem? Does it have to do with the long field name?

Thanks

---

### Post by bper on 2007-10-27
Hi,

I used dpkg -i instead and it worked.

Thanks

---

