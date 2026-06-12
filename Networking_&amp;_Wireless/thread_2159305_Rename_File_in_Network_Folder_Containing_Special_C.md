---
title: "Rename File in Network Folder Containing Special Characters"
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by Nezmo on 2013-07-02
Hi

I'm tryining to access a folder on a AFP-fileserver connected over VPN. My problem is, that the folder name contains a "/", which is allowed on Apple machines. But Ubuntu won't open it (altough it's correctly listed), because he interpretes it as a path.

The foldername is something like *26/27-2013 *and doubleclicking it gives the error *Could not display "27-2013" *because Ubuntu reads it as ~/26/27-2013, I guess.

I also tried to open it in Terminal so I could unescape the / with a backslah, but that didn't work either. Doesn't matter if cd, mv or cp, it's allways the error [I]bash: cd: 27/28_2013: No such file or directory.
[/I]
Is there a way to rename the folder or open it anyway? I'm kinda stuck here...

Thanks in advance!

---

