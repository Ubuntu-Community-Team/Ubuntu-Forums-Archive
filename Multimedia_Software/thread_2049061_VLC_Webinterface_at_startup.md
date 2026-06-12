---
title: "VLC Webinterface at startup"
date: 2012-08-27
forum: Multimedia Software
---

### Post by Sinopa on 2012-08-27
I've installed VLC and I got the web interface activated, so I can control it from my android phone.

I am however stuck with a little problem. How can I start VLC web interface at startup? So I don't have to start VLC every time I want to see a movie? I want to control everything from my phone.

I found a really simple solution a long time ago, but I have forgotten how and I can't find the solution to it now.

Does anyone out there know how I can solve this little problem?

---

### Post by nativehound on 2012-08-28
Add it to the startup application preferences with. 

```
vlc -I http &
```

after a reboot check to see if it's running with

```
top
```

gl

---

