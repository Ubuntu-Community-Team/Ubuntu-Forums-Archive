---
title: "Is there a 64 bit Handbrake for Ubuntu 12.10"
date: 2013-04-07
forum: Multimedia Software
---

### Post by thunderpenguin on 2013-04-07
Is there a 64 bit Handbrake for Ubuntu 12.10. The official PPA only has 32 bit versions and I don't want to install extra 32 bit libraries for it to work.

---

### Post by hansdown on 2013-04-07
Hi thunderpenguin.

Try this link.

[http://www.liberiangeek.net/2012/10/install-handbrake-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/10/install-handbrake-in-ubuntu-12-10-quantal-quetzal/)

---

### Post by sanderj on 2013-04-08
According to [http://packages.ubuntu.com/search?searchon=contents&keywords=handbrake&mode=exactfilename&suite=quantal&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=handbrake&mode=exactfilename&suite=quantal&arch=any) handbrake is not in the official repositories, neither for i386.

Is that correct? I've been using handbrake for a long time, so that means I've always installed in a special way?

---

### Post by monkeybrain2012 on 2013-04-08
Don't bother with the official repository, I always install handbrake from ppa

[https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)

There are both 32 and 64 bit packages for 12.10 and it always provides the latest stable version.

To add the repository and install handbrake, open the terminal and type

```
sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake


```

You will then get updated version from the normal package managing system through normal upgrades whenever there is a new release.

---

