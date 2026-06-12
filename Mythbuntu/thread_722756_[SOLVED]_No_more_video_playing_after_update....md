---
title: "[SOLVED] No more video playing after update..."
date: 2008-03-12
forum: Mythbuntu
---

### Post by LtPitt on 2008-03-12
Hello there!

After an update of mythbuntu asked by synaptic I'm no longer able to see videos :|
And I don't get any kind of errors...

When I click on "Media Library" and then on "Watch Videos" nothing happens...
Everything else is working fine...

When I try to understand what's happening looking into "Utilities", and then "Video Manager" nothing happens...

The same if I try "Utilities", "Setup", "Media settings" and then "Videos settings".

Things are getting desperate :'(

I want my videos back :'(

What can I do?

---

### Post by murbanci on 2008-03-12
> **LtPitt said:**
> Hello there!

After an update of mythbuntu asked by synaptic I'm no longer able to see videos :|
And I don't get any kind of errors...

When I click on "Media Library" and then on "Watch Videos" nothing happens...
Everything else is working fine...

When I try to understand what's happening looking into "Utilities", and then "Video Manager" nothing happens...

The same if I try "Utilities", "Setup", "Media settings" and then "Videos settings".

Things are getting desperate :'(

I want my videos back :'(

What can I do?

Open up symantec package manager and check if mythvideo has been updated to the 0.21 version.  If it hasn't, right click and mark for update and click apply.  It will tell you that it is going to remove mythdvd.  This is ok since mythdvd is combined with the latest version of mythvideo.  After I did this, everything worked fine.  Hope this woks for you.

---

### Post by LtPitt on 2008-03-12
just...

g r e a t

Thanks a lot =)

---

### Post by kreegor on 2008-03-12
I had the same issue. Fixed it by opening the terminal and running

```
sudo apt-get install mythvideo
```

---

### Post by nasha on 2008-03-12
Worth making a note that i had exactly the same issue a few days ago. It appears synaptic doesn't update MythVideo to 0.21 for some reason

---

### Post by tedder on 2008-03-13
> **murbanci said:**
> Open up symantec package manager and check if mythvideo has been updated to the 0.21 version.  If it hasn't, right click and mark for update and click apply.  It will tell you that it is going to remove mythdvd.  This is ok since mythdvd is combined with the latest version of mythvideo.  After I did this, everything worked fine.  Hope this woks for you.

Thanks! Exactly what I needed to do. It was nice to find your post for it :-)

---

