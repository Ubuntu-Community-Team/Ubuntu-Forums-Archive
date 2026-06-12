---
title: "can't listen live radio stations any more"
date: 2008-02-17
forum: Multimedia Production
---

### Post by liakosantonios on 2008-02-17
hi to all.
i was listening to live radio stations (like 'www.live24.gr/radio/loveradio.jsp' which uses windows media player for their transmission) with firefox and vlc but after a system update of my Gutsy this stopped. any thoughts about what might caused the problem?

---

### Post by twothird on 2008-03-17
maybe VLC got unchecked as being the default player for that (if you are opening it from firefox)
tools>options>content>file types>manage

---

### Post by kostkon on 2008-03-17
> **liakosantonios said:**
> hi to all.
i was listening to live radio stations (like 'www.live24.gr/radio/loveradio.jsp' which uses windows media player for their transmission) with firefox and vlc but after a system update of my Gutsy this stopped. any thoughts about what might caused the problem?

Do you remember what packages were updated? Also,could you be more specific on what actually happens now when you try to play a radio stream?

The *VLC* plugin for *Mozilla* is being used; so could you please do a
```
about:plugins
```
in the *Firefox* address bar and see if the output contains references to the *VLC* plugin for *Windows media* files and such?

---

