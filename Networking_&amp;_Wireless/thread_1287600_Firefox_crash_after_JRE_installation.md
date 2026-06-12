---
title: "Firefox crash after JRE installation"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by Corlito on 2009-10-10
Well the title says it. I installed JRE 1.6 and put the needed links in the firefox plugins folder, and next thing I know firefox crashes on startup. It runs for a few second, not even enough to load my homepage, and then closes without an error message.
When running through the terminal I get this error:

```
INTERNAL ERROR on Browser End: Could not get the plugin manager
System error?:: Success

```

safe mode does not help at all, epiphany has the exact same problem, but Arora (which I'm now using) seems to work, but also has had a few weird crashes, but I don't think that has anything to do with this problem.

Does anybody have any idea what this could be? I have searched the internet far an wide. Some people have had the same problems but they used wrong symbolic links... I have checked these and they seem to be allright

```
joep@Tesla:~$ file /usr/lib/firefox/plugins/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so: symbolic link to `/usr/java/jre1.6.0_16/plugin/i386/ns7/libjavaplugin_oji.so'

```

Thx in advance, tell me when I need to post some more info

---

