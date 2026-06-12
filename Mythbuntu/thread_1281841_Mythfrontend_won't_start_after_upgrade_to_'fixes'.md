---
title: "Mythfrontend won't start after upgrade to 'fixes'"
date: 2009-10-03
forum: Mythbuntu
---

### Post by korgman on 2009-10-03
I installed Mythbuntu fresh a few weeks ago.  I enabled jyavenard's repo and got that working no problem.  I now, just downloaded the deb package mythbuntu-repos_2-0ubuntu0+mythbuntu5_all.deb and installed that, selected "weekly builds", and did an update.  It looked like it updated some nvidia and vdpau stuff.

Now when I try to start mythfrontend all I get is:
```
/usr/bin/mythfronend.real: error while loading shared libraries: libvdpau.so.1: cannot open shared object file: No such file or directory
```

myth will no launch.  Any ideas?

---

### Post by superm1 on 2009-10-03
If it's looking for that file, you're on trunk...

---

### Post by jyavenard on 2009-10-04
> **korgman said:**
> I installed Mythbuntu fresh a few weeks ago.  I enabled jyavenard's repo and got that working no problem.  I now, just downloaded the deb package mythbuntu-repos_2-0ubuntu0+mythbuntu5_all.deb and installed that, selected "weekly builds", and did an update.  It looked like it updated some nvidia and vdpau stuff.

Now when I try to start mythfrontend all I get is:
```
/usr/bin/mythfronend.real: error while loading shared libraries: libvdpau.so.1: cannot open shared object file: No such file or directory
```

myth will no launch.  Any ideas?

You are probably using my nvidia packages.

I have separated the vdpau libraries from the nvidia drivers now.

So if you want to use mythbuntu trunk packages, manually install the package libvdpau0.

---

