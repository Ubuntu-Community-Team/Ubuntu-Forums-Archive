---
title: "Rip DVD on MythFrontend, transcode on Mythbackend - possible ?"
date: 2010-05-20
forum: Mythbuntu
---

### Post by picbits on 2010-05-20
Heres the setup - 10.04 on both frontend and backend. Myth 0.23 on both

Backend = Quad core Opteron server with 3Tb storage and 4Gb ram
Frontend = Acer Revo 3600 with a piece of lettuce for a processor and a 160gb Hard drive.

I can rip a DVD and transcode it to good quality on the Revo but it has taken 5 hours so far and still hasn't finished. Is there any way to rip on the Revo but queue the job to transcode/store the video on the main backend ?

It would also be nice to queue the job off the Revo frontend so I can continue using it to watch films while the server backend gets on with the transcoding. Also would be good to be able to shut down the frontend but keep the backend transcoding dvd jobs.

Any ideas ?

Ta
Dom

---

### Post by williammanda on 2010-05-20
Any reason you can't put a frontend on the backend computer and rip your dvds from that unit?

---

### Post by picbits on 2010-05-21
The server (backend) is in a pretty inaccessible place running headless so I need to SSH or VNC over to it if I need to run any maintenance etc on it. Its also on its side so insertion of a DVD into its built in drive would be impossible

It would be possible to put an external USB DVD drive on it but then I've got to train the wife how to SSH into it, run VNC Server, log onto it, fire up MythFrontend on it, rip the DVD and then closing it all and logging back off.

The thought of giving my wife access to my mail/web/music/webshop/tv server makes me somewhat nervous :P

---

### Post by JMcFly on 2010-05-21
Basically you want a script to rip an ISO, transfer it from the front end to the backend, execute transcode and rescan video folder for changes?
A way to rip multiple ISOs (since they take ~20 minutes with my setup) and save them as jobs in the queue to transcode later would be good, I can't figure out a way to do it inside Mythvideo (even though it gives status as 'Job 1 of 1').
 
I've tried ripping/transcoding from a secondary backend (dual-core 2.4ghz vs master's 2.4ghz single core), it sits forever with the transcode status bar at 50% so I'm not sure if its trying to send the job to the primary backend...

---

