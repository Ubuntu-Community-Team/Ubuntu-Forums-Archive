---
title: "mythbuntu control center starts on boot"
date: 2007-10-22
forum: Mythbuntu
---

### Post by mr_bungalow on 2007-10-22
whenever I reboot my mythbuntu box, I get prompted for my administrator password and then the mythbuntu control center pops up.  How can I stop this?  Using 7.10 Beta.  Thanks!

---

### Post by superm1 on 2007-10-22
> **mr_bungalow said:**
> whenever I reboot my mythbuntu box, I get prompted for my administrator password and then the mythbuntu control center pops up.  How can I stop this?  Using 7.10 Beta.  Thanks!
You have accidentally restarted the session with it running so it's "saved" on startup now.  Typically you can get rid of that by 

```
rm ~/.cache -rf
```

Followed by ctrl alt backspace (so that it can't save settings again)

---

