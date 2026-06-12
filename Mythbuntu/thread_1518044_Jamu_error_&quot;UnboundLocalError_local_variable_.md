---
title: "Jamu error &quot;UnboundLocalError: local variable 'dest' referenced before assignment&quot;"
date: 2010-06-25
forum: Mythbuntu
---

### Post by pearless on 2010-06-25
Using mythbuntu (latest version), I decied to try Jamu, because my files on on a CIFS/SMB mount and after warning me it could find some of my home videos it and died.

I entered:

/usr/share/mythtv/mythvideo/scripts/jamu.py -l en -C "/home/mythtv/.mythtv/jamu.conf" -sMNV > "jamu.log"

the error that it dies on is:

```
Traceback (most recent call last):
  File "/usr/share/mythtv/mythvideo/scripts/jamu.py", line 6429, in <module>
    main()
  File "/usr/share/mythtv/mythvideo/scripts/jamu.py", line 6414, in main
    process.processMythTvMetaData()
  File "/usr/share/mythtv/mythvideo/scripts/jamu.py", line 5793, in processMythTvMetaData
    available_metadata[graphic_type]= self.rtnRelativePath(dest,  graphicsDirectories[graphic_type])
UnboundLocalError: local variable 'dest' referenced before assignment
```

This seems to be a bug?
Cheers
Douglas.

---

