---
title: "Final steps for lirc config"
date: 2016-01-11
forum: Mythbuntu
---

### Post by m-chabot on 2016-01-11
Hello all,

 I manage to create my own lircd.conf using irrecord but I have a minor problem.  Here what I get when I use irw to get an outpout:

 Pressing once the UP buttons do Nothing, the second press does that:

 67 0 KEY_UP linux-input-layer
 67 0 KEY_UP_UP linux-input-layer

 Then the third press NOTHING and the fourth the same as the second.

 Same with every other key. Here is the OK button:

 First: Nothing
 Second:
 161 0 KEY_OK linux-input-layer
 161 1 KEY_OK linux-input-layer
 161 2 KEY_OK linux-input-layer
 161 3 KEY_OK linux-input-layer
 161 4 KEY_OK linux-input-layer
 161 0 KEY_OK_UP linux-input-layer
 Third: NOTHING
 Fourth: same as second

 That's not too bad becaude in OSMC I can go up, down, left right,but it takes 2 press in order to move once.
 
The OK seems to send 2 "OKs" so it's kinda annoying.

Any idea how I could resolve this?

 Here is my lircd.conf:  [http://pastebin.com/ueJqGE3T](http://pastebin.com/ueJqGE3T)

---

