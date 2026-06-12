---
title: "Mythfilldatabase fails on scheduled job"
date: 2013-05-22
forum: Mythbuntu
---

### Post by LorenzoS on 2013-05-22
mythfilldatabase is failing on the regularly scheduled job, although when I "sudo muthfilldatabase" from the command line it runs fine.  The message that displays on the status page of Mythweb is:

```
Last mythfilldatabase run started on 2013-05-19 15:34:23 and ended on 2013-05-19 15:35:52. mythfilldatabase ran, but did not insert any new data into the Guide for 1 of 1 sources. This can indicate a potential grabber failure.
Suggested next mythfilldatabase run: 2013-05-20 01:04.
There's guide data until 2013-06-02 06:30 (12 days).
```

I'm not sure where to start looking for a solution.  Any advice is appreciated.

Thanks in advance.

---

### Post by drewdin on 2013-05-22
did you try going into the setup and seeing if it works there? I had an issue where that was the only way I could get the newest data. It ended up being a bad password, not sure how

---

### Post by LorenzoS on 2013-05-28
The database password was fine, but thanks for the help.  I searched the web and found several folks experiencing the same problem, which was apparently resolved with a simple reboot.  I tried that and it seems to have worked.

Go figure.

---

