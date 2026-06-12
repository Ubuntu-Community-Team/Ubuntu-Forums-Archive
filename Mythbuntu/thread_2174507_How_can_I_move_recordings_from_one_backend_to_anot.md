---
title: "How can I move recordings from one backend to another at a different location?"
date: 2013-09-14
forum: Mythbuntu
---

### Post by bullwinkle2 on 2013-09-14
Here is the situation:  Two separate Mythbuntu installs at two separate locations that are not connected in any way (neither is slaved to the other), except both have Internet access.  In case it matters, these are used only to record shows from HDHomeRun dual devices and to serve as backends at each location.

If I schedule a show to record at one location but want to watch it at the other, how can I do that?  My preference would be to have it transcode the show to save bandwidth (without losing too much picture quality), then put it in a specific directory where another process (a cron job) will take care of moving it.  Then when it is placed on the other backend, I want it to be able to make the recording available to the frontends on that network.

So, there are probably three parts to this question:

- How do I make backend #1 save a copy of the transcoded video file to a specific directory on the system (doesn't need to be a directory of my choice, I just need to know where it is).

- When I bring the file over to backend #2, how do I make it available as a recording that can be viewed just as if it had been originally recorded on that system?

- When I'm at location 2, what's the easiest way to be able to modify the recording schedule on backend #1?

My assumption is that I can set up SSH access (on an alternate port) between the two machines, and use that to transfer files, but I haven't figured out the part about the schedule yet.  I know about the web interface, just don't want to expose it to the entire Internet for obvious reasons.

If these are frequently asked questions, please feel free to point me to a page or thread that gives the answers.  Thank you.

---

### Post by bullwinkle2 on 2013-09-17
Nobody knows if this is possible?  EDIT: I just figured out that the recordings are stored in /var/lib/mythtv/recordings (unless that is changed in the Default storage group), so I would guess that you could move the recordings from that directory on the backend of one system to the backend of another, but I wonder if the system receiving the files would recognize them, or if there is metadata stored elsewhere that should also be moved (if that is even possible)?

---

### Post by newlinux on 2013-09-18
I think you would have to insert the records from one mythtv database to the target database for mythtv to recognize them in the recordings screen. I'd think you'd need to the records from a few different tables (record, recorded, oldrecord, etc.). I think there used to be a script that let you import recordings one at a time (providing the metadata) but I believe that has been deprecated. 

Alternatively you could import the recordings into mythvideo. Before moving them you could use mythlink to give them names that can be recognized for the import of metadata by mythtvideo

[http://www.mythtv.org/wiki/Mythlink.pl](http://www.mythtv.org/wiki/Mythlink.pl)

---

### Post by bullwinkle2 on 2013-09-19
Thank you.  mythlink.pl looks like exactly what I need to get started.

---

