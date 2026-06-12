---
title: "mythfrontend and mythbackend screen resolution messed up after db restore"
date: 2012-12-20
forum: Mythbuntu
---

### Post by diesel48 on 2012-12-20
Kind of a strange question but I am switching my masterbackend to a mythbuntu machine. I have some hardware that is starting to die and now would be a good time to switch. Before restoring my database the mythfrontend or mythbackendsetup were full screen and looked nice on my monitor. When I restored my database these screens no longer fit properly. The screens now show the mythbuntu tool bar up top and are at a fixed resolution. They almost seem like that are a 1080 screen size on my small 4:3 computer monitor. Is there a way to reset this?

---

### Post by diesel48 on 2012-12-20
Figured it out. It took in my old resolution for the frontend. I had to start the mythfrontend by mythfrontend --geometry 1024x768. That then let me reset the resolution of the application. When I restored the DB it must have saved the old resolutions.

---

