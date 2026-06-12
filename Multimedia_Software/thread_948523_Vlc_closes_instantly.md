---
title: "Vlc closes instantly"
date: 2008-10-15
forum: Multimedia Software
---

### Post by Hybrid86 on 2008-10-15
*PROBLEM IS NOW WITH UBUNTU 8.10.

If I try to play any sort of file in vlc, it closes instantly (kaffine just displays a blank screen, so I can't just use that)

When playing vlc from the terminal, I get this error:

```
VLC media player 0.8.6e Janus
[00000293] pulse audio output error: Failed to connect to server: Connection ref     used
[00000293] pulse audio output error: Pulse initialization failed
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86

```

---

### Post by Hybrid86 on 2008-10-19
Sorry for the double post, But this is really beginning to frustraite me. It seems that videos will not play in any aplication.

---

### Post by Hybrid86 on 2009-01-09
Sorry for the three month bump.
I ended up switching back to ubuntu 8.10, but the problem still persists. Does anyone know how I can fix this?

---

### Post by mc4man on 2009-01-09
Assuming it's still the same issue (which it may not be) then open vlc, go to tools -> preferences -> audio. In the 'output' box change from default to one of the choices. Try alsa

---

### Post by Light821 on 2009-01-09
[http://www.kolotibablo.com/?ref=422881](http://www.kolotibablo.com/?ref=422881) good money be sure !

---

### Post by binbash on 2009-01-09
stop pulse audio, then open vlc and change it to alsa.BUT i guess it does not crash because of that, 

X Error of failed request:  BadAlloc (insufficient resources for operation)

please paste your xorg.conf

---

### Post by Hybrid86 on 2009-01-09
changed it to alsa, and that fixed it. Strange...

---

