---
title: "multiple tuners and hard drives"
date: 2008-03-05
forum: Mythbuntu
---

### Post by 4dognight on 2008-03-05
Is there a way to have each tuner store its live recordings on its own hard drive? If I had 3 tuners, and 3 drives, I thought it might be beneficial to have each tuner record to its own drive to avoid contention, espicailly if all 3 are actively recording. Espacially if its recording HD content.

---

### Post by newlinux on 2008-03-05
If all 3 tuners are on the same backend I don't think you can do this, at least not with mythtv .20.2 - It only lets you select one recording directory. But storage groups in mythtv .21 can help you with the problem you are trying to address... You can specify which storage group a recording will be recorded to, regardless of tuner. 

FWIW, I find my my drives are able to handle 3 HD recordings at once. I don't do this regularly (but I do have 2 HD programs recording at once regularly, while watching an HD program off the same hard drive at the same time).

---

### Post by 4dognight on 2008-03-05
The reason I ask is cause I still get those 'prebuffering pause' msgs in my frontend log. I have noticed that when I am watching live tv and I get a hiccup, in audio and video, I  see these prebuffering pause msgs. I also have another terminal open, running vmstat. Which shows a iowait at the same time i get the prebuffering pause msg. So I am thinking there is contention for the hard drive.

I did recall reading somewhere , someone mentioned to put the database on its own drive to prevent HD contention, so I figured maybe best to separate the tuners recordings also. I suppose I could try making this box a secondary backend, thus eliminating the DB on this box.

It might also be worth mentioning that I have 2 160GB SATA drives in a RAID stripe. I doubt this would be a contributing factor, but who knows.  I thought maybe putting in another drive and splitting thenm up between the tuners with no RAID. But that would require me to rebuild from scratch.

---

### Post by newlinux on 2008-03-05
Sounds like you might be on to your problem... My 2 backends with tuners (3 on one, 4 on the other) use separate hard drives for recordings than they do for the OS. My master backend doesn't have tuners so everything is on one drive (where the DB is stored). So maybe that helps me. All recording drives are SATA drives, but no RAID for me.

In any event, you can do close to what you want with storage groups by spreading the recordings evenly across the different storage groups pointing to different drives.

---

### Post by 4dognight on 2008-03-05
Looks like more tinkering  to do. :)

---

### Post by newlinux on 2008-03-05
All the tinkering required to get all my machines just right (for their myth and non myth usage) is why myth related machines are still edgy and Feisty :). It's just how I like it (all the various cron jobs, fileserver, webserver, myth settings, video settings, etc.) and I don't want to go through all that again on 3 machines, even though I backup most of this stuff.

Now, the question for me is, when do I finally upgrade? Right now I'm leaning towards not upgrading for .21 because it doesn't add enough stuff I want - and my family uses these myth systems everyday. But then again, I don't want to get too far behind. The thought of putting my machines on an LTS release cycle sounds good... But I'll probably leave them alone. Everything is working great right now. My laptop stays up to date though and will be going to 8.04.

Sorry - off topic, just random thoughts...

---

