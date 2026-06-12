---
title: "amarok 2.1 on ubuntu jaunty?"
date: 2009-06-06
forum: Multimedia Software
---

### Post by mosko on 2009-06-06
Hey guys, couldn't find a way to install amarok 2.1 on UBUNTU JAUNTY... what's the trick?

Thanks in advance,
Dor (:

---

### Post by SathyaBhat on 2009-06-06
Goto System ->  Administration ->  Software Sources

Click on third party sources, click on Add, enter the below line
```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
```
Save, update.  Launch Synaptic, search for amarok and mark for install

---

### Post by Marky-boy on 2009-06-14
I tried adding that source, and got an error

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A


Any ideas?

---

### Post by Scotty Bones on 2009-06-14
[This is the link to that repo from launchpad]("https://launchpad.net/~kubuntu-ppa/+archive/backports")

[Here are the instructions for adding the gpg key]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories")

that should get it done for you. not that it really matters any way. you can still install the software without the repos gpg key.

---

