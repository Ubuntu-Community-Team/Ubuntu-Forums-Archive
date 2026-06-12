---
title: "displaying to a different session"
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by djlosch on 2006-11-30
lets say i have user "bob" logged in at the desktop of the machine "bobs_box". i'm logged in as "djlosch" on a remote machine "remote_box". i want to ssh from remote_box to bobs_box, su up, and execute a command to have mplayer play "/home/bob/whatever.avi" in bob's session, so on bob's screen on bobs_box, he sees mplayer playing whatever.avi and hears out of his speakers the sound from whatever.avi. vnc is out of the question. it must be command line (so i can script it). is there any syntax to do this?

---

### Post by apjone on 2006-11-30
when you have su'd up you need to export your display
```

su -
password: xxxxx
export DISPLAY=:0
nohup mplayer whatever.avi

```

the nohup means if you log out mplayer will still work.

---

