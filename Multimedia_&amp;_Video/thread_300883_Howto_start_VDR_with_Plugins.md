---
title: "Howto start VDR with Plugins"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by sbrinkmann on 2006-11-16
Hello,
i have installed vdr with all plugins and now i want to start vdr with all these plugins but when i look into my plugins list i always see only the plugin of my remote control. This ist my line to start vdr:

```

vdr -P'remote -i/dev/input/event3'
```

What should i do to start vdr with all plugins?

Thanks for Help.

---

### Post by sbrinkmann on 2006-11-16
When u whant to start **vdr** with more than one plugin u have to do it like this

```
vdr -P'<name of plugin 1>' -P'<name of plugin 2>' -P'<name of plugin 3>'
```

---

