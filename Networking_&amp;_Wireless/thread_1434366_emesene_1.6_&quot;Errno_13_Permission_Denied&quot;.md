---
title: "emesene 1.6 &quot;Errno 13: Permission Denied&quot;"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by Inquisitorthemad on 2010-03-20
I've been using emesene 1.6 for some months now, and until last week, it was fine. I haven't done anything that would have changed it particularly, but it now gives me the following error message _every single time_ I try to receive a file:

> You are using emesene 1.6 "mate" so you're free to complain here:
[http://forum.emesene.org/index.php/board,19.0.html](http://forum.emesene.org/index.php/board,19.0.html)
Check already existing tickets for duplicates first, please.
Traceback (most recent call last):

  File "/usr/share/emesene/FileTransfer.py", line 251, in onFtReceived
    dest = open(self.localPath, 'wb')

IOError: [Errno 13] Permission denied: u'/usr/share/emesene/[file]'

Does anyone have any idea what I'm meant to do about this? FSCK and memtest have not fixed the problem, and I have no idea what else it could be.

I can send just fine, but I can't receive...

EDIT: Turns out emesene was defaulting to send files at a root directory, as you can see in the error message. Just changed the directory it sends to et voila.

---

