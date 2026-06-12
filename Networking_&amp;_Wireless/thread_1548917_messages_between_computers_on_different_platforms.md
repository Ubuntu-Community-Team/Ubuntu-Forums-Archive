---
title: "messages between computers on different platforms"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by dreamquartz on 2010-08-09
Is there software with GUI to send and receive instant pop-up messages to and from computers on whatever OS?

---

### Post by gerowen on 2010-08-09
> **dreamquartz said:**
> Is there software with GUI to send and receive instant pop-up messages to and from computers on whatever OS?

I don't know of any, but somebody with more time than I have right now could probably throw one together in about a day.  Here's some info on commands to accomplish the task.  I may write one in python later today, you could use a line like the following python line in other languages to force the program to run the command appropriate for the OS in use without prompting the user.

```

import os
if os.name=="posix":
     rununixcommand

```

**Edit:** Sorry forgot to include the actual link I found.
[http://www.computerhope.com/issues/ch000783.htm](http://www.computerhope.com/issues/ch000783.htm)

---

