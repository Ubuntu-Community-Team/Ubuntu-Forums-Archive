---
title: "Come test mythnettv and the new GUI for it"
date: 2008-08-26
forum: Mythbuntu
---

### Post by tgm4883 on 2008-08-26
MythNetTV has been packaged and a GUI app has been written for it.  Come test it out by grabbing the package for hardy or intrepid.

MythNetTV is a Video RSS Aggregator.  It will allow you to subscribe to video podcasts, download, and import them into your recordings directory and they will show up with the rest of your recorded content.  MythNetTV's homepage is [http://www.stillhq.com/mythtv/mythnettv/]("http://www.stillhq.com/mythtv/mythnettv/").

If you have added the ppa as a repo, then you should just be able to apt-get update then apt-get upgrade (or just apt-get install 'packagename', that will upgrade only that package and its dependencies).  The repo can be found here [http://launchpad.net/~mythbuntu-testing/+archive](http://launchpad.net/~mythbuntu-testing/+archive)

---

### Post by volkswagner on 2008-08-26
What is it, or where can I find information?  Is this a replacement for mythweb?

---

### Post by tgm4883 on 2008-08-26
Sorry, I've edited the first post for better clarification

---

### Post by tgm4883 on 2008-08-28
In an effort to consolidate testing software, a Mythbuntu-testing PPA has been formed.  This PPA will contain software that is targeted for the next release, but should also backport it to the current release (it also will be software not in the current release repos)

The new PPA is located here
[http://launchpad.net/~mythbuntu-testing/+archive](http://launchpad.net/~mythbuntu-testing/+archive)


Sorry for the confusion.

---

### Post by IamHungry on 2008-09-09
I am really excited about this.  I have been using miro to download stuff, but then have to go back and delete by hand.  I have installed the PPA but am getting "You need to create the configured data directory at "data"".

I am having a little trouble figuring out exactly where my problem is.  Could you point me in the right direction.

Thanks,  again very exciting stuff you are doing here.  this is the future of television.

---

### Post by tgm4883 on 2008-09-09
> **IamHungry said:**
> I am really excited about this.  I have been using miro to download stuff, but then have to go back and delete by hand.  I have installed the PPA but am getting "You need to create the configured data directory at "data"".

I am having a little trouble figuring out exactly where my problem is.  Could you point me in the right direction.

Thanks,  again very exciting stuff you are doing here.  this is the future of television.

Hmm, thats not supposed to happen.  Did you install it for i386 or amd64?

---

### Post by Disparu on 2008-09-09
unless the installer creates the "data" dir in /home/(user) automatically you need to do it.

I got it installed, but its seems flakey.
I can't get update now to work and it won't remove subscriptions when i use unsubscribe.

---

### Post by tgm4883 on 2008-09-09
> **Disparu said:**
> unless the installer creates the "data" dir in /home/(user) automatically you need to do it.

I got it installed, but its seems flakey.
I can't get update now to work and it won't remove subscriptions when i use unsubscribe.

The data directory should be created for you (in /var/lib/mythtv/mythnettv).

Subscriptions are not removed during unsubscribe, but are marked as inactive.  There is a bug where the inactive shows aren't removed from the todownload list, but there is a fix coming for that.

Update now updates the list of shows to be downloaded, but the downloading doesn't actually take place until the cron job is run (that is, if you set the daily cron job).


What version of mythnettv-gui are you running?

---

### Post by Disparu on 2008-09-10
Concerning the data dir: I was receiving the "you need to create the 'data' directory error until i made one myself, but i made it in /home/(user)

how do i schedule when the cron jobs run?

---

### Post by tgm4883 on 2008-09-10
> **Disparu said:**
> Concerning the data dir: I was receiving the "you need to create the 'data' directory error until i made one myself, but i made it in /home/(user)

how do i schedule when the cron jobs run?

You click the "Set Update Job" button.  I just realized that sounds funny and will probably rename it to "Set Hourly Download".  The cron job will download 1 show from your list every hour.

Alternatively, you can set the cron job manually, although it is unsupported.  If you look at /usr/share/mythnettv-gui/mythnettv.cron you will see what the cron job does.  Depending on the version of mythnettv-gui you have, it might be set to download 1 show or 2 shows.  The gui copies that file into /etc/cron.hourly/  

what is the output of "dpkg -l mythnettv"?

---

### Post by Disparu on 2008-09-10
> **tgm4883 said:**
> You click the "Set Update Job" button.  I just realized that sounds funny and will probably rename it to "Set Hourly Download".  The cron job will download 1 show from your list every hour.

Alternatively, you can set the cron job manually, although it is unsupported.  If you look at /usr/share/mythnettv-gui/mythnettv.cron you will see what the cron job does.  Depending on the version of mythnettv-gui you have, it might be set to download 1 show or 2 shows.  The gui copies that file into /etc/cron.hourly/  

what is the output of "dpkg -l mythnettv"?

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythnettv      6~svn138-0ubun Plugin to download RSS video feeds

the data dir problem def exists until i create a data dir in /home/(user)

is there anyway to manually purge the inactive jobs? once they become inactive and you want to add the same url it never becomes active again

i installed the latest gui and mythnettv and the gui no longer loads. i reverted back to 138 and bzr12 from 140 and bzr13

---

### Post by tgm4883 on 2008-09-11
> **Disparu said:**
> Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythnettv      6~svn138-0ubun Plugin to download RSS video feeds

the data dir problem def exists until i create a data dir in /home/(user)

is there anyway to manually purge the inactive jobs? once they become inactive and you want to add the same url it never becomes active again

i installed the latest gui and mythnettv and the gui no longer loads. i reverted back to 138 and bzr12 from 140 and bzr13

Sorry about that bug I introduced.  I just pushed a change for that.  Should be bzr14 for -gui and bzr140 for mythnettv.

I'm not sure there currently is a way to reactivate subscriptions.  I'll push that question upstream and see if we can't get that straightened out.

---

### Post by tgm4883 on 2008-09-12
> **tgm4883 said:**
> Sorry about that bug I introduced.  I just pushed a change for that.  Should be bzr14 for -gui and bzr140 for mythnettv.

I'm not sure there currently is a way to reactivate subscriptions.  I'll push that question upstream and see if we can't get that straightened out.

New versions are out.  I've talked to upstream and they have fixed the bug that you can't resubscribe to a feed.

---

### Post by Disparu on 2008-09-13
I guess I am the only one testing it?

So far so good. I can now reactivate subscriptions that are inactive, but still can not remove them, although that doesn't really matter.

I have yet to experience a successful cron job, is there an easy way to force that?

alright so i ran the cron jobs manually...

list of problems i had- 

1) The error regarding data directory didn't go away till i made a data directory in /home/(user) - I then had to permission it for read and write on my user account to get mythnettv to actually download stuff
2) The cron jobs are being set up in the context of a user called "mythtv" - this will not work as i don't have a user called that so i had to change it when i manually ran the command t download it.

suggestions for the gui..

ability to select run-as context for the cron job? ps i am a linux amature so some things i come up with might be retarded

for the title box default the entries to have quotes around them, otherwise multiword titles only get the first word for the title (this is fixable by using quotes, but it would be convenient if you didn't have to)

what about a download now option? 
PS
It is really nice to test something and actually see results being handed out in short periods of time, i am going to love the crap out of this program when the kinks are worked out.

cheers,
alex

---

### Post by tgm4883 on 2008-09-13
Let me try to break this down, and we can have a conversation about each of the issues.

> **Disparu said:**
> I guess I am the only one testing it?

So far so good. I can now reactivate subscriptions that are inactive, but still can not remove them, although that doesn't really matter.


I believe the reason that they are inactive and not removed, is because if you do delete them, then readd them it will download all the shows that you already downloaded.  If you just make it inactive the list of shows you downloaded is still kept.

> **Disparu said:**
> 
I have yet to experience a successful cron job, is there an easy way to force that?

alright so i ran the cron jobs manually...

list of problems i had- 

1) The error regarding data directory didn't go away till i made a data directory in /home/(user) - I then had to permission it for read and write on my user account to get mythnettv to actually download stuff


The data directory location is kept inside of the database.  Unfortunatly in order to test the fix, you would have to delete the mythnettv tables and try running the program again.  I'm looking into having those tables removed during uninstall.

> **Disparu said:**
> 
2) The cron jobs are being set up in the context of a user called "mythtv" - this will not work as i don't have a user called that so i had to change it when i manually ran the command t download it.

You should have a user called mythtv, it is created during install of MythTV.  Thats what the backend runs as and what group you must be a part of to run the frontend.  Also, the Mythtv user and whoever is in the mythtv group has write access to /var/lib/mythtv/, which is where I have set the data directory to.  I believe this would work correctly if you were able to delete the mythnettv tables and try again.


> **Disparu said:**
> 
suggestions for the gui..

ability to select run-as context for the cron job? ps i am a linux amature so some things i come up with might be retarded



see above, should work as mythtv user

> **Disparu said:**
> 
for the title box default the entries to have quotes around them, otherwise multiword titles only get the first word for the title (this is fixable by using quotes, but it would be convenient if you didn't have to)



I'll look into getting this fixed.

> **Disparu said:**
> 
what about a download now option? 
PS
It is really nice to test something and actually see results being handed out in short periods of time, i am going to love the crap out of this program when the kinks are worked out.

cheers,
alex

Downloading takes a long time.  I'm hesitant to add this feature.  I will look into this though.  If I can pipe the download status into the frontend I might add this.

---

### Post by Disparu on 2008-09-14
Really appreciate the one on one support,

I can't figure out this mythtv user issue, I definitely have a mythtv user, but the cron jobs never run. 

Could someone point me in the right direction?

---

### Post by Disparu on 2008-09-14
so i checked my cronjobs and there are no cronjobs listed. even after i set the download job. i checked both under root mythtv and my current user account.

---

### Post by tgm4883 on 2008-09-14
did you check in /etc/cron.hourly/  ?

---

### Post by managementboy on 2008-09-15
Hi, I installed the mythnettv packages provided by mythbuntu but I get the following error:

```
/usr/share/mythnettv/mythnettv                                                                           
Traceback (most recent call last):                                                                                      
  File "/usr/share/mythnettv/mythnettv", line 538, in <module>                                                          
    main(sys.argv)                                                                                                      
  File "/usr/share/mythnettv/mythnettv", line 184, in main                                                              
    db = database.MythNetTvDatabase()                                                                                   
  File "/usr/share/mythnettv/database.py", line 56, in __init__                                                         
    self.RepairMissingDates()                                                                                           
  File "/usr/share/mythnettv/database.py", line 234, in RepairMissingDates                                              
    prog = program.MythNetTvProgram(self)                                                                               
NameError: global name 'program' is not defined
```

what could be the problem?

cheers,

Elkin

---

### Post by tgm4883 on 2008-09-15
> **managementboy said:**
> Hi, I installed the mythnettv packages provided by mythbuntu but I get the following error:

```
/usr/share/mythnettv/mythnettv                                                                           
Traceback (most recent call last):                                                                                      
  File "/usr/share/mythnettv/mythnettv", line 538, in <module>                                                          
    main(sys.argv)                                                                                                      
  File "/usr/share/mythnettv/mythnettv", line 184, in main                                                              
    db = database.MythNetTvDatabase()                                                                                   
  File "/usr/share/mythnettv/database.py", line 56, in __init__                                                         
    self.RepairMissingDates()                                                                                           
  File "/usr/share/mythnettv/database.py", line 234, in RepairMissingDates                                              
    prog = program.MythNetTvProgram(self)                                                                               
NameError: global name 'program' is not defined
```

what could be the problem?

cheers,

Elkin

Well thats odd.  What is the output of  "dpkg -l | mythnettv"

---

### Post by Disparu on 2008-09-15
there is a mythnettv file in cron.hourly with the appropriate entries, but it never runs.

---

### Post by managementboy on 2008-09-15
> **tgm4883 said:**
> Well thats odd.  What is the output of  "dpkg -l | mythnettv"

I asumed you meant with "grep"

```
dpkg -l | grep mythnettv
ii  mythnettv                                  6~svn145-0ubuntu1~hardy                              Plugin to download RSS video feeds
ii  mythnettv-gui                              1.0r12-0ubuntu1                                      Gui frontend for MythNetTV
```

could there be files left over of an old version?

FIXED: just delete all mythnettv tables and start all over... strange but it worked

---

### Post by tgm4883 on 2008-09-15
> **Disparu said:**
> there is a mythnettv file in cron.hourly with the appropriate entries, but it never runs.

Odd.  Any error messages?  Can you run it by hand?


> **managementboy said:**
> I asumed you meant with "grep"

```
dpkg -l | grep mythnettv
ii  mythnettv                                  6~svn145-0ubuntu1~hardy                              Plugin to download RSS video feeds
ii  mythnettv-gui                              1.0r12-0ubuntu1                                      Gui frontend for MythNetTV
```

could there be files left over of an old version?

FIXED: just delete all mythnettv tables and start all over... strange but it worked

Heh, yea I meant with grep.  Odd that that fixed it.  Would have been nice if we could have looked into those tables to see what they were.

---

### Post by Disparu on 2008-09-15
2008-09-15 19:51:04.089968: downloaded 448 mb (470173696 bytes)
2008-09-15 19:51:06.580510: downloaded 451 mb (473246720 bytes)
Done
Download OK
Importing /var/lib/mythtv/mythnettv/tekzilla--0048--superhot--large.xvid.avi
Download Error: Could not determine the video directory for this machine. Please report this to [email]mikal@stillhq.com[/email]
Importing /var/lib/mythtv/mythnettv/tekzilla--0048--superhot--large.xvid.avi
Couldn't import straggling /tekzilla/0048/tekzilla--0048--superhot--large.xvid.avi, removing it from the queue



i first tried to run it as is and it obviously asked for the mythtv user password which i don't know.

i then sudo'd the cron.hourly/mythnettv and it said that it had been attempted too many times (over 3) and would not try anymore.

after that i unsubscribed and resubscribed and sudod it and it downloaded the show but had the above problem.

---

### Post by tgm4883 on 2008-09-15
> **Disparu said:**
> 2008-09-15 19:51:04.089968: downloaded 448 mb (470173696 bytes)
2008-09-15 19:51:06.580510: downloaded 451 mb (473246720 bytes)
Done
Download OK
Importing /var/lib/mythtv/mythnettv/tekzilla--0048--superhot--large.xvid.avi
Download Error: Could not determine the video directory for this machine. Please report this to [email]mikal@stillhq.com[/email]
Importing /var/lib/mythtv/mythnettv/tekzilla--0048--superhot--large.xvid.avi
Couldn't import straggling /tekzilla/0048/tekzilla--0048--superhot--large.xvid.avi, removing it from the queue



i first tried to run it as is and it obviously asked for the mythtv user password which i don't know.

i then sudo'd the cron.hourly/mythnettv and it said that it had been attempted too many times (over 3) and would not try anymore.

after that i unsubscribed and resubscribed and sudod it and it downloaded the show but had the above problem.

strange.  Whats the output of
```
ls -l /var/lib/mythtv/
```

---

### Post by managementboy on 2008-09-16
> **tgm4883 said:**
> Odd.  Any error messages?  Can you run it by hand?




Heh, yea I meant with grep.  Odd that that fixed it.  Would have been nice if we could have looked into those tables to see what they were.

Thanks for the help. Maybe I should have looked, but I was just trying things out. 

The scripts are working well, but for those that would download youtube. The logs say something about ffmpeg not liking compressed flv files. Any fix around that?

```
/usr/share/mythnettv/mythnettv url "http://video.google.com/videosearch?q=authors@google&so=1&num=20&dur=
3&output=rss" "Authors@Google"                                                                                          
{u'application/x-shockwave-flash': {u'medium': u'video', u'url': u'http://www.youtube.com/v/iKJxQvZHtLU&hl=en', u'type':
 u'application/x-shockwave-flash', u'height': u'0', u'width': u'0', u'duration': u'3315', u'expression': u'full'}}      
Error: SWF is currently unsupported due to ffmpeg and mencoder not supporting compressed SWF files as input. Let mythnet
tv@stillhq.com know if you are aware of an open source way of transcoding these files.
```

And lastly, should we not start to make a plug-in to configure your script via the myhtfrontend? could it be so hard? I could help on the theme side.

---

### Post by tgm4883 on 2008-09-16
> **managementboy said:**
> Thanks for the help. Maybe I should have looked, but I was just trying things out. 

The scripts are working well, but for those that would download youtube. The logs say something about ffmpeg not liking compressed flv files. Any fix around that?

```
/usr/share/mythnettv/mythnettv url "http://video.google.com/videosearch?q=authors@google&so=1&num=20&dur=
3&output=rss" "Authors@Google"                                                                                          
{u'application/x-shockwave-flash': {u'medium': u'video', u'url': u'http://www.youtube.com/v/iKJxQvZHtLU&hl=en', u'type':
 u'application/x-shockwave-flash', u'height': u'0', u'width': u'0', u'duration': u'3315', u'expression': u'full'}}      
Error: SWF is currently unsupported due to ffmpeg and mencoder not supporting compressed SWF files as input. Let mythnet
tv@stillhq.com know if you are aware of an open source way of transcoding these files.
```


This is an upstream error.  As the error message says, if you know of an open source way of transcoding those files let [email]mythnettv@stillhq.com[/email] know and they will try to implement that in the next release.

On the same note, if you install mythstream and grab an updated youtube parser you can watch the video that way.  It will stream though and not download.

> **managementboy said:**
> 
And lastly, should we not start to make a plug-in to configure your script via the myhtfrontend? could it be so hard? I could help on the theme side.

At some point I do plan on trying to make a frontend plugin.  Currently i'm in the middle of doing lots of stuff and I don't really know how to do proper frontend plugin like that.  I haven't really been that motivated to do that either as most people have multiple systems, and you need the rss feed link anyway (which you would normally get from using the internet)

---

### Post by managementboy on 2008-09-16
> **tgm4883 said:**
> This is an upstream error.  As the error message says, if you know of an open source way of transcoding those files let [email]mythnettv@stillhq.com[/email] know and they will try to implement that in the next release.

On the same note, if you install mythstream and grab an updated youtube parser you can watch the video that way.  It will stream though and not download.


Hi, before finding mythnettv I have been using ytcatcher + theyoke to get the RSS youtube feeds downloaded. check [http://ubuntuforums.org/showthread.php?t=365756](http://ubuntuforums.org/showthread.php?t=365756)

nice would be to use youtube-dl to download the Flv files. Then we could use ffmpeg or mencoder to make an avi out of it. for example:
```
ffmpeg -i youtube.flv -ar 48000 -ac 2 youtube.avi
```
and you get an avi

---

### Post by Disparu on 2008-09-18
the problem i had with the insertion of the videos went away.

But the cron jobs still don't run and if i run them manually you can see that they have tried to run, but failed since it says "4th attempt" etc.

i can successfully sudo the cron.hourly job and it runs fine.

i have no idea if i am doing something completely dumb, but these jobs refuse to run.


--- i have an idea and will try it when i get home... i think i may very well have been retarded about all of this.

---

### Post by tgm4883 on 2008-09-18
> **Disparu said:**
> the problem i had with the insertion of the videos went away.

But the cron jobs still don't run and if i run them manually you can see that they have tried to run, but failed since it says "4th attempt" etc.

i can successfully sudo the cron.hourly job and it runs fine.

i have no idea if i am doing something completely dumb, but these jobs refuse to run.


--- i have an idea and will try it when i get home... i think i may very well have been retarded about all of this.

Well let us know.  FYI, you cannot run the cron job on a system without a backend and storage dir

---

### Post by Disparu on 2008-09-19
well i don't think my idea worked.

i thought it was permissions on the recordings folder since i had moved the location somewhere abnormal.

but i do have more detailed information

FYI - i am testing on a mythbuntu CLEAN install with no changes now.

i noticed that videos were getting stuck in /var/lib/mythtv/mythnettv ... one of the videos was smaller than it was suppose to be. So it seems this video didn't finish downloading and wasn't moved to the recordings directory.

alright, odd as this may sound, a different video is in the directory now, but is the same exact size as the other one. it seems they are all stopping at 126MB.
\
could anyone point me in the right direction for recording cron errors?

---

### Post by tgm4883 on 2008-09-19
> **Disparu said:**
> well i don't think my idea worked.

i thought it was permissions on the recordings folder since i had moved the location somewhere abnormal.

but i do have more detailed information

FYI - i am testing on a mythbuntu CLEAN install with no changes now.

i noticed that videos were getting stuck in /var/lib/mythtv/mythnettv ... one of the videos was smaller than it was suppose to be. So it seems this video didn't finish downloading and wasn't moved to the recordings directory.

alright, odd as this may sound, a different video is in the directory now, but is the same exact size as the other one. it seems they are all stopping at 126MB.
\
could anyone point me in the right direction for recording cron errors?

That directory is just the temporary storage directory for mythnettv.  Once the show is downloaded, it gets moved into either a mythnettv storage directory, or your recording directory.

whats the output of 
```
dpkg -l | grep mythtv-backend
```

---

### Post by Disparu on 2008-09-19
dpkg -l | grep mythtv-backend
iU  mythtv-backend                             0.21.0+fixes18207-0ubuntu4~hardy1                    A personal video recorder application (serve
iU  mythtv-backend-master                      0.21.0+fixes18207-0ubuntu4~hardy1                    Metapackage to setup and configure a "Master

i know that directory is only a temporary one to download to, but what concerns me is the whole video doesn't get downloaded and it stops the job so the video just stays there. When the job attempts to download the same file again it has issues replacing the incomplete one (permissions or something)

---

### Post by tgm4883 on 2008-09-19
> **Disparu said:**
> dpkg -l | grep mythtv-backend
iU  mythtv-backend                             0.21.0+fixes18207-0ubuntu4~hardy1                    A personal video recorder application (serve
iU  mythtv-backend-master                      0.21.0+fixes18207-0ubuntu4~hardy1                    Metapackage to setup and configure a "Master

i know that directory is only a temporary one to download to, but what concerns me is the whole video doesn't get downloaded and it stops the job so the video just stays there. When the job attempts to download the same file again it has issues replacing the incomplete one (permissions or something)

How fast is your internet connection?  How large is the video that it's trying to download?  Any error messages when you run the cron job manually?

---

### Post by Disparu on 2008-09-19
my connection is more than ample usually the files come down at 2ish mbytes a sec (not bits)

files are around 200-300mb

when i run it manually (keep in mind i have to sudo it since it prompts for the mythtv user password otherwise [i thought there wasn't a password for that account]) it downloads the whole file and moves it to the recordings directory no problem and adds the database entries.

---

### Post by tgm4883 on 2008-09-19
Interesting, seems like it should be working fine.  The cron job is set to run hourly, how long does it take you to download the show?

---

### Post by Disparu on 2008-09-21
> **tgm4883 said:**
> Interesting, seems like it should be working fine.  The cron job is set to run hourly, how long does it take you to download the show?

a few minutes. whenever i sudo the cron job it downloads the full show and inserts it. whenever it just runs on it's own it only downloads 126mb and stops

how can i log cron.hourly jobs?

---

### Post by tgm4883 on 2008-09-21
> **Disparu said:**
> a few minutes. whenever i sudo the cron job it downloads the full show and inserts it. whenever it just runs on it's own it only downloads 126mb and stops

how can i log cron.hourly jobs?

The next version will have logging for the cron job.  You can add that now by replacing the contents of /etc/cron.hourly/mythnettv to look like this

```
#!/bin/bash

su mythtv -c "/usr/share/mythnettv/mythnettv update verbose" >> /var/log/mythtv/mythnettv.log 2>&1
su mythtv -c "/usr/share/mythnettv/mythnettv download 1" >> /var/log/mythtv/mythnettv.log 2>&1
```

This will create a log in /var/log/mythtv/mythnettv.log

---

### Post by Disparu on 2008-09-22
thanks for the info, I am going to try that tonight.

---

### Post by tgm4883 on 2008-09-22
> **Disparu said:**
> thanks for the info, I am going to try that tonight.

Yep, I found I was having the same issue.  I removed added that stuff, removed all of the videos in /var/lib/mythtv/mythnettv/ and set all the failed videos in the db to null for started, finished, tries, failed.

Overnight it has run and downloaded everything I wanted so far.  The only weird thing popping up is when a show takes longer than an hour to download.

---

### Post by itsdaveperdue on 2008-09-22
This is exactly what I've been looking for.  I've been playing with mythnettv for the past couple of days...then I found this post, the repo, and the gui.  I've configured it and I'll let you know if I have any problems.

I did have the data folder issue so I made the directory in var/lib/mythtv/mythnettv/.  We'll see how the cron job does!

Thanks for all the good work!

---

### Post by tgm4883 on 2008-09-22
> **itsdaveperdue said:**
> This is exactly what I've been looking for.  I've been playing with mythnettv for the past couple of days...then I found this post, the repo, and the gui.  I've configured it and I'll let you know if I have any problems.

I did have the data folder issue so I made the directory in var/lib/mythtv/mythnettv/.  We'll see how the cron job does!

Thanks for all the good work!

When did you install?

---

### Post by itsdaveperdue on 2008-09-22
> **tgm4883 said:**
> When did you install?

Just this morning.  I'm at work, but I'll check the logs when I get home to find out what it has been up to.

---

### Post by tgm4883 on 2008-09-22
> **itsdaveperdue said:**
> Just this morning.  I'm at work, but I'll check the logs when I get home to find out what it has been up to.

Hmm, means my fix didn't work.  Thanks, I'll check into it.

:EDIT:

BTW, how did you install?  apt-get, aptitude, synaptic?

---

### Post by itsdaveperdue on 2008-09-23
> **tgm4883 said:**
> Hmm, means my fix didn't work.  Thanks, I'll check into it.

:EDIT:

BTW, how did you install?  apt-get, aptitude, synaptic?


Sorry for the delay.

I used apt-get to install mythnettv and mythnettv-gui.

My logs so far just show the data directory error (several times, I'd imagine one entry each time the cron job ran):
> You need to create the configured data directory at "data"


As an aside I have a directory named data in the following places:
/home/mythtv/data
/var/lib/mythtv/mythnettv/data

---

### Post by tgm4883 on 2008-09-23
> **itsdaveperdue said:**
> Sorry for the delay.

I used apt-get to install mythnettv and mythnettv-gui.

My logs so far just show the data directory error (several times, I'd imagine one entry each time the cron job ran):


As an aside I have a directory named data in the following places:
/home/mythtv/data
/var/lib/mythtv/mythnettv/data

Strange.  Could you post the output of this command here

```
cat /usr/share/mythnettv/mythnettv
```

---

### Post by itsdaveperdue on 2008-09-23
Here ya go:
```

$cat /usr/share/mythnettv/mythnettv

#!/usr/bin/python

# This script requires that mplayer be installed

# Copyright (C) Michael Still (mikal@stillhq.com) 2006, 2007, 2008
# Released under the terms of the GNU GPL v2

# Latest source is always at http://www.stillhq.com/mythtv/mythnettv/


import commands
import datetime
import feedparser
import os
import re
import shutil
import subprocess
import sys
import tempfile
import time
import types

import database
import gflags
import program
import proxyhandler
import syndication
import mythnettvcore
import utility
import video

__author__ = 'Michael Still (mikal@stillhq.com)'
__version__ = 'Release 6'


# Define command line flags
FLAGS = gflags.FLAGS
gflags.DEFINE_string('datadirdefault', 'data',
                     'The default location of the data directory')
gflags.DEFINE_boolean('prompt', True,
                      'Prompt for user input when required')
gflags.DEFINE_boolean('promptforannounce', True,
                      'Should the user be prompted about subscribing to the '
                      'announce video feed?')


def GetPossible(array, index):
  """GetPossible -- get a value from an array, handling its absence nicely"""

  try:
    return array[index]
  except:
    return None


def Usage(out):
  out.write("""Unknown command line. Try one of:

(manual usage)
  url <url> <title> : to download an RSS feed and load the shows
                      from it into the TODO list. The title is
                      as the show title in the MythTV user
                      interface
  file <url> <title>: to do the same, but from a file, with a show
                      title like url above
  download <num>    : to download that number of shows from the
                      TODO list. We download some of the oldest
                      first, and then grab some of the newest as
                      well.
  download <num> <title filter>
                    : the same as above, but filter to only 
                      download shows with a title exactly 
                      matching the specified filter
  download <num> <title filter> <subtitle filter>
                    : the same as above, but with a regexp title
                      filter as well
  download <num> <title filter> <subtitle filter> justone
                    : the same as above, but download just one
                      and then mark all other matches as read

  cleartodo         : permanently remove all items from the TODO
                      list
  markread <num>    : interactively mark some of the oldest <num>
                      shows as already downloaded and imported
  markread <num> <title filter>
                    : the same as above, but filter to only mark
                      shows with a title exactly matching the
                      specified filter
  markread <num> <title filter> <subtitle filter>
                    : the same as above, but with a regexp title
                      filter as well

(handy stuff)
  todoremote        : add a remote URL to the TODO list. This will
                      prompt for needed information about the
                      video, and set the date of the program to
                      now
  todoremote <url> <title> <subtitle> <description>
                    : the same as above, but don't prompt for
                      anything
  importremote      : download and immediately import the named
                      URL. Will prompt for needed information
  importremote <url> <title> <subtitle> <description>
                    : the same as above, but don't prompt for
                      anything
  importtorrent <url> <title> <subtitle> <description>
                    : the same as above, but force the URL to be
                      treated as a torrent. This is useful when
                      MythNetTV doesn't automatically detect
                      that the URL is to a torrent file.
  importlocal <file>: import the named file, using the title, 
                      subtitle and description from the command
                      line. The file will be left on disk.
  importlocal <file>: import the named file. The file will be
                      left on disk. Will prompt for needed
                      information
  importmanylocal <path> <regexp> <title>:
                      import all the files from path matching
                      regexp. title is use as the title for the
                      program, and the filename is used as the
                      subtitle

(subscription management)
  subscribe <url> <title>
                    : subscribe to a URL, and specify the show 
                      title
  list              : list subscriptions
  unsubscribe <url> : unsubscribe from a URL
  update            : add new programs from subscribed URLs to the
                      TODO list

(things you can do to subscriptions)
  archive <title> <path>
                    : archive all programs with this title to the
                      specified path. This is useful for shows you
                      download and import, but want to build a
                      non-MythTV archive of as well
  category <title> <category>
                    : set the category for a given program. The
                      category is used for parental filtering  within
                      MythTV.
  group <title> <group>
                    : set the group for a given program. The
                      group is used as a recording group within
                      MythTV.
  http_proxy <url regexp> <proxy>
                    : you can choose to use a HTTP proxy for URL
                      requests matching a given regular expression.
                      Use this command to define such an entry. This
                      might be handy if some of the programs you
                      wish to subscribe to are only accessible over
                      a VPN.
  http_proxy <url regexp> <proxy> <budget mb>
                    : the same as above, but you can specify the
                      maximum number of megabytes to download via
                      the proxy in a given day. To see proxy usage
                      information, use the proxyusage command.

(reporting)
  statistics        : show some simple statistics about MythNetTV
  log               : dump the current internal log entries
  nextdownload <num>
                    : if you executed download <num>, what would
                      be downloaded?
  proxyusage        : print a simple report on HTTP proxy usage over
                      the last seven days

(debugging)
  videodir          : show where MythNetTV thinks it should be
                      placing video files
  explainvideodir   : verbosely explain why that video directory was
                      selected. This can help debug when the wrong
                      video directory is being used, or no video
                      directory at all is found
""")

  out.write('\n\nAdditionally, you can use these global flags:%s\n' % FLAGS)
  sys.exit(1)


def main(argv, out=sys.stdout):
  # Parse flags
  try:
    argv = FLAGS(argv)
  except gflags.FlagsError, e:
    out.write('%s\n' % e)
    Usage(out)
    
  db = database.MythNetTvDatabase()

  # Make sure the data directory exists
  datadir = db.GetSettingWithDefault('datadir', FLAGS.datadirdefault)
  if not os.path.exists(datadir):
    out.write('You need to create the configured data directory at "%s"\n'
              % datadir)
    sys.exit(1)

  # Ask if we can subscribe the user to the announcement video feed
  announce_prompted = db.GetSettingWithDefault('promptedforannounce',
                                               not FLAGS.promptforannounce)
  if not announce_prompted:
    row = db.GetOneRow('select * from mythnettv_subscriptions where '
                       'title="MythNetTV announcements";')
    if not row and FLAGS.promptforannounce:
      out.write('You are not currently subscribed to the MythNetTV\n'
                'announcements video feed. This feed is very low volume\n'
                'and is used to announce important things like new releases\n'
                'and major bug fixes.\n\n'
                'Would you like to be subscribed? You will only be asked\n'
                'this once.\n\n')
      confirm = raw_input('Type yes to subscribe: ')

      if confirm == 'yes':
        mythnettvcore.Subscribe('http://www.stillhq.com/mythtv/mythnettv/'
                                'announce/feed.xml',
                                'MythNetTV announcements')
        out.write('Subscribed to MythNetTV announcements\n')

    db.WriteSetting('promptedforannounce', True)

  # TODO(mikal): This command line processing is ghetto
  if len(argv) == 1:
    out.write('Invalid command line: %s\n' % ' '.join(argv))
    Usage(out)

  if argv[1] == 'url':
    # Go and grab the XML file from the remote HTTP server, and then parse it
    # as an RSS feed with enclosures. Populates a TODO list in 
    # mythnettv_programs
    proxy = proxyhandler.HttpHandler(db)
    xmlfile = proxy.Open(argv[2], out=out)
    syndication.Sync(db, xmlfile, argv[3], out=out)

  elif argv[1] == 'file':
    # Treat the local file as an RSS feed. Populates a TODO list in
    # mythnettv_programs
    xmlfile = open(argv[2])
    syndication.Sync(db, xmlfile, argv[3])

  elif argv[1] == 'download':
    # Download the specified number of programs and import them into MythTV
    filter = GetPossible(argv, 3)
    subtitle_filter = GetPossible(argv, 4)
    just_one = GetPossible(argv, 5) == 'justone'

    success = False
    previous = []
    for guid in mythnettvcore.NextDownloads(argv[2], filter,
                                            False, subtitle_filter,
                                            out=out):
      if not just_one:
        mythnettvcore.DownloadAndImport(db, guid, out=out)

      elif just_one and not success:
        success = mythnettvcore.DownloadAndImport(db, guid, out=out)
        if not success:
          previous.append(guid)

      else:
        prog = program.MythNetTvProgram(db)
        prog.Load(guid)
        out.write('Skipping because we already have one\n')
        out.write('  %s: %s\n' %(prog.GetTitle(), prog.GetSubtitle()))
        out.write('  (%s)\n\n' % prog.GetDate())
        prog.SetImported()
        prog.Store()

    # If some failed before we had one work, then we now need to mark them
    # read if we're fetching just one
    if just_one and previous:
      for guid in previous:
        prog = program.MythNetTvProgram(db)
        prog.Load(guid)
        out.write('Skipping because we already have one\n')
        out.write('  %s: %s\n' %(prog.GetTitle(), prog.GetSubtitle()))
        out.write('  (%s)\n\n' % prog.GetDate())
        prog.SetImported()
        prog.Store()

    # And now make sure there aren't any stragglers
    for guid in db.GetWaitingForImport():
      prog = program.MythNetTvProgram(db)
      prog.Load(guid)
      try:
        prog.Import(out=out)
      except:
        out.write('Couldn\'t import straggling %s, '
                  'removing it from the queue\n'
                  % guid)
        prog.SetImported()
        prog.Store()

  elif argv[1] == 'todoremote':
    # Add a remote URL to the TODO list. We have to prompt for a bunch of
    # stuff because we don't have a "real" RSS feed
    prog = program.MythNetTvProgram(db)
    url = GetPossible(argv, 2)
    title = GetPossible(argv, 3)
    subtitle = GetPossible(argv, 4)
    description = GetPossible(argv, 5)
    prog.FromInteractive(url, title, subtitle, description)

  elif argv[1] == 'importremote' or argv[1] == 'importtorrent':
    # Download a remote file and then import it as a program. We have to
    # prompt for details here, because this didn't come from a "real" RSS feed
    prog = program.MythNetTvProgram(db)
    url = GetPossible(argv, 2)
    title = GetPossible(argv, 3)
    subtitle = GetPossible(argv, 4)
    description = GetPossible(argv, 5)

    # TODO(mikal)
    # It is _possible_ that this show has already been created and
    # that this is an attempt to restart a download. Check.

    prog.FromInteractive(url, title, subtitle, description)
    if argv[1] == 'importtorrent':
      prog.SetMime('application/x-bittorrent')
    if prog.Download(db.GetSettingWithDefault('datadir',
                                              FLAGS.datadirdefault),
                     out=out) == True:
      prog.Import(out=out)

  elif argv[1] == 'importmanylocal':
    # Import files matching regexp from path with the title
    path = argv[2]
    regexp = argv[3]
    title = argv[4]

    rxp = re.compile(regexp)
    for ent in os.listdir(path):
      if os.path.isfile('%s/%s' %(path, ent)):
        out.write('Considering %s\n' % ent)
        m = rxp.match(ent)
        if m:
          prog = program.MythNetTvProgram(db)
          prog.SetUrl(ent)
          prog.FromInteractive('%s/%s' %(path, ent),
                               title,
                               ent,
                               '-')
          prog.CopyLocalFile(db.GetSettingWithDefault('datadir',
                                                      FLAGS.datadirdefault),
                             out=out)
          prog.Import(out=out)

  elif argv[1] == 'importlocal':
    # Take a local file, copy it to the temporary directory, and then import
    # it as if we had downloaded it
    prog = program.MythNetTvProgram(db)
    prog.SetUrl(argv[2])
    url = GetPossible(argv, 2)
    title = GetPossible(argv, 3)
    subtitle = GetPossible(argv, 4)
    description = GetPossible(argv, 5)
    prog.FromInteractive(url, title, subtitle, description)
    prog.CopyLocalFile(db.GetSettingWithDefault('datadir',
                                                FLAGS.datadirdefault),
                       out=out)
    prog.Import(out=out)

  elif argv[1] == 'subscribe':
    # Subscribe to an RSS feed
    mythnettvcore.Subscribe(argv[2], argv[3])
    out.write('Subscribed to %s\n' % argv[3])

  elif argv[1] == 'list':
    # List subscribed RSS feeds
    proxy = proxyhandler.HttpHandler(db)
    
    for row in db.GetRows('select distinct(title) from '
                          'mythnettv_subscriptions order by title'):
      out.write('%s\n' % row['title'])
      for subrow in db.GetRows('select * from mythnettv_subscriptions where '
                               'title="%s";' % row['title']):
        out.write(' - %s' % subrow['url'])
        
        (proxy_host, budget) = proxy.LookupProxy(subrow['url'])
        if proxy_host:
          out.write(' (proxy: %s' % proxy_host)
          if budget:
            out.write(' budget %s)' % utility.DisplayFriendlySize(budget))
          else:
            out.write(')')
        out.write('\n')
          
        if subrow['inactive'] == 1:
          out.write(' (inactive)\n')

      subrow = db.GetOneRow('select * from mythnettv_archive '
                            'where title="%s";'
                            % row['title'])
      if subrow:
        out.write('  Archived to %s\n' % subrow['path'])

      subrow = db.GetOneRow('select * from mythnettv_category '
                            'where title="%s";'
                            % row['title'])
      if subrow:
        out.write('  Category is %s\n' % subrow['category'])

      subrow = db.GetOneRow('select * from mythnettv_group '
                            'where title="%s";'
                            % row['title'])
      if subrow:
        out.write('  Group is %s\n' % subrow['recgroup'])

      out.write('\n')

  elif argv[1] == 'unsubscribe':
    # Remove a subscription to an RSS feed
    db.ExecuteSql('update mythnettv_subscriptions set inactive=1 '
                  'where url = "%s";'
                  % argv[2])

  elif argv[1] == 'update':
    # Update the TODO list based on subscriptions
    mythnettvcore.Update(out)

  elif argv[1] == 'archive':
    db.WriteOneRow('mythnettv_archive', 'title', {'title': argv[2],
                                                  'path': argv[3]})

  elif argv[1] == 'category':
    db.WriteOneRow('mythnettv_category', 'title', {'title': argv[2],
                                                   'category': argv[3]})

  elif argv[1] == 'group':
    db.WriteOneRow('mythnettv_group', 'title', {'title': argv[2],
                                                'recgroup': argv[3]})

  elif argv[1] == 'http_proxy':
    budget = GetPossible(argv, 4)
    if budget:
      budget = int(budget) * 1024 * 1024
      out.write('Setting proxy budget to %d bytes\n' % budget)

    db.WriteOneRow('mythnettv_proxies', 'url', {'url': argv[2],
                                                'http_proxy': argv[3],
                                                'daily_budget': budget})

  elif argv[1] == 'statistics':
    # Display some simple stats about the state of MythMYTHNETTV
    row = db.GetOneRow('select count(guid) from mythnettv_programs;')
    out.write('Programs tracked: %d\n' % row['count(guid)'])

    for show in db.GetRows('select distinct(title) from mythnettv_programs '
                           'where title is not NULL;'):
      row = db.GetOneRow('select count(guid) from mythnettv_programs where '
                         'title = "%s";' % show['title'])
      out.write('  %s: %d\n' %(show['title'], row['count(guid)']))
    out.write('\n')
    
    row = db.GetOneRow('select count(guid) from mythnettv_programs where '
                       'download_finished is NULL and title is not NULL '
                       'and inactive is NULL;')
    out.write('Programs still to download: %d\n'
              % row['count(guid)'])

    for show in db.GetRows('select distinct(title) from mythnettv_programs '
                           'where title is not NULL and '
                           'inactive is NULL and '
                           'download_finished is NULL;'):
      row = db.GetOneRow('select count(guid) from mythnettv_programs where '
                         'title = "%s" and inactive is NULL '
                         'and download_finished is NULL;'
                         % show['title'])
      out.write('  %s: %d\n' %(show['title'], row['count(guid)']))
    out.write('\n')

    try:
      row = db.GetOneRow('select sum(transfered) from mythnettv_programs;')
      out.write('Data transferred: %s\n'
             % (utility.DisplayFriendlySize(int(row['sum(transfered)']))))
    except:
      # TODO(mikal): I am sure there is a better way of doing this
      dummy = 'blah'

  elif argv[1] == 'log':
    for logline in db.GetRows('select * from mythnettv_log order by '
                              'sequence asc;'):
      out.write('%s %s\n' %(logline['timestamp'], logline['message']))

  elif argv[1] == 'nextdownload':
    filter = GetPossible(argv, 3)
    subtitle_filter = GetPossible(argv, 4)
    for guid in mythnettvcore.NextDownloads(argv[2], filter,
                                            False, subtitle_filter,
                                            out=out):
      out.write('%s\n' % guid)
      prog = program.MythNetTvProgram(db)
      prog.Load(guid)
      out.write('  %s: %s\n\n' %(prog.GetTitle(), prog.GetSubtitle()))

  elif argv[1] == 'cleartodo':
    out.write("""The command you are executing will permanently remove all
shows from the TODO list, as well as any record of shows which have
already been downloaded. Basically you\'ll be back at the start
again, although your preferences will remain set. Are you sure
you want to do this?\n\n""")
    confirm = raw_input('Type yes to do this: ')

    if confirm == 'yes':
      db.ExecuteSql('delete from mythnettv_programs;')
      out.write('Deleted\n')

  elif argv[1] == 'markread':
    filter = GetPossible(argv, 3)
    subtitle_filter = GetPossible(argv, 4)

    for guid in mythnettvcore.NextDownloads(argv[2], filter,
                                            True, subtitle_filter):
      prog = program.MythNetTvProgram(db)
      prog.Load(guid)
      out.write('  %s: %s\n' %(prog.GetTitle(), prog.GetSubtitle()))
      out.write('  (%s)\n\n' % prog.GetDate())

      if FLAGS.prompt:
        out.write('Are you sure you want to mark this show as downloaded?'
                  '\n\n')
        confirm = raw_input('Type yes to do this: ')
      else:
        confirm = 'yes'

      if confirm == 'yes':

        prog.SetImported()
        prog.Store()
        out.write('Done\n')
      out.write('\n')

  elif argv[1] == 'proxyusage':
    proxy = proxyhandler.HttpHandler(db)
    proxy.ReportRecentProxyUsage(out=out)

  elif argv[1] == 'videodir':
    try:
      print 'Video directory is: %s' % utility.GetVideoDir(db)
    except utility.FilenameException:
      print 'No video directory found! Use explainvideodir to debug'

  elif argv[1] == 'explainvideodir':
    utility.ExplainVideoDir(db)
      
  else:
    Usage(out)

if __name__ == "__main__":
  main(sys.argv)

```

---

### Post by tgm4883 on 2008-09-23
> **itsdaveperdue said:**
> Here ya go:
```

$cat /usr/share/mythnettv/mythnettv

#!/usr/bin/python

# This script requires that mplayer be installed

# Copyright (C) Michael Still (mikal@stillhq.com) 2006, 2007, 2008
# Released under the terms of the GNU GPL v2

# Latest source is always at http://www.stillhq.com/mythtv/mythnettv/


import commands
import datetime
import feedparser
import os
import re
import shutil
import subprocess
import sys
import tempfile
import time
import types

import database
import gflags
import program
import proxyhandler
import syndication
import mythnettvcore
import utility
import video

__author__ = 'Michael Still (mikal@stillhq.com)'
__version__ = 'Release 6'


# Define command line flags
FLAGS = gflags.FLAGS
gflags.DEFINE_string('datadirdefault', 'data',
                     'The default location of the data directory')
gflags.DEFINE_boolean('prompt', True,
                      'Prompt for user input when required')
gflags.DEFINE_boolean('promptforannounce', True,
                      'Should the user be prompted about subscribing to the '
                      'announce video feed?')


def GetPossible(array, index):
  """GetPossible -- get a value from an array, handling its absence nicely"""

  try:
    return array[index]
  except:
    return None


def Usage(out):
  out.write("""Unknown command line. Try one of:

(manual usage)
  url <url> <title> : to download an RSS feed and load the shows
                      from it into the TODO list. The title is
                      as the show title in the MythTV user
                      interface
  file <url> <title>: to do the same, but from a file, with a show
                      title like url above
  download <num>    : to download that number of shows from the
                      TODO list. We download some of the oldest
                      first, and then grab some of the newest as
                      well.
  download <num> <title filter>
                    : the same as above, but filter to only 
                      download shows with a title exactly 
                      matching the specified filter
  download <num> <title filter> <subtitle filter>
                    : the same as above, but with a regexp title
                      filter as well
  download <num> <title filter> <subtitle filter> justone
                    : the same as above, but download just one
                      and then mark all other matches as read

  cleartodo         : permanently remove all items from the TODO
                      list
  markread <num>    : interactively mark some of the oldest <num>
                      shows as already downloaded and imported
  markread <num> <title filter>
                    : the same as above, but filter to only mark
                      shows with a title exactly matching the
                      specified filter
  markread <num> <title filter> <subtitle filter>
                    : the same as above, but with a regexp title
                      filter as well

(handy stuff)
  todoremote        : add a remote URL to the TODO list. This will
                      prompt for needed information about the
                      video, and set the date of the program to
                      now
  todoremote <url> <title> <subtitle> <description>
                    : the same as above, but don't prompt for
                      anything
  importremote      : download and immediately import the named
                      URL. Will prompt for needed information
  importremote <url> <title> <subtitle> <description>
                    : the same as above, but don't prompt for
                      anything
  importtorrent <url> <title> <subtitle> <description>
                    : the same as above, but force the URL to be
                      treated as a torrent. This is useful when
                      MythNetTV doesn't automatically detect
                      that the URL is to a torrent file.
  importlocal <file>: import the named file, using the title, 
                      subtitle and description from the command
                      line. The file will be left on disk.
  importlocal <file>: import the named file. The file will be
                      left on disk. Will prompt for needed
                      information
  importmanylocal <path> <regexp> <title>:
                      import all the files from path matching
                      regexp. title is use as the title for the
                      program, and the filename is used as the
                      subtitle

(subscription management)
  subscribe <url> <title>
                    : subscribe to a URL, and specify the show 
                      title
  list              : list subscriptions
  unsubscribe <url> : unsubscribe from a URL
  update            : add new programs from subscribed URLs to the
                      TODO list

(things you can do to subscriptions)
  archive <title> <path>
                    : archive all programs with this title to the
                      specified path. This is useful for shows you
                      download and import, but want to build a
                      non-MythTV archive of as well
  category <title> <category>
                    : set the category for a given program. The
                      category is used for parental filtering  within
                      MythTV.
  group <title> <group>
                    : set the group for a given program. The
                      group is used as a recording group within
                      MythTV.
  http_proxy <url regexp> <proxy>
                    : you can choose to use a HTTP proxy for URL
                      requests matching a given regular expression.
                      Use this command to define such an entry. This
                      might be handy if some of the programs you
                      wish to subscribe to are only accessible over
                      a VPN.
  http_proxy <url regexp> <proxy> <budget mb>
                    : the same as above, but you can specify the
                      maximum number of megabytes to download via
                      the proxy in a given day. To see proxy usage
                      information, use the proxyusage command.

(reporting)
  statistics        : show some simple statistics about MythNetTV
  log               : dump the current internal log entries
  nextdownload <num>
                    : if you executed download <num>, what would
                      be downloaded?
  proxyusage        : print a simple report on HTTP proxy usage over
                      the last seven days

(debugging)
  videodir          : show where MythNetTV thinks it should be
                      placing video files
  explainvideodir   : verbosely explain why that video directory was
                      selected. This can help debug when the wrong
                      video directory is being used, or no video
                      directory at all is found
""")

  out.write('\n\nAdditionally, you can use these global flags:%s\n' % FLAGS)
  sys.exit(1)


def main(argv, out=sys.stdout):
  # Parse flags
  try:
    argv = FLAGS(argv)
  except gflags.FlagsError, e:
    out.write('%s\n' % e)
    Usage(out)
    
  db = database.MythNetTvDatabase()

  # Make sure the data directory exists
  datadir = db.GetSettingWithDefault('datadir', FLAGS.datadirdefault)
  if not os.path.exists(datadir):
    out.write('You need to create the configured data directory at "%s"\n'
              % datadir)
    sys.exit(1)

  # Ask if we can subscribe the user to the announcement video feed
  announce_prompted = db.GetSettingWithDefault('promptedforannounce',
                                               not FLAGS.promptforannounce)
  if not announce_prompted:
    row = db.GetOneRow('select * from mythnettv_subscriptions where '
                       'title="MythNetTV announcements";')
    if not row and FLAGS.promptforannounce:
      out.write('You are not currently subscribed to the MythNetTV\n'
                'announcements video feed. This feed is very low volume\n'
                'and is used to announce important things like new releases\n'
                'and major bug fixes.\n\n'
                'Would you like to be subscribed? You will only be asked\n'
                'this once.\n\n')
      confirm = raw_input('Type yes to subscribe: ')

      if confirm == 'yes':
        mythnettvcore.Subscribe('http://www.stillhq.com/mythtv/mythnettv/'
                                'announce/feed.xml',
                                'MythNetTV announcements')
        out.write('Subscribed to MythNetTV announcements\n')

    db.WriteSetting('promptedforannounce', True)

  # TODO(mikal): This command line processing is ghetto
  if len(argv) == 1:
    out.write('Invalid command line: %s\n' % ' '.join(argv))
    Usage(out)

  if argv[1] == 'url':
    # Go and grab the XML file from the remote HTTP server, and then parse it
    # as an RSS feed with enclosures. Populates a TODO list in 
    # mythnettv_programs
    proxy = proxyhandler.HttpHandler(db)
    xmlfile = proxy.Open(argv[2], out=out)
    syndication.Sync(db, xmlfile, argv[3], out=out)

  elif argv[1] == 'file':
    # Treat the local file as an RSS feed. Populates a TODO list in
    # mythnettv_programs
    xmlfile = open(argv[2])
    syndication.Sync(db, xmlfile, argv[3])

  elif argv[1] == 'download':
    # Download the specified number of programs and import them into MythTV
    filter = GetPossible(argv, 3)
    subtitle_filter = GetPossible(argv, 4)
    just_one = GetPossible(argv, 5) == 'justone'

    success = False
    previous = []
    for guid in mythnettvcore.NextDownloads(argv[2], filter,
                                            False, subtitle_filter,
                                            out=out):
      if not just_one:
        mythnettvcore.DownloadAndImport(db, guid, out=out)

      elif just_one and not success:
        success = mythnettvcore.DownloadAndImport(db, guid, out=out)
        if not success:
          previous.append(guid)

      else:
        prog = program.MythNetTvProgram(db)
        prog.Load(guid)
        out.write('Skipping because we already have one\n')
        out.write('  %s: %s\n' %(prog.GetTitle(), prog.GetSubtitle()))
        out.write('  (%s)\n\n' % prog.GetDate())
        prog.SetImported()
        prog.Store()

    # If some failed before we had one work, then we now need to mark them
    # read if we're fetching just one
    if just_one and previous:
      for guid in previous:
        prog = program.MythNetTvProgram(db)
        prog.Load(guid)
        out.write('Skipping because we already have one\n')
        out.write('  %s: %s\n' %(prog.GetTitle(), prog.GetSubtitle()))
        out.write('  (%s)\n\n' % prog.GetDate())
        prog.SetImported()
        prog.Store()

    # And now make sure there aren't any stragglers
    for guid in db.GetWaitingForImport():
      prog = program.MythNetTvProgram(db)
      prog.Load(guid)
      try:
        prog.Import(out=out)
      except:
        out.write('Couldn\'t import straggling %s, '
                  'removing it from the queue\n'
                  % guid)
        prog.SetImported()
        prog.Store()

  elif argv[1] == 'todoremote':
    # Add a remote URL to the TODO list. We have to prompt for a bunch of
    # stuff because we don't have a "real" RSS feed
    prog = program.MythNetTvProgram(db)
    url = GetPossible(argv, 2)
    title = GetPossible(argv, 3)
    subtitle = GetPossible(argv, 4)
    description = GetPossible(argv, 5)
    prog.FromInteractive(url, title, subtitle, description)

  elif argv[1] == 'importremote' or argv[1] == 'importtorrent':
    # Download a remote file and then import it as a program. We have to
    # prompt for details here, because this didn't come from a "real" RSS feed
    prog = program.MythNetTvProgram(db)
    url = GetPossible(argv, 2)
    title = GetPossible(argv, 3)
    subtitle = GetPossible(argv, 4)
    description = GetPossible(argv, 5)

    # TODO(mikal)
    # It is _possible_ that this show has already been created and
    # that this is an attempt to restart a download. Check.

    prog.FromInteractive(url, title, subtitle, description)
    if argv[1] == 'importtorrent':
      prog.SetMime('application/x-bittorrent')
    if prog.Download(db.GetSettingWithDefault('datadir',
                                              FLAGS.datadirdefault),
                     out=out) == True:
      prog.Import(out=out)

  elif argv[1] == 'importmanylocal':
    # Import files matching regexp from path with the title
    path = argv[2]
    regexp = argv[3]
    title = argv[4]

    rxp = re.compile(regexp)
    for ent in os.listdir(path):
      if os.path.isfile('%s/%s' %(path, ent)):
        out.write('Considering %s\n' % ent)
        m = rxp.match(ent)
        if m:
          prog = program.MythNetTvProgram(db)
          prog.SetUrl(ent)
          prog.FromInteractive('%s/%s' %(path, ent),
                               title,
                               ent,
                               '-')
          prog.CopyLocalFile(db.GetSettingWithDefault('datadir',
                                                      FLAGS.datadirdefault),
                             out=out)
          prog.Import(out=out)

  elif argv[1] == 'importlocal':
    # Take a local file, copy it to the temporary directory, and then import
    # it as if we had downloaded it
    prog = program.MythNetTvProgram(db)
    prog.SetUrl(argv[2])
    url = GetPossible(argv, 2)
    title = GetPossible(argv, 3)
    subtitle = GetPossible(argv, 4)
    description = GetPossible(argv, 5)
    prog.FromInteractive(url, title, subtitle, description)
    prog.CopyLocalFile(db.GetSettingWithDefault('datadir',
                                                FLAGS.datadirdefault),
                       out=out)
    prog.Import(out=out)

  elif argv[1] == 'subscribe':
    # Subscribe to an RSS feed
    mythnettvcore.Subscribe(argv[2], argv[3])
    out.write('Subscribed to %s\n' % argv[3])

  elif argv[1] == 'list':
    # List subscribed RSS feeds
    proxy = proxyhandler.HttpHandler(db)
    
    for row in db.GetRows('select distinct(title) from '
                          'mythnettv_subscriptions order by title'):
      out.write('%s\n' % row['title'])
      for subrow in db.GetRows('select * from mythnettv_subscriptions where '
                               'title="%s";' % row['title']):
        out.write(' - %s' % subrow['url'])
        
        (proxy_host, budget) = proxy.LookupProxy(subrow['url'])
        if proxy_host:
          out.write(' (proxy: %s' % proxy_host)
          if budget:
            out.write(' budget %s)' % utility.DisplayFriendlySize(budget))
          else:
            out.write(')')
        out.write('\n')
          
        if subrow['inactive'] == 1:
          out.write(' (inactive)\n')

      subrow = db.GetOneRow('select * from mythnettv_archive '
                            'where title="%s";'
                            % row['title'])
      if subrow:
        out.write('  Archived to %s\n' % subrow['path'])

      subrow = db.GetOneRow('select * from mythnettv_category '
                            'where title="%s";'
                            % row['title'])
      if subrow:
        out.write('  Category is %s\n' % subrow['category'])

      subrow = db.GetOneRow('select * from mythnettv_group '
                            'where title="%s";'
                            % row['title'])
      if subrow:
        out.write('  Group is %s\n' % subrow['recgroup'])

      out.write('\n')

  elif argv[1] == 'unsubscribe':
    # Remove a subscription to an RSS feed
    db.ExecuteSql('update mythnettv_subscriptions set inactive=1 '
                  'where url = "%s";'
                  % argv[2])

  elif argv[1] == 'update':
    # Update the TODO list based on subscriptions
    mythnettvcore.Update(out)

  elif argv[1] == 'archive':
    db.WriteOneRow('mythnettv_archive', 'title', {'title': argv[2],
                                                  'path': argv[3]})

  elif argv[1] == 'category':
    db.WriteOneRow('mythnettv_category', 'title', {'title': argv[2],
                                                   'category': argv[3]})

  elif argv[1] == 'group':
    db.WriteOneRow('mythnettv_group', 'title', {'title': argv[2],
                                                'recgroup': argv[3]})

  elif argv[1] == 'http_proxy':
    budget = GetPossible(argv, 4)
    if budget:
      budget = int(budget) * 1024 * 1024
      out.write('Setting proxy budget to %d bytes\n' % budget)

    db.WriteOneRow('mythnettv_proxies', 'url', {'url': argv[2],
                                                'http_proxy': argv[3],
                                                'daily_budget': budget})

  elif argv[1] == 'statistics':
    # Display some simple stats about the state of MythMYTHNETTV
    row = db.GetOneRow('select count(guid) from mythnettv_programs;')
    out.write('Programs tracked: %d\n' % row['count(guid)'])

    for show in db.GetRows('select distinct(title) from mythnettv_programs '
                           'where title is not NULL;'):
      row = db.GetOneRow('select count(guid) from mythnettv_programs where '
                         'title = "%s";' % show['title'])
      out.write('  %s: %d\n' %(show['title'], row['count(guid)']))
    out.write('\n')
    
    row = db.GetOneRow('select count(guid) from mythnettv_programs where '
                       'download_finished is NULL and title is not NULL '
                       'and inactive is NULL;')
    out.write('Programs still to download: %d\n'
              % row['count(guid)'])

    for show in db.GetRows('select distinct(title) from mythnettv_programs '
                           'where title is not NULL and '
                           'inactive is NULL and '
                           'download_finished is NULL;'):
      row = db.GetOneRow('select count(guid) from mythnettv_programs where '
                         'title = "%s" and inactive is NULL '
                         'and download_finished is NULL;'
                         % show['title'])
      out.write('  %s: %d\n' %(show['title'], row['count(guid)']))
    out.write('\n')

    try:
      row = db.GetOneRow('select sum(transfered) from mythnettv_programs;')
      out.write('Data transferred: %s\n'
             % (utility.DisplayFriendlySize(int(row['sum(transfered)']))))
    except:
      # TODO(mikal): I am sure there is a better way of doing this
      dummy = 'blah'

  elif argv[1] == 'log':
    for logline in db.GetRows('select * from mythnettv_log order by '
                              'sequence asc;'):
      out.write('%s %s\n' %(logline['timestamp'], logline['message']))

  elif argv[1] == 'nextdownload':
    filter = GetPossible(argv, 3)
    subtitle_filter = GetPossible(argv, 4)
    for guid in mythnettvcore.NextDownloads(argv[2], filter,
                                            False, subtitle_filter,
                                            out=out):
      out.write('%s\n' % guid)
      prog = program.MythNetTvProgram(db)
      prog.Load(guid)
      out.write('  %s: %s\n\n' %(prog.GetTitle(), prog.GetSubtitle()))

  elif argv[1] == 'cleartodo':
    out.write("""The command you are executing will permanently remove all
shows from the TODO list, as well as any record of shows which have
already been downloaded. Basically you\'ll be back at the start
again, although your preferences will remain set. Are you sure
you want to do this?\n\n""")
    confirm = raw_input('Type yes to do this: ')

    if confirm == 'yes':
      db.ExecuteSql('delete from mythnettv_programs;')
      out.write('Deleted\n')

  elif argv[1] == 'markread':
    filter = GetPossible(argv, 3)
    subtitle_filter = GetPossible(argv, 4)

    for guid in mythnettvcore.NextDownloads(argv[2], filter,
                                            True, subtitle_filter):
      prog = program.MythNetTvProgram(db)
      prog.Load(guid)
      out.write('  %s: %s\n' %(prog.GetTitle(), prog.GetSubtitle()))
      out.write('  (%s)\n\n' % prog.GetDate())

      if FLAGS.prompt:
        out.write('Are you sure you want to mark this show as downloaded?'
                  '\n\n')
        confirm = raw_input('Type yes to do this: ')
      else:
        confirm = 'yes'

      if confirm == 'yes':

        prog.SetImported()
        prog.Store()
        out.write('Done\n')
      out.write('\n')

  elif argv[1] == 'proxyusage':
    proxy = proxyhandler.HttpHandler(db)
    proxy.ReportRecentProxyUsage(out=out)

  elif argv[1] == 'videodir':
    try:
      print 'Video directory is: %s' % utility.GetVideoDir(db)
    except utility.FilenameException:
      print 'No video directory found! Use explainvideodir to debug'

  elif argv[1] == 'explainvideodir':
    utility.ExplainVideoDir(db)
      
  else:
    Usage(out)

if __name__ == "__main__":
  main(sys.argv)

```

Thanks, I've fixed the build for new users, however for anyone that already has this problem it will continue to exist until the db entry for it gets fixed.  Are you familiar with phpmyadmin?

---

### Post by itsdaveperdue on 2008-09-23
> **tgm4883 said:**
> Are you familiar with phpmyadmin?

Not so much.  Is there a walk through somewhere on how to install it or can I make the db changes through the command line?  I thought I saw something about making changes earlier in this thread; is it the same change?

**EDIT:** *I'm sure I can find out how to install it...*

---

### Post by tgm4883 on 2008-09-23
> **itsdaveperdue said:**
> Not so much.  Is there a walk through somewhere on how to install it or can I make the db changes through the command line?  I thought I saw something about making changes earlier in this thread; is it the same change?

**EDIT:** *I'm sure I can find out how to install it...*

If you are familiar with the command line you can change it that way also.  If you would rather use phpmyadmin, then you can apt-get install phpmyadmin, then open a web browser and go to [http://ipaddress/phpmyadmin](http://ipaddress/phpmyadmin)
You will need to do this on the machine that has your mysql server (usually your master backend).

The database is mythconverg
The table is mythnettv_settings
    This table has two columns, "name" and "value", the row we want to change has the name "datadir", the value for you should be "data", we want to change that value to "/var/lib/mythtv/mythnettv".  All of that is without the quotes.  If you run into any problems, let me know and i'll try to help.

---

### Post by itsdaveperdue on 2008-09-23
> **tgm4883 said:**
> 
The database is mythconverg
The table is mythnettv_settings
    This table has two columns, "name" and "value", the row we want to change has the name "datadir", the value for you should be "data", we want to change that value to "/var/lib/mythtv/mythnettv".  All of that is without the quotes.

I went ahead and installed phpMyAdmin and made the change.  It seems to have fixed the issue.  I'll monitor it and report back today or tomorrow.

Thanks again for your help!

---

### Post by itsdaveperdue on 2008-09-23
It is working after completing the steps above.  Thanks again!

P.S.: Did I see someone mention something about creating a MythTV plugin for mythnettv?  It would be cool to at least be able to see what is going to be downloaded and when.  If only I knew how to code I'd be able to help, heh.

---

### Post by tgm4883 on 2008-09-23
> **itsdaveperdue said:**
> It is working after completing the steps above.  Thanks again!

P.S.: Did I see someone mention something about creating a MythTV plugin for mythnettv?  It would be cool to at least be able to see what is going to be downloaded and when.  If only I knew how to code I'd be able to help, heh.

Yes someone above talked about helping with the theming for that.  The issue I have with that is A)  I don't know how to make a frontend plugin, and B) You have to get the feed links from somewhere, and typing those in with a remote would be a PITA.  I suppose it would be nice to have something that shows the next shows to be downloaded, but it isn't very high on my list of things to do.  You can though submit a Blueprint (feature request) at [https://blueprints.launchpad.net/mythbuntu](https://blueprints.launchpad.net/mythbuntu)

---

### Post by itsdaveperdue on 2008-09-24
> **tgm4883 said:**
> A)  I don't know how to make a frontend plugin, and B) You have to get the feed links from somewhere, and typing those in with a remote would be a PITA.  I suppose it would be nice to have something that shows the next shows to be downloaded, but it isn't very high on my list of things to do.

A) Me neither, heh.
B) I had the same thought; seeing the status, items to be downloaded would be cool.  Maybe just have it sitting in the Info Center somewhere.

I'll take a look at that link when I've got some time.

---

### Post by bah1976 on 2008-09-24
Just a quick note to add my successful test.  It's working well - thanks!

---

### Post by wombo on 2008-09-27
Anychance you can add some screenies on your website?

Im going to stay on my old release until I do my rebuild after 8.10 :)

---

### Post by managementboy on 2008-10-13
I am not sure if this is the right place to "bug report" but still:

- When using the torrent feature of mythnettv, bittornado is not a required dependency of mythnettv in the mythbuntu packages even tough it is necessary
- The torrent feature has a hard coded upload rate of 100, which floods my up channel and keeps the torrent from effectively downloading. If this could be a variable that could be set somewhere (database?) it would be nice.
- Somehow, and I have not found why, the cron job tries to repeatedly download a torrent again, and again. This can be seen in the log file and uses up the 3 download attempts within 3 hours (some torrents take a bit longer to download than that)
- Torrents via RSS get named by the link and not by the file name of the .torrent. This leads to always using download.php or similar files being stored at /var/lib/mythtv/mythnettv/ . I suppose this will eventually lead to errors.

---

### Post by tgm4883 on 2008-10-13
> **managementboy said:**
> I am not sure if this is the right place to "bug report" but still:

- When using the torrent feature of mythnettv, bittornado is not a required dependency of mythnettv in the mythbuntu packages even tough it is necessary
- The torrent feature has a hard coded upload rate of 100, which floods my up channel and keeps the torrent from effectively downloading. If this could be a variable that could be set somewhere (database?) it would be nice.
- Somehow, and I have not found why, the cron job tries to repeatedly download a torrent again, and again. This can be seen in the log file and uses up the 3 download attempts within 3 hours (some torrents take a bit longer to download than that)
- Torrents via RSS get named by the link and not by the file name of the .torrent. This leads to always using download.php or similar files being stored at /var/lib/mythtv/mythnettv/ . I suppose this will eventually lead to errors.

Which version of MythNetTV are you using?

---

### Post by managementboy on 2008-10-13
> **tgm4883 said:**
> Which version of MythNetTV are you using?

version 6 revision3 of mythbuntu

---

### Post by managementboy on 2008-10-13
here is the output 

```
tail /var/log/mythtv/mythnettv.log

Downloading http://www.mysite.org/get/1905908
Destination will be /var/lib/mythtv/mythnettv/1905908
Downloading Exter: Exter 3x3 [720P - HDTV - SYS]

Downloading http://www.mysite.org/get/1905908
Now fetching the bittorrent data
Executing: /usr/bin/btdownloadheadless.bittornado --max_upload_rate 60 --display_interval 60 --spew 1 --saveas /var/lib/mythtv/mythnettv/tmpqEREZS /var/lib/mythtv/mythnettv/1905908  (pid 13726)
Bittorrent download finished, kill download processes
```

for some reason it stops right there...

---

### Post by tgm4883 on 2008-10-13
I've sent what doesn't apply to my packaging or to the -gui portion upstream.  

The bittornado part is a recommends as for mythnettv to function you don't NEED bittornado, only if you want to download torrent shows.  Is there an error message that you receive when you try to do that and it isn't installed?

The 2nd and 4th issue i've sent upstream, hopefully a fix will follow soon.

I've sent 3 upstream too, but there is supposed to be checking if a show is already being downloaded so it doesn't try to download it twice.  I've also toyed with the idea of making the cron job daily and having it download 5 shows daily.  I'll wait until I hear what upstream says until I change that.

---

### Post by managementboy on 2008-10-14
> **tgm4883 said:**
> I've sent what doesn't apply to my packaging or to the -gui portion upstream.  

The bittornado part is a recommends as for mythnettv to function you don't NEED bittornado, only if you want to download torrent shows.  Is there an error message that you receive when you try to do that and it isn't installed?

The 2nd and 4th issue i've sent upstream, hopefully a fix will follow soon.

I've sent 3 upstream too, but there is supposed to be checking if a show is already being downloaded so it doesn't try to download it twice.  I've also toyed with the idea of making the cron job daily and having it download 5 shows daily.  I'll wait until I hear what upstream says until I change that.

thanks!

Here are two more outputs of a torrent that is being downloaded, but the "mythnettv update" command flags it as "failure" and adds one more attempt.

```

mythtv    14842  0.0  0.0   3944   556 pts/9    S+   08:04   0:00 /bin/sh -c /usr/bin/btdownloadheadless.bittornado --max
_upload_rate 60 --display_interval 60 --spew 1 --saveas /var/lib/mythtv/mythnettv/tmpt2kWlO /var/lib/mythtv/mythnettv/19
07600                                                                                                                   
mythtv    14843  1.4  0.3 114552 31660 pts/9    R+   08:04   0:55 /usr/bin/python /usr/bin/btdownloadheadless.bittornado 
--max_upload_rate 60 --display_interval 60 --spew 1 --saveas /var/lib/mythtv/mythnettv/tmpt2kWlO /var/lib/mythtv/mythnet
tv/1907600                                                                                                              
mythtv    15954  0.0  0.0   5168   936 pts/25   R+   09:05   0:00 grep --color=auto bt                                   
mythtv@mythtv:~$ ls -al /var/lib/mythtv/mythnettv/tmpt2kWlO                                                               
-rw-r--r-- 1 mythtv mythtv 335M 2008-10-14 09:06 /var/lib/mythtv/mythnettv/tmpt2kWlO                                      
mythtv@mythtv:~$ tail /var/log/mythtv/mythnettv.log -f                                                                    
Downloading http://www.mininova.org/get/1907600                                                                         
Destination will be /var/lib/mythtv/mythnettv/1907600                                                                   
Downloading TheShow: TheShow 3x5 [720P - HDTV - CTU]                                                                      
                                                                                                                        
This is a repeat attempt (2 attempts so far, max is 10)                                                                 
Downloading http://www.thesite.org/get/1907600                                                                         
Now fetching the bittorrent data                                                                                        
Executing: /usr/bin/btdownloadheadless.bittornado --max_upload_rate 60 --display_interval 60 --spew 1 --saveas /var/lib/
mythtv/mythnettv/tmpt2kWlO /var/lib/mythtv/mythnettv/1907600  (pid 15789)                                               
Bittorrent download finished, kill download processes                                                                   
Tue Oct 14 09:00:24 CEST 2008
```

---

### Post by managementboy on 2008-10-14
Found another bug. After downloading a Torrent, the file size in MythTV is the size of the .torrent file, not the final size of the show. Example: .torrent 44 kB but show is 354MB.

---

### Post by managementboy on 2008-10-14
I think I can track the download of torrents not working in a cron to [this ]("http://www.google.de/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.mail-archive.com%2Fdebian-bugs-dist%40lists.debian.org%2Fmsg91739.html&ei=0l_0SI-BEpLO0gXhlOj8Dg&usg=AFQjCNGU9S6TiWGbjE5-AbMPEtz7S7NWcg&sig2=pebiVLVGjKkwuUcS3iqxGQ") bug in the original Debian Packages. It seems that bittornado can not be run headless (cron). Can any one confirm this?

---

### Post by managementboy on 2008-10-14
and another bug: when you import a non existing file (by mistyping) using the "importlocal" option in mythnettv you get a "download job" added to the queue, that can never be completed, keeping all your legitimate downloads from working. Can someone test if it's just me having this problem?

---

### Post by tgm4883 on 2008-10-14
> **managementboy said:**
> Found another bug. After downloading a Torrent, the file size in MythTV is the size of the .torrent file, not the final size of the show. Example: .torrent 44 kB but show is 354MB.

Did this show download?

> **managementboy said:**
> I think I can track the download of torrents not working in a cron to [this ]("http://www.google.de/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.mail-archive.com%2Fdebian-bugs-dist%40lists.debian.org%2Fmsg91739.html&ei=0l_0SI-BEpLO0gXhlOj8Dg&usg=AFQjCNGU9S6TiWGbjE5-AbMPEtz7S7NWcg&sig2=pebiVLVGjKkwuUcS3iqxGQ") bug in the original Debian Packages. It seems that bittornado can not be run headless (cron). Can any one confirm this?

This bug seems to be fixed in hardy.  
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=327505](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=327505)

You could test this by manually running mythnettv from the command line.  Do this command.
```
/usr/share/mythnettv/mythnettv download 1
```

---

### Post by managementboy on 2008-10-14
> **tgm4883 said:**
> Did this show download?


yes it did, and it imported it, but the file size is reported wrong.

> **tgm4883 said:**
> 
This bug seems to be fixed in hardy.  
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=327505](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=327505)

You could test this by manually running mythnettv from the command line.  Do this command.
```
/usr/share/mythnettv/mythnettv download 1
```

running from the command line always works, my problem is the cron that just kills the bittornado process right after it downloads the .torrent file. Right now I am starting the download manually every morning, but thats a bit annoying.

I think a solution could be to use the "screen -S Tornado -d -m" in the cron right before the command to download. But I am not 100% sure.

---

### Post by tgm4883 on 2008-10-14
> **managementboy said:**
> 
I think a solution could be to use the "screen -S Tornado -d -m" in the cron right before the command to download. But I am not 100% sure.

Test that out and let me know how it works.  I'd be happy to add that, but I don't use the bittorrent features of mythnettv so I have nothing to test with.

---

### Post by managementboy on 2008-10-15
> **tgm4883 said:**
> 
This bug seems to be fixed in hardy.  
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=327505](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=327505)


just checked the file /usr/bin/btdownloadheadless.bittornado and the patch in the bugreport is not applied.

my version: bittornado 0.3.18-5

---

### Post by noii on 2008-11-01
I have mythtv (0.21.0+fixes16838-0ubuntu3.1) installed on a single front and backend box (x86_64) running ubuntu (hardy 8.04.1), and have mythnettv (release-6) working having installed it directly from [www.stillhq.com/mythtv/mythnettv/](www.stillhq.com/mythtv/mythnettv/). 

I'd like to try the gui - do I need to uninstall/delete my current mythnettv folder and/or mysql table entries?

Do I need to be using mythbuntu to try this? Or can I just apt-get install mythnettv-gui to give it a go?

---

### Post by tgm4883 on 2008-11-01
> **noii said:**
> I have mythtv (0.21.0+fixes16838-0ubuntu3.1) installed on a single front and backend box (x86_64) running ubuntu (hardy 8.04.1), and have mythnettv (release-6) working having installed it directly from [www.stillhq.com/mythtv/mythnettv/](www.stillhq.com/mythtv/mythnettv/). 

I'd like to try the gui - do I need to uninstall/delete my current mythnettv folder and/or mysql table entries?

Do I need to be using mythbuntu to try this? Or can I just apt-get install mythnettv-gui to give it a go?

mythnettv-gui is just a frontend for mythnettv.  You can install it on a regular ubuntu machine and don't have to do anything to your current installation

---

### Post by noii on 2008-11-01
It took me a while to work out what a [ppa was and how to add one]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories") in ubuntu. Once I'd added the [PPA for Mythbuntu Testing]("https://launchpad.net/~mythbuntu-testing/+archive"), ```
sudo apt-get install mythnettv-gui
``` worked, and the GUI was added to my menu as expected. 

I got an error message about creating a data directory when I opened the gui, so I went and did ```
mkdir data
``` in the /var/lib/mythtv/mythnettv directory. After that it displayed the subscriptions I already had fine - and seems to be working without a hitch.

Nice one, thanks.

---

### Post by managementboy on 2008-11-05
> **managementboy said:**
> just checked the file /usr/bin/btdownloadheadless.bittornado and the patch in the bugreport is not applied.

my version: bittornado 0.3.18-5

Just to close this issue:I have been using mythnettv with bittornado support since I applied the above fix to bittornado (manually) and it works like a charm in a cron job.

---

### Post by tgm4883 on 2008-11-05
> **managementboy said:**
> Just to close this issue:I have been using mythnettv with bittornado support since I applied the above fix to bittornado (manually) and it works like a charm in a cron job.

Which version of Mythbuntu are you using?

---

### Post by Archmage on 2008-11-11
Can someone please help me? I want to try this:

```
sudo su mythtv -c "/usr/share/mythnettv/mythnettv download 1"
1 matches

Downloading http://www.moviemaze.de/media/trailer/4431,special.html?6919
Destination will be /var/lib/mythtv/mythnettv/trailer01-en.m4v
Downloading Film- und Kino-Trailer Videopodcast: Special (en)

Downloading http://feeds.feedburner.com/~r/Film-UndKino-trailerVideopodcast/~5/446117360/trailer01-en.m4v
2008-11-11 20:35:11.863182: downloaded 2 mb (3074048 bytes)
2008-11-11 20:35:15.091477: downloaded 5 mb (6147072 bytes)
Done
Download OK
Importing /var/lib/mythtv/mythnettv/trailer01-en.m4v
Download Error: (<database.MythNetTvDatabase instance at 0x226f7a0>, 'Could not determine the video directory for this machine. Please report this to mythnettv@stillhq.com')
Importing /var/lib/mythtv/mythnettv/trailer01-en.m4v
Couldn't import straggling http://www.moviemaze.de/media/trailer/4431,special.html?6919, removing it from the queue

```

```
sudo su mythtv -c "/usr/share/mythnettv/mythnettv explainvideodir"
Checking storagegroup for an entry where groupname="MythNetTV"
Checking storagegroup for an entry where groupname="Default"
Found /var/lib/mythtv/recordings for OLDHOSTNAME
Checking settings for an entry where value="RecordFilePrefix"
Found /var/lib/mythtv/recordings for OLDHOSTNAME
Found no video directory

```

---

### Post by tgm4883 on 2008-11-11
> **managementboy said:**
> Just to close this issue:I have been using mythnettv with bittornado support since I applied the above fix to bittornado (manually) and it works like a charm in a cron job.

This should be fixed in Jaunty.  Not yet, but I've gotten the upstream author to commit that fix to CVS, and upstream Debian has told me that they will get this fix in before Jaunty is released.  Once it's in Debian, we can sync it here.

---

### Post by Archmage on 2008-11-17
> **Archmage said:**
> Can someone please help me? I want to try this:

Maybe I wansn't making myself clear, but mythnettv isn't working, because it isn't finding the video-directoy. What can I do to make it work?

---

### Post by tgm4883 on 2008-11-25
I'm happy to announce that [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=327505](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=327505) has been fixed upstream and is now in Jaunty in bittornado version 0.3.18-8

---

### Post by JerkyChew on 2008-12-17
I've built a VM to test this on - If I'm understanding it correctly, downloaded video should just show up in my recordings section, correct?

Can somebody provide me with a known-good RSS feed I can plug into this? I've tried several of everything from the Washington Post to Youtube, but nothing seems to work. My log file never shows anything other than:

semmottm@chimichanga:/var/log/mythtv$ tail mythnettv.log -f
0 matches
0 matches
0 matches
0 matches
0 matches

This is a clean build, and my versions are:

Mythtv-backend 0.21.0+fixes18722-0ubuntu1
mythnettv  6-0ubuntu3~hardy
mythnettv-gui 1.0~bzr29-0ubuntu1~hardy  

This is a really exciting product and I'd love to get it working!

---

### Post by tgm4883 on 2008-12-17
> **JerkyChew said:**
> I've built a VM to test this on - If I'm understanding it correctly, downloaded video should just show up in my recordings section, correct?

Can somebody provide me with a known-good RSS feed I can plug into this? I've tried several of everything from the Washington Post to Youtube, but nothing seems to work. My log file never shows anything other than:

semmottm@chimichanga:/var/log/mythtv$ tail mythnettv.log -f
0 matches
0 matches
0 matches
0 matches
0 matches

This is a clean build, and my versions are:

Mythtv-backend 0.21.0+fixes18722-0ubuntu1
mythnettv  6-0ubuntu3~hardy
mythnettv-gui 1.0~bzr29-0ubuntu1~hardy  

This is a really exciting product and I'd love to get it working!

Yep, you should just be able to add the rss feed link and title and the next day bammo, you have shows.  Here is a known working one.  It's not really HD, but it's the best quality one they have for it and IMO it's a good show.
```

Scam School HD  http://revision3.com/scamschool/feed/quicktime-high-definition/
```

---

### Post by JerkyChew on 2008-12-17
Thanks, I added it. You say it will be there tomorrow but won't hitting the "Update Now" button automatically update everything?

A couple bugs (I launch it via terminal):

After adding the feed that manage feeds window doesn't go away, which might be by design, but closing it via the X in the corner gives me "TypeError: destroy() takes no arguments (1 given) in my terminal window.

File - Quit does nothing, I need to click the x in the corner or ctrl-c in the terminal.

---

### Post by tgm4883 on 2008-12-17
> **JerkyChew said:**
> Thanks, I added it. You say it will be there tomorrow but won't hitting the "Update Now" button automatically update everything?

A couple bugs (I launch it via terminal):

After adding the feed that manage feeds window doesn't go away, which might be by design, but closing it via the X in the corner gives me "TypeError: destroy() takes no arguments (1 given) in my terminal window.

File - Quit does nothing, I need to click the x in the corner or ctrl-c in the terminal.

Those aren't bugs, they are feature ;)  But yea, I need to find time to fix those.  You aren't able to close that add subscription window and reopen it either.

You can click update now and check what the next downloaded shows are, but they won't update until your cron.daily gets run, which for me is in the morning.

---

### Post by Archmage on 2009-02-10
I notice a new version and did try it with this. Unfortunatly it is sill not downloading anything. :(

Is there a way to find the problem?

---

### Post by tgm4883 on 2009-02-10
> **Archmage said:**
> I notice a new version and did try it with this. Unfortunatly it is sill not downloading anything. :(

Is there a way to find the problem?

can you post the output of 

```
tail -n 20 /var/log/mythtv/mythnettv.log
```

and also 

```
ls -l /etc/cron.daily/
```

and also

```
ls -l /var/lib/mythtv/
```

also, is this a single system setup or a multi system setup?

---

### Post by Archmage on 2009-02-10
This has been done on my combine front- and backend. (I have more than one frontend, but of course I try to make this run first on the combine back- and frontend.

I did notice that mythtvnet isn't in the hourly cron.

tail -n 20 /var/log/mythtv/mythnettv.log

```

Assuming that audio/mpeg is a video format
Assuming that audio/mpeg is a video format
Assuming that audio/mpeg is a video format
Assuming that video/x-unguessable is a video format
Assuming that audio/mpeg is a video format
Assuming that audio/mpeg is a video format
Assuming that audio/mpeg is a video format
Assuming that audio/mpeg is a video format
Assuming that audio/mpeg is a video format
Assuming that application/octet-stream is a video format
Assuming that application/octet-stream is a video format
Assuming that application/octet-stream is a video format
Assuming that application/octet-stream is a video format
Assuming that application/octet-stream is a video format
Assuming that application/octet-stream is a video format
Assuming that application/octet-stream is a video format
Assuming that application/octet-stream is a video format
Assuming that application/octet-stream is a video format
Assuming that application/octet-stream is a video format
0 matches

```

ls -l /etc/cron.daily/
```

total 64
-rwxr-xr-x 1 root root  633 2008-02-02 05:26 apache2
-rwxr-xr-x 1 root root  219 2008-04-18 17:58 apport
-rwxr-xr-x 1 root root 7680 2008-08-14 18:56 apt
-rwxr-xr-x 1 root root  314 2008-04-04 11:53 aptitude
-rwxr-xr-x 1 root root  502 2007-12-12 16:31 bsdmainutils
-rwxr-xr-x 1 root root   89 2006-06-19 21:14 logrotate
-rwxr-xr-x 1 root root  954 2008-03-12 14:28 man-db
-rwxr-xr-x 1 root root  646 2008-06-26 16:19 mlocate
-rwxr-xr-x 1 root root  119 2008-08-26 18:30 mythbuntu-apple-trailers
-rwxr-xr-x 1 root root  166 2008-05-13 08:22 mythtv-status
-rwxr-xr-x 1 root root  613 2009-01-26 03:38 mythvideo-bulk-updater
-rwxr-xr-x 1 root root 1154 2008-03-07 21:37 ntp
-rwxr-xr-x 1 root root  893 2008-10-07 19:15 optimize_mythdb.pl
-rwxr-xr-x 1 root root 3349 2008-09-09 21:52 standard
-rwxr-xr-x 1 root root 1309 2007-11-23 10:02 sysklogd

```

ls -l /var/lib/mythtv/
```

total 64
drwxrwsr-x 2 mythtv mythtv  4096 2008-04-21 15:03 music
drwxrwxr-x 2 mythtv mythtv 32768 2009-02-09 16:17 mythnettv
drwxrwxr-x 3 mythtv mythtv  4096 2008-12-20 21:32 pictures
drwxrwsr-x 2 mythtv mythtv 20480 2009-02-10 19:01 recordings
drwxrwxr-x 2 mythtv mythtv  4096 2008-11-11 20:17 videos

```

---

### Post by tgm4883 on 2009-02-10
Very odd, can you give the output of 

```
dpkg -l mythnettv
```
```
dpkg -l mythnettv-gui
```
```
ls -l /etc/cron.hourly/
```

---

### Post by jdeslip on 2009-02-12
When I try to use this on Democracy Now - [http://www.democracynow.org/podcast-video.xml](http://www.democracynow.org/podcast-video.xml) (which are mp4 avc1 format videos) - the video when played back in mythfrotend (after being transcoded to avi) play back at fast-forward.  I.e. it looks like it is playing at about 5 speed.  

I edited the video.py to tell mythnettv not to transcode avc1 videos.  The playback is then improved, by the myth internal player still has trouble playing it, and skips around a lot.  Mplayer has no problem with it, and if it stream using flash from the mythweb interface it works good.  

Anyone have a solution for this?  Can I change the mencoder settings or something in video.py?

---

### Post by Archmage on 2009-02-13
Sorry, for the late reply. I was getting the two updates and try to see if it is working. But it is still not working., 

Here are the outputs. Any help would be highly appropriated.

dpkg -l mythnettv
```
Gewünscht=Unbekannt/Installieren/R=Entfernen/P=Vollständig Löschen/Halten
| Status=Nicht/Installiert/Config/U=Entpackt/Fehlgeschl. Konfiguration/
         Halb installiert/Trigger erWartet/Trigger anhängig
|/ Fehler?=(kein)/Halten/R=Neuinst notw/X=beide (Status, Fehler: GROSS=schlecht)
||/ Name                              Version                           Beschreibung
+++-=================================-=================================-==================================================================================
ii  mythnettv                         7-0ubuntu4~intrepid               Plugin to download RSS video feeds

```

dpkg -l mythnettv-gui
```
Gewünscht=Unbekannt/Installieren/R=Entfernen/P=Vollständig Löschen/Halten
| Status=Nicht/Installiert/Config/U=Entpackt/Fehlgeschl. Konfiguration/
         Halb installiert/Trigger erWartet/Trigger anhängig
|/ Fehler?=(kein)/Halten/R=Neuinst notw/X=beide (Status, Fehler: GROSS=schlecht)
||/ Name                              Version                           Beschreibung
+++-=================================-=================================-==================================================================================
ii  mythnettv-gui                     1.0~bzr36-0ubuntu3~intrepid       Gui frontend for MythNetTV

```

ls -l /etc/cron.hourly/
```
total 8
-rwxr-xr-x 1 root root 207 2009-02-09 20:08 mythnettv
-rwxr-xr-x 1 root root 502 2008-10-22 02:03 mythvideo-bulk-updater

```

I hope that the different language isn't a problem. For me everything looks okay.

But I'm sorry for the spamming but the new version seems to have changed the output of the other logs. I'll post the new ones here:


tail -n 20 /var/log/mythtv/mythnettv.log
```
***** Starting update and download at 08:06 02/13/2009*****
0 matches

0 matches
0 matches
0 matches
0 matches
0 matches
0 matches
0 matches
0 matches
0 matches
0 matches
0 matches
0 matches
0 matches
0 matches
0 matches

```

ls -l /etc/cron.daily/
```
total 68
-rwxr-xr-x 1 root root  633 2008-02-02 05:26 apache2
-rwxr-xr-x 1 root root  219 2008-04-18 17:58 apport
-rwxr-xr-x 1 root root 7680 2008-08-14 18:56 apt
-rwxr-xr-x 1 root root  314 2008-04-04 11:53 aptitude
-rwxr-xr-x 1 root root  502 2007-12-12 16:31 bsdmainutils
-rwxr-xr-x 1 root root   89 2006-06-19 21:14 logrotate
-rwxr-xr-x 1 root root  954 2008-03-12 14:28 man-db
-rwxr-xr-x 1 root root  646 2008-06-26 16:19 mlocate
-rwxr-xr-x 1 root root  119 2008-08-26 18:30 mythbuntu-apple-trailers
-rwxr-xr-x 1 root root  469 2009-02-10 20:07 mythnettv
-rwxr-xr-x 1 root root  166 2008-05-13 08:22 mythtv-status
-rwxr-xr-x 1 root root  613 2009-01-26 03:38 mythvideo-bulk-updater
-rwxr-xr-x 1 root root 1154 2008-03-07 21:37 ntp
-rwxr-xr-x 1 root root  893 2008-10-07 19:15 optimize_mythdb.pl
-rwxr-xr-x 1 root root 3349 2008-09-09 21:52 standard
-rwxr-xr-x 1 root root 1309 2007-11-23 10:02 sysklogd

```

ls -l /var/lib/mythtv/
```
total 64
drwxrwsr-x 2 mythtv mythtv  4096 2008-04-21 15:03 music
drwxrwxr-x 2 mythtv mythtv 32768 2009-02-09 16:17 mythnettv
drwxrwxr-x 3 mythtv mythtv  4096 2008-12-20 21:32 pictures
drwxrwsr-x 2 mythtv mythtv 20480 2009-02-13 20:15 recordings
drwxrwxr-x 2 mythtv mythtv  4096 2008-11-11 20:17 videos

```

---

### Post by Archmage on 2009-02-14
Okay, we are slowly getting here somewhere. Thanks for your patience.

I did notice that it seems to download. I notice some files in the folder /var/cache/mythtv/ (that I did configure as a temporary folder in the Mythnettv-gui). However they are not showing in the watch recording dialog, like they should, aren't they?

What are the needed steps to make them appear? I think it is now only a configuration-problem, isn't it?

---

### Post by Archmage on 2009-02-14
I found this in my logs:

```
Download Error: (<database.MythNetTvDatabase instance at 0x2794b00>, 'Could not determine the video directory for this machine. Please report this to mythnettv@stillhq.com')
```

Okay, what video-folder does it mean? The ones where I storage my videos or the ones where I storage my recordings? And how can I set them up?

I have the standard folder for my recordings and have an different partition for my videos (/space/Videos/).

---

### Post by tgm4883 on 2009-02-14
> **Archmage said:**
> I found this in my logs:

```
Download Error: (<database.MythNetTvDatabase instance at 0x2794b00>, 'Could not determine the video directory for this machine. Please report this to mythnettv@stillhq.com')
```

Okay, what video-folder does it mean? The ones where I storage my videos or the ones where I storage my recordings? And how can I set them up?

I have the standard folder for my recordings and have an different partition for my videos (/space/Videos/).

Sounds like you don't have storage directories setup.  Can you please post the output of

```
mythnettv videodir
mythnettv explainvideodir
```

---

### Post by Archmage on 2009-02-14
I think we are on the right way

mythnettv videodir
```
No video directory found! Use explainvideodir to debug
```

mythnettv explainvideodir
```
Checking storagegroup for an entry where groupname="MythNetTV"
Checking storagegroup for an entry where groupname="Default"
Found /var/lib/mythtv/recordings for OLDHOSTNAME
Checking settings for an entry where value="RecordFilePrefix"
Found /var/lib/mythtv/recordings for OLDHOSTNAME
Found no video directory
```

I'm puzzled what this OLDHOSTNAME means.

My hostname is hometv.desktop, but when I look on my harddrive the recordings are on /var/lib/mythtv/recordings.

---

### Post by tgm4883 on 2009-02-14
Do you have storage groups setup in mythtv-setup?

---

### Post by Archmage on 2009-02-15
> **tgm4883 said:**
> Do you have storage groups setup in mythtv-setup?

Thanks. That was the thing I was missing. It now works. Although I'm puzzled, why I can't add all channels on it. What kind of requirements do I need for a channel?

---

### Post by tgm4883 on 2009-02-15
> **Archmage said:**
> Thanks. That was the thing I was missing. It now works. Although I'm puzzled, why I can't add all channels on it. What kind of requirements do I need for a channel?

I'm a little confused.  What do you mean add all channels on it?  Are you talking about adding channels in mythtv-setup, or are you talking about subscribing things to mythnettv?

---

### Post by Archmage on 2009-02-15
> **tgm4883 said:**
> I'm a little confused.  What do you mean add all channels on it?  Are you talking about adding channels in mythtv-setup, or are you talking about subscribing things to mythnettv?

I'm sorry for this confusion. I did mean subsribing things to mythnettv. I notice that when I did add on some things in the mythnettv-gui, it say "subscribing to abc", but abc will never appear to the subscribed things.

---

### Post by tgm4883 on 2009-02-15
> **Archmage said:**
> I'm sorry for this confusion. I did mean subsribing things to mythnettv. I notice that when I did add on some things in the mythnettv-gui, it say "subscribing to abc", but abc will never appear to the subscribed things.

Are you saying that it's not showing up in your list of subscribed shows, or it's not showing any shows waiting to be downloaded?  Are you adding both a link and a title for the subscription?

---

### Post by Archmage on 2009-02-16
> **tgm4883 said:**
> Are you saying that it's not showing up in your list of subscribed shows, or it's not showing any shows waiting to be downloaded?  Are you adding both a link and a title for the subscription?

It isn't showing up in my list of subscribed shows, although I'm adding the link and a show-title.

E.g. I can't add the link below as a new show:

```
http://feeds2.feedburner.com/TimosHDMovieTrailers
```

I guess this is because of the special format, isn't it?

---

### Post by tgm4883 on 2009-02-16
> **Archmage said:**
> It isn't showing up in my list of subscribed shows, although I'm adding the link and a show-title.

E.g. I can't add the link below as a new show:

```
http://feeds2.feedburner.com/TimosHDMovieTrailers
```

I guess this is because of the special format, isn't it?

I didn't try to download any shows, but that link worked fine for me adding it to subscriptions and I updated my download list and it was going to download some of the shows from there.  I'm not sure why it's not working for you.  

Perhaps you should try starting mythnettv-gui from the command line "mythnettv-gui" and then try adding the subscription.  You should see any errors in the terminal window.

---

### Post by Archmage on 2009-02-17
> **tgm4883 said:**
> Perhaps you should try starting mythnettv-gui from the command line "mythnettv-gui" and then try adding the subscription.  You should see any errors in the terminal window.

When I got this, I receive the following message:
```
sh: Syntax error: Unterminated quoted string
```

But than I realize that I want to subscribe the feed with the name "Timo**'**s HDMovies Trailers". I did try it without the **'** and than it works. It seems that special chars are not allowed there.

---

### Post by tgm4883 on 2009-02-17
> **Archmage said:**
> When I got this, I receive the following message:
```
sh: Syntax error: Unterminated quoted string
```

But than I realize that I want to subscribe the feed with the name "Timo**'**s HDMovies Trailers". I did try it without the **'** and than it works. It seems that special chars are not allowed there.

Ah, that would be the problem.  Please file a bug about that here [https://blueprints.edge.launchpad.net/mythnettv](https://blueprints.edge.launchpad.net/mythnettv)

EDIT

Actually, this seems to be the same as this bug.  Please post a comment to this bug saying that it affects you to.
[https://bugs.edge.launchpad.net/mythnettv/+bug/328626](https://bugs.edge.launchpad.net/mythnettv/+bug/328626)

---

### Post by Archmage on 2009-03-04
The bug is already reported.

So far I'm quite happy with MythnetTV, but I'm still thinking that it isn't download and showing me everything that I'm subscribing too.

E.g. I'm notice that I can never "watch" a mp3-podcast. Is there a way to make them also apear at the "watch recordings" in MythTV?

I know that this seems to be stuipid, but I really like the idea to have one point where I can "watch" all. Beside the fact that I LOVE the option to speed up the output to save time.

---

### Post by tgm4883 on 2009-03-04
> **Archmage said:**
> The bug is already reported.

So far I'm quite happy with MythnetTV, but I'm still thinking that it isn't download and showing me everything that I'm subscribing too.

E.g. I'm notice that I can never "watch" a mp3-podcast. Is there a way to make them also apear at the "watch recordings" in MythTV?

I know that this seems to be stuipid, but I really like the idea to have one point where I can "watch" all. Beside the fact that I LOVE the option to speed up the output to save time.

Yea, I think it only shows you stuff it knows about.  So audio only stuff I don't think it shows.  This should be an easy change, file a bug on launchpad and I'll get Mikal to take a look at it.

---

### Post by Dysport on 2009-06-28
Hi, I'm having a little problem with MythNetTV: I can't delete the shows added by MythNetTV. Neither when I've already watched it nor when I haven't. Any suggestions?
Other than that it's running really smooth, especially with the GUI. Great program!

---

### Post by tgm4883 on 2009-06-28
> **Dysport said:**
> Hi, I'm having a little problem with MythNetTV: I can't delete the shows added by MythNetTV. Neither when I've already watched it nor when I haven't. Any suggestions?
Other than that it's running really smooth, especially with the GUI. Great program!

Thats odd.  Can you post your backend logs?

---

### Post by Dysport on 2009-06-29
Thanks for the tip. It revealed the following issue
```
dysport@mythtv-box:~$ tail /var/log/mythtv/mythbackend.log
2009-06-29 13:20:53.037 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-29 13:21:52.851 Error deleting '/var/lib/mythtv/recordings/1245937110_dok_20090611_201102_526k.avi' could not open 
			eno: **Permission denied (13)**
2009-06-29 13:21:52.892 Delete Error '/var/lib/mythtv/recordings/1245937110_dok_20090611_201102_526k.avi'
			eno: Permission denied (13)
2009-06-29 13:21:52.893 Error deleting file: /var/lib/mythtv/recordings/1245937110_dok_20090611_201102_526k.avi. Keeping metadata in database.
2009-06-29 13:21:54.433 MainServer::HandleAnnounce Playback
2009-06-29 13:21:54.439 adding: mythtv-box as a client (events: 0)
2009-06-29 13:21:54.441 MainServer::HandleAnnounce FileTransfer
2009-06-29 13:21:54.445 adding: mythtv-box as a remote file transfer

```

Silly me, not thinking of the fact that it could be a permission issue :rolleyes:
After running *sudo chown mythtv:mythtv -R /var/lib/mythtv/recordings* the deleting works fine :cool:

Okay so the cronjob ran successfully for the first time (just had to change it in the /etc/crontab from 6 am. to a reasonable time :)). I think everything's working now as it should so tgm4883 thank you very much for your quick reply!! 
However in the mythnettv.log it says
```
***** Starting update and download at 13:42 06/29/2009*****
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
0 matches

```
when I execute manually I get the same warning, after that it works and downloads as it should. So no big deal, just thought I'd mention it.
Once again: Great tool \\:D/

---

### Post by Dysport on 2009-07-06
Just posting a tiny little script I wrote - might be useful to other MythNetTV-users. I set up [automatic shutdown]("http://www.mythtv.org/wiki/ACPI_Wakeup") as it's described in the official MythTV-wiki. Also I wanted MythTV to first finish all the transcoding/flagging jobs and then shut down: [mythshutdown --check]("http://www.mythtv.org/wiki/Mythwelcome") takes care of that (no need to reinvent the wheel).
But I also wanted MythTV to wait until MythNetTV finished downloading, for that matter I wrote a little python script.

For everyone who doesn't know how to do this: here is how you set it up on your MythTV-Box.
First, download the attached script to your home folder. Then open a terminal and type:
```

:~$ sudo mv mythtv_shutdowncheck.py.txt /usr/local/bin/mythshutdowncheck.py
:~$ sudo chmod +x /usr/local/bin/mythshutdowncheck.py

```

Lastly you need to adjust your settings either in mythsetup or mythweb:

---

### Post by blahmartinblah on 2009-07-16
Finally got my install working on mythbuntu and it looks quite cool. 

1 question though not specific to mythnettv - how much content is available through syndication like this? I checked a few TV station websites that I hoped to be able to download their content from, and they don't have any links to syndication files.

Martin.

---

### Post by mlmurray on 2009-09-23
> **blahmartinblah said:**
> Finally got my install working on mythbuntu and it looks quite cool. 

1 question though not specific to mythnettv - how much content is available through syndication like this? I checked a few TV station websites that I hoped to be able to download their content from, and they don't have any links to syndication files.

Martin.


Check out these two sites:  
[http://www.ezrss.it/](http://www.ezrss.it/)
[http://showrss.karmorra.info/](http://showrss.karmorra.info/)

-Mark

---

### Post by Dysport on 2009-11-30
I've set up a new MythTV-Box with Ubuntu 8.10. Is there any way I can get the mythnettv-gui running on Intrepid? Seems not to be in the repositories.
Thanks for your help!

PS: Before anyone asks, I need it to be Intrepid because the ATI driver for my vga-card is not available for the new X-server in Jaunty.

---

### Post by tgm4883 on 2009-11-30
There isn't anything special about the mythnettv packages that should require a specific version of ubuntu installed. You could probably just download the .deb files and install them.

I'm not sure how well it would work with 0.22 though, so if you have that installed you have been warned.

---

### Post by Dysport on 2009-12-01
Install from the .deb didn't work (unsatisfiable dependency: python - even though I have installed all necessary dependencies…), installing from the source however worked. Of course I had to set up the cron-job manually, but it seems to work flawlessly, thanks! 
The only problem I have encountered so far is that for some reason it doesn't seem to read my torrent-rss feed from showrss.karmorra.info, but I figure that's not a GUI problem as trying from the terminal doesn't change anything.

---

### Post by Singing Dwarf on 2009-12-02
I'm hoping to install and test this in 9.10 Karmic - I'm new to Mythbuntu - is this possible?

From looking at [https://launchpad.net/~mythbuntu/+archive/testing?field.series_filter=karmic]("https://launchpad.net/%7Emythbuntu/+archive/testing?field.series_filter=karmic") and filtering on Karmic, it doesn't appear to be?

---

### Post by Archmage on 2009-12-27
> **Singing Dwarf said:**
> From looking at [https://launchpad.net/~mythbuntu/+archive/testing?field.series_filter=karmic]("https://launchpad.net/%7Emythbuntu/+archive/testing?field.series_filter=karmic") and filtering on Karmic, it doesn't appear to be?

I think it is in the normal repros, at least I could install it without any additional repros.

I have some questions.

Lately I seem to have problems subscribing. The GUI won't work

```
Traceback (most recent call last):
  File "/usr/share/mythnettv/mythnettv", line 637, in <module>
    main(sys.argv)
  File "/usr/share/mythnettv/mythnettv", line 394, in main
    mythnettvcore.Subscribe(argv[2], argv[3])
IndexError: list index out of range
```

And text subscribing will drop any space between the names. E.g. the name "A very interesting feed that has a lot of videos that I like and want to see" will just be describe as "A".

BTW: Is there a easy way to edit the subscribes? (E.g. editing, deleting) - like a nice text-config that I can edit?

---

### Post by tgm4883 on 2009-12-30
> **Archmage said:**
> I think it is in the normal repros, at least I could install it without any additional repros.

I have some questions.

Lately I seem to have problems subscribing. The GUI won't work

```
Traceback (most recent call last):
  File "/usr/share/mythnettv/mythnettv", line 637, in <module>
    main(sys.argv)
  File "/usr/share/mythnettv/mythnettv", line 394, in main
    mythnettvcore.Subscribe(argv[2], argv[3])
IndexError: list index out of range
```

And text subscribing will drop any space between the names. E.g. the name "A very interesting feed that has a lot of videos that I like and want to see" will just be describe as "A".

BTW: Is there a easy way to edit the subscribes? (E.g. editing, deleting) - like a nice text-config that I can edit?

There isn't, and probably wont be any development on mythnettv-gui anymore. With upstream mythtv creating miro-bridge and upstream mythnettv seemingly stopping development I've lost the urge to keep developing the -gui. If anyone wants to take it over, go ahead.

---

