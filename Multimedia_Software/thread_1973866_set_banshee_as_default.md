---
title: "set banshee as default"
date: 2012-05-05
forum: Multimedia Software
---

### Post by cybergalvez on 2012-05-05
Hi all, I switched to bansee a few versions back and don't want to switch back to rythmbox. I noticed that the ubuntu one intigration is gone from banshee, anyway to get ti back? Also how do I set Banshee as the default music player?

Thanks

---

### Post by Curtis6767 on 2012-05-05
System Settings/Details/Default Applications.

---

### Post by mc4man on 2012-05-05
System settings will just set 1 mimetype as default for banshee (audio/x-vorbis+ogg

If you want to get a big jump on all listed audio types that banshee has in it's .desktop you could run this command - will write to ~/.local/applications/mimeapps.list  - 1 long command

 ```
grep "^MimeType=" /usr/share/applications/banshee.desktop | cut -d "=" -f 2   | xargs -d ';' -n 1 | grep -e "^audio/" -e "^x-content/audio"   | xargs -n 1 -I '{}' xdg-mime default banshee.desktop '{}'
```

ubuntuone support was dropped, hasn't been brought back yet, maybe see if a banshee ppa has it yet (if it ever is coming back

---

### Post by cybergalvez on 2012-05-05
Thanks

---

