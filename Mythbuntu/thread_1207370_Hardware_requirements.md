---
title: "Hardware requirements"
date: 2009-07-08
forum: Mythbuntu
---

### Post by timbim on 2009-07-08
I'm thinking about building a mythbuntu backend system, using an Xbox classic as the frontend, to keep costs down.  That will easily be addable to my wired network, currently at 100mbit.  The tuner I will be basing this around is [this]("http://www.ebuyer.com/product/113946"), with the option then to upgrade with another of the same or a satellite card to get HD content from freesat.

Hardware-wise, I was looking down the lines of a fast core2duo, 4GB RAM, no GFX for backend, and at first two 1TB HDD's, with the ability to add more as and when.  I would also be running the system as a home fileserver and a very small lamp server for testing php and sql features of websites under construction.

Will that tuner be able to record two programs at once and still serve one of them to view on the frontend, or indeed another one of the recorded channels at the same time as recording two others?  Also, is the hardware up to the job, and futureproof enough to handle HD, or another two tuners without the need to upgrade much (other than maybe a bit more RAM, and obviously a new frontend if I want to go HD)?

Many thanks
Tim

---

### Post by bawilson2 on 2009-07-10
I'd say you'd have no problem.  I'm currently running an E6850 processor with 8GB of ram and a 750 GB hard drive for recordings.  I have it as my main desktop and currently have about four HD tuners hooked up to it.  I haven't had any problems with any combination of watching, recording, and using the computer.

---

### Post by timbim on 2009-07-10
Thanks.  One other question, does myth support time slipping, so starting to watch a program while it it still recording?

Got an old Xbox today to test the whole backend frontend connection, but I'm struggling to get my generic usb stick tuner to work.

---

### Post by bawilson2 on 2009-07-10
Yes it does great with time slipping.  I use that feature a lot with sporting events so I can skip the timeouts or halftime in addition to the commercials.

---

### Post by timbim on 2009-07-10
Great.  Makes much more sense to go with a backend and separate frontend when an xbox costs £20, but a case that will be quiet enough to use as a front/back combo, you can pay over £200.  Is it possible to play and rip DVD's to the backend from the front ends dvd drive?  Also, what sort of remote would you suggest.

---

### Post by bawilson2 on 2009-07-10
So what I've done is using MythVideo you can view the videos that you have stored on the backend.  I do use the frontend dvd player all the time to view movies.  I haven't tried ripping a dvd from the frontend to be stored on the backend but I'm sure it is possible even if you just setup some NFS mount.  

I use a Pinnacle MCE remote and it works out pretty well.  I got a great deal on it so it was worth putting in a little bit extra setup work.

---

### Post by uncle hammy on 2009-07-10
I think you're going to have an issue with the XBox frontend if your recordings are HD.  I think you'll find that the classic XBox doesn't have anywhere near the juice to play an HD stream.

---

### Post by bawilson2 on 2009-07-10
> **timbim said:**
>   **obviously a new frontend if I want to go HD**


Pretty sure he understood that part....

You could record things in HD and transcode them to something smaller without a problem in order to be able to use a xbox frontend.

---

### Post by uncle hammy on 2009-07-10
missed that part, somehow.

---

### Post by timbim on 2009-07-11
Thanks.  I'm about to start installing xebian basic on said xbox, next step will be to convert front panel ports to USB ports.

---

