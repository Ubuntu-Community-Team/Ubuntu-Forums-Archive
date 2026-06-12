---
title: "Jamu and Video scan"
date: 2010-04-15
forum: Mythbuntu
---

### Post by jbman on 2010-04-15
Hi guys,

If I have Jamu to autoscan my library via the cron job in MCC does it do a video scan first to check for any new shows? Or does it only scan for what it can see since I last did a manaual scan from mythvideo?

Cheers,

---

### Post by xinix on 2010-04-15
Personally I loathe what jamu has done for my mtythvideo stuff.  The fan art would stop loading and some iso files would stop working.  I have had zero metadata/fan art problems since I removed the jamu mythvideo cron scripts.

It works great for TV shows.

---

### Post by iamlindoro on 2010-04-15
> **xinix said:**
> Personally I loathe what jamu has done for my mtythvideo stuff.  The fan art would stop loading and some iso files would stop working.  I have had zero metadata/fan art problems since I removed the jamu mythvideo cron scripts.

It works great for TV shows.

The above issues have all long since been fixed in Jamu, and it also sounds like maybe you hadn't enabled auto-builds?  Ubuntu 9.10 went out with a version *before* .22 that was labeled as .22.  By the .22 release, the bug that would (in the case of some misconfigured systems) cause certain files metadata to break had been fixed.

---

### Post by larsolav on 2010-04-15
> **iamlindoro said:**
> The above issues have all long since been fixed in Jamu, and it also sounds like maybe you hadn't enabled auto-builds?  Ubuntu 9.10 went out with a version *before* .22 that was labeled as .22.  By the .22 release, the bug that would (in the case of some misconfigured systems) cause certain files metadata to break had been fixed.

I got autobuilds enabled, and I still have the JAMU problem with ISOs. I thought the problem with them is that they can't be used in storage groups and that JAMU only works with files in storage groups. Why JAMU still borks my manually downloaded meta fan art when it runs is slightly confusing to me...

---

### Post by RDV on 2010-04-15
jbman,
    The Jamu cron job that updates MythVideo metadata (-M) will only update videos that have a IMDB/TMDB/TVDB number and will skip any video that do not have reference number. If you are not doing a mass addition of new videos then use the built in MythVideo 'w" option. Jamu's general MythVideo value is for your initial mass updated of metadata and images and then regular maintenance of those videos to add missing images and/or metadata as they become available on TVDB or TMDB. When using the MythVideo "w" method the reference number is set and Jamu will include that video when it does it's next maintenance (-M) run.
    

xinix,
    The only relationship to image loading that Jamu has is updating a video's MythVideo record for the location of an image that matches the reference number from TVDB and/or TMDB. For the movies the actual reference number is used in the image file name while TVDB videos have the Series name and season number. To Jamu iso files are just video files and jamu is not relevant on whether they play or not. 


larsolav,
    Jamu works with both storage groups and local FE file paths including a mixture of the two. As far as manually downloaded image are concerned there could be more than one possibility. The first thing I would try is to run Jamu from a terminal session with the "-MVf" options. This will not do any updating but will display which settings Jamu is using. At the very top of the output is information on which directory paths that Jamu will use to find your videos files and which image directories it will use. They may not be what you are expecting and will need to be proper configuration. Jamu only uses the image paths as set in the Myth data base for the back end jamu is running on (identified by hostname).
    
    If your manually downloaded images have the same path and file name that is stored for that specific videos MythVideo record then Jamu will not over write or change that image. If you want Jamu to ignore specific videos then change the reference number to '99999999' eight nines. As stated above Jamu has not special logic or effect on iso files.
    

In the end Jamu is an optional tool and in the Lucid release of Mythbuntu a Jamu MCC plug-in is available which will allow you to easily enable/disable the Jamu con jobs.

---

### Post by larsolav on 2010-04-15
RDV, thanks for the explanation! I'll have to check out my settings when I get home. 

I really like what JAMU does with the TV recordings. When I said manually downloaded art, I really meant the stuff that is downloaded when you press i and select to download metadata and images, so I believe I manually do what JAMU is supposed to do automatically. Then after JAMU has run overnight the downloaded fan art does not appear for ISO files, but still remains for Video_TS folders... I guess I just have to tinker with some settings as you mention...

---

### Post by RDV on 2010-04-15
larsolav,
    Jamu will not process any VIDEO_TS folders. That is a stated under limitations on the Jamu wiki page. 

Instead of using the MythVideo "i" option to update your metadata and images use "w" as it is faster due to less menus to transverse.

If you supply a iso file name I can test if there are any issue on my local machine. Also please run from a terminal "./jamu -v" and supply the version number output.

---

### Post by xinix on 2010-04-15
> **RDV said:**
> 
    The only relationship to image loading that Jamu has is updating a video's MythVideo record for the location of an image that matches the reference number from TVDB and/or TMDB. For the movies the actual reference number is used in the image file name while TVDB videos have the Series name and season number. To Jamu iso files are just video files and jamu is not relevant on whether they play or not. 

I understand that Jamu should only affect the fanart, but it is an interesting coincidence that my playback issues could be fixed by reseting the metadata and went away completely after I disabled the scripts for mythvideo.  I was using 0.22+fixes from the very beginning and am on 0.23 currently.

---

### Post by RDV on 2010-04-16
xinix,
    Jamu downloads all image types: posters, banners (TV only) and fanart. The same naming conventions and processing is used for for all three image types. So if you are only having problems with fanart it is likely a configuration issue.

---

### Post by jbman on 2010-04-16
So if a dump some new files into my video share, will jamu pick them up and see what it can do with them? Or do I need to do a scan in mythvideo before jamu will see them?

I am not using storage groups on my setup. So I am wondering if I need to scan each time I add new videos for them to be visble for me to play and for jamu to read and get data for.

---

### Post by xinix on 2010-04-16
The images are downloaded just fine, at least when I manually navigate to the "download metadata" button.  And it, at first, works fine.  But at some point during the day the fanart will no longer load even though the file is still there.  Also an iso that was working before just fine will stop loading.  Disabling the cron scripts solved this.  Maybe it's not Jamu itself, but something is triggered in those scripts that messes things up and I don't mind manually telling it to grab the metadata/art when a new movie is added.

If this a configuration issue then it's a problem with the default configs because I haven't done anything special with mine.

---

### Post by RDV on 2010-04-16
jbman,
    Jamu will see the videos BUT as they do not have reference numbers (IMDB/TMDB/TVDB) they will be ignored. When they have the reference number either through MythVideo or through one of the Jamu options (-MI or -MG or in 0.23 -MR), Jamu will include the new videos with reference numbers in any maintenance processing.

---

### Post by jbman on 2010-04-16
Make perfect sense to me now.

I will sort the numbers and watch the magic happen.

Cheers for the great script.

Only hassle I have found is its not ignoring the folders I am adding while using 0.23 from the autobuilds.

I put this in the conf file

[ignore-directory]
ignore01: /myth/media/video/Music.Video (Music.Video is the folder name the full stop is meant to be there)

but I still see the scanning of that folder happening

---

### Post by dannyboy79 on 2010-04-16
i seem to be having a problem running jamu.
i issue:
/usr/share/mythtv/mythvideo/scripts/jamu.py -l en -C "/home/daniel/.mythtv/jamu.conf" -MV > "/home/daniel/jamu.log"
I tail  the log file and it seems to be stuck at a certain movie. Never Back DOwn. The process is still there  within ps aux | grep python but the log file isn't growing anymore?

So is it my understanding that I must first run through an entire Interactive mode jsut to fill in the imdb or tmdb numbers, so that then I can run a mass update? I am running jamu version 0.7.2, can I run the -MG option. will that just guess based on the title of the movie? most of my movies are named accurately. Except I do have some that I ripped from my dvd colllection into 2 parts, those are named home alone.[1].avi and home alone.[2].avi. I had to do this for XBMC, it's movie data collector ignores anything within the brackets. Will jamu or mythvideo handle this ok?

---

### Post by RDV on 2010-04-16
dannyboy79,
I tried Jamu with option (-MI) with a filename "Never Back DOwn.avi" and did not have a problem. Try to update that video files metadata in MythVideo with the "w" option. After that run Jamu again with -M and see if the issue disappears.

As you are running Jamu v0.7.2 update to v0.7.3 then you can use a new faster option to get your reference numbers (-MR). Unlike (-MI) it just focuses on getting the references number and skips the metadata and image downloads that slows down the (-MI). After running with -MR then run jamu with -M and the video metadata and images will be updated. 

As you suggested you can run with -MG if you trust your file names, but at least a few mistakes will be made which you will need to discover and correct. Many people which trust their file names do their mass updates using Jamu runs of these options in this order "-MG", "-MR" and last "-M".

---

### Post by RDV on 2010-04-16
jbman,
I tried the ignore directory issue you mentioned and did not have a problem. Here is the exact configuration entry I tried. With it the videos are ignored with out it the videos are found.

[ignore-directory]
ignore01: /media/video/0Review/Music.Video

Is there a chance you are putting quotes around the directory as that will not work?

I am using storage groups and did not try that test with a front end video path setting but I do not see why that would make a difference if it actually does.

---

### Post by dannyboy79 on 2010-04-16
> **RDV said:**
> dannyboy79,


As you are running Jamu v0.7.2 update to v0.7.3 
you know I tried to. i downloaded the file from trunk, jamu.py, to my windows computer, then i used winscp to transfer it to my backend mythtv server, when I try to run it though, i get an error message like this:
: No such file or directory
It's really weird. I checked the permissions and owner/group, they are the same as jamu.py version 0.7.2. so i don't know what i could've done wrong. any thoughts on this so that I can use jamu.py version 0.7.3?

don't know what I did last time, tried getting it again from trunk, got it and it's running. However, when I run this command:
/usr/share/mythtv/mythvideo/scripts/jamu.py -l en -C "/home/daniel/.mythtv/jamu.conf" -MG > "/home/daniel/jamu.log"
it's just sitting there and last thing on the screen is about some files it was going to skip because they are subtitle files. That's all that's in the jamu.py terminal that is running. WHen I try to tail the jamu.log, nothing is in the file. Am I doing something wrong? It appears like it only works in interactive mode, all other ways just appear to freeze. Although, ps aux | grep python still shows it there. it's also still in top. I wish I could see that it was still working in the terminal that I ran it in. Why isn't it logging to the /home/daniel/jamu.log file?

how can I tell when jamu.py is truely done. the python process is gone from top that I can see, but the terminal window I ran jamu.py  is still just sitting at this line:
! Warning: Skipping non-video file name: (/media/fat32/movies/The Showdown.srt)

it didn't go back to a prompt. that's what I mean, what gives? any help much appreciated.

so I finally just control C out of it, this is what it returned:
^C^C^C^C^CTraceback (most recent call last):
  File "/usr/share/mythtv/mythvideo/scripts/jamu.py", line 6429, in <module>
    main()
  File "/usr/share/mythtv/mythvideo/scripts/jamu.py", line 6414, in main
    process.processMythTvMetaData()
  File "/usr/share/mythtv/mythvideo/scripts/jamu.py", line 5710, in processMythTvMetaData
    inetref = self._getTmdbIMDB(available_metadata['title'])
  File "/usr/share/mythtv/mythvideo/scripts/jamu.py", line 3323, in _getTmdbIMDB
    movies_found = imdb_access.search_movie(tmp_title.encode("ascii", 'ignore'))
  File "/usr/lib/pymodules/python2.6/imdb/__init__.py", line 381, in search_movie
    res = self._search_movie(title, results)
  File "/usr/lib/pymodules/python2.6/imdb/parser/http/__init__.py", line 444, in _search_movie
^C^C
Should I jsut let it run forever? This is over SSH, how can I fork this into the background so that if I close hte ssh session, jamu.py will continue to run?

yet even more weird, if I just run jamu.py -C /home/daniel/.mythtv/jamu.conf -f, (the -f states per the script: ( Display in alphabetical order the state of all configuration variables ))it has a bunch of weird settings like these:

allgraphicsdir (/home/daniel)    - What does this mean? I set all the SG up for fanart, banners,  coverart, screenshots, etc etc

config_file (jamu-example.conf)    -HUH? I already told it what config file to use using -C switch. Plus I read that it's suppose to automagically use the jamu.conf from the persons home directory who's running it.
mythtv_guess (False)    - What does this mean?\

Worse yet, I am running it with the -MG option and i am seeing this now:

2010-04-16 16:05:05.267 Python Database Connection: Using connection settings from /home/daniel/.mythtv/config.xml
2010-04-16 16:05:18.287 Python Database Connection: Using connection settings from /home/daniel/.mythtv/config.xml
2010-04-16 16:05:31.124 Python Database Connection: Using connection settings from /home/daniel/.mythtv/config.xml
themoviedb.org Search Results:
 1 -> Watchmen (2009)                                    # [http://www.themoviedb.org/movie/13183](http://www.themoviedb.org/movie/13183)
 2 -> Watchmen: The Complete Motion Comic                # [http://www.themoviedb.org/movie/16542](http://www.themoviedb.org/movie/16542)
 3 -> Watchmen - The Ultimate Cut (2009)                 # [http://www.themoviedb.org/movie/25247](http://www.themoviedb.org/movie/25247)
 4 -> Tales of the Black Freighter (2009)                # [http://www.themoviedb.org/movie/16440](http://www.themoviedb.org/movie/16440)
 5 -> 99999999 # Set this video to be ignored by Jamu with a reference number of '99999999'
Direct search of themoviedb.org # [http://themoviedb.org/](http://themoviedb.org/)
Enter choice:
("Enter" key equals first selection (1)) or input a zero padded 5 digit movie TMDB id number, ? for help):

I didn't leave anything from teh output out either, it doesn't even tell me what movie it's trying to find info for? How come the -MIV shows me what movie it's looking for so then I know which number to press where as the -MG doesn't even show you what movie it's working on? not to mention, I thought the -MG was going to guess what movie it should download info for? Not just sit there.
I am using 0.7.3 by the way

---

### Post by RDV on 2010-04-16
dannyboy79,
I will answer your other questions but here is a quick comment, TMDB is down for the day (16APR2010 17:00EST). Try this url below and see the message. 

[http://www.themoviedb.org/search](http://www.themoviedb.org/search)

Jamu has long timeouts waiting for the URL calls to TMDB and TVDB. That may be what you are seeing at least today. When something is taking a very odd amount of time always check that TVDB and TMDB sites are working as they have issues from time to time.

---

### Post by dannyboy79 on 2010-04-16
> **RDV said:**
> dannyboy79,
I will answer your other questions but here is a quick comment, TMDB is down for the day (16APR2010 17:00EST). Try this url below and see the message. 

[http://www.themoviedb.org/search](http://www.themoviedb.org/search)

Jamu has long timeouts waiting for the URL calls to TMDB and TVDB. That may be what you are seeing at least today. When something is taking a very odd amount of time always check that TVDB and TMDB sites are working as they have issues from time to time.

thanks for the heads up. i will give up for awhile. also, I would really really appreciate answers to all my questions.

---

### Post by RDV on 2010-04-16
dannyboy79,
    Here are answers to the many questions in your post:
    
1) "... i get an error message like this: No such file or directory ..."
I have no idea what the issue is but you certainly are not using a usual way to updated Jamu. Check this link for the changeset for Jamu v0.7.3 as there was more than one file involved in the update:
[http://svn.mythtv.org/trac/changeset/24096](http://svn.mythtv.org/trac/changeset/24096)

2) "... it's just sitting there and last thing on the screen..."
Likely due to TMDB being down and long time outs for the URL calls.

3) "...! Warning: Skipping non-video file name: (/media/fat32/movies/The Showdown.srt) ..."
These are just warning that the file is not a video file. If you see that message Jamu has already moved to another file. When you add the "V" verbose option e.g. -MGV you will get a lot more information in the log and is better to track progress if you are tailing the log.

4) "... it has a bunch of weird settings like these: ..."
Jamu has many options and uses some that are not related to MythTV. Some of the options you see listed by running with -f would not even be used when you use Jamu with MythTV. If you want to see the settings Jamu uses with MythTV you should run these options instead "-MVf" the (M) tells Jamu that you are using Jamu for MythTV. This is especially relevant when you want to see what directories Jamu will reference for videos and images. The "allgraphicsdir" is one of the settings that is irrelevant when using Jamu for MythTV.

5) "... config_file (jamu-example.conf) -HUH? ..."
If you open your jamu.conf file you will likely see this entry "[File jamu-example.conf]". This just means you never changed the name in this setting. You could have more than one config file. Not changing this name has does no harm at all. The entry is only for documentation purposes.

6) "... jamu.py -C /home/daniel/.mythtv/jamu.conf ..."
An FYI the MythTV 0.23 version of Jamu looks for "~/.mythtv/jamu.conf" by default so you could get rid of the "-C /home/daniel/.mythtv/jamu.conf" if you wished as it is now redundant.

7) "Python Database Connection: Using connection settings from /home/daniel/.mythtv/config.xml"
These messages are generated by the new MythTV python bindings and just means things are working.

8) You ran "-MG" and got a interactive display????
If you can reproduce that I would like you to capture the out put including the "> jamu -MGV" and pastebin ALL of the details before and including the first interactive display. Make sure that the pastebin will be around for at least 3 days and put the link in a reply post. According to me this cannot happen unless it was caused due to the way you updated Jamu to v0.7.3 and may have missed the two other files that went  along with the change.

9) "... -MG doesn't even show you what movie it's working on? ..."
Use "-MGV" to get verbose output.

Hopefully these answers did not put you to sleep.

---

### Post by dannyboy79 on 2010-04-18
THANK YOU SO MUCH! i am going to download the other 2 files, tmdb_api.py and tmdb_au.py and put them here as that's where the original ones are.
/usr/lib/python2.6/dist-packages/MythTV/tmdb/
there are other files in that folder that have the same name but they are:
tmdb_ui.pyc
tmdb_api.pyc
Do these matter? I didn't see these updated in teh changeset. So, I am running 0.7.3 of the main jamu.py script and now I put the 2 other files in the respective locations. will try and get back to you. I am sure that the Interactive session when running -MG was only because I didn't update the ui and api files. thanks so much for your help!!!!! will post back results.

---

### Post by dannyboy79 on 2010-04-18
running in -MG  mode it just seems to stall here:

Now processing video file (SIN CITY)(0)(0)
At least (rating) needs updating
Nothing to update for video file(SIN CITY)

Now processing video file (nine.[2])(0)(0)
At least (rating) needs updating

when I keep tailing the jamu.log file, it hasn't moved past Nine for the last 1.5 hours. The main screen I am running jamu in just has this:

! Warning: Skipping non-video file name: (/media/500gb/new_movies/English H.I..srt)

! Warning: Skipping non-video file name: (/media/500gb1/movies/Thumbs.db)

! Warning: Skipping non-video file name: (/media/fat32/movies/tethering_iphone.txt)

! Warning: Skipping non-video file name: (/media/fat32/movies/The Showdown.srt)


and it's just sitting there. does jamu exit back to a command prompt after it finishes going through all movies? i even checked the movie database movie and nine was there, searching works. so i don't think the site is down. any thoughts?

---

### Post by RDV on 2010-04-19
dannyboy79,
    I am concerned that you are not properly updating Jamu to v0.7.3. The link I gave you was to "diff" files that were all included in the Jamu v0.7.3 updated. Three different python files were effected in that update. What is the usual way you update your MythTV install? If you use packages (e.g. Mythbuntu 0.23 PPA) then use that method, if you use SVN 0.23+fixes or trunk then use that method. Just copying the commit's diff files does not buy you anything. So at this point I am not sure if you have updated Jamu correctly. There was actually no file named "tmdb_au.py" it is "tmdb_ui.py" I assume this was just a mistype.
    
I created a file named "nine.[2].avi" and tried Jamu on it without issue. As stated in the wiki, Jamu does not support multi-part video files so "nine.[2]" will not match any video on TMDB. You would need to use MythVideo for this video.

Jamu does exit to the command line when it is done. Here is what my -MG run looked like for the "nine.[2].avi" file:

> ./jamu -MG "/media/virtual/VB_Share/nine.[2].avi" "/media/video/0Review"
2010-04-19 12:55:08.279 Python Database Connection: Using connection settings from /home/doug/.mythtv/config.xml

--------------Move Statistics---------------
Number of subdirectories ............(    0)
Number of files moved ...............(    1)
Number of symbolic links recreated...(    0)
Number of renamed TV-eps or movies.. (    0)
Number of Myth database updates .... (    0)
--------------------------------------------

Mythtv video database maintenance start: 2010-04-19 12:55

Entry does not exist in MythDB.  Adding (nine.[2]).

Mythtv video database maintenance ends at  : 2010-04-19 12:55

------------------Statistics---------------
Number of video files processed .....(    1)
Number of Fanart graphics downloaded (    0)
Number of Poster graphics downloaded (    0)
Number of Banner graphics downloaded (    0)
Number of 2nd source graphics downld (    0)
Number of metadata downloads.........(    0)
Number of 2nd source metadata found .(    0)
Number of symbolic links created.....(    0)
Number of Myth database updates......(    0)
Number of undersized posters ........(    0)
Number of Movies using IMDB numbers .(    0)

----------------No Inetref Found-----------
nine [2]

---

### Post by dannyboy79 on 2010-04-19
> **RDV said:**
> dannyboy79,
    I am concerned that you are not properly updating Jamu to v0.7.3. The link I gave you was to "diff" files that were all included in the Jamu v0.7.3 updated. Three different python files were effected in that update. What is the usual way you update your MythTV install? If you use packages (e.g. Mythbuntu 0.23 PPA) then use that method, if you use SVN 0.23+fixes or trunk then use that method. Just copying the commit's diff files does not buy you anything. So at this point I am not sure if you have updated Jamu correctly. There was actually no file named "tmdb_au.py" it is "tmdb_ui.py" I assume this was just a mistype.
    
I created a file named "nine.[2].avi" and tried Jamu on it without issue. As stated in the wiki, Jamu does not support multi-part video files so "nine.[2]" will not match any video on TMDB. You would need to use MythVideo for this video.

Jamu does exit to the command line when it is done. Here is what my -MG run looked like for the "nine.[2].avi" file:

> ./jamu -MG "/media/virtual/VB_Share/nine.[2].avi" "/media/video/0Review"
2010-04-19 12:55:08.279 Python Database Connection: Using connection settings from /home/doug/.mythtv/config.xml

--------------Move Statistics---------------
Number of subdirectories ............(    0)
Number of files moved ...............(    1)
Number of symbolic links recreated...(    0)
Number of renamed TV-eps or movies.. (    0)
Number of Myth database updates .... (    0)
--------------------------------------------

Mythtv video database maintenance start: 2010-04-19 12:55

Entry does not exist in MythDB.  Adding (nine.[2]).

Mythtv video database maintenance ends at  : 2010-04-19 12:55

------------------Statistics---------------
Number of video files processed .....(    1)
Number of Fanart graphics downloaded (    0)
Number of Poster graphics downloaded (    0)
Number of Banner graphics downloaded (    0)
Number of 2nd source graphics downld (    0)
Number of metadata downloads.........(    0)
Number of 2nd source metadata found .(    0)
Number of symbolic links created.....(    0)
Number of Myth database updates......(    0)
Number of undersized posters ........(    0)
Number of Movies using IMDB numbers .(    0)

----------------No Inetref Found-----------
nine [2]

I normally just upgrade and update using the mythbuntu auto builds repo. what was weird is that i only had 0.7.2 installed despite me being all up to date with the mythbuntu repo. so I figured I could just download the 0.7.3 python file as they are only scripts (not code that has to be compiled) and I figured i could just put those 3 files int eh place where I found them on my system. I did mean tmdb_ui.py. So I have these files in my python folder here: 
/usr/lib/python2.6/dist-packages/MythTV/tmdb/

__init__.py
__init__.pyc
tmdb_api.py
tmdb_api.pyc
tmdb_api.py_old
tmdb_exceptions.py
tmdb_exceptions.pyc
tmdb_ui.py
tmdb_ui.pyc
tmdb_ui.py_old

I don't know what I could do now to fix this issue. I do not get anything like you get when running with -MG. I get this right off the bat:

jamu.py -MG
2010-04-19 15:35:21.109 Python Database Connection: Using connection settings from /home/daniel/.mythtv/config.xml
Mythtv video database maintenance start: 2010-04-19 15:35

! Warning: Jamu does not process multi-part video files, video directory (/media/500gb/new_movies/28_weeks_later/VIDEO_TS).
Skipping this directory. Use MythVideo to retrieve meta data for these video files.

! Warning: Skipping non-video file name: (/media/500gb/new_movies/my.cnf)

! Warning: Skipping non-video file name: (/media/500gb/new_movies/.DS_Store)

! Warning: Skipping non-video file name: (/media/500gb/new_movies/the_protector)

! Warning: Skipping non-video file name: (/media/500gb/new_movies/iphone_videos/.DS_Store)

! Warning: Skipping non-video file name: (/media/500gb/new_movies/district 9.srt)

! Warning: Skipping non-video file name: (/media/500gb/new_movies/English.srt)

! Warning: Skipping non-video file name: (/media/500gb/new_movies/English H.I..srt)

! Warning: Skipping non-video file name: (/media/500gb1/movies/Thumbs.db)

! Warning: Skipping non-video file name: (/media/fat32/movies/tethering_iphone.txt)

! Warning: Skipping non-video file name: (/media/fat32/movies/The Showdown.srt)

I don't see anything about statistics or anything.

---

### Post by RDV on 2010-04-19
dannyboy79,
    Lets try to focus on just one video to see if that at least works. All the Jamu output from your last post looked normal, except as you mentioned the process never seems to end.  Are you using NFS storage that is shared with Windows? I ask that as some people had issues with characters in file names that Windows does not support. There is a jamu.conf setting you can use to tell Jamu not to create file names with specific characters. It is documented in the jamu.conf file.
    
First lets see what version Jamu thinks you have installed:
> ./jamu -v
Copy the version number that is out put into your next post.

Next just focus on the video file that you thought was hanging Jamu. Obviously change the paths to where the "nine.[2].???" video file is located and set the proper file extension.

> ./jamu -MGV "/the directories/to your video/nine.[2].???" "/the directories/to your video"

Pastebin ALL of the results and put the pastebin link into your reply post.

---

### Post by dannyboy79 on 2010-04-19
> **RDV said:**
> dannyboy79,
    Lets try to focus on just one video to see if that at least works. All the Jamu output from your last post looked normal, except as you mentioned the process never seems to end.  Are you using NFS storage that is shared with Windows? I ask that as some people had issues with characters in file names that Windows does not support. There is a jamu.conf setting you can use to tell Jamu not to create file names with specific characters. It is documented in the jamu.conf file.
    
First lets see what version Jamu thinks you have installed:
> ./jamu -v
Copy the version number that is out put into your next post.

I do have NFS shares that are shared with 1 windows box but it's hardly ever on (trying to convert my girlfriend). it runs windows 7 ultimate. the 4 folders (defined in SG within mythtv-setup on backend) that do have movies and shows are all shared via NFS. this was due to when i was running prior to storage groups. they are also shared via samba for an xbox (xbmc).
i can't run ./jamu -v, I get 
-bash: ./jamu: No such file or directory

but when I run jamu.py -v, i get this
Title: (JAMU - Just.Another.Metadata.Utility); Version: (v0.7.3); Author: (R.D.Vaughan)

> **RDV said:**
> 
Next just focus on the video file that you thought was hanging Jamu. Obviously change the paths to where the "nine.[2].???" video file is located and set the proper file extension.

> ./jamu -MGV "/the directories/to your video/nine.[2].???" "/the directories/to your video"

Pastebin ALL of the results and put the pastebin link into your reply post.
[http://pastebin.com/dWcVtT1b](http://pastebin.com/dWcVtT1b)


From the above it appears to be working, i can go into mythfrontend and nine has the info for the [.2] file but not the [.1] file. It is also appearing mythweb videos.

Do you know how I can get it to download metadata and posters fanart for both parts of the movie?

Also, I will say that when ever I run it with -MGV or -MRV it always hangs on something. Last time I ran it it hung on street kings[.2].avi

Yeap, it's been running for the last 2 hours still stuck at Now processing video file (Street Kings.[2])(0)(0). 
I killed the -MGV process and ran it by itself to see if it works. I works just fine so I am not sure why jamu keep stalling on me. I only have about 900 files to process.

Any suggestions to get it to not hang?

---

### Post by dannyboy79 on 2010-04-20
back again, well I tried to run -MGV and only selecting one file. I ran this command
[CODE]jamu.py -MGV "/media/500gb/new_movies/Street Kings.[2].avi"
 "/media/500gb/new_movies"/CODE]
and I am actually in INTERACTIVE MODE as we speak. So it's happening again and I have no idea why. Here's the output when I hit ctrl-c:
^C1-At least (the punisher.[2])'s value(director) has changed new(Jonathan Hensleigh)(<type 'unicode'>) old(None)(<type 'NoneType'>)
Updated Mythdb for video file(the punisher.[2])

Now processing video file (state of play.[1])(0)(0)
^CTraceback (most recent call last):
  File "/usr/local/bin/jamu.py", line 6429, in <module>
    main()
  File "/usr/local/bin/jamu.py", line 6414, in main
    process.processMythTvMetaData()
  File "/usr/local/bin/jamu.py", line 5821, in processMythTvMetaData
    filename = self.findFileInDir(u"%s.%s" % (inetref, ext), [graphicsdir], suffix=self.graphic_suffix[graphic_type])
  File "/usr/local/bin/jamu.py", line 5510, in findFileInDir
    if os.path.isfile(file_path):
  File "/usr/lib/python2.6/genericpath.py", line 32, in isfile
    return stat.S_ISREG(st.st_mode)
  File "/usr/lib/python2.6/stat.py", line 50, in S_ISREG
    return S_IFMT(mode) == S_IFREG
KeyboardInterrupt

I didn't start -MGV with a > log on the end so I don't have a log file. I will do that next. This is driving me nuts.

---

