---
title: "Mythbuntu wont pick up my asus p7131 remote"
date: 2009-11-24
forum: Multimedia Software
---

### Post by tominated on 2009-11-24
Hi,
I just installed mythbuntu on a machine with an asus my cinema p7131 hybrid, which runs tv just fine, but I cannot for the life of me get the ir receiver to work. It doesn't even show up in /dev/. I am a total newb to hardware on linux. Can anybody help? I'd like to get this htpc finished.

Thanks in advance!

---

### Post by tominated on 2009-11-25
bump?

---

### Post by tominated on 2009-11-25
Ok, i figured it out. lirc wasn't looking at the right device. for some reason the IR reciever was at /dev/input/event5, instead of /dev/lirc0 or something. Don't really know why it did it, but reconfiguring lirc worked fine

---

### Post by mehturt on 2010-01-22
hi.. do you have the lirc running or does your remote work without it as well?

---

