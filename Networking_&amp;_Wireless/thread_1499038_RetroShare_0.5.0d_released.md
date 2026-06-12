---
title: "RetroShare 0.5.0d released"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by xenonlight on 2010-06-01
```
Changes for v0.5.0d

Package improvements:

* suppressed package dependency on gpg-agent

Improvements:

* implemented a free disk space checking method, with a warning when running low
* fixed proper sorting/updating of IP lists.
* only keep the most recent port for identical ips.
* don't start when the local address+port are already in use to avoid corrupting file lists, config files etc
* added failure tests for fwrite
* added tests against wrong ip 1.0.0.0 on MacOS

Major bug corrections:

* added missing locks in search requests into fimonitor.cc
* Suppressed the possibility for browsable only files to be searched by hash from turtle router.
* cleaned up some deadly code in rsdiscitems.cc, causing crashes
* improved the security of size determination for file lists, that caused a chain reaction ending in crash at clients.
* added missign lock in ftcontroller

Minor bug corrections:

* added a check to avoid (possibly rare) data races in data multiplex
* suppressed double click action for download in Shared File lists
```**Ubuntu Lucid:**
[RetroShare_0.5.0d.3036_lucid_i386.deb]("http://sourceforge.net/projects/retroshare/files/RetroShare/0.5.0d/RetroShare_0.5.0d.3036_lucid_i386.deb/download")
[RetroShare_0.5.0d.3036_lucid_amd64.deb]("http://sourceforge.net/projects/retroshare/files/RetroShare/0.5.0d/RetroShare_0.5.0d.3036_lucid_amd64.deb/download")

**Ubuntu Karmic:**
[RetroShare_0.5.0d.3036_karmic_i386.deb]("http://sourceforge.net/projects/retroshare/files/RetroShare/0.5.0d/RetroShare_0.5.0d.3036_karmic_i386.deb/download")
[RetroShare_0.5.0d.3036_karmic_amd64.deb]("http://sourceforge.net/projects/retroshare/files/RetroShare/0.5.0d/RetroShare_0.5.0d.3036_karmic_amd64.deb/download")

**Ubuntu Jaunty:**
[RetroShare_0.5.0d.3036_jaunty_i386.deb]("http://sourceforge.net/projects/retroshare/files/RetroShare/0.5.0d/RetroShare_0.5.0d.3036_jaunty_i386.deb/download")
[RetroShare_0.5.0d.3036_jaunty_amd64.deb]("http://sourceforge.net/projects/retroshare/files/RetroShare/0.5.0d/RetroShare_0.5.0d.3036_jaunty_amd64.deb/download")

**Source:**
[RetroShare_v0.5.0d.tar.gz]("http://sourceforge.net/projects/retroshare/files/RetroShare/0.5.0d/RetroShare_v0.5.0d.tar.gz/download")

**SHA512 hashes:**
```

9cc1c53a3d4ad02951f870ab4cb0f3930c5da624a9d72e4933550524a748ed1c6bd7b6421c2ed9b59910b6c1a4fbdfae23dc45ad17b9a8d5e657af2ea3eecb22  RetroShare_v0.5.0d.tar.gz
33f423ed412c727235e8e28ffc8cf3fe0f5b5d3e4d92e902cb7d9f4690bba1c477be31e57732e9ac0cbaea32b4aabfd87c260833f95353272666e64576a90caf  RetroShare_0.5.0d.3036_jaunty_i386.deb
208b4ce0432f390a12713886193cad79f94041d1ec1fc90ed04483744e510d0e27a6fcdb54c10039f1a02e515476b579fba45554d1b4ff8a13ee5baf44991a3c  RetroShare_0.5.0d.3036_jaunty_amd64.deb
e1e77678c302d1795261403a98ea181c998ef7f501ec3cad1e973b5bf98febc884b1e7a8c15b49581347a9046342d44d9fa97d024d6997cb72de5e1036198763  RetroShare_0.5.0d.3036_lucid_i386.deb
36382d6e76659086b793265bba2be4af3d26b08dcf1e28914dc0600d67365a031c01ef55edec0fbbbdfebfa289001e1145308fead86b0a09943a89de3aeea78f  RetroShare_0.5.0d.3036_lucid_amd64.deb
b905ada35999b86b964add113a10bfacfd2cc1497c788e58f85d8ff87619f864cee9a777920b32d6eeee59a26d7a9c35c9de10115f56add505b72b74e38695e1  RetroShare_0.5.0d.3036_karmic_i386.deb
a2b514fe6f5ca3dba407542dec87df17a8a0241dad2fc790e9fdba9c26f986bdaf6e3ecdae25e80ae82b85d76e51d7b31daaa8602a5a1da8ef12fee2719649c7  RetroShare_0.5.0d.3036_karmic_amd64.deb

```

---

