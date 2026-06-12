---
title: "Curious Netatalk issue - files with no extension"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by bartek on 2010-10-27
I'm serving a dataset to Mac clients over netatalk. Many files in the dataset have no extension, but are actually eps files (don't ask)...
These files show up as "Unix Executable" to the Mac clients, which presents a problem. These same files served over Samba show up as Plain Text and the Mac clients can deal with them just fine.

How do I make these files with no extension appear as plain text to the Mac clients? Here is my netatalk config, any clues appreciated... :(

```
AFPD_MAX_CLIENTS=50
ATALK_NAME=`/bin/hostname --short`
ATALK_MAC_CHARSET='MAC_ROMAN'
ATALK_UNIX_CHARSET='LOCALE'
AFPD_GUEST=nobody
ATALKD_RUN=yes
PAPD_RUN=no
CNID_METAD_RUN=yes
AFPD_RUN=yes
TIMELORD_RUN=no
A2BOOT_RUN=no
ATALK_BGROUND=no
export ATALK_MAC_CHARSET
export ATALK_UNIX_CHARSET 
```

AppleVolumes.default:

```
~/ "$u" SERVER options:usedots,upriv
```

---

