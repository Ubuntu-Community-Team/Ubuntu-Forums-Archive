---
title: "Disabling agpgart"
date: 2008-12-25
forum: Multimedia Software
---

### Post by dread on 2008-12-25
Ok so I have an issue where xvmc locks up my system, and was told to try adding Option "NVAGP" "1" to my /etc/X11/xorg.config. However that still doesn't allow the nvidia driver to take over because agpgart is compiled into my kernel. So I am trying to build a new kernel without agpgart and apparently that is also not possible as I am unable to unselect it. Any ideas, or further questions?

---

