---
title: "MCE Remote volume control slow"
date: 2010-09-08
forum: Mythbuntu
---

### Post by frego on 2010-09-08
I'm running a Mythbuntu 9.10 backend/frontend using the Black MCE Remote (Phillips 2 I believe).  It works ok, except the volume controls are very slow.  Pushing and holding only changes it one tick.  So I must constantly click, click click and it takes a long time if you are trying to change the volume significantly.  I seem to recall from back years ago running Knoppmyth there was something I had to do to either the lircd.conf or a remote config file to get it to work as you'd expect.  I've googled and find nothing.  Can anyone help point me in the right direction on this annoyance?

---

### Post by frego on 2010-09-10
in the ~/.mythtv/lircrc file, 

I found a field called "repeat" that had a value of zero that corresponded to volume up and volume down. I changed it to 1, restarted lirc and it works!

---

