---
title: "Restart sound system without restarting computer"
date: 2019-10-01
forum: Multimedia Software
---

### Post by rCXer on 2019-10-01
I've have an issue where sometimes there's no sound in Ubuntu 18.04.  Restarting the computer usually resolves this issue.  Is there an terminal command I can use to restart the sound system (alsa/pulseaudio) without rebooting?

---

### Post by CatKiller on 2019-10-02
```
pulseaudio -k
```

---

### Post by guiverc on 2019-10-02
I have a couple of boxes that lose sound on occasion after suspend, which I can correct by toggling the profile off & back on in `pavucontrol` (last configuration tab). If you want a GUI method, it maybe worth a shot.

---

### Post by nik.charles on 2019-11-23
```
systemctl --user restart pulseaudio
```

---

