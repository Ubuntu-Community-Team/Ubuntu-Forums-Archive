---
title: "Apport: incomplete work?"
date: 2011-02-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bestgun on 2011-02-16
Hi everybody!
While working with the latest Natty on testdrive an error occurred 
during the installation of some packages (the problem was in lintian pkg).

I follow the Apport instructions to report the problem [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs), but 
the process seem to end just after I click "Send Report" (without choosing any title or added any info).

Where is now my (incomplete) bug report? (no trace at [https://bugs.launchpad.net/ubuntu/+source/lintian](https://bugs.launchpad.net/ubuntu/+source/lintian))

tks people

---

### Post by Yofel on 2011-02-17
After that apport should open a webbrowser window where you finish filing the bug report. If it doesn't do that you can try to file the bug with apport-cli in a terminal which will give you the launchpad URL after it uploads the files.
You can also check in ~/.xsession-errors what happened to apport, as the fact that it didn't open a webbrowser would be a bug.

---

### Post by bestgun on 2011-02-17
Tks Yofel! 
I guess so my report has gone without any chances to recover it because I was working on testdrive.
Anyway, good to know!

---

