---
title: "Quodlibet - ImportError: No module named wma"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by seditiousmonkey on 2007-08-24
Can anyone help me with installing quodlibet.  I recently installed quodlibet from the repositories and now get this error when I try to start it.

> joe@joe-desktop:~$ quodlibet
Supported formats: mod, mp3, mp4, mpc, trueaudio, wav, wavpack, xiph
Traceback (most recent call last):
  File "/usr/bin/quodlibet", line 301, in <module>
    main()
  File "/usr/bin/quodlibet", line 33, in main
    library = load_library()
  File "/usr/bin/quodlibet", line 255, in load_library
    lib = library.init(const.LIBRARY)
  File "/usr/share/quodlibet/library/__init__.py", line 38, in init
    library.load(cache_fn, skip=True)
  File "/usr/share/quodlibet/library/_library.py", line 124, in load
    try: items = pickle.load(fileobj)
ImportError: No module named wma

I'm pretty sure all dependencies are satisfied but I did have had a getdeb version before this one.  Could that be the cause of my problem.  Installing using synaptic package manager on another computer caused no problems whatsoever.

any ideas would be so appreciated.

---

### Post by seditiousmonkey on 2007-08-24
bump

---

### Post by hugmenot on 2007-08-24
You might want to install those packages, wma is included there.
[http://ubuntuforums.org/showpost.php?p=2596985&postcount=201](http://ubuntuforums.org/showpost.php?p=2596985&postcount=201)

---

### Post by seditiousmonkey on 2007-08-24
thanks hugmenot,  I was hoping to use the 'official' version and would still love to know how this installation differs from my other but glad to have my music playing again.

---

### Post by hugmenot on 2007-08-24
> **seditiousmonkey said:**
> thanks hugmenot,  I was hoping to use the 'official' version and would still love to know how this installation differs from my other but glad to have my music playing again.

I guess you had an older python-mutagen installed which lacks wma support and this lead to the error.

---

