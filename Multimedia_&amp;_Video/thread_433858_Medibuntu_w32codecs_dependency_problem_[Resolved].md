---
title: "Medibuntu w32codecs dependency problem [Resolved]"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by bailout on 2007-05-05
I downloaded the feisty w32codecs deb from medibuntu but when I try to install it on kubuntu feisty it gives a dependency not met error. It says that the package needs libstdc++5 is needed but not installed.

Any ideas? thanks

---

### Post by aysiu on 2007-05-05
```
sudo apt-get update
sudo apt-get install libstdc++5
```

---

### Post by bailout on 2007-05-05
> **aysiu said:**
> ```
sudo apt-get update
sudo apt-get install libstdc++5
```

Thanks for the reply but is it standard that the feisty w32 package needs this dependency? Feisty has libstdc++6 installed. My knowledge of these things is pretty limited but I am surprised that a package compiled for feisty doesn't use the lib version that is installed.

---

### Post by aysiu on 2007-05-05
Well the best way to do it is to add the Medibuntu repositories and let Adept or *apt-get* handle all the dependencies and versions.

---

### Post by bailout on 2007-05-06
In the end I found a w32codec deb that I downloaded before that worked without needing the extra libs. I think I got it from the debian repos last year. The codec package version is the same 20061022 so I assume the functionality is the same.

---

