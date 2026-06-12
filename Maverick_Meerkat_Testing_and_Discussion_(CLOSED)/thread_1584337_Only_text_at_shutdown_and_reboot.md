---
title: "Only text at shutdown and reboot"
date: 2010-09-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by northar on 2010-09-29
The nice boot and shutdown ubuntu logo disappered some updates ago for me, and is now replaced with an ugly text. Anyone else seeing this, and anyone got a solution?

---

### Post by garvinrick4 on 2010-09-29
> **northar said:**
> The nice boot and shutdown ubuntu logo disappered some updates ago for me, and is now replaced with an ugly text. Anyone else seeing this, and anyone got a solution?
Do you have plymouth at boot? If so I would say you are OK. It shutdowns so quick that
the graphic drivers do not have time to kick in. If no plymouth at boot there is a way to fix that. Copy and paste:
```
sudo -i 
``````
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u 
```

---

