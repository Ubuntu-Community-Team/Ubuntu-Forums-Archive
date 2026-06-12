---
title: "list of mythbuntu packages"
date: 2008-11-30
forum: Mythbuntu
---

### Post by lerrup on 2008-11-30
I am looking for a list of the packages that are installed on the mythbuntu cd (backend and frontend together).

Does anyone know where I could find one?

At the moment I have a partially sick installation with some packages from ubuntu-desktop, etc.  I would ideally like to strip out the other packages and reinstall the mythbuntu packages.  Any ideas how to do this without a complete install from scratch would be great; a list of packages would be a good start.

thanks.

---

### Post by lerrup on 2008-12-01
I know this isn't too interesting, but can anyone help?

---

### Post by laga on 2008-12-01
Hi,

take a look at the dependencies of the mythbuntu-desktop package:
```
apt-cache show mythbuntu-desktop
```

---

