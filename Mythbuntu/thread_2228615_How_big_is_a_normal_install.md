---
title: "How big is a normal install?"
date: 2014-06-08
forum: Mythbuntu
---

### Post by klaus8 on 2014-06-08
Hi there,
got 90 GB for the Mythbuntu install and after instal and use 4 weeks, it seems I only got 45 GB free for recording stuff? I have deleted all recordings and emptied the trash can ofcouse, but seems to me to be a rather big install for a linux distro? So what should it be and where else to delete?

Klaus

---

### Post by LastDino on 2014-06-08
I really don't think there is any Linux Distro which takes that much amount of HD.

Normally, it is below 7GB min, generally we suggest people to keep ''/'' of 20-24GB, which is quite sufficient if you've separate /home partition to save everything.

I think disk space is consumed by something else.

---

### Post by ajgreeny on 2014-06-08
Run the command ```
sudo su
``` in terminal, which will get you to a root terminal, then run command ```
du -d1 -ha
``` which will show you the space taken up by all the main directories in your system, using human readable sizes.  That should give you some clues about where all your space is being used; look at /var in particular as log files can sometimes generate in a logarithmic mode, taking space at an alarming rate if things are going wrong.

---

### Post by dannyboy79 on 2014-06-10
i'd bet you're hit with some bug which is creating gigantic log files. how large is your .xsession-errors file located within your /home/user/ folder? and like ajgreeny suggested, check your /var/log/ directories for any large log files.

to give you perspective, my mythbuntu / partition is 20GB and it's only using 14GB right now and I have a ton of other stuff besides just mythtv running on it.

---

### Post by tgm4883 on 2014-06-12
> **klaus8 said:**
> Hi there,
got 90 GB for the Mythbuntu install and after instal and use 4 weeks, it seems I only got 45 GB free for recording stuff? I have deleted all recordings and emptied the trash can ofcouse, but seems to me to be a rather big install for a linux distro? So what should it be and where else to delete?

Klaus

How did you delete the recordings? Did you delete them in mythfrontend or on the filesystem?

---

### Post by klaus8 on 2015-01-06
Dear All, thanks for the support! I have made a new install and the whole linux one the entier HD. I know that is not the best if something happens, but it solve the other issue for now and while I play around wit MythTV it is fine :-)

> [COLOR=#DD4814][tgm4883]("http://ubuntuforums.org/member.php?u=191664"), [/COLOR][COLOR=#000000]How did you delete the recordings? Did you delete them in mythfrontend or on the filesystem?[/COLOR] I did both, and also tried though XBMC/Kodi.......so what is the best way so to speak...........mtyhtv frontend I assume now?

---

### Post by kpatz on 2015-01-06
I installed Mythbuntu 14.04 last weekend (fresh install replacing 10.04) and the root filesystem is about 8 GB used, including a bunch of stuff in /home that was brought over from the old install.  My media (recordings, music) are in a separate, larger partition.

Are your recordings in the same partition, or a different one?

---

### Post by tgm4883 on 2015-01-06
Yes the frontend is the best way to delete them. IIRC, by default they go into what is essentially a trash can in case you want to undelete them. They will automatically be deleted (expired) when mythtv needs additional space

---

### Post by hollywoodpete on 2015-01-06
> **tgm4883 said:**
> Yes the frontend is the best way to delete them. IIRC, by default they go into what is essentially a trash can in case you want to undelete them. They will automatically be deleted (expired) when mythtv needs additional space

Just to clairify,

Is it OK to delete with Kodi or Mythweb? It appears to work for meed now but I am a new user and would like to avoid a catasrophic melt down in a week or two. FWIW, I haven't really gotten the frontend working well and prefer Kodi anyway.

---

### Post by tgm4883 on 2015-01-06
> **hollywoodpete said:**
> Just to clairify,

Is it OK to delete with Kodi or Mythweb? It appears to work for meed now but I am a new user and would like to avoid a catasrophic melt down in a week or two. FWIW, I haven't really gotten the frontend working well and prefer Kodi anyway.

I don't use Kodi, so I can't comment on that. You can delete via mythweb though

---

### Post by wyliecoyoteuk on 2015-01-12
I run my / partition on an 8 Gb SSD. it is about half full.
swap, /var and /home are on a 1TB HDD.
/var is where Myth stores all the recordings, songs, videos, pictures etc.

---

