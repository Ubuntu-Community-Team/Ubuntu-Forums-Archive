---
title: "Update Snap Store ...?"
date: 2024-03-09
forum: Multimedia Software
---

### Post by holten on 2024-03-09
Don't know if this is the right place to ask, but I'll take a chance - got an update on the Snap Store, but I can't update because I got the update on the Snap store, it has to be closed before the update happens AND therefore I don't get the update Anyone who can help?? 
Thank You if you could give me some answer!

---

### Post by cybrsaylr on 2024-03-09
Been having the same problem.

I get this message when attempting to update:
[IMG]https://i.postimg.cc/FsGHzpwX/Screenshot-from-2024-03-09-10-35-18.png[/IMG]

---

### Post by ian-weisser on 2024-03-09
That window is snap-store running.  Snaps must be stopped to refresh.
Thus, Snap-store cannot update itself from the GUI. 

Quit and wait a few hours (real Quit. Merely closing the window is not enough)

Or update it from the terminal:
```

snap-store --quit
sudo snap refresh

```

Classic 22.04 and 20.04 bug. Fixed in newer releases.

---

### Post by cybrsaylr on 2024-03-10
Thanks  ian-weisser

 Put that code in terminal and think it did the trick.

---

