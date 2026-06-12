---
title: "remove libmono?"
date: 2010-10-21
forum: Multimedia Software
---

### Post by bro on 2010-10-21
Is it possible to remove libmono-wcf3.0cil completely? 

I get this error:
```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to lock the download directory
```

---

### Post by Yellow Pasque on 2010-10-21
Yes, you can remove all the mono/cil stuff completely if you don't use any mono apps. The error looks like you have another package manager open.

---

### Post by bro on 2010-10-21
Thanks. I might have been a bit confused. I was trying to remove moonlight, in which I didn't succeed, but I came across this one. 

How does one remove moonlight? Where is it installed?

---

### Post by directhex on 2010-10-22
libmono-wcf3.0-cil isn't used by anything within Ubuntu - it's part of the Moonlight SDK. It's the Windows Communication Foundation library. You can remove it all you like.

---

