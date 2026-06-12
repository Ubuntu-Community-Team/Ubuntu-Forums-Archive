---
title: "Where is nfs-utils package?"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by XEtedBear on 2011-11-26
Being a total sucker, I'm trying to follow the Linux NFS-HOWTO on Sourceforge, believing, so naively, that it will work. It fails at almost the first step - it asks me to make sure I have the correct level of nfs-utils installed. Synaptic Package Manager informs me that it is NOT installed, but, more importantly, has no knowledge of a package called nfs-utils. Great. Plus one for yet another misleading Linux document.

Is there an NFS HOWTO that actually works on Ubuntu 10.10 and 11.10 ?

---

### Post by SeijiSensei on 2011-11-26
It's hard to know why you didn't find [this](https://help.ubuntu.com/community/SettingUpNFSHowTo) since it's the first result returned by a Google search for "nfs ubuntu".

If you're looking for the NFS client, install the **nfs-common** package.  For the server, install **nfs-kernel-server**.

---

