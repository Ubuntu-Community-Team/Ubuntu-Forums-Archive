---
title: "Moving mythtv data from desktop to server w/ raid 5 help"
date: 2012-10-24
forum: Mythbuntu
---

### Post by grunge09 on 2012-10-24
I have a Ubuntu Desktop edition with mythtv backend and frontend installed on a 2tb drive.  All is well but would like to change purpose of current system to include a samba file server and RAID 5 setup with multiple 2tb drives.  

PC is:

AMD 965 4x core 3.4GHZ CPU
2 GB RAM (gonna be 4gb soon)
2tb sata HD
DVD ROM Drive
Gigabit Nic
Nvidia 210 Video card with HDMI out to 37" LCD HDTV

I would install the 12.04 Server OS on a 60GB SSD Drive, and create RAID 5 (using 4 2tb green power drives) with MLADM (probably spelled that wrong) during install.  Would have Boot as SSD and everything else on RAID.  Then setup Samba, already done that on another box to test on.  

I am guessing to make things easier I would need to install ubuntu-desktop on server to then install Mythtv.  

I can copy the mythtv data folders to he new location on the RAID5, but the big question is ...

How do I get the new install to see all the old programs.  is there a way to do this?

---

### Post by Rotak on 2012-10-24
It can be done using nuvexport, using the SQL export. That will copy/backup the video file + the related info from the database as an SQL file.

I don't know if there is a batch job to export all recordings at once, or if you need to do it one by one.


:idea: An alternative is to backup the whole mythconverg database along with /home/mythtv and /var/lib/mythtv. But the restore process is a little bit more tricky.

---

### Post by tgm4883 on 2012-10-24
> **Rotak said:**
> It can be done using nuvexport, using the SQL export. That will copy/backup the video file + the related info from the database as an SQL file.

I don't know if there is a batch job to export all recordings at once, or if you need to do it one by one.


:idea: An alternative is to backup the whole mythconverg database along with /home/mythtv and /var/lib/mythtv. But the restore process is a little bit more tricky.

Um, the alternative solution of yours is (IMO) the better one. It would be far faster to backup the recording directory and database and then restore it. I'm unsure what you mean when you say it's "tricky" to do the restore.

---

### Post by Rotak on 2012-10-24
@tgm4883

Ok, what comes to mind first.... You need to do the following tasks after restoring on the new system:

* Update directories in myth backend setup (depending on where the new raid-array is mounted).
* Do not restore mysql.txt and config.xml in /home/mythtv

Maybe there are other things to keep an eye on. That's what I meant with tricky. :D

---

### Post by nickrout on 2012-10-24
> **Rotak said:**
> @tgm4883

Ok, what comes to mind first.... You need to do the following tasks after restoring on the new system:

* Update directories in myth backend setup (depending on where the new raid-array is mounted).
* Do not restore mysql.txt and config.xml in /home/mythtv

Maybe there are other things to keep an eye on. That's what I meant with tricky. :DNone of that is tricky. It is in fact the right way to do it.

---

### Post by nainsurvolte on 2012-12-26
Hi, I am in a somehow similar situation.

All my recording are spanned over 2 drives, a 1TB and a the rest of the 250 GB OS drive as a security  in case I run out of space on the other one.

I am in the process of upgrading the server to get 4x2TB like the grunge09 but not necessarily in Raid 5 configuration. The configuration I will use is still to determine and I will ask opinion in another forum.

As for this one, I want to move all the recordings from the exiting drives to the new place (to be configured soon). 

Reading the different solution let me puzzled. I know a bit about Linux but the answers are incomplete for me. Is there a wiki, a sticky or another thread I have not found that explains the details? I have already done a Mythconverge backup in the past to go from 0.24 to 0.25, but that only backed up the database entries.

Thanks,

---

### Post by Zorbitz on 2012-12-29
For what it's worth, I just recently moved all my recordings / music / videos to a NAS. Somewhere, sometime, I read that recordings can be moved freely among defined storage groups, so what I did was simply

- stop the backend
- move the recordings to new location
- enter backend config to remove old and set up new storage groups
- restart backend
- launch frontend and set up new directories for music / videos

All my recordings are working just as before the move.

---

### Post by nainsurvolte on 2013-01-02
Thanks, I`ll test it the minute I can manage to get some space to work that out. I am pretty sure it will work since this is also the answer I found in another thread on another forum about Mythtv.

---

