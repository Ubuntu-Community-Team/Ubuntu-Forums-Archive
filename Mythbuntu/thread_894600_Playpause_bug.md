---
title: "Play/pause bug"
date: 2008-08-19
forum: Mythbuntu
---

### Post by kreegor on 2008-08-19
Hey guys. I have found a bug but I'm not sure where to report it.

Basically on a clean install of Mythbuntu if you set the remote to be the DVICO USB remote the following code appears twice in the lirc file

```

begin
    remote = DVICO_MCE
    prog = mythtv
    button = playpause
    config = P
    repeat = 0
    delay = 0
end

```

All it does it makes it impossible for anything to be paused with the remote as it automatically plays again because it appears twice in the file.

---

### Post by db260179 on 2008-08-20
I reported this issue, and posted a fix

[https://bugs.launchpad.net/mythbuntu/+bug/238275](https://bugs.launchpad.net/mythbuntu/+bug/238275)

> **kreegor said:**
> Hey guys. I have found a bug but I'm not sure where to report it.

Basically on a clean install of Mythbuntu if you set the remote to be the DVICO USB remote the following code appears twice in the lirc file

```

begin
    remote = DVICO_MCE
    prog = mythtv
    button = playpause
    config = P
    repeat = 0
    delay = 0
end

```

All it does it makes it impossible for anything to be paused with the remote as it automatically plays again because it appears twice in the file.

---

### Post by db260179 on 2008-08-20
This will help as well

[https://bugs.launchpad.net/mythbuntu/+bug/231577](https://bugs.launchpad.net/mythbuntu/+bug/231577)

---

### Post by kreegor on 2008-08-21
Ok cool :)

---

