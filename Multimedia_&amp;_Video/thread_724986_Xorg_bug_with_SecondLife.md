---
title: "Xorg bug with SecondLife"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by kr0ots on 2008-03-15
Hey guys, 

Im a new user of Hardy heron, but i have an issue with it.
when a run the second life client, first it works pretty cool but a few time after thats going weird.
It exactly like i push one arrows onmy keyboard without stopping....
I have to restart xorg to keep this bug away.

tail -n 40 /var/log/Xorg.0.log return :

(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(=:) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(=:) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9

If you have a clue about this ....

---

