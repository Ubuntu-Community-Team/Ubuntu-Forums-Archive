---
title: "Going back to autobuilds from Avenard repo"
date: 2010-10-27
forum: Mythbuntu
---

### Post by cedyathome on 2010-10-27
When I built my mythtv system, the avenard repos allowed me to use the latest nvidia drivers & vdpau for acceptable hd playback. I use the nvidia 8200 on the ASUS M3N78-EM motherboard.

Now, it seems like the autobuild supports the right nvidia drivers, so I want to move back to using it.

But, I don't know how to do this short of removing mythtv and reinstalling it. I have done a lot of tweaks to mythtv over the last 10 months without documenting them all, so I don't want to lose them.

Has anyone done this before and can point me in the right direction? Thank you.

---

### Post by tgm4883 on 2010-10-27
Any tweaks you have done should be kept in the database, so you shouldn't lose  them. Last I checked, there was a page on the avenard site that showed how to go back to auto-builds, but I haven't checked in a while.

---

### Post by cedyathome on 2010-11-02
Thanks tgm. I went through his blog and couldn't find any instructions. If anyone else has done this, would appreciate some help.

Otherwise, I think I'll just wait till I'm ready to move to ver .24

---

### Post by Nikas on 2010-11-12
I would also like to change from avenard to autobuilds.. any "news"? :)

I want 0.24.. NOW. ;)

---

### Post by kyfehr on 2010-11-14
Any luck on this yet?

I have been scouring the internets trying to figure out how to go back to Autobuilds - If I knew this would happen I wouldn't have made the change to Avenard.

He should really put a warning on the site.

---

### Post by Nikas on 2010-11-14
No luck here.

Do we need to backup the db, remove the packages and then reinstall the pagages from the autobuilds repo?

If that can be done.. what packages needs to be removed and so on? Do i need to move my recordings?

---

### Post by nickrout on 2010-11-14
what happens if you 

1. comment out the references to the avenard repos in /etc/apt/sources.list.d/

2. enable autobuilds and do an update & safe-upgrade

You shouldn't need to back up the database, as removing mythtv-database package does not touch the data. However, as always, backing it up before you do something major is always a good idea, just in case.

I don't believe that JYA lurks in this forum, but you will get a reply from him on the mailing list - in fact i think this has been discussed lately so search the archives :)

---

### Post by Nikas on 2010-11-14
> **nickrout said:**
> what happens if you.... 

Nothing. ;)

Found this: [http://www.gossamer-threads.com/lists/mythtv/users/459308](http://www.gossamer-threads.com/lists/mythtv/users/459308)

I am going to remove and reinstall all myth packages in a couple of hours. Ill post when i'm done.

---

### Post by Nikas on 2010-11-15
Purge and then install worked great!

---

### Post by nickrout on 2010-11-15
> **Nikas said:**
> Purge and then install worked great!

would be good to hear what exactly you purged.

ie exactly what commands you ran.

---

### Post by Nikas on 2010-11-15
> **nickrout said:**
> would be good to hear what exactly you purged.

ie exactly what commands you ran.

Remove the avenard repo and activate the auto-builds repo (sudo dpkg-reconfigure mythbuntu-repos)

sudo stop gdm
sudo apt-get purge mythtv*
sudo apt-get install mythtv*
sudo start gdm

Backed up my DB but no need to restore.

---

### Post by nickrout on 2010-11-15
Thanks, you might like to note that aptitude is a better alternative to apt-get.

---

### Post by Nikas on 2010-11-15
> **nickrout said:**
> Thanks, you might like to note that aptitude is a better alternative to apt-get.

Why? I'm learning. ;)

Having some problems now.. 
See this post: [http://ubuntuforums.org/showpost.php?p=10117731&postcount=253](http://ubuntuforums.org/showpost.php?p=10117731&postcount=253)

---

### Post by nickrout on 2010-11-16
> **Nikas said:**
> Why? I'm learning. ;)

Having some problems now.. 
See this post: [http://ubuntuforums.org/showpost.php?p=10117731&postcount=253](http://ubuntuforums.org/showpost.php?p=10117731&postcount=253)

[http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

---

### Post by cedyathome on 2010-11-16
Thank you! I had given up on seeing a reponse, so this made my day! I'll try it when I have a free day.

---

