---
title: "Ps3MediaServer Error: Depends ps3mediaserver-multiarch not going to be installed"
date: 2013-04-02
forum: Multimedia Software
---

### Post by usersock on 2013-04-02
**[COLOR="#800080"]Fixed by uninstalling Wubi and doing a full install using 12.04 LTS.[/COLOR]**

I'm using Ubuntu 12.10 64bit

I installed Ubuntu last night and am running into a problem when installing Ps3 Media Server ([using this guide]("https://help.ubuntu.com/community/Ps3MediaServer")). I'm using the "Install from PPA" option, and was able to complete the first two steps:
```
sudo add-apt-repository ppa:happy-neko/ps3mediaserver
sudo apt-get update
```
but the third step gives me errors:
```
sudo apt-get install ps3mediaserver
```

Error:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ps3mediaserver : Depends: ps3mediaserver-multiarch but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I searched around online but I wasn't able to find a solution. Any idea what the problem may be?

---

