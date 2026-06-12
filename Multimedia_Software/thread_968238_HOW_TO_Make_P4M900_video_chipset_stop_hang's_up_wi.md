---
title: "HOW TO: Make P4M900 video chipset stop hang's up with openchrome drivers"
date: 2008-11-02
forum: Multimedia Software
---

### Post by doubledrop on 2008-11-02
For all dudes, who have P4M900 graphic chipset with standart openchrome driver from repositories and it's hang's up the system with white lines on screen slowly shows up, insert following options to xorg.conf Device section:
```

Option "AccelMethod" "EXA"
Option "ExaNoComposite" "True"
Option "MigrationHeuristic" "greedy"
Option "ExaScratchSize" "8192"
Option "MaxDRIMem" "16384"

```

Find this solution [here]("http://forums.fedoraforum.org/showthread.php?t=189424&page=4"), and test it on ubuntu 8.10.

---

