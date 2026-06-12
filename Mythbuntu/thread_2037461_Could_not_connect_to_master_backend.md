---
title: "Could not connect to master backend"
date: 2012-08-04
forum: Mythbuntu
---

### Post by Dukenukemx on 2012-08-04
I've installed Mint, MythBuntu, and now Ubuntu 12.04 with MythTV installed and I always get this error when I start the frontend.  These are clean installs with nothing changed but the capture card setup.  Then this starts happening.  

What could I be doing wrong?

---

### Post by klc5555 on 2012-08-04
> **Dukenukemx said:**
> I've installed Mint, MythBuntu, and now Ubuntu 12.04 with MythTV installed and I always get this error when I start the frontend.  These are clean installs with nothing changed but the capture card setup.  Then this starts happening.  

What could I be doing wrong?

Have you configured the backend (with mythtv-setup)?

If you've configured it, is mythbackend started and running before you attempt to connect the frontend to it?

Have you checked out the mythtv manual for configuration help at [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index)

---

### Post by Dukenukemx on 2012-08-04
I ran the backend setup which allowed me to setup the TV Tuner.  I don't know if that's what you're talking about?  Everytime I exit the setup it asks me if I wanna start up the backend, and I say yes.  When I check the status though, the service is stopped. 

I tried setting the IP to 127.0.0.1 in setup and then tried giving the machine a static IP and using that instead.  

I'll try removing the capture card, since that start this whole mess.

---

### Post by nickrout on 2012-08-04
> **Dukenukemx said:**
> I ran the backend setup which allowed me to setup the TV Tuner.  I don't know if that's what you're talking about?  Everytime I exit the setup it asks me if I wanna start up the backend, and I say yes.  When I check the status though, the service is stopped. 

I tried setting the IP to 127.0.0.1 in setup and then tried giving the machine a static IP and using that instead.  

I'll try removing the capture card, since that start this whole mess.

Did you complete all the steps in mythtv-setup? capture card, video source, bind source to capture card, scan for channels?

What does your mythbackend log tell you? We cannot read your computer logs from here, you need to look at them and post what you see.

---

### Post by Dukenukemx on 2012-08-04
> **nickrout said:**
> Did you complete all the steps in mythtv-setup? capture card, video source, bind source to capture card, scan for channels?

What does your mythbackend log tell you? We cannot read your computer logs from here, you need to look at them and post what you see.

Thanks, I just did those things and now it works.  I didn't think I needed to setup the rest to get it to stop giving me this error.

---

