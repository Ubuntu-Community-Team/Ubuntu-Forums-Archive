---
title: "How can I edit remote control config?"
date: 2010-05-24
forum: Mythbuntu
---

### Post by Daminator on 2010-05-24
Hello all,

I had a lircrc file set up a couple of years ago and never got around to setting it back up after I did a clean reinstall of Ubuntu/Myhthbuntu a short time later. I did however save a copy of the file.

I recently got the Hauppage remote working again and all seems fine, but I don't like the key assignments as much as the ones I chose.

That's fine, I don't mind changing them. The problem I have got is that I don't know how! I keep thinking that I've found the right file, I edit it and restart lirc, but there seems to be no difference made in the key assignments,

Can anyone point me to the correct files I need to be editing?

Thanks
D

---

### Post by jb5 on 2010-05-25
```
gedit ~/.lirc/mythtv
```Should do the trick.

---

### Post by Daminator on 2010-05-28
That worked perfectly. Thanks jb5. I now have a lovely configured remote which works just the way I like it.

Can anyone tell me how to control the behaviour of the power button when it's pressed outside of MythTV? Currently, it brings up a menu where I can choose to close down the system. I'd like the button to open up MythTV if it's not running (and then close it if it is running). Is that possible?

Thanks again
Damian

---

