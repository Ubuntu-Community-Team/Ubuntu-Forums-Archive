---
title: "Where to report gwget bugs"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by dewdrop_world on 2011-01-09
Sorry if this is a dumb question, but where does one go to report bugs with gwget?

I needed to download a file with some punctuation -- (, ) -- in the filename. Gwget connected to the server okay but then produced an "error: couldn't write to target directory." That was my home directory, so obviously I have permission. The most likely explanation is that the file open call failed because of the special characters.

Fortunately Firefox stopped barfing on the connection and I was able to download it, but gwget's behavior there was a bit less than robust.

(BTW it appears, when adding a new download, that the target filename is always derived from the URL -- there's no box to specify a different filename to write. If it did, the problem would be easy to work around.)

Thanks,
James

---

### Post by chili555 on 2011-01-09
Right here; see the red 'Report a bug' at the top right.

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by PatchesTheCaveman on 2011-01-09
You can also run this command:
```
apport-bug gwget
```

That will collect some information about your system and send it along with your bug report.  It will also work for any Ubuntu package, just replace *gwget* with the package name you'd normally use with *apt-get*.

---

### Post by dewdrop_world on 2011-01-09
'k, done, thanks!

---

