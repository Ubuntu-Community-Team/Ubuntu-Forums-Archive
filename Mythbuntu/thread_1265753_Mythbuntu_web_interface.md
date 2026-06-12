---
title: "Mythbuntu web interface"
date: 2009-09-13
forum: Mythbuntu
---

### Post by turtle02 on 2009-09-13
I am running mythbuntu 9.04 I had my system up and running ok but today I find that my roommate has downloaded and installed the ubuntu updates that pop up. Everything still seems to be working ok except for the web interface. it is there and i can log in but there are not options to record things or anything like that I uploaded a screen shot of what it shows.

---

### Post by crez79 on 2009-09-13
Try this ```
http://*backendip*/mythweb/?RESET_TMPL=true
```
It appears your mythweb is stuck on the mobile interface. This command should reset it.

---

### Post by turtle02 on 2009-09-13
Sweet that worked, is it ok to use my phone to get to my mythbuntu server?

---

### Post by crez79 on 2009-09-14
Sure. As long as you have security properly set up, it is fine.

---

### Post by wizgnome on 2009-09-15
> **turtle02 said:**
> Sweet that worked, is it ok to use my phone to get to my mythbuntu server?

I used a separate username/password for mobile access, otherwise I had to reset the web template every time when switching back to the PC view after accessing from a mobile.

---

