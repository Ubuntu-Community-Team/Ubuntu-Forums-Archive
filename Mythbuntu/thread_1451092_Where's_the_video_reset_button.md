---
title: "Where's the video reset button?"
date: 2010-04-10
forum: Mythbuntu
---

### Post by mookie60 on 2010-04-10
. . . nothing like typing a long post, then having the login timeout and losing the entire thing . . . maybe it's floating around somewhere, but I can't find it.   this one will be much shorter

i had a fully functioning 9.04 mythbox.   needed to give it an svideo output for a different tv.   bought an msi 8400 gs.   couldn't get it to work with either of the nvidia drivers.   the best was "low graphics mode" with the unbuntu default driver.   gave up and took out the card.

now i can't get my integrated graphics to work again.   i'm getting what appears to be the same "low graphics mode" windows during bootup , but i can't be sure what they say - they're so small i can't read them.

i just want to get back to what previously worked - how can i reset this?

any help is GREATLY APPRECIATED

thanks,
John

---

### Post by nickrout on 2010-04-10
remove (preferably backing it up) /etc/X11/xorg.conf and then restart X.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo /etc/init.d/gdm restart
```

---

### Post by mookie60 on 2010-04-10
thank you, thank you

---

