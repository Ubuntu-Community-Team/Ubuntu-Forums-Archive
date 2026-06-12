---
title: "MTP workarounds"
date: 2014-12-30
forum: Multimedia Software
---

### Post by Vladimir_Oufa on 2014-12-30
Some workarounds to survive with MTP mess in Android.

[I]The day Cyanogen implement a robust open protocol in place of MTP, I will install Cyanogen.
[/I]
These commands are tested on Ubuntu 14.04 LTS with a Galaxy S5 running Android 4.4.

Device is unlocked, then plugged on USB port, then after 30 secondes device should appear in Nautilus

If MTP not selected on device, select it, unplug device then plug again device on USB.

Many MTP commands are run through **script -c** due to mishandling of buffers by MTP commands when not run in interactive shell.

I hope these few scripts will help until MTP replacement.

Vladimir

**How-to identify device**
```
script -c mtp-detect > mtp-detect.res1-via-script-c
```

most interesting sections are _USB low-level info:_ , _Device info:_ and _MTP-specific device properties:_

**How-to list device files LINUX way**
```
ls -l /run/user/$(id -u)/gvfs/mtp*/
```

Files are easy to list but simple copy or rsync are not allowed through MTP

**How-to list device files MTP way**
```
script -c mtp-files > mtp-files.res1-via-script-c
script -c mtp-filetree > mtp-filetree.res1-via-script-c
```

To Handle copy through MTP you need to catch ID of file.

**How-to extract ID of files from above list, except Undefined filetype ones**
```
cat mtp-files.res1-via-script-c | sed 's/^[[:blank:]]\{1,\}/\x09/' | tr '\012' '|' | tr -d '\015' | sed 's/|\x09/\x09/g' | tr '|' '\012' | cut -f 1-2,6 | grep '^File ID:' | grep -v 'Filetype: Undefined filetype' | sort -t ':' -k 4 -k 3n
```

**How-to copy to local folder all .flv files**
```
cat mtp-files.res1-via-script-c | sed 's/^[[:blank:]]\{1,\}/\x09/' | tr '\012' '|' | tr -d '\015' | sed 's/|\x09/\x09/g' | tr '|' '\012' | cut -f 1-2,6 | grep '^File ID:' | grep -P '\.flv\x09Filetype: ' | while read FILE ; do ID=$( echo "$FILE" | cut -f 1 | cut -d ' ' -f 3 ) ; NAME=$( echo "$FILE" | cut -f 2 | cut -d ' ' -f 2 ) ; mtp-getfile "$ID" "$NAME" ; done
```

To copy others file suffix, replace **flv** by expected one in **grep -P** part of script.

---

