---
title: "MythTV Watch TV just exits"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by jc508 on 2007-10-05
I was just finishing setting up with MythTv and it was working.
Then, for some unknown reason, I entered 'mythwelcome'  - this appeared to do nothing.

Now when I start the Mythfrontend and choose "watch TV" it just blinks and comes back to the main menu!
I have cycled the box and thus restarted the backend to no avail

Does anybody have any ideas?   Are there logs anywhere I could look at ?

Thanks
JC

---

### Post by NT4usB on 2007-10-06
You can run mythfrontend from a terminal```
mythfrontend -v all
```Alt+Tab to bring the terminal window back to the front and look at the output. 
Usual suspects are the path to the folder that holds recordings (live tv records too) is incorrect or user permissions on that folder.

---

### Post by jc508 on 2007-10-07
Thanks that helped - amazing how much furthur you get with some evidence!

Problem was two corrupt databse tables - pretty crappy error reporting but once these were repaired things returned to normal.

JC

---

