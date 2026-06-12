---
title: "Drive wont automaticaly mount becuse of password restrictions"
date: 2012-10-11
forum: Mythbuntu
---

### Post by RTIInstaller on 2012-10-11
How do I remove permissions from a drive or auto enter the password? Under the drives properties tab there is a permissions section but it is all greyed out?

---

### Post by RTIInstaller on 2012-10-11
OK I just installed Pysdm but the Drive utility is all greyed out and wont let me do anything, its like I am not logged in as an administrator or something? never mind you just have to click the little triangles  duh

---

### Post by RTIInstaller on 2012-10-11
pydsm worked great:guitar:Problem solved

---

### Post by nickrout on 2012-10-11
> **RTIInstaller said:**
> How do I remove permissions from a drive or auto enter the password? Under the drives properties tab there is a permissions section but it is all greyed out?Drives don't have passwords as such, unless the whole drive is encrypted. 
Tell us EXACTLY where this password is being asked for. I assume you are typing```
sudo mount /dev/sdc1 /mnt/raid
```

That of course will ask for your user password to authorise against sudo, but when you mount on boot the mount will run as user root and will not need a password.

---

### Post by RTIInstaller on 2012-10-12
Thanks Nick! I was able to solve this by using the pydsm utility, which is an great app for noobs like me

---

