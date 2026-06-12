---
title: "ubuntustudio-audio"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by leg on 2008-04-01
I have just been looking at this package and have seen that a new kernel is paret of the install. Can anyone tell me why this is needed and any consequences of installing it such as reverting etc.

---

### Post by artfwo on 2008-04-02
The ubuntustudio (rt) kernel is much better suited for realtime audio work. It won't overwrite you current kernel and you'll be able to choose which one to boot :)

Oh, and if you use any proprietary drivers, make sure to install the restricted-modules package for the -rt kernel as well. Uninstalling the rt kernel later is also safe - only ubuntustudio metapackage will be removed with that. Hope this helps :)

---

### Post by leg on 2008-04-02
Thanks yes it did help.

---

