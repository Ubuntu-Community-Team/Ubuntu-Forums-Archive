---
title: "[SOLVED] What does this error mean and how to?"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by TRANQU111TY on 2008-01-17
Just trying to install the ATI drivers on [BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a") when something I do not understand (because I'm a noob) comes up.

```
j@j-desktop:~$ sudo apt-get install linux-restricted-modules-generic restricted-manager-kde
[sudo] password for j:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-generic is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  restricted-manager-kde: Depends: adept-batch but it is not installable
                          Depends: libpythonize0 but it is not installable
                          PreDepends: python-kde3 (>= 3.16.0-0ubuntu11) but it is not installable
E: Broken packages

```

Can I continue on with the tutorial or do I need to kinda fix this command line first?

---

### Post by namnam on 2008-01-17
restricted-manager-kde is for Kubuntu. Maybe the problem is that you're running Ubuntu and not Kubuntu?

---

### Post by TRANQU111TY on 2008-01-17
Yeah it must be lol... thank you :)

---

