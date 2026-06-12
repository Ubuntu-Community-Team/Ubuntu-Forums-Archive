---
title: "Automatically update MythVideo database"
date: 2007-11-22
forum: Mythbuntu
---

### Post by eqqfooyoung on 2007-11-22
I have liferea setup to automatically download video podcasts to my MythVideo directory.  In order to see the new videos that have been downloaded, I must go to Utilities / Setup > Video Manager 

The video database is then updated and my videos are now listed in Media Library > Watch Videos

Does anyone know how I can automatically update this database?

---

### Post by newlinux on 2007-11-22
If you don't feel it necessary to add any metadata about your video files you don't have to use the video manager to scan them in. There  is a setting in the video settings menu in the frontend that lets you browse files that haven't  been scanned. Turn the appropriate one on for teh view you use.

---

### Post by mthaddon on 2008-03-21
I have a similar issue (I would like to be able to run the video DB updater programmatically). Browsing files not added to the DB is okay, but it would be better to be able to add them to the DB. The reason is that I have a separate script that can create thumbnails of videos that don't have a cover, and this makes them a lot easier to browse.

---

### Post by freymann on 2008-03-22
> **eqqfooyoung said:**
> I have liferea setup to automatically download video podcasts to my MythVideo directory.  In order to see the new videos that have been downloaded, I must go to Utilities / Setup > Video Manager 

The video database is then updated and my videos are now listed in Media Library > Watch Videos

Does anyone know how I can automatically update this database?

 While I was searching around looking for info on something else, I ran across this post:

[http://www.mythtvtalk.com/forum/viewtopic.php?t=7077]("http://www.mythtvtalk.com/forum/viewtopic.php?t=7077")

which contains info on doing what you want and a link to download the script(s). Have a look.

---

### Post by mthaddon on 2008-03-23
> **freymann said:**
> While I was searching around looking for info on something else, I ran across this post:

[http://www.mythtvtalk.com/forum/viewtopic.php?t=7077]("http://www.mythtvtalk.com/forum/viewtopic.php?t=7077")

which contains info on doing what you want and a link to download the script(s). Have a look.

Looks promising, but the script it links to no longer seems to exist. Thanks in any case.

Tom

---

### Post by tgm4883 on 2008-03-23
> **mthaddon said:**
> Looks promising, but the script it links to no longer seems to exist. Thanks in any case.

Tom

3 minutes of reading/following links in the linked post led me to the script.  It still exists, you just have to follow some directions.

---

### Post by majoridiot on 2008-03-24
> **tgm4883 said:**
> 3 minutes of reading/following links in the linked post led me to the script.  It still exists, you just have to follow some directions.

it would be helpful for others if you posted the correct current link ;)

---

### Post by tgm4883 on 2008-03-25
> **majoridiot said:**
> it would be helpful for others if you posted the correct current link ;)

Sorry, was actually like 30 seconds

[http://thepisanis.com/files/imdbupdater.tar.gz](http://thepisanis.com/files/imdbupdater.tar.gz)

:EDIT:

Forgot to add that this seems to be the permanent link, according to the documentation

---

### Post by ed3120 on 2008-06-12
Go to:

Utilities/Setup -> Setup -> Media Settings -> Videos Settings -> General Settings 

Check the boxes for:

Video Browser browses files
Video Gallery browses files
Video List browses files

---

