---
title: "mythbuntu-control-centre Segmentation fault"
date: 2012-04-14
forum: Mythbuntu
---

### Post by larsolav on 2012-04-14
Hi,
I am trying to access the control centre to select 0.25 in the Repositories tab. However, when I click on the mythbuntu-control-centre icon nothing happens, and when I type mythbuntu-control-centre in the terminal, I get this error message: Segmentation fault

The control center used to work. How do I fix?
Running 11.10 with 0.24.0+fixes.20110908.1de0431-0ubuntu1

Any help is much appreciated.
Cheers!

---

### Post by tgm4883 on 2012-04-14
> **larsolav said:**
> Hi,
I am trying to access the control centre to select 0.25 in the Repositories tab. However, when I click on the mythbuntu-control-centre icon nothing happens, and when I type mythbuntu-control-centre in the terminal, I get this error message: Segmentation fault

The control center used to work. How do I fix?
Running 11.10 with 0.24.0+fixes.20110908.1de0431-0ubuntu1

Any help is much appreciated.
Cheers!

What is the full output when you try to launch it and the following two commands

```
dpkg -l mythbuntu-common
dpkg -l mythbuntu-control-centre
```

---

### Post by larsolav on 2012-04-14
Hi! Thanks for the quick response!

What does the following tell you?

> ~$ mythbuntu-control-centre
Segmentation fault



> ~$ dpkg -l mythbuntu-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythbuntu-comm 0.63           Mythbuntu application support functions



> ~$ dpkg -l mythbuntu-control-centre
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythbuntu-cont 0.63-0ubuntu2  Mythbuntu Configuration Application


Cheers!

---

### Post by nickrout on 2012-04-14
If you simply want to change to the 0.25 repo try ```
sudo dpkg-reconfigure mythbuntu-repos
```

---

### Post by larsolav on 2012-04-14
Well, that is interesting....
> ~$ sudo dpkg-reconfigure mythbuntu-repos
sudo: Can't open /var/lib/sudo/husebo/0: Read-only file system
Package `mythbuntu-repos' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mythbuntu-repos is not installed

What has happened?
And more importantly, how do I fix? Re-install anew?

---

