---
title: "Kernel 2.6.38 rc5 is in Launchpad for Natty"
date: 2011-02-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-02-17
The new rc5 of the kernel 2.6.38 has been released.
It has already been built in Launchpad for Natty.
It will soon be uploaded into repos.
Or - if you want it now, download it from the link below.

Here:
[https://launchpad.net/ubuntu/natty/+source/linux/2.6.38-4.31](https://launchpad.net/ubuntu/natty/+source/linux/2.6.38-4.31)

Changelog:
```
linux (2.6.38-4.31) natty; urgency=low

  [ Andy Whitcroft ]
  * add in bugs closed by upstream patches pulled in by rebases
  * rebase to 795abaf1e4e188c4171e3cd3dbb11a9fcacaf505
  * [Config] enable CONFIG_VSX to allow use of vector instuctions
  * resync with maverick 98defa1c5773a3d7e4c524967eb01d5bae035816
  * rebase to mainline v2.6.38-rc5
  * SAUCE: ecryptfs: read on a directory should return EISDIR if not
    supported
    - LP: #719691

  [ Colin Ian King ]
  * SAUCE: Dell All-In-One: Remove need for Dell module alias

  [ Manoj Iyer ]
  * SAUCE: (drop after 2.6.38) add ricoh 0xe823 pci id.
    - LP: #717435

  [ Tim Gardner ]
  * [Config] CONFIG_CRYPTO_CRC32C_INTEL=y

  [ Upstream Kernel Changes ]
  * Quirk to fix suspend/resume on Lenovo Edge 11,13,14,15
    - LP: #702434
  * vfs: fix BUG_ON() in fs/namei.c:1461

  [ Vladislav P ]
  * SAUCE: Release BTM while sleeping to avoid deadlock.
    - LP: #713837

  [ Major Kernel Changes ]
  * rebase from v2.6.38-rc4 to v2.6.38-rc5
    - LP: #579276
    - LP: #715877
    - LP: #713769
  * resync with Maverick Ubuntu-2.6.35-27.47
 -- Andy Whitcroft <email address hidden>   Fri, 11 Feb 2011 17:24:09 +0000
```

---

