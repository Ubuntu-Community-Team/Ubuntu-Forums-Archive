---
title: "what user runs mytharchive?"
date: 2010-01-03
forum: Mythbuntu
---

### Post by pinacate on 2010-01-03
How can I tell/change the user account the various myth components run? I'm running mythbuntu 9.10.

mythfrontend, mythbackend, mytharcive?

---

### Post by NightStorm on 2010-01-03
A quick way is to just do a "ps -ef | egrep myth".  You will see the user in the left column.   To answer your subject line, I believe that mytharchive runs with the same user as does the mythfrontend.  If you've ever run it you can do an "ls -l" under the assigned mytharchive temporary directory to see who owns the files.  For example:
  ls -l /var/lib/mytharchive/temp
  drwxrwsrwx 2 athome mythtv 4096 2010-01-03 22:21 config
  drwxrwsrwx 2 athome mythtv 4096 2010-01-03 22:21 logs
  drwxrwsrwx 3 athome mythtv 4096 2010-01-03 22:21 work

The above were created from the "athome" user.

    - Bruce

---

