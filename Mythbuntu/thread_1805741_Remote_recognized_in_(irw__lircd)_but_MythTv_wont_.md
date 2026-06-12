---
title: "Remote recognized in (irw / lircd) but MythTv wont recognized it."
date: 2011-07-16
forum: Mythbuntu
---

### Post by Kr0nZ on 2011-07-16
Hi today I decided to try and get my half working remote fully working. The problem it had before was that the OS would recognize it as a keyboard / mouse combo
lircd would not recognize it at all.
Being recognized as a keyboard / mouse combo resulted in some of the buttons not working correctly.

Well now I have lircd seeing my remote, and it sees all buttons except 1 or 2, but when I go into myth to set the keys up nothing happens.
I have tried setting the lircd socket in 'setup >>> general' to both '/dev/lircd' and '/dev/lircd1' both it still does not detect it.

Also in the terminal if I try 'irw' I get this response
```
demon@mythDemon:~$ irw
connect: Connection refused

```

I have to always specify '/dev/lircd' or '/dev/lircd1' both are the same device, if I do I get the expected response like
```
mythDemon:~$ irw /dev/lircd
000000008001006c 00 KEY_DOWN devinput
000000008001006a 00 KEY_RIGHT devinput

```

Im not sure what else to try to do to get myth to see it
Thanks for any help

---

### Post by Kr0nZ on 2011-07-16
Got it working now
I had to run mythbuntu-lirc-generator then everything just worked, I hope, testing now

---

