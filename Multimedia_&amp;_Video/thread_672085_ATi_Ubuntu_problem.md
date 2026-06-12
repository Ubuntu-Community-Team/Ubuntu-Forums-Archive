---
title: "ATi Ubuntu problem"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by Tarmael on 2008-01-19
$ less /var/log/Xorg.0.log |grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): [pcie] Failed to gather memory of size 262144Kb for PCIe. Error (-1000)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(EE) AIGLX: Screen 0 is not DRI capable

Any thoughts?

Ubuntu 7.10.
X1600

Xorg.conf is fine, got AIGLX on.
GLX is uninstalled.

Cheers, Bas.

---

