---
title: "Streaming to PS3"
date: 2008-08-07
forum: Multimedia Software
---

### Post by banzairx7 on 2008-08-07
Im trying to setup streaming of video to my PS3. I installed mediatomb. I tired to go through the tutorials on the board here to get it working. I get errors every step of the way. It wont let me edit the config file. A few of the command lines dont seem to work either. 

I can see mediatomb on my ps3. For some reason its there twice. When I go into on the ps3 it says there are no files. I think I added the correct directories to mediatomb. To be honest though the inerface for mediatomb is pretty bad. You can't tell if you've actually done anything.

I wish they had tversity for linux. Ive used that for a while and am happy with it for the most part.

I am a complete nube on Linux. I just installed it last night. Ive got almost everything working to my liking except this. Please try to keep the cryptic command line stuff to a minimum. I have no idea what any of it means at this point. Not trying to be rude, just trying to say Im going to have a tough time comprehending what your telling me.

---

### Post by pormogo on 2008-08-07
I've had no issues getting mt to read my files and serve them to my PS3. If you're seeing it twice that most likely means it's started twice. There is an init script for mt now (there wasn't before) so it starts at boot. If you ran it from the terminal a second time then you have 2 instances of it running.

$pgreg -fl media

will show you how many instances of tomb are running. In order for your files to be read the user running mediatomb must have r permissions to all of the files. The interface is passable but not excellent. Click the add button on the filesystem side and it should add to the database. Select database to view all of the items currently added into the database.

---

### Post by banzairx7 on 2008-08-07
That command line doesnt work for me. I just get-

bash: -fl: command not found

---

### Post by Neezer on 2009-10-11
That is the same error I am getting too....did you end up figuring out what the problem was?

---

