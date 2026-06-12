---
title: "f-spot 0.4.2 Received exception &quot;libfspot&quot; (patch)"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by yosemite610 on 2008-03-26
After installing f-spot 0.4.2 from source, I got the  Received exception "libfspot" error when I tried to use the 'Automatically adjust colors' button. Bug is outlined here: [Bug #192933]("https://bugs.launchpad.net/f-spot/+bug/192933").

As I have no idea of how I might apply the supplied debdiff file, I manually made the changes required and the error is gone... 

This is what I did:
I opened f-spot-0.4.2/src/Cms.dll.config and changed the contents from:
```
<configuration>
  <dllmap dll="liblcms-1.0.0.dll" target="liblcms.so.1"/>
</configuration>
```

To:
```
<configuration>
  <dllmap dll="liblcms-1.0.0.dll" target="liblcms.so.1"/>
  <dllmap dll="libfspot" target="/usr/lib/f-spot/libfspot.so.0"/>
</configuration>
```

Then I did a make clean, ./configure --prefix=/usr, make, sudo make install.

Hope  this helps save another soul some time ;')  Feel free to criticize/add/delete.

---

