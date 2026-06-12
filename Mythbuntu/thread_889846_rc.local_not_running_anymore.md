---
title: "rc.local not running anymore"
date: 2008-08-14
forum: Mythbuntu
---

### Post by Nikas on 2008-08-14
Hello.

I have three computers with mythbuntu 8.04. 1 server and 2 backends.
After updating (apt-get) all the computers rc.local are not running on start anymore. What to do?

Thanks.

---

### Post by bazzer on 2008-10-22
if you haven't got this yet, try removing the '-e' option on the first line of rc.local:
```
#!/bin/sh -e
```
becomes 
```
#!/bin/sh
```

---

