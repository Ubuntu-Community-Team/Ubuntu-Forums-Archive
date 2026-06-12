---
title: "HOWTO: automating metadata for mythvideo made easy"
date: 2008-10-05
forum: Mythbuntu
---

### Post by oobe-feisty on 2008-10-05
Imagine being able to update multiple videos that you just added to your mythvideo folder by typing one single command below are screenshots to demonstrate how cool this looks

all tv show info about each episode and screen shots added as pics for mythvideo plus all imdb movie searchs to 

that is what this howto covers and somthing i searched for a long time for before the authors of these 2 very nice scripts made them.

download these scripts

metacleanup-0.4.tar.gz at [http://www.fecitfacta.com/metacleanup-01-30-09.tar.gz](http://www.fecitfacta.com/metacleanup-01-30-09.tar.gz)

and [http://www.thepisanis.com/files/imdbupdater.tar.gz](http://www.thepisanis.com/files/imdbupdater.tar.gz) 


make a temp folder

mkdir ~/tmp/meta

cd ~/tmp/meta

unpack them in the ~/tmp/meta folder 

tar xvzf  metacleanup-0.4.tar.gz

tar xvzf imdbupdater.tar.gz


later on we will put them somewhere more permanent 


metacleanup requires modifying so open metacleanup.sh with you favourate text editor 

joe metacleanup.sh


you need to edit these parimters 

# Myth Database Name
DBNAME=mythconverg
# SQL Server Hostname (usually localhost)
SQLSERVER=localhost
# Myth DB User
DBUSER=mythtv
# Myth DB Password
DBPASSWORD=mythtv

# Where do your movies live? (Root MythVideo Directory)
MOVIEHOME=/movies
# Where do your posters live? (Mythvideo Poster Dir)
POSTERHOME=/home/mythtv/.mythtv/MythVideo

DBNAME should be fine as is 

SQLSERVER should be ok unless your on a remote frontend

DBUSER should be fine unless you changed it in which case you would already know about as you probably have needed to modify many things in the past

DBPASSWORD get you password from /etc/mythtv/mysql.txt


MOVIEHOME=/path/to/tveps  i keep my tveps in one folder and my movies in another i instruct metacleanup.sh to use tveps only here although for some reason it will update everything ../ anyway which im ok with

POSTERHOME=/home/oobe/.mythtv/MythVideo path to movie posters


quick shortcut 

here is a small script that i use instead of having to remember all the syntax for imdbupdater ( you will need to edit cd /path/to/script/folder and replace yourpassword with your mythtv password from mysql.txt)

```

#!/bin/bash

cd /path/to/script/folder

cd imdbupdater

## this line searchs for any files that are not in the mythvideo database then adds them (this way you do not have to go to utility's / setup in mythfrontend and rescan your videos)  
##you will need to edit the path
 ./imdb-bulk-update.pl  -Host localhost -User mythtv -Password yourpassword -Fileup -Folder /data/Documents/media/vids 

#runs metacleanup.sh it does not require any paremeter's
cd ..
./metacleanup.sh

#adds any movies it finds in you movies folder you will need to edit the path you will be prompted if more that one title exists if it fails to find movie you will not be prompted
cd imdbupdater
 ./imdb-bulk-update.pl -N -Host localhost -User mythtv -Password yourpassword -Fileup -Folder /data/Documents/media/vids/moviez

# this line does the same as above however if you missed out on any that it could not find it will prompt you for a imdb number

./imdb-bulk-update.pl -N -Host localhost -User mythtv -Password yourpassword -Manual -Fileup -Folder /data/Documents/media/vids/moviez

```


save it to the same folder 

UPDATE: this now works without prompting very well thanks to and update to the metacleanup.sh

as you can see if you read the comments this will not work without prompting i.e if you want to add it as a cronjob it will not work 

you can simply add this line to a text file and make it executable then set it to run as a cronjob 

 ./imdb-bulk-update.pl  -Host localhost -User mythtv -Password yourpassword -Fileup -Folder /data/Documents/media/vids 


i dont feel the need to do this but i have seen people want to add this feature to mythtv


once you test it all and your happy move the folder to somewhere permanent might i suggest /usr/share/mythtv/mythvideo/scripts

this way you will have /usr/share/mythtv/mythvideo/scripts/meta


you can now copy your saved script to  /usr/local/bin/myscript i called mine auto for some reason


now all you have to do is type myscripts and it will run all the above commands you can do the same if you choose to make a cronjob as mentioned above.

---

### Post by Baka no Kami on 2008-10-06
Thanks for this.  It's a little easier than searching for titles one at a time through the front end for those of us with large video collections.

---

### Post by Caps18 on 2008-10-06
Thanks for this.  I will have to try this out.  

But, I'm not expecting much.  I'm still unsure on how it all works, and if it is possible to manually edit records that can't be found on IMDB.

This is one of those backend tasks that I would think Mythbuntu/MythTV would make easier and automatic.  If I move a movie file into my MythVideo directory, the next time I select Watch Videos, it should automatically look for new files and download the new metadata.

---

### Post by oobe-feisty on 2008-10-06
I probably should of explained better what we hope to achieve by following the steps i wrote this is aimed at people who have a lot of stuff in mythvideo like tv eps and movies plus things that dont fit into that category and cant retrieve relavant meta data like sporting events and porn :P 


what metacleanup does is retrieve info for all you tveps provided they are named in a sensible fashion 1x07 or s01e07 and add's the episode info plus make's a screenshot that is displayed in the mythvideo using mplayer i forgot to mention i modified mine to make 16:9 fit properly using a post i found in this [thread ]("http://www.mythtvtalk.com/forum/viewtopic.php?t=7077&postdays=0&postorder=asc&start=20") look at the first post in that thread for a more detailed explanation from the author and as for imdbupdater it simple updates your movies using imdb.pl but you don't have to mess around in mythfrontend to use it i find this method the most convienant as i use the same method i put in the tutorial turning all the scripts into one simple command then executing it when i add some videos 


example i just dload a torrent of an entire tv series that has 13 eps in it i move the episode folder into my /vids/TVeps folder which mythvideo has acces to the i type auto from console and all eps are added i get prompted for each ep though you have to say y to each episode add it to database then all my eps get the episode name and screenshot plus a description and if i have added a few movies to my movie folder they automatically get added and if imdb.pl cant find it it will then prompt me for the imdb number stuff that isnt tveps will be automatically added to with screenshot's only the only way i know to add metadata manually for those things is from the front end in setup / utility's



**EDIT BTW: **i attached the imdbupdater 1.13 as 1.14 seems not to work with this tutorial and i cant find a direct link

---

### Post by Baka no Kami on 2008-10-06
> **Caps18 said:**
> Thanks for this.  I will have to try this out.  

But, I'm not expecting much.  I'm still unsure on how it all works, and if it is possible to manually edit records that can't be found on IMDB.

This is one of those backend tasks that I would think Mythbuntu/MythTV would make easier and automatic.  If I move a movie file into my MythVideo directory, the next time I select Watch Videos, it should automatically look for new files and download the new metadata.

I'm not in front of my system right now to check, but I thought there were mythvideo options to make the views browse your folders rather than only listing scanned video.

--------------

I don't use mplayer on my system I use VLC and [this guy]("http://www.kryogenix.org/days/2008/02/11/video-thumbnails-for-mythtv") has a script for making the thumbnails with totem-video-thumbnailer instead of mplayer.  Again, I'm not at my system right now so I haven't tried it and don't know if it needs any modification to work with the metacleanup script.

---

### Post by oobe-feisty on 2008-10-06
that is correct

BTW i looked at that script and its a good option if you can't use mplayer and you dont really care about properly updating your metadata but do not under estimate the metacleanup script it gets all the tv ep info as well it doesn't just make screenshots

---

### Post by rswing on 2008-11-02
Thank you so much for your guide...it was very helpful. I have one question. It seems that a lot of my TV episodes were not updated. I currently have them organized like this...

/Seinfeld/Season 1/01 - Pilot.avi

When the script runs, it seems to only search "01 - Pilot.avi". Is there any way to have it search using the names of the above directories? Or is there a way that I can rename my files to have better results?

Secondly, is there a way to use this script to apply artwork manually? Like if I would like to apply artwork to an entire directory?

---

### Post by toorima on 2008-11-02
Organize your shows like
/Seinfeld/Season 1/Seinfeld.1x01 - Pilot.avi
and it will work fine

edit: sorry missed the second question, you can put an image like a dvd cover in the directory, must be called folder.jpg

---

### Post by oobe-feisty on 2008-11-03
> **toorima said:**
> Organize your shows like
/Seinfeld/Season 1/Seinfeld.1x01 - Pilot.avi
and it will work fine

edit: sorry missed the second question, you can put an image like a dvd cover in the directory, must be called folder.jpg

thank you for posting this reply that is correct and i how i use it i didnt include this tip as i made an assumption people already have a structure similar

---

### Post by EasyRiderOnTheStorm on 2008-12-14
> **rswing said:**
> When the script runs, it seems to only search "01 - Pilot.avi". Is there any way to have it search using the names of the above directories? Or is there a way that I can rename my files to have better results?

Secondly, is there a way to use this script to apply artwork manually? Like if I would like to apply artwork to an entire directory?

I don't wish to belittle the original poster's great how-to or hijack the thread, but for anybody interested, there is a script that does pretty much the same thing: looks over your collection, tries to figure out your notation system for TV series, updates what it should from either TVRage or IMDB, downloads covers for videos and their folders, and needs no more attention than unpacking and running. It's called Mythvideo-scanner, and I'm pretty happy with how it works so far. Look for it [[here]("http://mysettopbox.tv/phpBB2/viewtopic.php?t=19082")].

---

