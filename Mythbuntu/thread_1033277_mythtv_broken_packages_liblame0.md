---
title: "mythtv broken packages liblame0"
date: 2009-01-07
forum: Mythbuntu
---

### Post by maff on 2009-01-07
Hi, just tried the dist upgrade and it removed bits of mythtv, on trying to install it i get:

```

The following packages have unmet dependencies.
  mythtv: Depends: mythtv-backend (= 0.21.0+fixes19594-0ubuntu0+mythbuntu1) but it is not going to be installed
          Depends: mythtv-frontend (= 0.21.0+fixes19594-0ubuntu0+mythbuntu1) but it is not going to be installed
E: Broken packages

```

so i try mythtv-frontend on its own and get
```

The following packages have unmet dependencies.
  mythtv-backend: Depends: liblame0 (>= 3.97) but it is not installable
                  Depends: libmyth-0.21-0 (>= 0.21.0+fixes19594) but 0.21.0+fixes18722-0ubuntu1 is to be installed
                  Depends: mythtv-transcode-utils (= 0.21.0+fixes19594-0ubuntu0+mythbuntu1) but it is not going to be installed
E: Broken packages

```

so try liblame0 and get
```

Package liblame0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libmp3lame0
E: Package liblame0 has no installation candidate

```

and finally libmp3lame0 and get
```

libmp3lame0 is already the newest version.
libmp3lame0 set to manually installed.

```

any help would be apreciated, cheers :D

---

### Post by maff on 2009-01-07
my bad, my sources were messed up, ignore this ](*,)

---

