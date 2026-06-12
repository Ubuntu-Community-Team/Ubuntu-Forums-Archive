---
title: "[SOLVED] Remote support for Fusion HDTV5 RT GOLD"
date: 2008-08-27
forum: Mythbuntu
---

### Post by dmdbdd on 2008-08-27
This remote isn't supported in this version(2.6.24) of Linux - it looks like it well be in later versions. I found this site  [http://lirc.sourceforge.net/remotes/dvico/](http://lirc.sourceforge.net/remotes/dvico/)   . The FusionRemote file appears to have the correct keys corresponding to my remote and the FusionRemote.jpg is the exact remote that I have. However I don't know how to implement this code. I'm assuming that I could just paste this code into some file, however I'm not sure which file. If this is what I need to do, then how do I configure the IR Remotes and Transmitter screen?

Maybe I'm all wet - does anyone know how to get this remote working.

Regards,

dmdbdd

---

### Post by Spoonite on 2009-04-25
If you figured the problem with the remote out could you please let me know how you did it.

Thanks

---

### Post by bhampton on 2009-04-28
I don't know why this thread says SOLVED when it seems nothing was SOLVED.


-Brian

---

### Post by bhampton on 2009-04-28
OK,

I think I fixed this...

I did this one...

sudo apt-get --reinstall install lirc
And now when I run IRW I get responses that look correct!

I have to run off and try myth frontend again..

EDIT --- Really SOLVED this time at least for me! AWESOME!!!

-Brian

---

