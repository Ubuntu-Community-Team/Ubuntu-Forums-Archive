---
title: "Poulsbo/gma500 installation script lost"
date: 2012-02-07
forum: Multimedia Software
---

### Post by rozo on 2012-02-07
Hello all,

I'm trying to install the poulsbo/gma500 driver for 10.04 lts from the [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) and receive the following:

Resolving dl.dropbox.com... 107.20.141.233, 50.16.240.166, 107.20.135.122, ...
Connecting to dl.dropbox.com|107.20.141.233|:80... connected.
HTTP request sent, awaiting response... 404 NOT FOUND
2012-02-07 16:25:48 ERROR 404: NOT FOUND.

it seems the script is not there anymore, anyone knows where it is or how can I install this driver for 10.04 lts?

Marcin

---

### Post by mikewhatever on 2012-02-13
EMGD 1.6 that you've tried installing is old, the current version is 1.10. It also showed abysmal performance. For 10.04, use the psb driver:
```

sudo apt-get remove compiz*

sudo add-apt-repository ppa:gma500/ppa && sudo apt-get update && sudo apt-get install poulsbo-driver-3d


```

---

### Post by rozo on 2012-02-23
I've tried this already. After removing compiz and installing psb I restart the pc, Ubuntu shows the splash screen for one second or so and then I get a black screen and thats all.
Emgd 1.6 worked for me perfectly. Is there a way to get the script and driver from the repository or somewhere else?

---

