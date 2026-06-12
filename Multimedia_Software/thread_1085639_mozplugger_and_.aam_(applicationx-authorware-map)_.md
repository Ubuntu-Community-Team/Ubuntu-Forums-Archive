---
title: "mozplugger and .aam (application/x-authorware-map) formats?"
date: 2009-03-03
forum: Multimedia Software
---

### Post by aLiEnTxC on 2009-03-03
I try to setup mozplugger for use authorware.

Test side from adobe is [http://www.adobe.com/shockwave/welcome/authorwareonly.html](http://www.adobe.com/shockwave/welcome/authorwareonly.html)

I followed the steps from [https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave) and the shockwave installation is running.

I added now the follow lines in my mozpluggerrc file:

```
application/x-authorware-map: aam: Macromedia Shockwave Authorware
        swallow(firefox.exe) fill stream: wine "C:\\Programme\\Mozilla Firefox\\firefox.exe" -chrome "$file"
```

In the wine driven firefox I can open the page and the the animation.

On the linux Firefox i see only a textblock:
> ver	0	8
get	.
seg	all	cabl0000_FL.aas	0	44752
# HTML_PARAMS: WIDTH=378 HEIGHT=150 BGCOLOR=FFFFFF
opt	all	BypassSecurityDialog=TRUE
opt	all	UniqueID=8860360


any ideas?

---

