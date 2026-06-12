---
title: "sshfs prevents other programs from working"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by jfacemyer on 2010-04-06
I use sshfs frequently and have never had this problem.  Just today, however, if I start sshfs, nothing else works, to the point that even the browser opening a new tab will just hang.

Command line apps seem to work ok, though (the few I've tried), and if I killall sshfs, things start working right away.

For example, if I start sshfs and then try to open Inkscape (from the command line), it just hangs (I can't enter another command in that terminal just as if the program had started, but it doesn't start).  The cpu spikes for an instant then goes back to "nothing".  Then I killall sshfs, and the program continues to start as if nothing unusual had happened.

Any ideas?

---

### Post by jfacemyer on 2010-04-07
*hem* bump

---

### Post by jfacemyer on 2010-04-09
Nothing, eh?  Not even a suggestion on how to debug the problem?

---

