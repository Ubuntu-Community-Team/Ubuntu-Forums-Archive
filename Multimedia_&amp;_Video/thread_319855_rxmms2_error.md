---
title: "rxmms2 error"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by Hakimio on 2006-12-16
Even I think I installed all the needed packages I get this error when trying to start rxmms2:
```
/home/tomas/.rxmms2/rxmms2:5:in `require': no such file to load -- gui/main (LoadError)
        from /home/tomas/.rxmms2/rxmms2:5

```

Step by step explanation what to do would be highly appreciated ;)

---

### Post by Hakimio on 2006-12-16
Okey, it was because I was starting it incorrectly. 
Now, when I am trying to start it correctly I get this error:
```
./xmms2.rb:10: uninitialized constant Xmms2::XmmsClient (NameError)
        from ./rxmms2:10

```

..and I think it's because I don't have libxmms2client-ecore, but when I am trying to install it I get this error:
```
The following packages are BROKEN:
  libxmms2client-ecore
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8112B of archives. After unpacking 57.3kB will be used.
The following packages have unmet dependencies:
  libxmms2client-ecore: Depends: libecore0 which is a virtual package.
                        Depends: libxmms2client (= 0.2+git20060328-2dapper0) but 0.2+git20060717-1dapper0 is installed.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
```

Somewhere I read that it can be installed from source files overcoming these dependence errors. Can someone tell me where to find the source files and how to compile them?

---

