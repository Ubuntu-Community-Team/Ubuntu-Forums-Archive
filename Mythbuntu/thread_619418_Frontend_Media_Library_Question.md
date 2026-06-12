---
title: "Frontend Media Library Question"
date: 2007-11-21
forum: Mythbuntu
---

### Post by basherdesigns on 2007-11-21
I have my MythTV server running as frontend/backend.  I'm not using it as a PVR just to watch video files.  I can watch videos in my Media Library > Watch Videos just fine on the server.

Now I'm trying to do the same on a frontend machine.  On the frontend, once it opens under Media Library, the only option I have is Watch Recordings.  Where is Watch Videos and Listen to Music?

Am I not really connecting to the backend?  I've tested my mysql username and password via terminal from the frontend and i can connect and see the mythconverg database.

Any ideas?? ThankS!!  Happy Thanksgiving too!

---

### Post by uopjohnson on 2007-11-21
It sounds like you haven't installed the mythvideo and myth music plugins.  Launch the mythbuntu control center and select application & plugins and then check mythmusic and mythvideo.

---

### Post by basherdesigns on 2007-11-21
hmm.. i don't have a Mythbuntu control center on the frontend.  Did i miss some packages or what??

---

### Post by basherdesigns on 2007-11-21
Ok. .i installed Mythvideo and Mythmusic.  I can see the videos now but I can not watch them.

Do i need to mount to the same directory path to where my videos are physically located, just like the backend server or?  It seems my frontend just reads the database but can't get to the actual files...

thanks!!

---

### Post by basherdesigns on 2007-11-21
Ok.. yep. I mounted to the shares that the backend has setup and i can watch vids now. thx!

---

