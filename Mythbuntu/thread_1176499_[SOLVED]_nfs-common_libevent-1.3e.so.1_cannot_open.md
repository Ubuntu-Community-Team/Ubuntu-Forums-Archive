---
title: "[SOLVED] nfs-common: libevent-1.3e.so.1 cannot open shared object"
date: 2009-06-02
forum: Mythbuntu
---

### Post by Verzweifler on 2009-06-02
During startup of my fresh Mythbuntu 9.04 install, "nfs-common" threw the above error message. It originated from rpc.idmapd...

I solved this issue by manually reinstalling the libevent1 package using aptitude. 
```
sudo aptitude reinstall libevent1
```

After that, another missing module (libnfsidmap2) popped up. I tried the very same reinstall method and it worked just fine. No more [fail] messages...:D

---

