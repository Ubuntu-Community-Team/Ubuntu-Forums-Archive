---
title: "recordmydesktop in 20.04LTS has no UI"
date: 2020-10-02
forum: Multimedia Software
---

### Post by ccor58 on 2020-10-02
recordmydesktop in 20.04LTS has no UI launching it from command line terminal or launcher created on desktop just causes it to launch full screen with no control buttons to stop and save when done or select area to record. If one had extended desktop it just records all displays on a single desktop view. the only way to kill it is to issue kill PID command results in a random length out.ogv result reinstall does nothing and many updates have not included anything to restore it's original functionality.

Any suggestions?? bug reports??
thnx

---

### Post by deadflowr on 2020-10-03
Probably because they removed python-gtk2 as python2 packages are being slowly deprecated.
Suggestions? Try simplescreenrecorder, it is in the repos.
(there is also a snap version)

---

