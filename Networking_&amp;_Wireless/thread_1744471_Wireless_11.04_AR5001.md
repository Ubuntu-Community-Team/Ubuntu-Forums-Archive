---
title: "Wireless 11.04 AR5001"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by KaiJordanDay on 2011-04-30
On 10.10 my wireless card worked out of the box. Now on 11.04 it stopped working after the update!

My card is Atheros AR5001.

---

### Post by notesetter on 2011-04-30
Same problem here. It seems to work only intermittently, and from what I've noticed, only after I hook it up to an ethernet cable (but not always).

I've tried hooking up to ethernet and then running ```
jockey-gtk
``` in a terminal to see if Ubuntu needed to fetch additional drivers, but nothing popped up.

David

---

### Post by KaiJordanDay on 2011-04-30
Have you tried ndiswrapper with the drivers? I'm trying now...

---

### Post by notesetter on 2011-04-30
I haven't tried ndiswrapper, but I just found [this thread]("http://ubuntuforums.org/showthread.php?t=1742231&highlight=AR5001"). I'd prefer not to use ndiswrapper if possible. Let me know how it goes. I'm tempted to try the procedure in the linked thread after I research a little to make sure it pertains to the AR5001. Probably won't be able to get to it until later this afternoon or tonight (U.S. East Coast).

---

### Post by KaiJordanDay on 2011-04-30
That relies on your card being present. My card isn't even detected!

---

### Post by KaiJordanDay on 2011-04-30
Fixed it :) Type this into terminal

> sudo rfkill unblock wifi

---

### Post by notesetter on 2011-04-30
That rocks! I bet we can make it automatic too. I'll peruse the linked post from above and post the procedure here if you don't get to it first.

---

