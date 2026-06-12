---
title: "Wireless AWOL after cmus install and dnet configure."
date: 2012-09-21
forum: Multimedia Software
---

### Post by casbahdk on 2012-09-21
I just installed cmus after a Lubuntu 12.04 install and now my wireless refuses to work. There is a bug [here]("https://bugs.launchpad.net/ubuntu/+source/cmus/+bug/923027") in connection with cmus. I tried to just install dnet-common, without actually configuring, but cmus complained about lacking a dnet config file, and wouldn't work until I configured dnet. I used the defaults, but now I can't log onto my wireless connection.

How can I get myself out of this mess and keep cmus funtioning?

Edit:

I should probably add that I went through a similar process on my home built desktop computer, running Ubuntu 12.04. The interesting difference was that I was at no time forced to configure dnet-common before cmus would work, and after the install, I was able to remove dnet-common again, just as long as I didn't remove the config file.

---

### Post by casbahdk on 2012-09-21
I was lucky enough to be able to solve this by uninstalling everything including configuration files, and then reinstalling using the following:```
sudo apt-get --no-install-recommends install cmus
```

---

