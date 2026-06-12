---
title: "TV shows metadata script"
date: 2009-02-06
forum: Mythbuntu
---

### Post by menny on 2009-02-06
Hi guys,
I've made a script which goes over all my tv shows files, parse their names and retrieve episode name, plot, air date and director data from TV.com (thanks to perl module WWW::TV) and store into MythTV database.
Then, the script will take the show's poster, and set it as the folder's art.
Then it will use MPlayer to find out what is the length of the video and will take a snapshot from the somewhere in the 15% of the video. This thumb will be the image of the video file in MythTV.

Please, test it and tell me what you think.
You should edit the file for your system (path to files, and SQL password). There is an explanation in the beginning of the file.
Menny


#ideas taken from:
#shabba's script ([http://www.skynet.ie/~shabba/tveps.txt](http://www.skynet.ie/~shabba/tveps.txt)). Thread at [http://www.gossamer-threads.com/lists/mythtv/users/320471](http://www.gossamer-threads.com/lists/mythtv/users/320471).
#Video length and video thumbs from [http://www.perlmonks.org/?node_id=604177](http://www.perlmonks.org/?node_id=604177). Thanks to MonkE.

#This script requires the awesome perl module WWW::TV from [http://search.cpan.org/~tigris/WWW-TV-0.13/](http://search.cpan.org/~tigris/WWW-TV-0.13/). Thanks to Danial Pearce.

---

### Post by menny on 2009-02-06
New version.
Fixed some bugs

---

### Post by august495 on 2009-02-07
When I run the script, I get the following error:


```
 ./mythtv_tv_shows_metadata.pl 
Can't locate String/Approx.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at ./mythtv_tv_shows_metadata.pl line 38.

```

---

### Post by menny on 2009-02-07
Hi,
You need to install some perl modules first.
Run the followings in shell:
****
sudo perl -MCPAN -e 'install WWW::TV'
sudo perl -MCPAN -e 'install String::Approx'
****

These commands will install the two required modules (it will download them from the internet and install).
It will ask you some questions, just press ENTER (for the default answer), and it will be OK.

---

### Post by menny on 2009-02-07
Version 0.3:
Some bug fixes

To use this script, you need to first install the Perl module "WWW::TV". Run the following command in shell:
sudo perl -MCPAN -e 'install WWW::TV'

---

### Post by august495 on 2009-02-07
That fixed it! Works like a charm, thank you.

---

### Post by orduek on 2009-02-07
can it fetch movies or just TV shows?
Does it works better than metacleanup?

---

### Post by menny on 2009-02-11
I'm working on a version which will also find metadata from IMDB.
I do not know what is metacleanup.

---

### Post by menny on 2009-02-19
Hi.
New version:
* better posters handling
* IMDB support - now it can handle TV shows and Movies
* Since this script supports TV and Movies, there is no need to specify the folder. It will be taken from the database.
* No need for extension specification. It will be taken from the database.
* New filesystem files will be automatically be added to MythVideo database.
* Bug fixes


If you want to test it, please install WWW::TV and IMDB::Film perl modules:

sudo perl -MCPAN -e 'install WWW::TV'
sudo perl -MCPAN -e 'install IMDB::Film'


Enjoy.
PS, I've changed the name of the file.

---

### Post by theophile on 2009-02-20
This looks really good. I started using XBMC for local content because of its very good handling of TV shows.

Does this script to filename regex matching? Can I give it a file called Foo.s03e16.xvid.avi and it will know to look for:
Show: Foo
Season: 3
Episode: 16

?

---

### Post by menny on 2009-02-20
It can handle three types of file naming formats:
1) [ShowName]S[SeasonNumber]E[EpisodeNumber]: "My.Show.S01E04.avi"
2) [ShowName] [SeasonNumber]x[EpisodeNumber]: "My.Show 1x08.avi"
3) [ShowName] [SeasonNumber(in one digit)][EpisodeNumber(two digits]: "My.Show 108.avi"

And, yes, it uses regexp for parsing the details.

---

### Post by theophile on 2009-02-20
Excellent. Will have to fire this bad boy up. ;-)

---

### Post by menny on 2009-02-25
Hi,
A new version is available.
This version adds the followings:
* support for downloading subtitles - will be downloaded if no subtitle file exists for the TV show file. Movies subtitles are not supported yet.
* video snapshot will be created anyway - e.g., could not locate a IMDB poster, or the file was not parsed as TV show.
* if file was not found in TV.COM it will be handled as a movie.
* bug fixes.

The subtitles thing is disabled by default, so you'll have to enable it, if you want to use it.
The script will download subtitles files (srt format) from [www.tvsubtitles.net](www.tvsubtitles.net).

Enjoy

---

### Post by theophile on 2009-02-25
Does this scrape TV.com? It might be worth looking into [www.thetvdb.com](www.thetvdb.com), which is specifically designed for applications like this and has an open API.

Also, does this currently apply season posters for folder images? So I have a poster for the folder "Scrubs." Can it also apply a poster to the subdirectory "Season 1" (etc.)?

I'm looking forward to 0.22 and MythUI. I use XBMC for handling of local media because it's more robust, but 0.22 looks fantastic. I'm hoping it will have good support for local content, especially TV shows.

---

### Post by menny on 2009-02-26
theophile, this script uses TV.COM for details. I'll look into [www.thetvdb.com](www.thetvdb.com). If its API is better, I'll use it, since TV.COM requires HTML pages parsing, and it slows the process.

Each folder has it own poster. Each season will have it own poster, as specified by TV.COM. But from my experience, all seasons look the same. For this reason, the script will create a really snapshot from the actual video file, for each of the files - so the UI will be interesting :)

I wasn't aware that 0.22 will have any special support for local content. I know that mythui will be implemented across the application, and QT4 will be used (which will probably make MythTV make nicer).

Menny

---

### Post by theophile on 2009-02-26
thetvdb.com has support for season posters and also fanart, which it seems will make an appearance with the new MythUI. I think you'll find the API easier. I'm not a coder but from what I've read, metadata scrapers much prefer it. I *still* haven't tried the script out yet, but I promise I will. ;-)

---

### Post by Lorenzo1985 on 2009-02-27
Impressive script, definetly better than most of the others. Thanks for putting in the time.

Couple of questions:
I get the following errors when I run it:
```
main::trim() called too early to check prototype at ./fill_mythvideo_metadata.pl line 216.
main::trim() called too early to check prototype at ./fill_mythvideo_metadata.pl line 217.
main::trim() called too early to check prototype at ./fill_mythvideo_metadata.pl line 218.
main::trim() called too early to check prototype at ./fill_mythvideo_metadata.pl line 328.

```
Any ideas? it seems to work anyway!

Why does it download the cover files to my video folder rather than the artwork folder? Also can you put an option in to stop it putting in spaces in the file names. spaces in file names are a pain to deal with on a *nix command line.

Can it be extended to purge files that appear to have been deleted or renamed?

---

### Post by menny on 2009-02-28
Hi,

> I get the following errors when I run it:
Code:

main::trim() called too early to check prototype at ./fill_mythvideo_metadata.pl line 216.
main::trim() called too early to check prototype at ./fill_mythvideo_metadata.pl line 217.
main::trim() called too early to check prototype at ./fill_mythvideo_metadata.pl line 218.
main::trim() called too early to check prototype at ./fill_mythvideo_metadata.pl line 328.

Any ideas? it seems to work anyway!

I don't know why it does it, I'm not a perl expert, but I does it at my end too, and it works, so, you know, if it ain't broken, don't fix it.

> Why does it download the cover files to my video folder rather than the artwork folder? 

The cover art, is stored next to files for two reasons:
1) if I want MythTV to show the cool folder art, it has to be located inside the folder, and it should be named "folder.jpg".
2) I didn't want the artwork folder to be bloated - I don't want to keep track on cover-art files to be deleted. If the art is next to the video file, then when you'll delete the video, you probably delete the jpg too..

> Also can you put an option in to stop it putting in spaces in the file names
I do not understand, which spaces? I name the jpg according to the video filename.

---

### Post by Lorenzo1985 on 2009-03-01
Firstly, thanks for your time in answering my questions. a few counterpoints:

> **menny said:**
> 
The cover art, is stored next to files for two reasons:
1) if I want MythTV to show the cool folder art, it has to be located inside the folder, and it should be named "folder.jpg".
2) I didn't want the artwork folder to be bloated - I don't want to keep track on cover-art files to be deleted. If the art is next to the video file, then when you'll delete the video, you probably delete the jpg too..
I see your point... unfortunatly it does seem to mean the video artwork becomes broken links in mythweb. 


> **menny said:**
> 
I do not understand, which spaces? I name the jpg according to the video filename.
That doesn't seem to be strictly true. particularly for Movies.

An ls on a movies folder look a bit like this:
```
-rw-r--r-- 1 loz    loz     944951296 2009-02-24 12:33 Australia.avi
-rw-r--r-- 1 loz    loz          6118 2009-02-02 06:24 australia.jpg
-rw-r--r-- 1 loz    loz     735698944 2009-02-24 16:21 Body_Of_Lies.avi
-rw-r--r-- 1 loz    loz          6204 2008-12-30 06:38 body of lies.jpg
-rw-r--r-- 1 loz    loz     840165376 2009-02-24 16:03 Changeling.avi
-rw-r--r-- 1 loz    loz          3643 2008-10-06 18:37 changeling.jpg
-rw-r--r-- 1 loz    loz     733849656 2009-02-26 10:53 Choke.avi
-rw-r--r-- 1 loz    loz          4500 2009-01-22 08:54 choke.jpg
-rw-r--r-- 1 loz    loz     735922176 2009-02-25 18:29 Death.Race.avi
-rw-r--r-- 1 loz    loz          6078 2008-06-26 20:52 death race.jpg
-rw-r--r-- 1 loz    loz     736272384 2009-02-24 15:24 Eagle_Eye.avi
-rw-r--r-- 1 loz    loz          7095 2008-11-27 06:33 eagle eye.jpg
-rw-r--r-- 1 loz    loz          6078 2009-02-27 16:54 folder.jpg
-rw-r--r-- 1 loz    loz     733368320 2009-02-26 19:57 Nine_and_a_half_weeks.avi
-rw-r--r-- 1 loz    loz          5493 2008-03-14 04:07 nine and a half weeks.jpg
-rw-r--r-- 1 loz    loz     736296960 2009-02-24 14:48 RocknRolla.avi
-rw-r--r-- 1 loz    loz          5730 2008-08-06 01:30 rocknrolla.jpg
-rw-r--r-- 1 loz    loz     735528960 2009-02-24 16:09 Role_Models.avi
-rw-r--r-- 1 loz    loz          5369 2008-10-08 18:32 role models.jpg
-rw-r--r-- 1 loz    loz     735641600 2009-02-24 14:32 Sex_Drive.avi
-rw-r--r-- 1 loz    loz          7925 2009-01-13 06:52 sex drive.jpg
-rw-r--r-- 1 loz    loz     736256000 2009-02-25 18:21 Taken.avi
-rw-r--r-- 1 loz    loz          3876 2009-01-09 00:04 taken.jpg
-rwxr--r-- 1 nobody nogroup 735959040 2006-02-19 12:16 The_Accidental_Husband.avi
-rw-r--r-- 1 loz    loz          6502 2008-06-06 00:10 the accidental husband.jpg
-rw-r--r-- 1 loz    loz     944125952 2009-02-24 13:29 The_Assassination_of_Jesse_James.avi
-rw-r--r-- 1 loz    loz          5559 2008-03-16 13:40 the assassination of jesse james.jpg
-rw-r--r-- 1 loz    loz     735418368 2009-02-25 18:51 The.Wackness.avi
-rw-r--r-- 1 loz    loz          6437 2008-05-06 20:58 the wackness.jpg
-rw-r--r-- 1 loz    loz     735461376 2009-02-24 12:56 Thick.As.Thieves.avi
-rw-r--r-- 1 loz    loz          3394 2009-02-27 21:27 thick as thieves.jpg
-rw-r--r-- 1 loz    loz     732692480 2009-02-26 12:56 Valkyrie.avi
-rw-r--r-- 1 loz    loz          5300 2008-09-26 00:56 valkyrie.jpg

```

---

### Post by menny on 2009-03-02
I see your points.

I'll think of a way to move to the artwork folder, and to some delete old images.

I'll fix the spaces issue.

Thanks.

---

### Post by menny on 2009-03-02
Version 0.6:
* command line support:
	* Scan specific directory, recursive (overriding the automatic media folder detection): -D [path]
	* Perform "full" (0)/"new files only" (1) scan (overriding the default specified): -N [1/0]
	* Perform subtitles download: -S [1/0]
	* Specify DB password: -DBP [whatever]
	* Help: -h
* better IMDB handling... Will take data only if the title is levenshtein similar.
* bug fixes - including spaces in cover filenames

I encourage you to use the command line arguments, so you will not be required to edit the file to match your system.

Menny

---

### Post by Lorenzo1985 on 2009-03-02
Menny
Wow your quick! thanks for responding so positively on the feedback. I'll test this stuff tonight!

---

### Post by Lorenzo1985 on 2009-03-02
> **menny said:**
> Hi,
I don't know why it does it, I'm not a perl expert, but I does it at my end too, and it works, so, you know, if it ain't broken, don't fix it.
```
loz@gravity:~$ diff fill_mythvideo_metadata.pl fill_mythvideo_metadata2.pl
291,293c291,293
<               $show = trim($show);
<               $season = trim($season);
<               $episode = trim($episode);
---
>               $show = &trim($show);
>               $season = &trim($season);
>               $episode = &trim($episode);
401c401
<               $movie_name = trim($movie_name);
---
>               $movie_name = &trim($movie_name);
loz@gravity:~$

```

Adding ampersand before those trim calls will get rid of those errors.

> %s() called too early to check prototype
(W prototype) You've called a function that has a prototype before the parser saw a definition or declaration for it, and Perl could not check that the call conforms to the prototype.  You need to either add an early prototype declaration for the subroutine in question, or move the subroutine definition ahead of the call to get proper prototype checking.  Alternatively, if you are certain that you're calling the function correctly, you may put an ampersand before the name to avoid the warning.  See perlsub.

---

### Post by menny on 2009-03-02
Lorenzo1985, Thanks for the code-review :)

And I'm not quick, I was working on some new things and some bug fixes in the script, and your request just came at the right moment :)

---

### Post by Lorenzo1985 on 2009-03-16
Menny (and anyone else whos interested)

I hope you dont mind but I've hacked the hell out of your script and ported it to use thetvdb.com API for for TV episode. this seems to be a bit more reliable than than TV.COM. It also collects the TV art from there in a similar way to the imdb cover files.

Also it now places videos in a defined artwork folder. (should probbably make this retrieve the artwork folder from the database)

It's not perfect and doesnt do folder art for TV yet, but it's a work in progress. Just thought people might be interested!

you'll need to install the theTvDB module
sudo perl -MCPAN -e 'install TVDB::API'

---

### Post by menny on 2009-03-16
Lorenzo1985, COOL!

Actually, I've just finished testing a new version of the script, which also uses THETVDB API too :)
This version does not use the "TVDB::API" - I didn't want users to install perl modules (which the script required them with TV.COM, and still require for IMDB).
So I've written the API calls with regular PERL functions - no additional modules. I'll do the same with IMDB in some next version.

**Lorenzo1985**, I think that it is better to NO use the "TVDB::API" (so users will not be required to install modules). I'll look into your script for the ART folder thing, or maybe you can do it yourself? Or change your script to use the the meta-data functions I've added in my script.
Also, do you delete image files which their video files do not exist any more?

_#version 0.7:_
#* Moved away from WWW::TV perl module. Now uses [www.thetvdb.com](www.thetvdb.com) API!
#* New command line arguments:
#	* Take snapshots for movies (don't take IMDB's poster) - "0" for take from IMDB.COM, "1" generate snapshot from file: -MOVIE_SNAP [1/0]
#	* Take snapshots for TV shows (don't take The TV DB's poster) - "0" for take from [www.thetvdb.com](www.thetvdb.com), "1" generate snapshot from file: -TV_SNAP [1/0]
#* major change in images download.
#* bug fixes
#* Known bug: images are not saved in the ART folder, but next to the video files - which means no images in the MythWeb.

---

### Post by Lorenzo1985 on 2009-03-17
Awesome

Nice work, I'm really happy that this script exists. It's getting to be quite a good all in one solution. There are lots of half solutions out there but this does everything.


> **menny said:**
> 
 I think that it is better to NO use the "TVDB::API" (so users will not be required to install modules). I'll look into your script for the ART folder thing, or maybe you can do it yourself? Or change your script to use the the meta-data functions I've added in my script.
Also, do you delete image files which their video files do not exist any more?

I'll have a look at changing your version of the script to use the Artwork folder. I havent done anything about deleting old image files. I simply ran "find <my video folder> -name *.jpg -delete" and then re-ran the script against all files to collect all the images again and put them in the correct place.

I also want to add deleting of database entries for files that no longer exists. That way you can delete, rename, move files and just leave the script to sort out the database rocords you leave behind.

Does your script collect Season and series artwork for the folder.jpg's ordoes it simply copy one of the episode images to the folder?

---

### Post by menny on 2009-03-17
> I'll have a look at changing your version of the script to use the Artwork folder. I havent done anything about deleting old image files. I simply ran "find <my video folder> -name *.jpg -delete" and then re-ran the script against all files to collect all the images again and put them in the correct place.
This can be a stress issue with THETVDB servers, no?

> 
I also want to add deleting of database entries for files that no longer exists. That way you can delete, rename, move files and just leave the script to sort out the database rocords you leave behind.
I noticed that every time you start browsing files in MythVideo, it will automatically delete all DB entries of files which no longer exist, and add new files.
But this raises an idea about the artwork folder: After the script finish its work, it can go over all the files in the artwork folder, and check if they exist in the DB, if not, then delete! How about this?

---

### Post by menny on 2009-03-17
> Does your script collect Season and series artwork for the folder.jpg's ordoes it simply copy one of the episode images to the folder?
No. It uses the same artwork for all series folder. This is a good idea to do it per season... should be too hard.

---

### Post by Lorenzo1985 on 2009-03-17
morning menny

Firstly attached is a version of your script which places files in the artwork folder.

Changes:
* places video artwork in mythvideo artwork folder
* does substitution on artwork filenames to remove spaces
* Added some extra line prints to output to make it easier to see where one file starts and the other ends.


> **menny said:**
> This can be a stress issue with THETVDB servers, no?
Possibly, but it was a one off. It shouldnt be too much stress as I dont have that many videos yet!

> **menny said:**
> 
I noticed that every time you start browsing files in MythVideo, it will automatically delete all DB entries of files which no longer exist, and add new files.
Weird, mine doesnt do this, perhaps your working with the trunk builds? If I enter the video manager it will delete no existant files but I dont think it ever adds them. in any case I dont wish to have to visit the video manger to make it update. I'd like to just be able to cron this script to run every so often and leave that to maintain the database.

> **menny said:**
> 
But this raises an idea about the artwork folder: After the script finish its work, it can go over all the files in the artwork folder, and check if they exist in the DB, if not, then delete! How about this?
This sounds like a plan!

---

### Post by menny on 2009-03-17
Hi Lorenzo,
I like you changes, when I gone over your version from yesterday, I wanted to merge these features into my script, thanks :)

> Weird, mine doesnt do this, perhaps your working with the trunk builds? If I enter the video manager it will delete no existant files but I dont think it ever adds them. in any case I dont wish to have to visit the video manger to make it update. I'd like to just be able to cron this script to run every so often and leave that to maintain the database.
I'm using the weekly updates, but I'm pretty sure it did it in 0.20 too. In any case, I think that you are right - the script should delete entries if the files do not exist anymore!

> This sounds like a plan!
I think that I'll add this idea, and the deletion of non-existing files from the DB.
I'll work on your version

---

### Post by menny on 2009-03-18
Hi Lorenzo1985.
I've finished the things we talked about.
* DB entries will be deleted
* Un-used images in the art-work folder will be deleted.

The attached script DOES NOT delete the files, since I commented the delete command.
Since I, mistakenly, deleted two video files (due to a bug), I figured that it will be safer if you first run the script, check if the prints are OK, and then try the full thing (un-comment line number 1028).

Menny

(Attachement removed)

---

### Post by Lorenzo1985 on 2009-03-18
Something has gone wrong I think.

Whilst it does go through my artwork folder and delete non existant files. And i think it sorts out my redundant database aswell.

It doesnt seem to be parsing and adding new files.
> ======================================================================
Finished going over all the files: Found 0, updated 0 files.
Going over all video files in the database, and deleting any redundant entries (files no longer exist)...
======================================================================


---

### Post by menny on 2009-03-18
opps...
Remove the "last;" command in line 652.

I used that for testing the last section :)

---

### Post by Lorenzo1985 on 2009-03-18
We like :-)

Obviously you meant 1027 should be uncommented, as the 7 got turned into a smiley.

It's excellent work!

Do you have any other features you are thinking of implementing?

---

### Post by menny on 2009-03-18
Good to hear that all is working :)

I have two more things:
1) The season folder should show the season's art-work, and not the series. The series folder should show the series art-work..
2) Do my own IMDB parser.

Attached is a working version.

Thanks Lorenzo.

---

### Post by Lorenzo1985 on 2009-03-18
bug:

inetref for files populated from imdb seem to allways be populated with 1111.

I may look into some of the following:

- parsing db pass from mysql.txt (ushally found in /etc/mythtv/mysql.txt)
- Some way of specifying a imdb id against a file and getting it to to collect the information from imdb. For the rare ocasions it collects the wrong data or fails to collect the data.

It might be a good idea to publish this in the mythtv wiki and therefore publish it to a wider audience.

---

### Post by menny on 2009-03-18
> bug:

inetref for files populated from imdb seem to allways be populated with 1111.
I've hard-coded this ID... The perl module does not provide a real IMDB ID. This is another reason for creating a specialized IMDB parser.

> I may look into some of the following:

- parsing db pass from mysql.txt (ushally found in /etc/mythtv/mysql.txt)
- Some way of specifying a imdb id against a file and getting it to to collect the information from imdb. For the rare ocasions it collects the wrong data or fails to collect the data.
Great idea. BTW, my sql password is located under "~/.mythtv/sql.txt".

> It might be a good idea to publish this in the mythtv wiki and therefore publish it to a wider audience. 
Sounds good. Do you know how to do it?

---

### Post by paulyche on 2009-03-18
Hi,

I tried this script last night and it generally worked well. I have a couple of comments though in addition to what's already been mentioned:

1. It would be nice if there was a switch to change the title in the database to a different (longer) format. For example, I would prefer "The West Wing S01E01 Pilot" to "01: Pilot". I've hacked this into the version I downloaded but I could make the change in a better manner and get it back to you if you're interested?
2. My frontend is displaying &'s and quotes in the description and titles incorrectly, but I'm not sure if that's my setup: I'll get back to you on that.
3. I would prefer the episode image for tv shows to just be the season image (i.e. what's usually the DVD cover) rather than a screen grab. But of course that's just my preference.

Thanks,

---

### Post by menny on 2009-03-18
Hi,
> 1. It would be nice if there was a switch to change the title in the database to a different (longer) format. For example, I would prefer "The West Wing S01E01 Pilot" to "01: Pilot". I've hacked this into the version I downloaded but I could make the change in a better manner and get it back to you if you're interested?
Sure, go ahead and do it :) I prefer the way it is now, so please make it configurable via command line arguments.

> 2. My frontend is displaying &'s and quotes in the description and titles incorrectly, but I'm not sure if that's my setup: I'll get back to you on that.
Can you tell me on which show,season,episode you are experiencing this problem? The script does some SQL fixing, but I haven't testing very much with the new THETVDB API.

> 3. I would prefer the episode image for tv shows to just be the season image (i.e. what's usually the DVD cover) rather than a screen grab. But of course that's just my preference
If youi'll add "-TV_SNAP 0" to the command line argument, it will download the official episode cover from the Internet. But, if you prefer the season cover instead, this should be implemented. It seems that there are several types of TV show covers: Snapshot, Season cover, Series Cover, or Episode cover from The-TV-DB servers...

---

### Post by menny on 2009-03-20
Hi,
I got a problem with the script, and I think I have solution for it, I want to hear what you think:

I have a folder for Battlestar Galactica, and the files in it are something like "Battlestar.Galactica.S04E19.HDTV.avi".
The script tries to get information for "Battlestar Galactica", season "4" episode "19", which is cool - but the problem is that when searching for "Battlestar Galactica", THETVDB.com API return the original show, and not the 2003 remake...

I couldn't find a solution for this problem, but I thought that I can get around it by creating an override mechanism:
if the video folder includes a file with extension "nfo", the script will look for <thetvdb seriesid="number"/> in its contents, and if there is, will use that instead of searching for the show in THETVDB.com.

How about it?

This can be extended to overriding a specific file, e.g., if there is a nfo file with the same name as a video file, then the script will look in the nfo file contents for <thetvdb seriesid="[ID from thetvdb.com]" season="[number]" episode="[number]"/>.
Lorenzo, if the file contents include <imdb id="id from imdb.com"/> then the script will handle the file as a movie with the specified ID - which can handle the problem you raised before.

---

### Post by Lorenzo1985 on 2009-03-21
> **menny said:**
> 
If the video folder includes a file with extension "nfo", the script will look for <thetvdb seriesid="number"/> in its contents, and if there is, will use that instead of searching for the show in THETVDB.com.

How about it?

This can be extended to overriding a specific file, e.g., if there is a nfo file with the same name as a video file, then the script will look in the nfo file contents for <thetvdb seriesid="[ID from thetvdb.com]" season="[number]" episode="[number]"/>.
Lorenzo, if the file contents include <imdb id="id from imdb.com"/> then the script will handle the file as a movie with the specified ID - which can handle the problem you raised before.

Yeah I agree there definetly needs to be a way to help the script along when it doesn't manage by itself. Most Other scripts deal with this by having an interactive mode. When it parses the files in interactive mode it queries the user for every file so so the user can either agree with the scripts guesses or provide an id for the correct file.

However I actually think your solution is better because it means  you can still perform a full scan without having to manually correct the scripts guesses afterwards. 

An extension to this idea that I think would be useful is a <noupdate/> parameter in an .nfo file. So that if you manually specify the data for file it won't get overwritten if you do a full scan.

I also think it would be handy if it recognised hidden .nfo (as well as non hidden ones) file so the format was .<filename>.nfo so if you wish the nfo files could be hidden in the directory.

(as an aside, I wish you could also use files named .folder.jpg rather than folder.jpg, but I can't for the life of me work out which file I'd have to customise to make these recognised by the mythvideo frontend.)

---

### Post by theophile on 2009-03-21
Other scrapers that use the TVDB API have a prompt when the search returns more than one possible show match. It presents the user with the possibilities and lets him choose. It then applies the same result to every file in the directory. It's not fully automatic but it sure isn't as tedious as prompting the user to confirm every single result.

Also, I would suggest that if you implement a .nfo parser it be the same format as used by XBMC:
[http://xbmc.org/wiki/?title=Import_-_Export_Library#Video_nfo_Files](http://xbmc.org/wiki/?title=Import_-_Export_Library#Video_nfo_Files)

---

### Post by menny on 2009-03-22
Hi theophile,
> Also, I would suggest that if you implement a .nfo parser it be the same format as used by XBMC:
[http://xbmc.org/wiki/?title=Import_-...ideo_nfo_Files](http://xbmc.org/wiki/?title=Import_-...ideo_nfo_Files)

This can be useful for importing data from XBMC, but I'm not sure that it can be used for my initial intention - telling the script to skip its logic, and take the ID from a file, and with that ID, harvest the information from the internet. I do not want to create a file with all the data, just to point the script to the correct show. 

Lorenzo1985
> An extension to this idea that I think would be useful is a <noupdate/> parameter in an .nfo file. So that if you manually specify the data for file it won't get overwritten if you do a full scan.
Can you explain again the use of <noupdate/>? Why will the data will be overwritten? The script does not try to harvest data from the-tv-db if the file already have meta-data associated with it in the MythVideo database.

---

### Post by Lorenzo1985 on 2009-03-25
> **menny said:**
> 
Lorenzo1985

Can you explain again the use of <noupdate/>? Why will the data will be overwritten? The script does not try to harvest data from the-tv-db if the file already have meta-data associated with it in the MythVideo database.

I thought it would update the meta for a script that already has meta if you use the -N 0 option.

---

### Post by menny on 2009-03-25
I see.
How about <noupdate/> for skipping files?
This can be used for files you do not want to be overwritten (as you suggested).
And <simple_update/> for just adding the snapshot and add the file to the database?
This can be used for files which do not exist in IMDB, e.g. family videos, or something like that.

---

### Post by Lorenzo1985 on 2009-03-25
> **menny said:**
> I see.
How about <noupdate/> for skipping files?
This can be used for files you do not want to be overwritten (as you suggested).
And <simple_update/> for just adding the snapshot and add the file to the database?
This can be used for files which do not exist in IMDB, e.g. family videos, or something like that.

That all sounds very good.

---

### Post by menny on 2009-03-25
I'm working on a huge update.
It will include the NFO file support, new command line arguments, and bug fixes.

---

### Post by menny on 2009-03-25
Hi,
I've finished the new version, which contains many changes:
#* It is possible to override the search for a tv show or movie, by creating a file within the video file folder ("nfo" extension)
#which includes the video file info:
#	* TV Show:
#		* To override the series: any .nfo file within the video file folder which contain '<thetvdb seriesid="[ID from thetvdb.com]"/>'
#		* To override the video file: create a file with the same name as the file but with .nfo extension. The file should contain '<thetvdb seriesid="[ID from thetvdb.com]" season="[number]" episode="[number]"/>'
#	* Movie:
#		* To override the video file: create a file with the same name as the file but with .nfo extension. The file should contain '<imdb id="[ID from imdb.com]"/>'
#	* Skip markers:
#		* To skip a file complete (just ignore, whatever in the database , if any, is OK): create a file with the same name as the file but with .nfo extension. The file should contain '<no_update/>'
#		* To skip a file parsing, and just add the file with a snapshot to the database (usefull for private videos): create a file with the same name as the file but with .nfo extension. The file should contain '<simple_update/>'
#* Selects the most similar TV show from all results, rather than the first.
#* New command line argument:
#       * Work on a specific file (can be usefull for replacing imdb.pl script): -F [full path to file]
#* bug fixes

This is a testing version - it wont delete all you files or something, but it may harm the meta-data.
I've tested it, and it works for me.

Please tell me what you think.

---

### Post by utar on 2009-03-25
Hi


Just tried this script for the first time and I'm impressed!

I just have a couple of questions/points:

1) I had to set myth to ignore jpg files to avoid the folder.jpg showing in the video browser.  Is this the right thing to do, or is there another way?

2) The script does not work with certain files with the following naming format "the.big.bang.theory.s02e02.720p.hdtv.x264-ctu".  Is this just me, or the script?


Many thanks again for writing the script.

[Edit: Would it be possible to increase the file size of the video thumbnails so that they look better on the full screen preview, or is this a myth issue? Would it also be possible to expand the naming format so for example, episode s1e10 is named as as to include the season, as otherwise s01e10 and s02e10 would both be named "10" - hope you followed that!]

---

### Post by menny on 2009-03-25
Hi,

> 1) I had to set myth to ignore jpg files to avoid the folder.jpg showing in the video browser. Is this the right thing to do, or is there another way?
I never had this problem, JPEGs were never visible in my system.

> 2) The script does not work with certain files with the following naming format "the.big.bang.theory.s02e02.720p.hdtv.x264-ctu". Is this just me, or the script?
That's weird, since I have these types of files too. But since I made a lot of changes, I'll check that again.

> Would it be possible to increase the file size of the video thumbnails so that they look better on the full screen preview, or is this a myth issue?
I'll look into that.

> Would it also be possible to expand the naming format so for example, episode s1e10 is named as as to include the season, as otherwise s01e10 and s02e10 would both be named "10" - hope you followed that!]
You are the second to ask for that - I'll add it soon.

Thanks for testing.

---

### Post by theophile on 2009-03-25
Hey guys. Forgive me if this is off topic, but how difficult would it be to use the TVDB API to search for show and episode name and have it return season and episode numbers? If so, it could be used in conjunction with mythrename.pl to automatically make human readable names for MythTV recordings that conform to the general internet naming standard: ShowName.S0XE0X.EpidodeName.mpg

This would be absolutely killer, IMHO.

---

### Post by menny on 2009-03-26
> Hey guys. Forgive me if this is off topic, but how difficult would it be to use the TVDB API to search for show and episode name and have it return season and episode numbers? If so, it could be used in conjunction with mythrename.pl to automatically make human readable names for MythTV recordings that conform to the general internet naming standard: ShowName.S0XE0X.EpidodeName.mpg

This would be absolutely killer, IMHO. 
Take a look at the API reference at [http://thetvdb.com/wiki/index.php/Programmers_API](http://thetvdb.com/wiki/index.php/Programmers_API).
I think that the best way to do it, is to download the entire series data ([http://thetvdb.com/wiki/index.php/API:Full_Series_Record](http://thetvdb.com/wiki/index.php/API:Full_Series_Record)), and then look for it there.

---

### Post by Lorenzo1985 on 2009-03-26
Nice work Menny

Generally looking good:

**One issue:** (nothing to do with new functionality)
If you have a folder.png it will still add a folder.jpg

Additionally placeing a folder.jpg in the top level videos directory is a bit unnecessary.

**Query:**
How would you go about using .nfo files for Special episodes.

I might for example have a file called:
/media/media/Videos/TV/The_Vicar_of_Dibley/Specials/The Vicar Of Dibley - SP01 - The Easter Bunny.avi
(Don't laugh, my girlfriend likes it)

All the specials are listed in thetvdb [here]("http://www.thetvdb.com/?tab=seasonall&id=74873&lid=7")

So how would you make it recognise these files.

---

### Post by menny on 2009-03-26
> **Lorenzo1985 said:**
> **One issue:** (nothing to do with new functionality)
If you have a folder.png it will still add a folder.jpg
I missed that - this is a bug which I'll fix.

> **Lorenzo1985 said:**
> Additionally placeing a folder.jpg in the top level videos directory is a bit unnecessary.
Another bug.

> **Lorenzo1985 said:**
> 
**Query:**
How would you go about using .nfo files for Special episodes.

I might for example have a file called:
/media/media/Videos/TV/The_Vicar_of_Dibley/Specials/The Vicar Of Dibley - SP01 - The Easter Bunny.avi
(Don't laugh, my girlfriend likes it)

All the specials are listed in thetvdb [here]("http://www.thetvdb.com/?tab=seasonall&id=74873&lid=7")

So how would you make it recognise these files.
This is a good point. It is possible to do something like: <thetvdb episodeid="332100"/>, but, as I saw for The Vicar, some shows have a lot of specials, which may be annoying for the user. 
I prefer to parse the filename and look for it at the-tv-db, but I do not know of any agreed method of naming specials.

> **Lorenzo1985 said:**
> (Don't laugh, my girlfriend likes it)
I have "The Gilmore Girls" due to the same reason.

---

### Post by Lorenzo1985 on 2009-03-26
I added this starting at line 941. it deals with hidden nfo files. I dont like clutter so tend to like files like these to be hidden files. Quite a personal preference I suppose.
```

        my ($video_file_with_hidden_nfo) = $filename =~ m/(.*)\..*/;
        $video_file_with_hidden_nfo = $directory.".".$video_file_with_hidden_nfo;
        $video_file_with_hidden_nfo .= ".nfo";
        if (-e $video_file_with_hidden_nfo)
        {
        $video_file_with_nfo = $video_file_with_hidden_nfo;
        }
```

---

### Post by Lorenzo1985 on 2009-03-27
More testing feedback I'm afraid:

**1.**
I get allot of feedback like this, any ideas what it means
> Exiting eval via next at ./fill_mythvideo_metadata.pl line 1296.


**2.**
Snapshotting is a bit unreliable, I quite often get this

> Cannot find codec matching selected -vo and video format 0x30355844.
I'll have a look into snapshotting with VLC and see if its more reliable

3.
Video's with .nfo files allways attempt to get metadata even if it's already done
> ======================================================================
Video file 'Balls_Out-The_Gary_Houseman_Story.avi' has metadata in the database.
D=/media/media/Videos/Movies/, F=Balls_Out-The_Gary_Houseman_Story.avi
looking for '/media/media/Videos/Movies/.Balls_Out-The_Gary_Houseman_Story.nfo' for file details.
Video file has NFO file. Looking for video information in it...
Found IMDB information in NFO file (imdb id: tt0787470), using it to get meta-data about the file
Trying to load information for 'balls out the gary houseman story' from IMDB...
Cannot find codec matching selected -vo and video format 0x30355844.
downloading poster from 'http://ia.media-imdb.com/images/M/MV5BMjA5OTMzNDY3MV5BMl5BanBnXkFtZTcwMjE2MTQyMg@@._V1._SX100_SY129_.jpg'...
Folder art for '/media/media/Artwork/Balls_Out-The_Gary_Houseman_Story.avi.jpg' already exist.
found (0787470) Balls Out: Gary the Tennis Coach:
'Balls Out: Gary the Tennis Coach' is set!
======================================================================


---

### Post by utar on 2009-03-28
Just thought I would post a couple of observations:

1) I have some DVDs ripped to folders, and for these the script incorrectly adds VIDEO_TS to the database:
 
Video file 'VIDEO_TS' does not exist in the DB metadata. Inserting dummy row...

2) I'm not convinced that the script is looking in every directory.  This may be linked to the post I made earlier episodes with the following naming format not being detected:

the.big.bang.theory.s02e02.720p.hdtv.x264-ctu

[Edit: I realised what was causing issue 2.  I didn't have a mkv filetype set-up in myth and therefore the script was ignoring all mkv files.  Now I've added mkv as a filetype the script is correctly detecting the files]

---

### Post by Lorenzo1985 on 2009-03-28
I've coded auto configuration.

Add the following above the "#checking variables" line.
```

if ((length $dbpass) < 1) {
   if (-e "/etc/mythtv/mysql.txt") {
   print "Using password from mysql.txt\n";
   open( my $R, '<', "/etc/mythtv/mysql.txt" ) or die "couldn't open mysql.txt\n";
   while ( my $line = <$R> ) {
        if ( $line =~ /DBPassword/ ) {
                 $dbpass = $line;
            }
   }
   close $R;
   $dbpass =~ s/DBPassword=//g;
   chomp($dbpass);
   }
}
```

---

### Post by jyavenard on 2009-03-28
Hi.

If you use my ubuntu repository:
[http://avenard.com/media/Ubuntu_Repository/Ubuntu_Repository.html](http://avenard.com/media/Ubuntu_Repository/Ubuntu_Repository.html)

It adds features to the myth python bindings.
So you can modify the video metadata using the IMDB python scripts using either the myth video setup screen or from the command line.

To scan every day your whole set of videos and correctly insert full metadata (cast, country, plot, multiple genres etc...)
I have a cron entry:
0 5 * * * /usr/share/mythtv/mythvideo/scripts/find_meta.py -r /data/videos

And change in the mythtv settings to use the python imdb instead of the perl one:
replace calls to /usr/share/mythtv/mythvideo/scripts/imdb.pl
with /usr/share/mythtv/mythvideo/scripts/imdbpy.py

It works best with imdbpy version 3.9 and above for good TV support...
(actually, will make packages for this one will be easier that way)

Not as fancy as the perl script posted above, but it does get the poster and metadata properly filled up and is I believe a tad easier to set up...

---

### Post by liorkr on 2009-03-28
the script cant see my *.mkv files every thing is great with *.avi fils

do i need to edit/add somthing ?

---

### Post by utar on 2009-03-28
> **liorkr said:**
> the script cant see my *.mkv files every thing is great with *.avi fils

do i need to edit/add somthing ?

I had this problem.  Just add mkv as a filetype in myth.

---

### Post by liorkr on 2009-03-29
> **utar said:**
> I had this problem.  Just add mkv as a filetype in myth.

now everything is fine thanks for help

---

### Post by paulyche on 2009-03-29
Menny,

I've finally got around to uploading my edited version of this script (attached). This is using version 0.9 as a base.

Basically there is a new argument which allows the titles displayed in the frontend to be either in a short format (i.e. "01: Pilot") or a long format (i.e. "The West Wing S01E01 Pilot"). The short format is still the default.

The setting can be set in the script, or alternatively in a command line argument with '-SHORT_NAME 0/1'.

I am still seeing an issue where certain characters are not displaying properly. For example see the attached screen shot for the West Wing Season 1 Episode 1 (my all purpose example episode :-)). This could be a problem with tvdvb or mythfrontend though...

---

### Post by menny on 2009-03-30
Hi guys,
I've finished another version, which is much more stable than the one I've posted some days ago.
This one includes bug fixes (including the .nfo file repeating query Lorenzo1985 found), support for hidden nfo files, and support for setting the resolution of the snapshot, and support for specific episode ID (Lorenzo1985, this is for your girlfriend).

**Lorenzo1985**, please add your DB thing to it.
**paulyche**, please add you patch too.

Thanks for helping.

You can download the latest version from [http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl]("http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl"). This is a google code project, so if you want to work with SVN to add you fixes, tell me and I'll add your users to the google code project. Or you can just post your revised version, and I'll post it.

**utar**, regarding the 'VIDEO_TS' files, I have the same problem, I just didn't have the time to handle this.

Complete changelog from 0.8:
#version 0.9
#* It is possible to override the search for a tv show or movie, by creating a file within the video file folder ("nfo" extension)
#which includes the video file info:
#	* TV Show:
#		* To override the series: any .nfo file within the video file folder which contain '<thetvdb seriesid="[ID from thetvdb.com]"/>'
#		* To override the video file: create a file with the same name as the file but with .nfo extension. The file should contain '<thetvdb seriesid="[ID from thetvdb.com]" season="[number]" episode="[number]"/>'
#	* Movie:
#		* To override the video file: create a file with the same name as the file but with .nfo extension. The file should contain '<imdb id="[ID from imdb.com]"/>'
#	* Skip markers:
#		* To skip a file completely (just ignore, whatever in the database, if any, is OK): create a file with the same name as the file but with .nfo extension. The file should contain '<no_update/>'
#		* To skip a file parsing, and just add the file with a snapshot to the database (usefull for private videos): create a file with the same name as the file but with .nfo extension. The file should contain '<simple_update/>'
#NOTE: NFO files can be hidden.
#* Selects the most similar TV show from all results, rather than the first.
#* New command line argument:
#       * Work on a specific file (can be usefull for replacing imdb.pl script): -F [full path to file]
#       * Change the default snapshot width (height is calcualted by the aspect ratio): -SNAPSHOT_WIDTH [number]
#* bug fixes

---

### Post by menny on 2009-03-30
I've added code Paul posted to the script (again, it can be downloaded from "[http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl]("http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl")").
I also saw that paul added Lorenzo SQL password thingy, so I've merged that too, but haven't test that.

Please test, and tell me what you think.

---

### Post by grytpype on 2009-03-30
> **menny said:**
> I've added code Paul posted to the script (again, it can be downloaded from "[http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl]("http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl")").
I also saw that paul added Lorenzo SQL password thingy, so I've merged that too, but haven't test that.

Please test, and tell me what you think.

You know, Boxee already does a really good job of handling TV series metadata, why not just copy their code and modify it to write to the myth database?

[http://app.boxee.tv/download/source](http://app.boxee.tv/download/source)

---

### Post by menny on 2009-03-30
> You know, Boxee already does a really good job of handling TV series metadata, why not just copy their code and modify it to write to the myth database?
I've never ran Boxee, so I do not know how good their code is, furthermore, as I understand from THE-TV-DB site, Boxee also uses the same source as this script uses, so the quality of the information is the same.
And in any case, I'm pretty sure that Boxee is not using a script, but instead the tv-show handling is integrated into the Boxee application (which is good). I do not have the knowledge to do the same to MythVideo.
Maybe in 0.22, it will be handled by the MythVideo code.

---

### Post by paulyche on 2009-03-30
Hi just tried and every thing seems OK... Just one change though:

```
#this member will be used for show title.
my $actual_show_name;
```

on line 1251-1252 needs to be defined further up. I put it after line 988
```
my $last_folder_poster = '';
#this member will be used for show title.
my $actual_show_name;
```

Otherwise when long names are set only the first episode in a folder/series will be correct (i.e. "The West Wing S01E01 Pilot"), the rest will be missing the series name (i.e. " S01E02 Post Hoc, Ergo Propter Hoc")

---

### Post by menny on 2009-03-30
Fixed.
Please try again [http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl]("http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl")

---

### Post by utar on 2009-03-30
Menny


Many thanks for updating your script.  

I have just completed a quick test and all the new features (larger thumbnails, longer episode names, parsing of the mysql pw etc) are working great.

The only thing that doesn't seem to be working is imdb lookup when nothing can be found in thetvdb:

Video file 'Sin City.720p.h264.mkv' does not exist in the DB metadata. Inserting dummy row...
D=/var/lib/mythtv/videos/, F=Sin City.720p.h264.mkv
TV format 3: Show: 'Sin City', S:'7', E:'20'
Found Show: (id: ), 'sin city', season '7', episode '20'. last ID: 82046
Returning cached series ID '' for folder '/var/lib/mythtv/videos/'
Getting metadata for 'Sin City.720p.h264.mkv'...
Missing series ID. Searching by series name 'sin city'...
Searching THE-TV-DB for series 'sin city'
Found ID '' for series 'sin city' at THE-TV-DB.
Getting episode information...
Found meta-data: series id: , show: 'sin city', season: 7, episode: 20.
Did not find meta-data for episode!

I think that perhaps the naming convention I use is making the script think it is a TV show?

Cheers again for all your time you are spending on the script.  For the first time ever I now have my TV shows properly catalogued in Myth.

Edit: Just one question for the nfo series override is the following correct <thetvdb seriesid="73545"/>.nfo (for Battlestar in this case) as I'm having trouble naming a file to include the special characters.

---

### Post by menny on 2009-03-30
Hi uter,
I'll look into the problem you had with the sin city video.
Regarding the naming of the nfo file:
The name of the nfo can be anything!
I also had the problem with battlestar (too bad it is over, ah), and I created a file named "bg.nfo", and inside this file I've written > <thetvdb seriesid="73545"/>.
Like the file attached (unzip it, of course).

If you want to override a movie (maybe you'll like to do it for Sin City), create an nfo file with the same name like the movie, e.g., "Sin City.720p.h264.nfo", and inside of it write:
> <imdb id="tt0401792"/>

---

### Post by utar on 2009-03-30
Yes it is a pity BSG has finished.  I'm going to have to find something else to watch.  There is a lack of decent sci-fi around.

Thanks for the clarification re nfo files.  I was thinking that the string had to in the the name of the nfo, which explains why I couldn't get it to work.

For movies it is definitely my naming format that is confusing the script into thinking movies are TV shows.  Other movies I have named the same way are also not looked up on imdb.

Would a work around where "Found ID '' for series" caused the script to then look up at imdb be the easiest solution?

I would do this myself, unfortunately I'm not a programmer and the perl looks like a foreign language to me!

---

### Post by menny on 2009-03-30
**uter**, I've updated the script, please try the new version and see if it fixes your "sin city" issue.

**paulyche**, I think I know why the weird characters are happening to you. Try the updated script.

---

### Post by utar on 2009-03-30
Menny - yep the script is now working with my movies.  I was also having the same issue as paulyche in that quotes weren't working.  Have just tested and these are working as well.

The only thing that remains is that DVDs ripped to a directory are not parsed by the script.  For example if I had a directory called Sin City and in this had the video_ts directory etc.   Perhaps some logic could be put in the script where if there is a video-ts directory the script takes the name of the directory above it and then does a imdb search?

Now I just need to purchase a bigger HDD so I can archive all my TV shows on my myth box nicely catalogued :P


Utar

---

### Post by ranch hand on 2009-03-30
I do not have myth TV or Mythbuntu yet so I am lurking in hopes of learning.  When I build my system I will be downloading this script.  Thanks a bunch.

I don't know what nfo files really are but get a kick out of them.  NFO is an old farmers org.  National Farmers Organization.  I love it.

---

### Post by utar on 2009-03-30
Whoops just done a full rescan and noticed that a bug has appeared.  This seems to be one that was there earlier, in that when using long filenames only the first episode that is scanned has the "Show Name SxEx"  the other are missing the show name.

Edit: Also noticed that some shows aren't working, not sure if this is the latest version of the script or not as I have just copied the show across to my myth box:

```
~$ ./fill_mythvideo_metadata.pl -N 0 -D /var/lib/mythtv/videos/My\ Name\ is\ Earl/
looking at '-N'
Overriding new files scan. Will use '0'
looking at '-D'
Overriding DB folder. Will use '/var/lib/mythtv/videos/My Name is Earl/'
Using password from mysql.txt
NOTICE: You have selected to update ALL files! This will overwrite all previous data with new data.
Connecting to database...
Videos folder is: /var/lib/mythtv/videos/My Name is Earl/
Artwork folder is: /home/xxxx/.mythtv/MythVideo
Extensions: mpg|avi|vob|mpeg|VIDEO_TS|iso|img|mkv
======================================================================
Video file 'My Name is Earl 422 - Pinky.720p.h264.tvrip.mkv' does have not metadata in database.
D=/var/lib/mythtv/videos/My Name is Earl/, F=My Name is Earl 422 - Pinky.720p.h264.tvrip.mkv
TV format 3: Show: 'My Name is Earl 422 - Pinky', S:'7', E:'20'
Found Show: (id: ), 'my name is earl 422   pinky', season '7', episode '20'. last ID:
Will look at '/var/lib/mythtv/videos/My Name is Earl/'
Getting metadata for 'My Name is Earl 422 - Pinky.720p.h264.tvrip.mkv'...
Missing series ID. Searching by series name 'my name is earl 422   pinky'...
Searching THE-TV-DB for series 'my name is earl 422   pinky'
Found ID '' for series 'my name is earl 422   pinky' at THE-TV-DB.
Getting episode information...
Found meta-data: series id: , show: 'my name is earl 422   pinky', season: 7, episode: 20.
Did not find meta-data for episode! Will try as a movie...
Trying to load information for 'my name is earl 422 pinky' from IMDB...
Can not load IMDB data for 'my name is earl 422 pinky'.
Exiting eval via next at ./fill_mythvideo_metadata.pl line 1466.
======================================================================
Finished going over all the files: Found 1, updated 0 files.
Going over all video files in the database, and deleting any redundant entries (i.e., video files no longer exist)...
Deleted 0 entries from database!
======================================================================
Going over all image files in the artwork folder (at '/home/xxxx/.mythtv/MythVideo'), and deleting any redundant image files (i.e., owner video file does not exist)...
Deleted 0 redundant image files from the artwork folder.
======================================================================
Completing database...
======================================================================
Thanks for using MythVideo Metadata Updater v0.9.beta2.
======================================================================

```




Utar

---

### Post by menny on 2009-03-31
Uter, it seems like a new bug. I think I understand why - it is due to the spaces in the filename.

---

### Post by utar on 2009-03-31
> **menny said:**
> Uter, it seems like a new bug. I think I understand why - it is due to the spaces in the filename.

Is that the long episode naming or not reading the file names correctly issue (or both)?  Is it an easy fix?


Utar

---

### Post by menny on 2009-04-01
> Is that the long episode naming or not reading the file names correctly issue (or both)? Is it an easy fix?
It looks like a paring problem. And I think it is a simple fix, I fix it soon.

---

### Post by menny on 2009-04-01
Uter,
Please download the latest version from [http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl]("http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl")

Tell me if it fixes you issue

---

### Post by utar on 2009-04-01
Thanks for updating the script.

Just rescanned all my files.  The script seems to be working now with files with spaces, however the long episode naming is still broken.  The first episode is named correctly but then subsequent episodes have the short name.

I have also run the script with the default "new files only" option and the script looks to be updating files that already exist.  For example on my last run:

Finished going over all the files: Found 48, updated 32 files.

This is with no new files added.  The script says things like:

Video file 'the.big.bang.theory.s02e19.720p.hdtv.x264-ctu.mkv' does have not metadata in database.

When the file has already been scanned and a picture, and episode narrative is included.  This doesn't particularly matter since it adds the metadata again, but it does slow down the execution speed since files are rescanned and looked up on thetvdb.




utar

---

### Post by menny on 2009-04-02
Uter,

> Just rescanned all my files. The script seems to be working now with files with spaces, however the long episode naming is still broken. The first episode is named correctly but then subsequent episodes have the short name.

fixed, take the new version from [http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl]("http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl")

I'm working on the rest

---

### Post by menny on 2009-04-02
Uter,

> I have also run the script with the default "new files only" option and the script looks to be updating files that already exist. For example on my last run:

Finished going over all the files: Found 48, updated 32 files.

This is with no new files added. The script says things like:

Video file 'the.big.bang.theory.s02e19.720p.hdtv.x264-ctu.mkv' does have not metadata in database.

When the file has already been scanned and a picture, and episode narrative is included. This doesn't particularly matter since it adds the metadata again, but it does slow down the execution speed since files are rescanned and looked up on thetvdb.

Please download the latest version of the script and try again.
I found the bug, and fixed it.
There was a bug in the database upadting, so, the first time you'll run the fixed script, it will update the files AGAIN, and from the second time, it will not update them.

This is a dumb bug, and it is very important to use the latest, since it will reduce the stress on THE-TV-DB servers.

Thanks for finding this bug.

---

### Post by utar on 2009-04-02
Cheers

I'm currently at work but will run the script tonight when I get home.

I was thinking that it may be worth expanding the short episode naming format from EE to SSEE as if you have more then one season the current naming convention will be confusing.  This is a personal preference thing though, I personally like the long name format. 

Feature wise the other thing I can think is missing is to deal with DVDs ripped to a folder, rather then an iso.

There was one other very minor thing I noticed yesterday.  BSG was named "battlestar galactica", i.e. with no capital B and G.  Not sure if this is a tvdb issue or potentially linked to the fact that I have a nfo override for this series.  As I say it's hardly worth bothering about, just thought I would note it for completeness.

Have you considering adding a page on the mythtv wiki for the script.  I'm sure lots of people would find the script useful, I have already recommended it to all my friends who use myth.


Utar

---

### Post by menny on 2009-04-02
Uter,
Please tell me if it works, and I think it will also fix the capital letters issue you said (tell me if it doesn't).

Menny

---

### Post by utar on 2009-04-02
Just done a quick test.  Something seems to be wrong as the script gives 404 errors in some cases:

```
D=/var/lib/mythtv/videos/Chuck/, F=chuck.s02e17.720p.hdtv.x264-ctu.mkv
looking for '/var/lib/mythtv/videos/Chuck/.chuck.s02e17.720p.hdtv.x264-ctu.nfo' for video file details.
TV format 1: Show: 'chuck.', S:'02', E:'17'
Found Show: (id: ), 'chuck', season '2', episode '17'. last ID:
Will look at '/var/lib/mythtv/videos/Chuck/'
Getting metadata for 'chuck.s02e17.720p.hdtv.x264-ctu.mkv'...
Missing series ID. Searching by series name 'chuck'...
Searching THE-TV-DB for series 'chuck'
Found a possible match for 'chuck' as 'Chuck' (ID 80348)
Found ID '80348' for series 'chuck' at THE-TV-DB.
Downloading folder art for series from 'http://70.98.76.33/banners/graphical/80348-g.jpg' to '/var/lib/mythtv/videos/Chuck/'...
Checking folder art at directory '/var/lib/mythtv/videos/Chuck/'
Downloading http://70.98.76.33/banners/graphical/80348-g.jpg to /var/lib/mythtv/videos/Chuck/folder.jpg
--2009-04-02 18:51:28--  http://70.98.76.33/banners/graphical/80348-g.jpg
Connecting to 70.98.76.33:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://images.thetvdb.com/banners/graphical/80348-g.jpg [following]
--2009-04-02 18:51:29--  http://images.thetvdb.com/banners/graphical/80348-g.jpg
Resolving images.thetvdb.com... 205.196.222.35
Connecting to images.thetvdb.com|205.196.222.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 71187 (70K) [image/jpeg]
Saving to: `/var/lib/mythtv/videos/Chuck/folder.jpg'

100%[======================================>] 71,187      46.0K/s   in 1.5s

2009-04-02 18:51:31 (46.0 KB/s) - `/var/lib/mythtv/videos/Chuck/folder.jpg' saved [71187/71187]

Checking folder art at directory '/var/lib/mythtv/videos/'
No need to download http://70.98.76.33/banners/graphical/80348-g.jpg. I have it locally at /var/lib/mythtv/videos/Chuck/folder.jpg.
Getting episode information...
Failed to get response! Status '404 Not Found'
```


Thetvdb seems to be working as the folder.jpg is being downloaded etc so this may be a bug in the script. [Edit: metadata does download for some other files so this is a bug]

There is a simple bug with DVDs in a folder too.  Basically it looks like the video_ts folder is added to the database, rather then the parent folder.  This means that the video browser doesn't detect the metadata.

---

### Post by Slate8 on 2009-04-02
Great script! I've just started playing around with it and something I have noticed. When the $ArtworkDirectory var is set by executing:

```
select data from settings where value="VideoArtworkDir"
```

The hostname fields is not taken into account in the settings table. On my network I have three myth systems all connecting to a common backend. When I ran the script $ArtworkDirectory was set from my bedroom machine's settings rather than the backend machine.

On another note I can't seem to get it to scan mkv files but I've only just started playing so probably something I'm doing :)

---

### Post by utar on 2009-04-02
> **Slate8 said:**
> On another note I can't seem to get it to scan mkv files but I've only just started playing so probably something I'm doing :)

Add mkv as a file type into myth and the script will then scan the files.

---

### Post by Slate8 on 2009-04-02
> **utar said:**
> Add mkv as a file type into myth and the script will then scan the files.

Thanks for the tip but I couldn't see anywhere in the script to add it in? The script seems to look it up from the videotypes table for MythVideo. Added mkv in there and it works a treat now :)

---

### Post by menny on 2009-04-02
uter,
Try the new version now.
Also, if you still having 404 errors, it is due to servers upgrades of the-tv-db ([http://forums.thetvdb.com/viewtopic.php?f=3&t=847]("http://forums.thetvdb.com/viewtopic.php?f=3&t=847")).

Slate8,
The hostname is a good point. I need to look into that.
Regarding the MKV files, you should add them to the MythVideo file-types (it is somewhere in the frontend setup options).

---

### Post by utar on 2009-04-02
Still getting 404 errors when the script tries to load things like:

[http://www.thetvdb.com/api/6770D263BF045B96/series/73545/default/4/20/en.xml](http://www.thetvdb.com/api/6770D263BF045B96/series/73545/default/4/20/en.xml)

I'll wait to thetvdb servers are working again.

There has been no change with DVDs in folders.  The script still adds, for example, "2001 Maniacs/video_ts" to the database rather then the correct "2001 Maniacs".

EDIT: Just noticed the script uses two different urls:

[http://www.thetvdb.com/api/6770D263BF045B96/series/73545/en.xml](http://www.thetvdb.com/api/6770D263BF045B96/series/73545/en.xml)
[http://www.thetvdb.com/api/6770D263BF045B96/series/73545/default/4/20/en.xml](http://www.thetvdb.com/api/6770D263BF045B96/series/73545/default/4/20/en.xml)

The first is for folder art, which works and the second I believe is for metadata, which doesn't work.  However I note that metadata (episode overview etc) is included in the first link. [Edit2! - ignore that I now see that it is just the series overview in the first link, not the episode overview.  Will wait until the servers are working again.]

Utar

---

### Post by utar on 2009-04-02
The server is back up.

Long file names are working fine, and the bug where the script was updating files that had already been scanned has been fixed.

There is still the minor issue with capitals with BSG, although interestingly with nothing else.  Don't suppose this is due to either the nfo override or the fact that the full title "Battlestar Galactica (2003)" has brackets in the name?


Utar

---

### Post by menny on 2009-04-03
> The server is back up.

Long file names are working fine, and the bug where the script was updating files that had already been scanned has been fixed.
Good to hear, thanks for notifying :)

> There is still the minor issue with capitals with BSG, although interestingly with nothing else. Don't suppose this is due to either the nfo override or the fact that the full title "Battlestar Galactica (2003)" has brackets in the name?
I'll look into that, I have BSG in my folders, so it won't be hard to reproduce.

---

### Post by menny on 2009-04-04
> **utar said:**
> There has been no change with DVDs in folders.  The script still adds, for example, "2001 Maniacs/video_ts" to the database rather then the correct "2001 Maniacs".

Uter, can you explain again the problem you are having with DVDs?

---

### Post by utar on 2009-04-04
For DVDs in a folder myth wants the name of the parent folder in the database (the one containing a video_ts subdirectory).  However the script adds the video_ts directory instead.

So "Folder/video_ts" gets added to the database instead of "Folder" and as such it doesn't work.

---

### Post by jbman on 2009-04-04
I have tried this out with not much luck.

I downloaded the latest version, made is executable. Edited the file to change my db password. 

This is what i get when i run the file

```
Extensions: mpg|avi|vob|mpeg|VIDEO_TS|iso|img
grep: Support for the -P option is not compiled into this --disable-perl-regexp binary
find: write error: Broken pipe
======================================================================
Finished going over all the files: Found 0, updated 0 files.
Going over all video files in the database, and deleting any redundant entries (i.e., video files no longer exist)...
Deleted 0 entries from database!

```

I am running mythbuntu 8.04
Cheers

---

### Post by utar on 2009-04-04
Found a bug in the script with episodes where the season is 2 digits:

The Simpsons 2015 - Wedding For Disaster.720p.h264.tvrip.mkv
South Park 1303 - Margaritaville.720p.h264.tvrip.mkv

Although it does work when the episode is named, for example, "s20e15".  

Would it be possible to add support of the above naming convention to the script?


Utar

---

### Post by utar on 2009-04-04
> **jbman said:**
> I have tried this out with not much luck.

I downloaded the latest version, made is executable. Edited the file to change my db password. 

This is what i get when i run the file

```
Extensions: mpg|avi|vob|mpeg|VIDEO_TS|iso|img
grep: Support for the -P option is not compiled into this --disable-perl-regexp binary
find: write error: Broken pipe
======================================================================
Finished going over all the files: Found 0, updated 0 files.
Going over all video files in the database, and deleting any redundant entries (i.e., video files no longer exist)...
Deleted 0 entries from database!

```

Cheers

Not sure if this will help but have you installed the imdb perl module the script requires?  You can do this by the following (without the quotes):

"sudo perl -MCPAN -e 'install IMDB::Film'"

---

### Post by jbman on 2009-04-04
Thanks, but I did that on reading the info at the start of the file.

---

### Post by menny on 2009-04-05
jbman,
I'll try to remove the grep-perl dependency.

utar,
I see the problem, I'll try to do a quick fix for you.

---

### Post by Sdx1978 on 2009-04-06
Hi Menny,

This looks to be an amazing script. Congratulations for this work.

However I can not enjoy it myself:

Running on Mythbuntu 8.10 x86

> sudo perl -MCPAN -e 'install WWW::TV'

returns
> <...>
Failed Test    Stat Wstat Total Fail  List of Failed
-------------------------------------------------------------------------------
t/10_episode.t  255 65280    41   45  13 15-41
t/20_series.t   255 65280    33   41  3 5-10 13-16 18-33
2 tests skipped.
Failed 2/4 test scripts. 55/74 subtests failed.
Files=4, Tests=74, 50 wallclock secs ( 0.64 cusr +  0.05 csys =  0.69 CPU)
Failed 2/4 test programs. 55/74 subtests failed.
make: *** [test_dynamic] Error 255
  TIGRIS/WWW-TV-0.14.tar.gz
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports TIGRIS/WWW-TV-0.14.tar.gz
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make install
  make test had returned bad status, won't install without force

Could you help me solving this issue?

Thx

---

### Post by utar on 2009-04-06
Looks like you have a typo, s/b :

sudo perl -MCPAN -e 'install IMDB::Film'


Utar

---

### Post by menny on 2009-04-06
Sdx1978,
There is no need to run "sudo perl -MCPAN -e 'install WWW::TV'".
Just the "sudo perl -MCPAN -e 'install IMDB::Film'", as uter mentioned.

---

### Post by Sdx1978 on 2009-04-06
Hi Menny,

I followed your comment and now it is working fine. Fine means I can get run the script, get metadata, posters and see them in Mythbuntu.

However, I have the following issues:

1- After runnning the script, I can not see the banner of the TV show at the place of directory, but I can see an image for each episode of the show.
To be clearer:
> 
Series
[INDENT]|_____ Dexter
[INDENT]|_______s3   <- No picture but "folder.jpg" file
[INDENT]|_____ dexter.s3e01.avi   <- Get metadata & picture
|_____ dexter.s3e02.avi   <- Get metadata & picture
[/INDENT]
[/INDENT]
[/INDENT]

2- If I go to "Setup" -> "Video Manager", I have the following pop-up
 Videos/Series/Dexter/Dexter.s3e01.avi appears to be missing. Remove it from database?
If I accept, I'm loosing all metadatas related to video files, but folder.jpg are displayed, and listed in sub directories.
To be clearer:
> 
Series
[INDENT]|_____ Dexter
[INDENT]|_______s3   <- "folder.jpg" is displayed
[INDENT]|_____ dexter.s3e01.avi   <- No metadata & no picture
 |_____ dexter.s3e02.avi   <- No metadata & no picture
[/INDENT]
[/INDENT]
[/INDENT]
				
If I refuse, all video files appear twice in the list "Video database".
For each file, one contains the metadata and the other is raw.

3- You could ask why would I go to "Setup" -> "Video Manager". Some video files are not recognised by the script, thus I must update them by end, and believe the "Video Manager" would be the right place.
Any other idea ?

4- One of my video file is nammed "La clef.avi". The script log is:
> 
Video file 'la clef.avi' does have not metadata in database.
D=Videos/Movies/, F=la clef.avi
looking for 'Videos/Movies/.la clef.nfo' for video file details.
Can not parse 'la clef.avi' as tv show. Will try as a movie...
Trying to load information for 'la clef' from IMDB...
Since local name 'la clef' and IMDB name 'Clef, La' (ID: 0920454) are not very similar, I'll skip this...

The two names are very similar. Is it possible for the script to manage such cases?

Last point, if I manage my movie folder as
Movies
[INDENT]|_____ scarface.avi
|_____ la clef.avi
|_____ the eye.avi
[/INDENT]
While script is running, it only find metadata for "scarface.avi". It stores the right "jpg" file in artwork, but in my "Movies" folder, it stores as well a "folder.jpg", which in this particular case if the cover of Scarface.
I think if I got more movies recognised by the script, the "folder.jpg" would be the cover of the last parsed movie.
Does it mean I must create a folder by movie?

Again, let me congratulate for this job. I hope my comments will be useful.
I saw some similar comments in the discussion, but I don't find a clear solution to those various points.

Regards. :p

PS:
I'm using the 0.9.1 version
> #created by Menny Even-Danan (mennyed at the g mail thing)
#additional work by Lorenzo1985 and paulyche (from Mythbuntu forums).
my $script_version = "0.9.1";
#version 0.9
#2nd April 2009


---

### Post by utar on 2009-04-06
Sdx


For 1 & 2 I believe what is confusing the script is that you have sub folders for each season.  Try putting the episodes straight into the Dexter directory and running the script again. 

For 4, you can override the search using an nfo file (details are in the narrative at the start of the script).  Re the folder.jpg for movies I can see what you mean and I'm not sure about the best solution.  Suppose you could add a blank folder.jpg and write protect the file so the script can't overwrite it as a work around. **Menny **- perhaps a better solution would be a nfo override option that stops the script from downloading a folder.jpg for certain directories?


Utar

---

### Post by menny on 2009-04-06
Hi,
A new version is available at: [http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl]("http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl")
jbman, I've removed the dependency for grep-perl. You can try now.

Sdx1978, your folders structure should work.
Can you run the script again and paste the console trace if there is a problem?

utar, your "the simpsons" parsing should work now.

---

### Post by utar on 2009-04-06
TV episodes with the SSEE naming convention are now working great thanks.

Unfortunately a new bug has been introduced, which I am guessing is due to the changes you made for sdx1978.  For DVDs ripped to a folder the script looks up every vob file on imdb and then adds a dummy row to the database.  It is also still not putting the right path in the database and is instead adding the video_ts folder, but am not sure if you have had chance to look at this yet.


Utar

---

### Post by menny on 2009-04-06
Uter,
Try the new version now.
It should fix the DVD issue.

---

### Post by joshoekstra on 2009-04-06
Is there an option to set the artwork dir?
I don't use the /home/user/.mythtv/MythVideo folder but one in the root of the NFS-exported moviedir which enables the posters on remote frontends as well.
Is there a way to get it from the DB where it's properly stored?

EDIT: ah found it: search for Artwork and then fill in the right dir here:
> my $ArtworkDirectory = '/your/dir/here';

---

### Post by utar on 2009-04-06
> **menny said:**
> Uter,
Try the new version now.
It should fix the DVD issue.

Yep, DVDs in a folder are now working.

I think I have run out of things to pester you about as everything is working!  

[Edit: Don't worry I have remembered a minor issue!  Basically I have been testing with nfo series over rides and as I mentioned with BSG the name is all in lower case.  The exact same issue arose when I used an over ride for The Simpsons.]

[Is the following right to override a file?

<thetvdb seriesid="75978" season="23437" episode="419067"/>

This is for Family Guy Blue Harvest Special.  The script complains about "Use of uninitialised value $episode_id"]


Utar

---

### Post by menny on 2009-04-07
> **utar said:**
> Yep, DVDs in a folder are now working.

I think I have run out of things to pester you about as everything is working!  

Good to hear :)
> **utar said:**
> 
[Edit: Don't worry I have remembered a minor issue!  Basically I have been testing with nfo series over rides and as I mentioned with BSG the name is all in lower case.  The exact same issue arose when I used an over ride for The Simpsons.]

I will check the lowercase issue
> **utar said:**
> 
[Is the following right to override a file?

<thetvdb seriesid="75978" season="23437" episode="419067"/>
This is for Family Guy Blue Harvest Special.  The script complains about "Use of uninitialised value $episode_id"]
Utar
No, it should be:
> <thetvdb episodeid="419067"/>
If you know the exact episode ID, there is no need to set the series or season.
BTW, a great episode :)

---

### Post by utar on 2009-04-07
> **menny said:**
> Good to hear :)

I will check the lowercase issue

No, it should be:

If you know the exact episode ID, there is no need to set the series or season.
BTW, a great episode :)

Cheers for checking on the lower case issue.

Still can't get the episode override to work, I have tried all of the following:

<thetvdb episode="419067"/>  
<thetvdb episodeid="419067"/>  
<thetvdb episode_id="419067"/>  

And they all give the same error message.  Changing the episode number also has no effect.

I have ordered a 1TB HDD for my media centre to go with the existing drive and am looking forward to having everything nicely archived with proper metadata thanks to your script :)



Utar

---

### Post by jbman on 2009-04-07
Thanks for removing the perl-grep dependency.

I have a couple of questions/ideas.

folder.jpg what to I put in the mythvideo setup to stop that showing up as a file? Will mythvideo read teh file if its set t hidden? Can we make the folder.jpg hidden or have the option?

Also with movies with two files cd1 cd2 is there a way to make that like mythvideo does where its set to autorun the next file and it seems to hide the cd2 from view?

All in all great script. Grabbed my tv show data a treat :) 

Thanks heaps cheers

---

### Post by crez79 on 2009-04-07
> **jbman said:**
> 
Also with movies with two files cd1 cd2 is there a way to make that like mythvideo does where its set to autorun the next file and it seems to hide the cd2 from view?

I ran into this problem and I found joining them with avimerge was easiest for me. But there is a setting in video manager to have it play another file after. For whatever reason, myth automagically plays the sequel to the movie I play, like if I watch Back to the Future it will play the second then the third. I haven't done anything so I don't know why, but it does it for all the movies that have sequels..

And the script grabs data and makes screen shots excellent for my tv shows. Thanks!

---

### Post by menny on 2009-04-08
> **utar said:**
> Cheers for checking on the lower case issue.

Still can't get the episode override to work, I have tried all of the following:

<thetvdb episode="419067"/>  
<thetvdb episodeid="419067"/>  
<thetvdb episode_id="419067"/>  

And they all give the same error message.  Changing the episode number also has no effect.

I have ordered a 1TB HDD for my media centre to go with the existing drive and am looking forward to having everything nicely archived with proper metadata thanks to your script :)



Utar
Found the bug. Please try now.

---

### Post by menny on 2009-04-08
> **jbman said:**
> Thanks for removing the perl-grep dependency.

So it works?


> **jbman said:**
> 
folder.jpg what to I put in the mythvideo setup to stop that showing up as a file? Will mythvideo read teh file if its set t hidden? Can we make the folder.jpg hidden or have the option?

You should remove the "jpg" file type from the MythVideo list (it is somewhere in the frontend setup menu).
You do not need to set the file to hidden.

> **jbman said:**
> 
Also with movies with two files cd1 cd2 is there a way to make that like mythvideo does where its set to autorun the next file and it seems to hide the cd2 from view?

I do not know of any such feature in MythVideo.

---

### Post by utar on 2009-04-08
> **menny said:**
> 
You should remove the "jpg" file type from the MythVideo list (it is somewhere in the frontend setup menu).
You do not need to set the file to hidden.


That actually depends on if you have the option to show all files types selected in Myth, this will show files even if the file type is not set-up.

Assuming you have this option selected, add jpg as a file type in Myth, can't remember where exactly but look under media setting.  There is then a box on the same set-up screen where you can select to hide the file.



Utar

---

### Post by Lorenzo1985 on 2009-04-08
Episode Id selection still doesn't seem to work.

> 
======================================================================
Video file 'The_Vicar_Of_Dibley.SP04.The_Vicar_in_White.avi' does have not metadata in database.
D=/media/media/Videos/TV/The_Vicar_of_Dibley/Specials/, F=The_Vicar_Of_Dibley.SP04.The_Vicar_in_White.avi
Video file has NFO file. Looking for video information in it...
Found THE-TV-DB information in NFO file (episode id: 332108). Getting identifies parameters...
About to call GET HTTP url: 'http://www.thetvdb.com/api/6770D263BF045B96/episodes/332108/en.xml'
Found THE-TV-DB information in NFO file (series id: , season: , episode: ), using it to get meta-data about the file
Found Show: (id: ), '', season '', episode ''. last ID:
Will look at '/media/media/Videos/TV/The_Vicar_of_Dibley/Specials/'
nfo: '/media/media/Videos/TV/The_Vicar_of_Dibley/Specials/The_Vicar_Of_Dibley.SP04.The_Vicar_in_White.nfo'
Getting metadata for 'The_Vicar_Of_Dibley.SP04.The_Vicar_in_White.avi'...
FATAL ERROR!! no series_id and no show name!!
Exiting eval via next at /home/loz/fill_mythvideo_metadata.pl line 1412.
======================================================================


---

### Post by menny on 2009-04-08
Lorenzo and uter, try the new version now.
It should work - I found another bug, and tested better this time :)

joshoekstra, please download the latest script, and use the new command line argument for overriding the artwork folder. This way you wont have to edit the script every time you update it.
> -ARTFOLDER [full path to folder]

---

### Post by jbman on 2009-04-08
Added ignore jpg and now folder does not come up.

Going to check the cd1 cd2 settings and see what happens.

Otherwise working well me me thanks heaps.

---

### Post by utar on 2009-04-08
> **menny said:**
> Lorenzo and uter, try the new version now.
It should work - I found another bug, and tested better this time :)

joshoekstra, please download the latest script, and use the new command line argument for overriding the artwork folder. This way you wont have to edit the script every time you update it.

Yep, the nfo file override is now working :p

Quick question - I have tried to change the time into each video file the screen grab is taken (as with South Park for example every thumb nail is the same as they are taken from the intro credits) by changing the numbers in the following lines:

my $thumb_offset = int( $video_length *  0.3 );
my $thumb_offset = int( $video_length *  0.6 );

But this has no effect whatsoever.  What am I doing wrong?



Utar

---

### Post by silverdulcet on 2009-04-08
> **menny said:**
> Lorenzo and uter, try the new version now.
It should work - I found another bug, and tested better this time :)

joshoekstra, please download the latest script, and use the new command line argument for overriding the artwork folder. This way you wont have to edit the script every time you update it.

joshoekstra/menny,

Just thought I'd point out that you can change the default artwork folder from within the Mythvideo Settings.

Utilities/Setup>Setup>Media Settings>Video Settings>General Settings>(1/7)

Second configuration box down:
```
Directory that holds movie posters: /home/mythtv/.mythtv/MythVideo
```

Then you won't require a commandline switch to specify it. Still it is handy in case you want to override the default setting for whatever reason.

---

### Post by jbman on 2009-04-08
I have found the play next setting. Take a look at a video in the video manager and check the metadata there is an option to load the next video.

If i do a scan from the video manager it hides cd2, but at the moment running the script it labels the movie the same with two copies

```
  Per-file Configuration

Individual videos can be configured using the video manager at Main Screen->Utilities /Setup -> Video Manager.

You can also run specified files with a non-standard command. While in the video manager, if you hit enter on a specific file, you are presented with the settings for that file. The categories here are fairly self explanatory, but in the Unique Player Command box at the bottom you can specify different parameters to launch the file with.

If your movie comes in two or more parts, you can specify the file you always want to play next under File to Always Play Next. For example, if I'm editing "A Film Too Long CD1", I can shift left and right until I find "A Film Too Long CD2" and so on. This will give you seamless playback of your chosen flick. 
``` 

thats from the mythtv wiki

---

### Post by joshoekstra on 2009-04-09
> **silverdulcet said:**
> joshoekstra/menny,

Just thought I'd point out that you can change the default artwork folder from within the Mythvideo Settings.

Utilities/Setup>Setup>Media Settings>Video Settings>General Settings>(1/7)

Second configuration box down:
```
Directory that holds movie posters: /home/mythtv/.mythtv/MythVideo
```

Then you won't require a commandline switch to specify it. Still it is handy in case you want to override the default setting for whatever reason.

I know, but I've got several frontends and some of them used to have the default set, since I'm running the script on the MBE I'd like to keep the covers there as well. Somehow the script was using another setting from the database before which gave the wrong folder. With this override I can now grab the metadata and posters in the desired folder.
One thing to not as I'm 'tab-crazy' a trailing '/' caused my coversfolder to be wiped clean :S

---

### Post by joshoekstra on 2009-04-09
> **silverdulcet said:**
> joshoekstra/menny,

Just thought I'd point out that you can change the default artwork folder from within the Mythvideo Settings.

Utilities/Setup>Setup>Media Settings>Video Settings>General Settings>(1/7)

Second configuration box down:
```
Directory that holds movie posters: /home/mythtv/.mythtv/MythVideo
```

Then you won't require a commandline switch to specify it. Still it is handy in case you want to override the default setting for whatever reason.

I know, but I've got several frontends and some of them used to have the default set, since I'm running the script on the MBE I'd like to keep the covers there as well. Somehow the script was using another setting from the database before which gave the wrong folder. With this override I can now grab the metadata and posters in the desired folder.
One thing to not as I'm 'tab-crazy' a trailing '/' caused my coversfolder to be wiped clean :S Other than that it pretty much works perfectly.

---

### Post by oobe-feisty on 2009-04-09
> **joshoekstra said:**
> I know, but I've got several frontends and some of them used to have the default set, since I'm running the script on the MBE I'd like to keep the covers there as well. Somehow the script was using another setting from the database before which gave the wrong folder. With this override I can now grab the metadata and posters in the desired folder.
One thing to not as I'm 'tab-crazy' a trailing '/' caused my coversfolder to be wiped clean :S Other than that it pretty much works perfectly.

just use and NFS mount on each of your frontends to mount ~/.mythtv/MythVideo on your backend in the same spot

im sure your already familar with setting up mounts so i wont bother explaining how

---

### Post by Slate8 on 2009-04-10
Oops, ignore me...

---

### Post by joshoekstra on 2009-04-11
> **oobe-feisty said:**
> just use and NFS mount on each of your frontends to mount ~/.mythtv/MythVideo on your backend in the same spot

im sure your already familar with setting up mounts so i wont bother explaining how
Why use 2 mounts when you can do it in one? ;)

---

### Post by Lorenzo1985 on 2009-04-11
> **joshoekstra said:**
> I know, but I've got several frontends and some of them used to have the default set, since I'm running the script on the MBE I'd like to keep the covers there as well. Somehow the script was using another setting from the database before which gave the wrong folder. With this override I can now grab the metadata and posters in the desired folder.
One thing to not as I'm 'tab-crazy' a trailing '/' caused my coversfolder to be wiped clean :S Other than that it pretty much works perfectly.

The issue here is that the script doesn't select settings based on the host name. You could force it to select the correct record for your MBE by changing line 1090 from
```
$sqlstat=qq {select data from settings where value="VideoArtworkDir"}; 
```
to
```
$sqlstat=qq {select data from settings where value="VideoArtworkDir" and hostname="<hostname>"};
```

where <hostname> is replaced by the hostname of the MBE. We need to work out a way for the script to work out the hostname of the computer it's running on so this can be added. Preferably without any dependencies on other packages. I'm not sure how to do that in perl.

---

### Post by Lorenzo1985 on 2009-04-14
Weirdly the script still seems to be adding jpg folder are where png folder art exists.

Even thought the code definetly exists to prevent this. I'm sure this issue was actually fixed in the past aswell.

---

### Post by joshoekstra on 2009-04-14
> **Lorenzo1985 said:**
> The issue here is that the script doesn't select settings based on the host name. You could force it to select the correct record for your MBE by changing line 1090 from
```
$sqlstat=qq {select data from settings where value="VideoArtworkDir"}; 
```
to
```
$sqlstat=qq {select data from settings where value="VideoArtworkDir" and hostname="<hostname>"};
```

where <hostname> is replaced by the hostname of the MBE. We need to work out a way for the script to work out the hostname of the computer it's running on so this can be added. Preferably without any dependencies on other packages. I'm not sure how to do that in perl.

Well the command hostname gives me the right hostname back, how to incorporate it, is still pretty much abacadabra for me...

---

### Post by menny on 2009-04-14
Hi guys.
I've just finished a new version of the script.
The major issue is that the script now parses IMDB by itself, and does not require outside modules - the script can run on any myth-tv box without installing 3rd party perl modules!
As a result, the IMDB is much more precise for our needs.
Also, the script detects the hostname of the machine, and will detect the correct art-work folder and video folder (the hostname can be overridden, if needed).
And there are new titles format for use.
And I've fixed some more bugs.

> 
#*New IMDB parser. No need for IMDB::Film perl module!
#*New command line arguments:
#	-HOST [hostname] : Override the automatic hostname resolving.
#	-TV_TITLE_TYPE [0/1/2]
#			0-[Filename]
#			1(default)-[Episode number]: [Episode name]
#			2-[Show] S[Season number]E[Episode number] [Episode name]
#			3-[Show] [Season number]x[Episode number] [Episode name]
#	-MOVIE_TITLE_TYPE [0/1/2]
#			0-[Filename]
#			1(default)-[Movie name from IMDB]
#*Bug fixes


Please test it and tell me what you think, and what bugs you've found.

Thanks,
Menny

The script can be downloaded from here: [http://mythvideo.ByInter.net]("mythvideo.ByInter.net")

---

### Post by oobe-feisty on 2009-04-15
Hi thanks for adding the new episode title feature so fast however there is a problem the season gets the epsisode number aswell i.e 

a file named 
life.on.mars.s01e01.avi will look ok 

Life on mars 1x01 '


but life.on.mars.s01e05.avi

will look like this 

Life on mars 05x05

---

### Post by jbman on 2009-04-15
I would like to see the -TV_TITLE_TYPE put back into the script or even a config file so it does not need to be editied.

running the new version now, will report back if i have any issues.

thanks heaps for your work on this

---

### Post by menny on 2009-04-15
> **jbman said:**
> I would like to see the -TV_TITLE_TYPE put back into the script or even a config file so it does not need to be editied.
Please explain.

---

### Post by Slate8 on 2009-04-15
Nice looking update. Looking forward to trying this one. Good work!

---

### Post by utar on 2009-04-15
> **jbman said:**
> I would like to see the -TV_TITLE_TYPE put back into the script or even a config file so it does not need to be editied.

I agree it would be good to have this option back in the script. By which I mean that in the old version of the script you could edit the default option directly at the start of the script, while now it can only be done through the command line.

I have done some testing and note the following:

1) TV_TITLE_TYPE 1 does not work and gives the same EE names as TV_TITLE_TYPE 0.  However TV_TITLE_TYPE 2 works fine;

2) I like how the file name is included in the metadata.

3) For DVDs in a folder the script adds the "audio_ts" directory to the database (and also tries to do an imdb lookup as well). This bug was in the last version of the script as well.

4) The lower case bug where there is an nfo override still exists.

5) As pointed out in a post above a folder.jpg is still created even when there is a folder.png.


Thanks

---

### Post by menny on 2009-04-15
> **utar said:**
> I agree it would be good to have this option back in the script. By which I mean that in the old version of the script you could edit the default option directly at the start of the script, while now it can only be done through the command line.
I've added the variables at the beginning of the script.
But I still think that it is much better to use command line arguments, this way you do not need to remember which variables you need to edit every time you download a new version of the script. I use another file to run the script, and this file uses all the arguments I want.

> **utar said:**
> 
I have done some testing and note the following:

1) TV_TITLE_TYPE 1 does not work and gives the same EE names as TV_TITLE_TYPE 0.  However TV_TITLE_TYPE 2 works fine;

I was unable to reproduce it. 0,1,2, and 3 all are working for me, and produce different titles:
0-[Filename]
1(default)-[Episode number]: [Episode name]
2-[Show] S[Season number]E[Episode number] [Episode name]
3-[Show] [Season number]x[Episode number] [Episode name]
> **utar said:**
> 
2) I like how the file name is included in the metadata.

:)

> **utar said:**
> 
3) For DVDs in a folder the script adds the "audio_ts" directory to the database (and also tries to do an imdb lookup as well). This bug was in the last version of the script as well.

what is this folder? I do not have it in my DVD rips.
> **utar said:**
> 
4) The lower case bug where there is an nfo override still exists.

I'll look into that.
> **utar said:**
> 
5) As pointed out in a post above a folder.jpg is still created even when there is a folder.png.

Fixed. Can you try now.

The new version is available at: [http://mythvideo.byinter.net/](http://mythvideo.byinter.net/)

BTW, Has anyone tried movies? I've created a new IMDB parser, and I'll like to get some feedback about it.

Thanks for testing.

---

### Post by utar on 2009-04-15
> **menny said:**
> I've added the variables at the beginning of the script.

That's great, many thanks for adding the variables.

> **menny said:**
> I was unable to reproduce it. 0,1,2, and 3 all are working for me, and produce different titles:
0-[Filename]
1(default)-[Episode number]: [Episode name]
2-[Show] S[Season number]E[Episode number] [Episode name]
3-[Show] [Season number]x[Episode number] [Episode name]

Whoops!  Sorry I misread the options in your earlier post.

> **menny said:**
> what is this folder? I do not have it in my DVD rips.

An Audio_ts folder is on all video DVDs, albeit it's empty.  I believe it's part of the specification that this folder should be included.  The DVD ripping software I use includes this directory, presumably because it's part of the specification.  I can easily delete this folder so it's not a problem if it's too much trouble to modify the script. 

> **menny said:**
> BTW, Has anyone tried movies? I've created a new IMDB parser, and I'll like to get some feedback about it.

I've tried it on a couple and everything looks to be working.

---

### Post by menny on 2009-04-15
> **utar said:**
> 
An Audio_ts folder is on all video DVDs, albeit it's empty.  I believe it's part of the specification that this folder should be included.  The DVD ripping software I use includes this directory, presumably because it's part of the specification.  I can easily delete this folder so it's not a problem if it's too much trouble to modify the script.

So, it is a folder in the same level as the video_ts folder? Or is it a sub-folder of video_ts?

> **utar said:**
> 
I've tried it on a couple and everything looks to be working.
Good to hear.

---

### Post by utar on 2009-04-15
> **menny said:**
> So, it is a folder in the same level as the video_ts folder? Or is it a sub-folder of video_ts?

It's on the same level as video_ts

---

### Post by menny on 2009-04-15
Please try the new version now.

---

### Post by utar on 2009-04-15
> **menny said:**
> Please try the new version now.

Yep, that has fixed the audio_ts issue.


Thanks.

---

### Post by menny on 2009-04-16
The latest version of the script can be downloaded from:
[http://tinyurl.com/fill-mythvideo]("http://tinyurl.com/fill-mythvideo")

---

### Post by utar on 2009-04-16
Has anything changed, or is this just a new download location?

---

### Post by menny on 2009-04-16
Nothing changed.
This URL will always point to the latest version, and it is short :)

---

### Post by jbman on 2009-04-16
i see the option toset tv show tv is back in the code. Cheers for that.

---

### Post by jbman on 2009-04-19
Is i possible to have a nfo file with an ignore option so it will ignore a whole folder?

---

### Post by crez79 on 2009-04-19
I just used the script to get data for 180 movies and about 275 episodes of different tv shows and it correctly got data and covers/screenshots for all but 6. The 6 were because I had the release year in the filename and it didn't like that. So basically it did everything perfectly!

I did notice a couple things. 
1. It properly follows directories but it won't follow directories that are soft linked. It parses them when I specifically tell it to do that directory, but it won't go into it by itself. It's not that big of a deal, if I had a more organized setup it wouldn't even happen. 
2. The covers it gets are the poor quality ones from imdb.com. I don't know if it would be possible to use the higher quality ones from imdb like [here]("http://www.oneweb.co.uk/mythtv/2009/02/updated-imdbpl-for-getting-hi-res-movie-posters/") or by using covers from themoviedb.org like [here]("http://www.mythtv.org/wiki/Tmdb.pl"). I have previously used the tmdb script for the covers, I didn't use the metadata from there because I didn't like the incomplete details. themoviedb.com has an api, I have no idea what to do with it, but I have read it makes it easier for people like you to do amazing things!

Thank you for your hard work!

---

### Post by menny on 2009-04-19
> **crez79 said:**
> I just used the script to get data for 180 movies and about 275 episodes of different tv shows and it correctly got data and covers/screenshots for all but 6. The 6 were because I had the release year in the filename and it didn't like that. So basically it did everything perfectly!

I did notice a couple things. 
1. It properly follows directories but it won't follow directories that are soft linked. It parses them when I specifically tell it to do that directory, but it won't go into it by itself. It's not that big of a deal, if I had a more organized setup it wouldn't even happen. 
2. The covers it gets are the poor quality ones from imdb.com. I don't know if it would be possible to use the higher quality ones from imdb like [here]("http://www.oneweb.co.uk/mythtv/2009/02/updated-imdbpl-for-getting-hi-res-movie-posters/") or by using covers from themoviedb.org like [here]("http://www.mythtv.org/wiki/Tmdb.pl"). I have previously used the tmdb script for the covers, I didn't use the metadata from there because I didn't like the incomplete details. themoviedb.com has an api, I have no idea what to do with it, but I have read it makes it easier for people like you to do amazing things!

Thank you for your hard work!

Thanks for testing :)
I'll work on you suggestions.

---

### Post by menny on 2009-04-19
I looked at themoviedb.org site, and it is quite nice, and it also supports API calls, just like thetvdb.

I think I'll try to use that source for movies.

Menny

---

### Post by RDV on 2009-04-19
FYI: If you are running MythTv trunk (v0.22), here are a couple of scripts that you may be interested in. The Jamu script accesses both thetvdb.com and themoviedb.com. It also allows you to add secondary source data and graphics scripts through a user configuration file.

ttvdb.py - wiki page: [http://www.mythtv.org/wiki/Ttvdb.py](http://www.mythtv.org/wiki/Ttvdb.py)

Jamu - wiki page: [http://www.mythtv.org/wiki/Jamu](http://www.mythtv.org/wiki/Jamu)

Just to be clear these script are submissions for the trunk 0.22 version of MythTV. They will not work with 0.21. The scripts are positioned for the future MythTV release and the data base changes that accompany that release.

---

### Post by menny on 2009-04-19
Wow. I read the Jamu wiki page is quite impressive!
I guess it puts a time-limit on my script :)

I was hoping that MythVideo itself will include the functionality of my script. Maybe next version.

Menny

---

### Post by utar on 2009-04-19
> **menny said:**
> Wow. I read the Jamu wiki page is quite impressive!
I guess it puts a time-limit on my script :)Menny

Well given that Myth 0.22 is unlikely to be out before Ubuntu 9.10 is released I personally will be using your script for quite a while yet :D


Utar

---

### Post by RDV on 2009-04-19
Thanks Menny. The other comment is correct that unless you already use trunk then wait for the official 0.22 release. 

Heck I do not even know if Jamu will be accepted into MythTV. While ttvdb.py will likely be accepted any day now.

Menny when I read your wiki page I wondered what the odds were that two new metadata utilities would be release within one week.

As Jamu overlaps the functionality of find_meta.py I named Jamu - Just.Another.Metadata.Utility. Neither of our scripts will be the last of their kind.

Cheers

---

### Post by utar on 2009-04-21
Hi Menny


Just noticed a minor bug.  When using an nfo to override a series the folder.jpg download ignores the override.

For example with a folder called "Jericho" and using an override of "<thetvdb seriesid="79330"/>" the folder.jpg is downloaded for Jericho (2005) instead of Jericho (2006).  The override however works fine for the video files (apart from the lower case issue.)



Utar

---

### Post by menny on 2009-04-22
> **utar said:**
> Hi Menny


Just noticed a minor bug.  When using an nfo to override a series the folder.jpg download ignores the override.

For example with a folder called "Jericho" and using an override of "<thetvdb seriesid="79330"/>" the folder.jpg is downloaded for Jericho (2005) instead of Jericho (2006).  The override however works fine for the video files (apart from the lower case issue.)



Utar
OK, I'll look into that. This is quite weird...
Uter, I've tried to reproduce the lowercase issue, and couldn't.
I understand that it happens to you in any series override you do, right?

---

### Post by joshoekstra on 2009-04-22
Another request if possible:
I like categorizing my series bij name: ie My name is Earl, is there a passibillity to add that? Now I manually search for the category ID and then change for every file with the name 'My.name.is.Earl%' via mysql.
If there would be an option to set category via a cmd-line option it would be great.

---

### Post by menny on 2009-04-22
> **joshoekstra said:**
> Another request if possible:
I like categorizing my series bij name: ie My name is Earl, is there a passibillity to add that? Now I manually search for the category ID and then change for every file with the name 'My.name.is.Earl%' via mysql.
If there would be an option to set category via a cmd-line option it would be great.

Can you send me the sql command for this, I'll see how to use it in the script.
Also, you can open issues/requests at [http://code.google.com/p/fill-mythvideo-metadata/issues]("http://code.google.com/p/fill-mythvideo-metadata/issues"). This way you'll be able to get notified about their status.

---

### Post by utar on 2009-04-22
> **menny said:**
> OK, I'll look into that. This is quite weird...
Uter, I've tried to reproduce the lowercase issue, and couldn't.
I understand that it happens to you in any series override you do, right?

Yes this happens every time I override a folder.  For example with The Simpsons, BSG and Jericho all of which I override.  Can you replicate the issue if you create a folder named "Jericho" use the override I posted earlier in a file called "override.nfo" with a file named "Jericho 101 - Home (Pilot).720p.h264.tvrip.mkv"?

I'm not in front of my machine at the moment and can't remember if the lowercase issue also exists when I just override a file (rather then the whole folder) but I will check. [Edit: everything is fine when I override individual files, the case issue only appears when I override a whole folder.]


Utar

---

### Post by oobe-feisty on 2009-04-22
i added the show final 24 to thetvdb manually [http://www.thetvdb.com/?tab=series&id=90351&lid=7](http://www.thetvdb.com/?tab=series&id=90351&lid=7)

i named my episodes like this 

Final.24.S01E01.Sid.Vicious.avi             Final.24.S01E03.River.Phoenix.HDTV.oobe.avi      Final.24.S01E05.Marvin.Gaye.HDTV.oobe.avi
Final.24.S01E02.John.Belushi.HDTV.oobe.avi  Final.24.S01E04.Hunter.S.Thompson.HDTV.oobe.avi  Final.24.S01E06.John.F.Kennedy-Jr.avi

/data/Documents/media/vids/TVeps/Final.24/Season 2:
Final.24.S02E04.Janis.Joplin.avi

/data/Documents/media/vids/TVeps/Final.24/Season 3:
Final.24.S03E01.Keith.Moon.HDTV.oobe.avi  Final.24.S03E02.Nicole.Brown-Simpson.HDTV.oobe.avi  Final.24.S03E03.David.Koresh.HDTV.oobe.avi  Final.24.S03E04.Tupac.Shakur.HDTV.oobe.avi



and not long after the xml files were available


[http://www.thetvdb.com/api/6770D263BF045B96/series/90351/default/3/2/en.xml](http://www.thetvdb.com/api/6770D263BF045B96/series/90351/default/3/2/en.xml)


but when i run the fill_mythvideo_metadata.pl script it fails to find the index i can only assume there is a step im missing to adding a show to the thetvdb.com

does anything know if im doing somthing wrong

---

### Post by utar on 2009-04-22
Can you run:

```
./fill_mythvideo_metadata.pl -N 0 -F /data/Documents/media/vids/TVeps/Final.24/Season 2
```

And post the output.  Note this will overwrite any metadata you may have for this folder.


Utar

---

### Post by oobe-feisty on 2009-04-22
the -F option did nothing so i changed it to -D 

oobe@box:~$ fill_mythvideo_metadata.pl -N 0 -D /data/Documents/media/vids/TVeps/Final.24/Season\ 2
looking at '-N'
Overriding new files scan. Will use '0'
looking at '-D'
Overriding DB folder. Will use '/data/Documents/media/vids/TVeps/Final.24/Season 2/'
NOTICE: You have selected to update ALL files! This will overwrite all previous data with new data.
Connecting to database...
MythVideos folder is: /data/Documents/media/vids
Will scan videos from folder: /data/Documents/media/vids/TVeps/Final.24/Season 2/
Artwork folder is: /home/oobe/.mythtv/MythVideo
Extensions: mpg|avi|wmv|mp4|flv|mov|m4v|iso|mkv
======================================================================
Video file 'Final.24.S02E04.Janis.Joplin.avi' has metadata in the database.
D=/data/Documents/media/vids/TVeps/Final.24/Season 2/, F=Final.24.S02E04.Janis.Joplin.avi
TV format 1: Show: 'Final.24.', S:'02', E:'04'
Found Show: (id: ), 'final 24', season '2', episode '4'. last ID:
Will look at '/data/Documents/media/vids/TVeps/Final.24/Season 2/'
Getting metadata for 'Final.24.S02E04.Janis.Joplin.avi'...
Missing series ID. Searching by series name 'final 24'...
Searching THE-TV-DB for series 'final 24'
About to call GET HTTP url: 'http://www.thetvdb.com/api/GetSeries.php?seriesname=final%2024'
Can not locate series 'final 24' in THE-TV-DB.
Trying to load information for 'final 24 s02e04 janis joplin' from IMDB...
About to call GET HTTP url: 'http://www.imdb.com/find?s=tt&q=final 24 s02e04 janis joplin'
Can not load IMDB data for 'final 24 s02e04 janis joplin'.
Exiting eval via next at /usr/local/bin/fill_mythvideo_metadata.pl line 1820.
======================================================================
Finished going over all the files: Found 1, updated 0 files.
Going over all video files in the database, and deleting any redundant entries (i.e., video files no longer exist)...
Deleted 0 entries from database!
======================================================================
Going over all image files in the artwork folder (at '/home/oobe/.mythtv/MythVideo'), and deleting any redundant image files (i.e., owner video file does not exist)...

---

### Post by utar on 2009-04-22
You were right with "D", my mistake.

Basically the auto search isn't working.  You can override this by creating a text file with an .nfo extention in the Final 24 folder (you may need this in each season folder, not sure offhand.)

Details of over rides are at the start of the script, and to quote the relevant part:

> To override the series: any .nfo file within the video file folder which contain '<thetvdb seriesid="[ID from thetvdb.com]"/>'

So in the case of Final 24 add the following to the .nfo file:

> <thetvdb seriesid="90351"/>

Then run the same command line again.

[Edit: although not sure why the auto search isn't working.  If you paste the search string of [http://www.thetvdb.com/api/GetSeries.php?seriesname=final%2024](http://www.thetvdb.com/api/GetSeries.php?seriesname=final%2024) into a browser it does work.  Anyway hopefully the above will work]

Utar

---

### Post by joshoekstra on 2009-04-23
> **menny said:**
> Can you send me the sql command for this, I'll see how to use it in the script.
Also, you can open issues/requests at [http://code.google.com/p/fill-mythvideo-metadata/issues]("http://code.google.com/p/fill-mythvideo-metadata/issues"). This way you'll be able to get notified about their status.

Ok, I opened an issue(cannot choose enhancement?) on the googlecode page with an example of commands. I hope it's clear enough to be helpfull :)

---

### Post by utar on 2009-04-23
I have just looked at the Google issues page for the script for the first time and like it.

Will make sure I raise any issues on that page in future.


Utar

---

### Post by menny on 2009-04-24
Hi all.
I've fixed some issues with the script including the show name capitals issue.

Uter, can you try, and see if it fixes your problem?

---

### Post by menny on 2009-04-24
oobe-feisty, I've fixed the Final.24 issue.
Can you check it?

---

### Post by utar on 2009-04-24
> **menny said:**
> Hi all.
I've fixed some issues with the script including the show name capitals issue.

Uter, can you try, and see if it fixes your problem?

Fixed!  Many thanks.  I also like the new random screenshot time feature, this really helps makes the thumbnails on many of my shows look more interesting, rather then all being of the credits.



Utar

---

### Post by menny on 2009-04-25
Uter,
I was unable to reproduce the folder.jpg issue you raised.
You said that you have a folder with Jerich, and you added a nfo file with the correct seriesid, and as I understand, it downloads the correct metadata for the files, but the folder art is of Jericho (2005).
Can you try again? With the "-N 0" argument, and, please, delete the folder.jpg file which already there (the bad one).

Thanks.

---

### Post by utar on 2009-04-25
> **menny said:**
> Uter,
I was unable to reproduce the folder.jpg issue you raised.
You said that you have a folder with Jerich, and you added a nfo file with the correct seriesid, and as I understand, it downloads the correct metadata for the files, but the folder art is of Jericho (2005).
Can you try again? With the "-N 0" argument, and, please, delete the folder.jpg file which already there (the bad one).

Thanks.

Strange.  Everything is working fine now.  I wonder with the benefit of hindsight if Myth was still caching the old folder.jpg as I have noticed when thumbnails change Myth does not detect this instantly and still uses the old ones for a while.  Anyway it's working which is the important thing.

While I am posting I have noticed a bug which I believe arises when there is a "-" in a movie file name which the script looks up on imdb:

```
50 First Dates - tvrip.mpg
DBD::mysql::st execute failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ' inetref="1297817"
where filename="/var/lib/mythtv/videos/1 - Unwatched/50 First' at line 4 at ./fill_mythvideo_metadata.pl line 1873.
```




Utar

---

### Post by utar on 2009-04-25
Just remembered a minor bug I noticed the other day.  Basically when a TV episode has "&" in the title the script misses this from the file name.

For example "Terminator, The Sarah Connor Chronicles 201 - Samson & Delilah.720p.h264.tvrip" the script correctly finds this on thetvdb where the episode name is "Samson & Delilah" but enters "Samson  Delilah" into the database.  Not a big deal, but thought I would mention it.

I have added this to the googlecode page.


Utar

---

### Post by oobe-feisty on 2009-04-25
> **menny said:**
> oobe-feisty, I've fixed the Final.24 issue.
Can you check it?


thanks it works sorry for the late reply i have been busy and only just looked back at this thread

also feature suggestion would it be possible to add an option to just make screen shots and not get data for a certain directory

---

### Post by menny on 2009-04-26
There is an option to do it for a certian file. Look at [http://www.mythtv.org/wiki/Fill_mythvideo_metadata.pl#NFO_Files]("http://www.mythtv.org/wiki/Fill_mythvideo_metadata.pl#NFO_Files").
> <simple_update/>

You want to extend this feature to allow override the entire folder?

---

### Post by paulyche on 2009-04-26
Hi,

I have attached a new version of the script (based on Menny's latest version) which implements a new feature. 

You can now select to download Movie posters from an external script (the command line must be defined in the header of script). The main use I can imagine for this is that you can now use any standard mythvideo scripts to download the posters.

For example, I have have copied the tmdb.pl script from trunk into my 0.21-fixes installation and now I can put the command line for tmdb.pl into the fill_mythvideo_metadata.pl script and get high definition posters from tmdb simply by changing a variable in the fill_mythvideo_metadata script to point to the location of tmdb.pl. TMDB (and the tmdb.pl script) allow queries with the imdb id.

tmdb.pl can be ported from trunk to 0.21 using the instructions here:
[http://www.mythtv.org/wiki/Tmdb.pl]("http://www.mythtv.org/wiki/Tmdb.pl")

---

### Post by oobe-feisty on 2009-04-26
excellent work i hope menny adds this to his script

> **paulyche said:**
> Hi,

I have attached a new version of the script (based on Menny's latest version) which implements a new feature. 

You can now select to download Movie posters from an external script (the command line must be defined in the header of script). The main use I can imagine for this is that you can now use any standard mythvideo scripts to download the posters.

For example, I have have copied the tmdb.pl script from trunk into my 0.21-fixes installation and now I can put the command line for tmdb.pl into the fill_mythvideo_metadata.pl script and get high definition posters from tmdb simply by changing a variable in the fill_mythvideo_metadata script to point to the location of tmdb.pl. TMDB (and the tmdb.pl script) allow queries with the imdb id.

tmdb.pl can be ported from trunk to 0.21 using the instructions here:
[http://www.mythtv.org/wiki/Tmdb.pl]("http://www.mythtv.org/wiki/Tmdb.pl")

---

### Post by crez79 on 2009-04-27
> **paulyche said:**
> Hi,

I have attached a new version of the script (based on Menny's latest version) which implements a new feature. 

You can now select to download Movie posters from an external script (the command line must be defined in the header of script). The main use I can imagine for this is that you can now use any standard mythvideo scripts to download the posters.

For example, I have have copied the tmdb.pl script from trunk into my 0.21-fixes installation and now I can put the command line for tmdb.pl into the fill_mythvideo_metadata.pl script and get high definition posters from tmdb simply by changing a variable in the fill_mythvideo_metadata script to point to the location of tmdb.pl. TMDB (and the tmdb.pl script) allow queries with the imdb id.

tmdb.pl can be ported from trunk to 0.21 using the instructions here:
[http://www.mythtv.org/wiki/Tmdb.pl]("http://www.mythtv.org/wiki/Tmdb.pl")

This is great. It works well if there is a cover, but if there isn't one found, it makes a file with a size of 0 and mythweb doesn't like it. Thanks for doing what I wanted but am not smart enough to do.

---

### Post by menny on 2009-04-27
Thanks paulyche
I've merged your changes. Can you check the new version at [http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl]("http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl").

---

### Post by paulyche on 2009-04-27
Looks good from here. (At work at the mo so can't check it actually runs properly until tonight).

Will probably have to make further changes to fix crez79's issue. Although the easy way to solve the issue is to upload a poster to TMDB (civic duty and all!) :-)

---

### Post by utar on 2009-04-27
> **paulyche said:**
> Hi,

I have attached a new version of the script (based on Menny's latest version) which implements a new feature. 

You can now select to download Movie posters from an external script (the command line must be defined in the header of script). The main use I can imagine for this is that you can now use any standard mythvideo scripts to download the posters.

For example, I have have copied the tmdb.pl script from trunk into my 0.21-fixes installation and now I can put the command line for tmdb.pl into the fill_mythvideo_metadata.pl script and get high definition posters from tmdb simply by changing a variable in the fill_mythvideo_metadata script to point to the location of tmdb.pl. TMDB (and the tmdb.pl script) allow queries with the imdb id.

tmdb.pl can be ported from trunk to 0.21 using the instructions here:
[http://www.mythtv.org/wiki/Tmdb.pl]("http://www.mythtv.org/wiki/Tmdb.pl")

I want to try this out but I'm unsure from the tmdb.pl install instructions if this will overwrite any of the Myth default scripts/settings which I would rather not do (well not unless I know how to reverse the process.)  Can anyone give me a few pointers?

Menny - thanks for fixing the "&" issue.


Utar

---

### Post by paulyche on 2009-04-28
> I want to try this out but I'm unsure from the tmdb.pl install instructions if this will overwrite any of the Myth default scripts/settings which I would rather not do (well not unless I know how to reverse the process.) Can anyone give me a few pointers?

If you follow the whole procedure on the wiki it may ovewrite settings (I haven't actually tried it). However the simplest thing to do is to simply download the relevant files

```
wget http://svn.mythtv.org/svn/trunk/mythplugins/mythvideo/mythvideo/scripts/tmdb.pl
```

```
wget http://svn.mythtv.org/svn/trunk/mythplugins/mythvideo/mythvideo/scripts/MythTV/MythVideoCommon.pm
```

and put the files in the relevant directories i.e. '/usr/share/mythtv/mythvideo/scripts/' for tmdb.pl and '/usr/share/mythtv/mythvideo/scripts/MythTV/' for MythVideoCommon.pm

---

### Post by menny on 2009-04-28
I like this TheMovieDb.org site - I want to use it instead of imdb.com in the script.
did anyone work with it?

---

### Post by paulyche on 2009-04-28
TMDB is getting better, and it has an API which is good. But I've found that though the graphics are good, the text (plot synopses etc..) is SOMETIMES substandard compared to IMDB - Badly spelled, bad grammar. I especially dislike the way some of the text is way too long and actually gives away the plot a bit too much..

I haven't tried it properly for a while though.

---

### Post by Lorenzo1985 on 2009-04-28
> **paulyche said:**
> TMDB is getting better, and it has an API which is good. But I've found that though the graphics are good, the text (plot synopses etc..) is SOMETIMES substandard compared to IMDB - Badly spelled, bad grammar. I especially dislike the way some of the text is way too long and actually gives away the plot a bit too much..

I haven't tried it properly for a while though.

I agree with Paul, while the principal is great The texts are occasionally inacurate. Also movies occasional take a while to get on to TMDB

---

### Post by utar on 2009-04-28
> **Lorenzo1985 said:**
> I agree with Paul, while the principal is great The texts are occasionally inacurate. Also movies occasional take a while to get on to TMDB

What about taking the graphics from tmdb and the narrative from imdb so we can have the best of both worlds. Or having an option in the script to select so each user can form their own view of what they think is best?

As someone said in an earlier post the optimal solution would be to correct tmdb if the narrative is inaccurate.


Utar

---

### Post by utar on 2009-04-28
> **paulyche said:**
> If you follow the whole procedure on the wiki it may ovewrite settings (I haven't actually tried it). However the simplest thing to do is to simply download the relevant files

```
wget http://svn.mythtv.org/svn/trunk/mythplugins/mythvideo/mythvideo/scripts/tmdb.pl
```

```
wget http://svn.mythtv.org/svn/trunk/mythplugins/mythvideo/mythvideo/scripts/MythTV/MythVideoCommon.pm
```

and put the files in the relevant directories i.e. '/usr/share/mythtv/mythvideo/scripts/' for tmdb.pl and '/usr/share/mythtv/mythvideo/scripts/MythTV/' for MythVideoCommon.pm

Thanks that worked great.

The movie posters now look **much** better.


Utar

---

### Post by menny on 2009-04-29
I see your point about the tmdb. Too bad.
Anyhow, slate8 said that he knows how to get hi-res posters from imdb, so the hi-res thing can be handled by this script.
Slate8, any progress about that?

---

### Post by menny on 2009-04-29
I think I found a quick way to download hi-res posters.
There is a nice site called posters.motechnet.com which hold pretty good quality posters (600px).
So I've fixed the script:
If the user wishes to download posters from imdb, the script will first try to download from posters.motechnet.com, and if failed, it will download from imdb.

I've tried it, and it produce pretty decent posters. Can anyone try too?

Thanks.

---

### Post by utar on 2009-04-29
> **menny said:**
> I think I found a quick way to download hi-res posters.
There is a nice site called posters.motechnet.com which hold pretty good quality posters (600px).
So I've fixed the script:
If the user wishes to download posters from imdb, the script will first try to download from posters.motechnet.com, and if failed, it will download from imdb.

I've tried it, and it produce pretty decent posters. Can anyone try too?

Thanks.

Is this in beta6?

I can see no reference to motechnet in the script so I'm guessing not?


Utar

---

### Post by menny on 2009-04-29
Uter, you are correct, I haven't uploaded the new version :)
Now it is up there (beta7)

---

### Post by utar on 2009-04-29
> **menny said:**
> Uter, you are correct, I haven't uploaded the new version :)
Now it is up there (beta7)

Well I will forgive you this time.  Just don't do it again ;-)

I've run the script on two movies where I had low res covers, everything worked and I now have high res posters.


Utar

---

### Post by menny on 2009-05-03
Hi guys,
I've added a new requested feature:
You can now specify to skip an entire folder, the same way to skip a specific file:

#version 1.0.1
#*Entire folder skip markers - same overriding mechanism for file, has been extended to folder:
#If you wish to override an entire folder, create a file with a name in this format: folder.[folder-name].nfo
#E.g., for folder "MyMovies", create inside this folder a file named "folder.MyMovies.nfo".
#the override options are as file:
#       * To skip a folder completely (just ignore, whatever in the database, if any, is OK): The file should contain '<no_update/>'
#       * To skip a folder parsing, and just add the file with a snapshot to the database (usefull for private videos): The file should contain '<simple_update/>'


Please test and tell me what you think,
Menny.

---

### Post by crez79 on 2009-05-03
Everything works great! I like the external script, it makes it very versatile. 

Using the folder no update works to prevent adding new metadata to the database, but it still deletes metadata from the data base if that files doesn't exist anymore. Is this the desired effect?

Again, thanks for the great script!

---

### Post by menny on 2009-05-03
thanks for testing :)

and, yes, deleting unrequired meta-data (it is, right?) is the correct behavior.

---

### Post by crez79 on 2009-05-03
It works for me. I just expected it to leave it alone entirely, but it is probably better to get outdated metadata out of the database.

---

### Post by jbman on 2009-05-03
Thanks heaps for adding that feature. I was having a few problems with some folders, since adding this those folders are now ignored and working very very well.

---

### Post by utar on 2009-05-04
> **menny said:**
> Please test and tell me what you think,
Menny.

The update is working fine on my system as well.



Utar

---

### Post by oobe-feisty on 2009-05-04
thanks for the latest update menny im very happy with this feature i have a lot of things that dont need to lookup metadata

---

### Post by xioustic on 2009-05-15
This script is some sort of godsend. Especially for me, as I've got something around 2-3TB of ripped movies from my collection and TV shows (both recorded and downloaded from friends).

However, I'm obsessive compulsive about how I label my files. I would like to adopt a naming convention for both my movies (which is currently The.Name.Of.The.Movie[year].ext) and my TV shows (which currently are a large mix of conventions from the internet and whatever mythtv defaults to after I set it to transcoding).

For this script to work best at retrieving metadata, what convention should I adopt?

I saw this from the wiki:

[quote="http://www.mythtv.org/wiki/Fill_mythvideo_metadata.pl"]-TV_TITLE_TYPE [0/1/2]
  0-[File name]
  1(default)-[Episode number]: [Episode name]
  2-[Show] S[Season number]E[Episode number] [Episode name]
  3-[Show] [Season number]x[Episode number] [Episode name]

-MOVIE_TITLE_TYPE [0/1/2]
  0-[File name]
  1(default)-[Movie name from IMDB][/quote]

This is somewhat ambiguous how I should name the movie files. Also, the default for TV_TITLE_TYPE seems a bit bare on season/episode details.

So I'm asking for an opinion from you guys so I (or we) can derive a convention. :D

(Hopefully I haven't missed this previously in this post, I haven't quite combed through all 20 pages of it...)

Also, a few suggestions for the script (both relatively simple modifications):

[LIST]
[*]The ability to tag a folder (and it's sub-folders) as movies or tv shows only
[*]The ability to autodetect multiple folders (as it stands, it doesn't recognize the : delimiter that mythtv uses, as such I have to manually use -D for each of my three folders)
[*]Detection of year in filename when looking at a movie file for IMDB query. I have a lot of movies with the same title, different year... So this makes it somewhat of a pain to comb back through.
[/LIST]

---

### Post by Lorenzo1985 on 2009-05-15
> **xioustic said:**
> 
So I'm asking for an opinion from you guys so I (or we) can derive a convention. :D


I tend to use <showname>.S<Season number>E<episode number>.<episode title>.<ext>

eg: Dollhouse.S01E01.Ghost.avi

This seems to work quite well. Particularly with some clever folders. There's plenty scripts out there that will rename all your files.

Eg:
[http://robmeerman.co.uk/coding/file_renamer](http://robmeerman.co.uk/coding/file_renamer)
[http://wiki.github.com/dbr/tvdb_api/tvnamer](http://wiki.github.com/dbr/tvdb_api/tvnamer)

---

### Post by xioustic on 2009-05-15
In followup to my previous post, from my (very short) experience with Boxee I found this and considered adopting these:

[quote="agentlame @ http://forum.boxee.tv/showthread.php?t=5214"]**[SIZE=4]naming tv shows[/SIZE]**

...

*Show.Title.S##E##.info.extension* (double digits are required: S#E# will not work.)
Examples

[LIST]
[*]The.Sopranos.S02E01.avi
[*]Entourage.S05E01.avi
[/LIST]



*Show.Title.#x##.info.extension*
Examples

[LIST]
[*]How.I.Met.Your.Mother.1x01.Pilot.avi
[*]The.Office.02×02.stuff.avi
[/LIST]



*Show.Name.###.info.extension*
Examples

[LIST]
[*]30.rock.101.avi
[*]Battlestar.Galactica.501.avi
[/LIST]


------------------------------------------------------------------------------------------------------------------
**[SIZE=4]naming movies[/SIZE]**

boxee currently supports one naming convention for movies:
*Title.extension*

optionally, you can add additional parameters for grater accuracy:
*Title.(Year).part.extension *


*Title.extension* the simplist, and is recommended for most movies.
Examples

[LIST]
[*]Die.Hard.avi
[*]Toy.Story.2.avi
[/LIST]


*Title.(YEAR).extension* is helpful in the case of reamakes.
Examples

[LIST]
[*]The.Day.the.Earth.Stood.Still.(1951).avi
[*]The.Day.the.Earth.Stood.Still.(2008).avi
[/LIST]



*Title.part.extension* for multi-part movie both part# and cd# are supported
Examples

[LIST]
[*]Seven.Pounds.cd1.avi
[*]Seven.Pounds.cd2.avi
[*]The.Simpsons.Movie.part1.avi
[*]The.Simpsons.Movie.part2.avi
[/LIST]



*Title.(Year).part.extension* all parameters can be used in conjunction
Examples

[LIST]
[*]The.Stepford.Wives.(2004).part1.avi
[*]The.Stepford.Wives.(2004).part2.avi
[*]The.Stepford.Wives.(1975).cd1.avi
[*]The.Stepford.Wives.(1975).cd2.avi
[/LIST]
[/quote]This all seems to imply the best (most informative conventions) is:

**Movies: **Title.(YEAR).ext
**TV Shows:** Show.Title.S##E##.Episode.Name.ext

Of course, this is all still opinion.

---

### Post by utar on 2009-05-16
Hi


For clarity, do you realise that the script renames the file (in the database, rather then the file name) so it doesn't matter what naming convention you use for the file names?



Utar

---

### Post by xioustic on 2009-05-16
> **utar said:**
> Hi


For clarity, do you realise that the script renames the file (in the database, rather then the file name) so it doesn't matter what naming convention you use for the file names?



Utar
I'm starting with a completely empty database and a completely full collection, so I assume the only thing the autodetection has to go by is the filename...?

---

### Post by utar on 2009-05-16
> **xioustic said:**
> I'm starting with a completely empty database and a completely full collection, so I assume the only thing the autodetection has to go by is the filename...?

Yes.  The only thing you actually need in the name is the show title and the episode number, e.g. "My Name is Earl s01e01.avi" anything else doesn't matter.  

If you have an empty database you have nothing to lose so I would just run the script.


Utar

---

### Post by xioustic on 2009-05-16
The script doesn't support multiple folders?

[quote="fill_mythvideo_metadata.pl"]...
MythVideos folder is: /var/lib/mythtv/videos:/media/MythMedia/Movies:/media/MythMedia/Movies 2:/media/MythMedia/TV Shows
Will scan videos from folder: /var/lib/mythtv/videos:/media/MythMedia/Movies:/media/MythMedia/Movies 2:/media/MythMedia/TV Shows
Artwork folder is: /var/lib/mythtv/posters
Extensions: mpg|avi|vob|mpeg|VIDEO_TS|iso|img
find: `/var/lib/mythtv/videos:/media/MythMedia/Movies:/media/MythMedia/Movies 2:/media/MythMedia/TV Shows': No such file or directory
...[/quote]

---

### Post by utar on 2009-05-16
> **xioustic said:**
> The script doesn't support multiple folders?

Seems like you have discovered a bug.  I only use one folder myself, you could post a bug report at:

[http://code.google.com/p/fill-mythvideo-metadata/issues/list](http://code.google.com/p/fill-mythvideo-metadata/issues/list)

As a work around you could manually specify the directory on the command line, for example:

./fill_mythvideo_metadata.pl -D /var/lib/mythtv/videos



Utar

---

### Post by Slate8 on 2009-05-19
> **menny said:**
> I see your point about the tmdb. Too bad.
Anyhow, slate8 said that he knows how to get hi-res posters from imdb, so the hi-res thing can be handled by this script.
Slate8, any progress about that?

So sorry I've been off the radar for a while. I'm organising my wedding and have had a few weeks with too much to do.

I haven't tried the script for a while but see that you have high-res posters coming in. Congrats!

Sorry again I haven't been able to put in the time I'd anticipated.

---

### Post by jbman on 2009-05-21
on the latest version dated may 17th i am getting 

The cover of the video file is invalid! I'll try to regenerate it... at every show

---

### Post by utar on 2009-05-23
> **jbman said:**
> on the latest version dated may 17th i am getting 

The cover of the video file is invalid! I'll try to regenerate it... at every show

I'm not seeing this error myself.  Can you post the script output.


[Edit: just seen the message once when the script downloaded a cover for one of my movies.  For some reason the old version of the script couldn't find this movie on imdb and so didn't download any metadate.  The new version however found it fine.  Running the script with no new files does not show the message though.  Are you seeing this message every time you run the script?]


Utar

---

### Post by jbman on 2009-05-24
i will run it again and check, i saw it twice and it took a while like it was the first run again. it seemed to do a better job and found more info for shows.

---

### Post by jbman on 2009-05-26
Ran it again same thing. But I am also noticing it seems to be deleting all the covers it downloads at the end.

---

### Post by utar on 2009-05-26
> **jbman said:**
> Ran it again same thing. But I am also noticing it seems to be deleting all the covers it downloads at the end.

Strange.

Can you run the script on just one file where you are having problems (use "-F filename" on the command line) and post the script output.


Utar

---

### Post by jbman on 2009-05-27
Here it is - this seems to be happening with every file.

```

jbman@mythtv:~$ ./fill_mythvideo_metadata.pl -F /myth/media/video/TV/U.V.W.X.Y.Z/Weeds/Season\ 1/Weeds.S01E10.HDTV.XviD-LOKi.avi 
looking at '-F'
One file mode. Target file is '/myth/media/video/TV/U.V.W.X.Y.Z/Weeds/Season 1/Weeds.S01E10.HDTV.XviD-LOKi.avi'.
Using password from mysql.txt
Connecting to database...
MythVideos folder is: /myth/media/video
Will scan videos from folder: /myth/media/video
Artwork folder is: /home/jbman/.mythtv/mythvideo
Extensions: mpg|avi|vob|mpeg|VIDEO_TS|iso|img|mkv
======================================================================
File 0 out of 1...
Video file 'Weeds.S01E10.HDTV.XviD-LOKi.avi' has metadata in the database.
The cover of the video file is invalid! I'll try to regenerate it...
D=/myth/media/video/TV/U.V.W.X.Y.Z/Weeds/Season 1/, F=Weeds.S01E10.HDTV.XviD-LOKi.avi
TV format 1: Show: 'Weeds.', S:'01', E:'10'
Found Show: (id: ), 'weeds', season '1', episode '10'. last ID: 
Will look at '/myth/media/video/TV/U.V.W.X.Y.Z/Weeds/Season 1/'
Getting metadata for 'Weeds.S01E10.HDTV.XviD-LOKi.avi'...
Missing series ID. Searching by series name 'weeds'...
Searching THE-TV-DB for series 'weeds'
About to call GET HTTP url: 'http://www.thetvdb.com/api/GetSeries.php?seriesname=weeds'
Found a possible match for 'weeds' as 'Weeds' (ID 74845)
Found ID '74845' for series 'weeds' at THE-TV-DB.
Downloading folder art for series from 'http://www.thetvdb.com/banners/graphical/74845-g5.jpg' to '/myth/media/video/TV/U.V.W.X.Y.Z/Weeds/Season 1/'...
Checking folder art at directory '/myth/media/video/TV/U.V.W.X.Y.Z/Weeds/Season 1/'
Checking folder art at directory '/myth/media/video/TV/U.V.W.X.Y.Z/Weeds/'
Checking folder art at directory '/myth/media/video/TV/U.V.W.X.Y.Z/'
Checking folder art at directory '/myth/media/video/TV/'
Getting episode information...
About to call GET HTTP url: 'http://www.thetvdb.com/api/6770D263BF045B96/series/74845/default/1/10/en.xml'
Found meta-data: series id: 74845, show: 'weeds', season: 1, episode: 10.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Cannot find codec matching selected -vo and video format 0x44495658.
downloading poster from 'http://www.thetvdb.com/banners/episodes/74845/296500.jpg'...
Downloading http://www.thetvdb.com/banners/episodes/74845/296500.jpg to /home/jbman/.mythtv/mythvideo/weeds-10-1.jpg
--13:48:58--  http://www.thetvdb.com/banners/episodes/74845/296500.jpg
           => `/home/jbman/.mythtv/mythvideo/weeds-10-1.jpg'
Resolving www.thetvdb.com... 208.76.155.58
Connecting to www.thetvdb.com|208.76.155.58|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 42 [image/gif]

100%[====================================>] 42            --.--K/s             

13:48:58 (3.03 MB/s) - `/home/jbman/.mythtv/mythvideo/weeds-10-1.jpg' saved [42/42]

The cover is invalid! Using the folder art instead.
found 'Weeds S01E10 The Godmother': Isabelle experiments, Andy gets drafted, Peter may not be who Nancy thinks he is, Silas gets high, and Nancy cuts out the middleman.
Weeds.S01E10.HDTV.XviD-LOKi.avi
'Weeds S01E10 The Godmother' is set!
======================================================================
Finished going over all the files: Found 1, updated 1 files.
Going over all video files in the database, and deleting any redundant entries (i.e., video files no longer exist)...
Deleted 0 entries from database!
======================================================================
Going over all image files in the artwork folder (at '/home/jbman/.mythtv/mythvideo'), and deleting any redundant image files (i.e., owner video file does not exist)...
Image '/home/jbman/.mythtv/mythvideo/weeds-10-1.jpg' does not exist in the DB metadata. deleting the file...
Deleted 1 redundant image files from the artwork folder.
======================================================================
Completing database...
======================================================================
Thanks for using MythVideo Metadata Updater v1.0.2.beta.
======================================================================
jbman@mythtv:~$ 

```

---

### Post by utar on 2009-05-27
Sorry not sure what is going wrong.

If you post a bug report at [http://code.google.com/p/fill-mythvideo-metadata/issues/list](http://code.google.com/p/fill-mythvideo-metadata/issues/list) I'm sure Menny will look into the problem.


Utar

---

### Post by jbman on 2009-05-27
done. lets see what can be done to find whats happening.

---

### Post by norjms on 2009-05-30
Here is where I'm at:

Fresh Install of Mythbuntu 9.0.4
Updated system via Update Manager

Opened a terminal
Installed subversion
grabbed the files via
svn checkout [http://fill-mythvideo-metadata.googlecode.com/svn/trunk/](http://fill-mythvideo-metadata.googlecode.com/svn/trunk/) fill-mythvideo-metadata-read-only


mounted cifs tv show share in fstab to /temp
verified proper permissions
Setup Videos directory in mythtv
mythtv sees the files

opened terminal
ran
sudo perl -MCPAN -e 'install WWW::TV'

and I get a fail to install

```
norjms@ryan-nix-main:~$ sudo perl -MCPAN -e 'install WWW::TV'
CPAN: Storable loaded ok (v2.18)
Going to read /home/norjms/.cpan/Metadata
  Database was generated on Sat, 30 May 2009 06:26:56 GMT
Running install for module 'WWW::TV'
CPAN: Data::Dumper loaded ok (v2.121_14)
'YAML' not installed, falling back to Data::Dumper and Storable to read prefs '/home/norjms/.cpan/prefs'
Running make for T/TI/TIGRIS/WWW-TV-0.14.tar.gz
CPAN: Digest::SHA loaded ok (v5.45)
CPAN: Compress::Zlib loaded ok (v2.015)
Checksum for /home/norjms/.cpan/sources/authors/id/T/TI/TIGRIS/WWW-TV-0.14.tar.gz ok
WWW-TV-0.14/
WWW-TV-0.14/t/
WWW-TV-0.14/t/99_pod_coverage.t
WWW-TV-0.14/t/98_pod.t
WWW-TV-0.14/t/10_episode.t
WWW-TV-0.14/t/20_series.t
WWW-TV-0.14/LICENSE
WWW-TV-0.14/MANIFEST
WWW-TV-0.14/TODO
WWW-TV-0.14/lib/
WWW-TV-0.14/lib/WWW/
WWW-TV-0.14/lib/WWW/TV/
WWW-TV-0.14/lib/WWW/TV/Episode.pm
WWW-TV-0.14/lib/WWW/TV/Series.pm
WWW-TV-0.14/lib/WWW/TV.pm
WWW-TV-0.14/META.yml
WWW-TV-0.14/MANIFEST.SKIP
WWW-TV-0.14/Makefile.PL
WWW-TV-0.14/Changes
WWW-TV-0.14/README
CPAN: File::Temp loaded ok (v0.18)
Warning (usually harmless): 'YAML' not installed, will not store persistent state

  CPAN.pm: Going to build T/TI/TIGRIS/WWW-TV-0.14.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for WWW::TV
Could not read '/home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/META.yml'. Falling back to other methods to determine prerequisites
cp lib/WWW/TV.pm blib/lib/WWW/TV.pm
cp lib/WWW/TV/Episode.pm blib/lib/WWW/TV/Episode.pm
cp lib/WWW/TV/Series.pm blib/lib/WWW/TV/Series.pm
Manifying blib/man3/WWW::TV.3pm
Manifying blib/man3/WWW::TV::Episode.3pm
Manifying blib/man3/WWW::TV::Series.3pm
  TIGRIS/WWW-TV-0.14.tar.gz
  /usr/bin/make -- OK
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/10_episode.........Ignoring unknown site value: [bogus]
t/10_episode.........ok 1/41Use of uninitialized value in substitution (s///) at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Episode.pm line 133.
Use of uninitialized value in substitution (s///) at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Episode.pm line 134.
Use of uninitialized value in substitution (s///) at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Episode.pm line 135.
Use of uninitialized value in substitution (s///) at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Episode.pm line 135.

#   Failed test 'summary includes: Fox River'
#   at t/10_episode.t line 49.
t/10_episode.........ok 14/41                                                
#   Failed test 'title is: Pilot'
#   at t/10_episode.t line 51.
t/10_episode.........NOK 15/41#          got: undef                          
#     expected: 'Pilot'

#   Failed test 'season number is 1'
#   at t/10_episode.t line 52.
t/10_episode.........NOK 16/41#          got: undef                          
#     expected: '1'

#   Failed test 'episode_number is 1'
#   at t/10_episode.t line 53.
t/10_episode.........NOK 17/41#          got: undef                          
#     expected: '1'
Use of uninitialized value in pattern match (m//) at t/10_episode.t line 54.

#   Failed test 'stars include: Wentworth Miller'
#   at t/10_episode.t line 54.
t/10_episode.........NOK 18/41Use of uninitialized value in pattern match (m//) at t/10_episode.t line 55.

#   Failed test 'guest_stars include: Jeff Parker'
#   at t/10_episode.t line 55.
t/10_episode.........NOK 19/41Use of uninitialized value in pattern match (m//) at t/10_episode.t line 56.

#   Failed test 'recurring_roles include: Stacy Keach'
#   at t/10_episode.t line 56.
t/10_episode.........NOK 20/41                                               
#   Failed test 'directors is: Brett Ratner'
#   at t/10_episode.t line 57.
t/10_episode.........NOK 21/41#          got: undef                          
#     expected: 'Brett Ratner'

#   Failed test 'writers is: Paul T. Scheuring'
#   at t/10_episode.t line 58.
t/10_episode.........NOK 22/41#          got: undef                          
#     expected: 'Paul T. Scheuring'

#   Failed test 'first_aired is: 2005-08-29'
#   at t/10_episode.t line 59.
t/10_episode.........NOK 23/41#          got: 'n/a'                          
#     expected: '2005-08-29'
Use of uninitialized value in substitution iterator at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Episode.pm line 214.

#   Failed test 'format_details: %I - series ID'
#   at t/10_episode.t line 62.
t/10_episode.........NOK 24/41#          got: ''                             
#     expected: '31635'
Can't find series_id for this episode at t/10_episode.t line 67
# Looks like you planned 41 tests but only ran 24.
# Looks like you failed 11 tests of 24 run.
# Looks like your test died just after 24.
t/10_episode.........dubious                                                 
	Test returned status 255 (wstat 65280, 0xff00)
DIED. FAILED tests 13, 15-41
	Failed 28/41 tests, 31.71% okay
t/20_series..........ok 1/33                                                 
#   Failed test 'series name is: M*A*S*H'
#   at t/20_series.t line 14.
#          got: undef
#     expected: 'M*A*S*H'
t/20_series..........NOK 3/33Use of uninitialized value $genres_row in split at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Series.pm line 158.
t/20_series..........ok 4/33                                                 
#   Failed test 'genres (scalar context) are: Comedy, Drama'
#   at t/20_series.t line 20.
t/20_series..........NOK 5/33#          got: ''                              
#     expected: 'Comedy, Drama'
Use of uninitialized value $episode_line in split at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Series.pm line 275.

#   Failed test 'total episode count'
#   at t/20_series.t line 27.
#          got: '0'
#     expected: '251'
t/20_series..........NOK 6/33                                                
#   Failed test 'total episode count (using season 0)'
#   at t/20_series.t line 30.
t/20_series..........NOK 7/33#          got: '0'                             
#     expected: '251'
Use of uninitialized value $episode_line in split at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Series.pm line 275.

#   Failed test 'season 1 episode count'
#   at t/20_series.t line 33.
#          got: '0'
#     expected: '24'
t/20_series..........NOK 8/33Use of uninitialized value $episode_line in split at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Series.pm line 275.

#   Failed test 'season 9 episode count'
#   at t/20_series.t line 36.
t/20_series..........NOK 9/33#          got: '0'                             
#     expected: '20'

#   Failed test 'genres (array context)'
#   at t/20_series.t line 39.
t/20_series..........NOK 10/33#          got: '0'                            
#     expected: '2'
t/20_series..........ok 11/33Use of uninitialized value in substitution (s///) at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Series.pm line 125.
Use of uninitialized value in substitution (s///) at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Series.pm line 126.
Use of uninitialized value in substitution (s///) at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Series.pm line 127.
Use of uninitialized value in substitution (s///) at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Series.pm line 127.
t/20_series..........NOK 13/33                                               
#   Failed test 'summary includes "fox river"'
#   at t/20_series.t line 49.
Use of uninitialized value $cast_line in split at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Series.pm line 190.
t/20_series..........NOK 14/33                                               
#   Failed test 'cast (scalar context) includes Wentworth Miller'
#   at t/20_series.t line 50.
t/20_series..........NOK 15/33                                               
#   Failed test 'cast (array context)'
#   at t/20_series.t line 55.
#          got: '0'
#     expected: '5'
Use of uninitialized value in pattern match (m//) at t/20_series.t line 56.
t/20_series..........NOK 16/33                                               
#   Failed test 'series image uri includes .jpg'
#   at t/20_series.t line 56.
t/20_series..........NOK 18/33                                               
#   Failed test 'series name is: Joey'
#   at t/20_series.t line 62.
#          got: undef
#     expected: 'Joey'
Use of uninitialized value $episode_line in split at /home/norjms/.cpan/build/WWW-TV-0.14-ui0ZFy/blib/lib/WWW/TV/Series.pm line 275.
t/20_series..........NOK 19/33                                               
#   Failed test 'The object isa WWW::TV::Episode'
#   at t/20_series.t line 63.
#     The object isn't defined
Can't call method "name" on an undefined value at t/20_series.t line 67.
# Looks like you planned 33 tests but only ran 19.
# Looks like you failed 13 tests of 19 run.
# Looks like your test died just after 19.
t/20_series..........dubious                                                 
	Test returned status 255 (wstat 65280, 0xff00)
DIED. FAILED tests 3, 5-10, 13-16, 18-33
	Failed 27/33 tests, 18.18% okay
t/98_pod.............skipped
        all skipped: Skipping author tests
t/99_pod_coverage....skipped
        all skipped: Skipping author tests
Failed Test    Stat Wstat Total Fail  List of Failed
-------------------------------------------------------------------------------
t/10_episode.t  255 65280    41   45  13 15-41
t/20_series.t   255 65280    33   41  3 5-10 13-16 18-33
2 tests skipped.
Failed 2/4 test scripts. 55/74 subtests failed.
Files=4, Tests=74, 46 wallclock secs ( 0.52 cusr +  0.06 csys =  0.58 CPU)
Failed 2/4 test programs. 55/74 subtests failed.
make: *** [test_dynamic] Error 255
  TIGRIS/WWW-TV-0.14.tar.gz
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports TIGRIS/WWW-TV-0.14.tar.gz
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make install
  make test had returned bad status, won't install without force

```

Any ideas what is wrong?

I don't want to go past this point without resolving issues and messing somethign up.

---

### Post by silverdulcet on 2009-05-30
> **norjms said:**
> Here is where I'm at:

Fresh Install of Mythbuntu 9.0.4
Updated system via Update Manager

Opened a terminal
Installed subversion
grabbed the files via
svn checkout [http://fill-mythvideo-metadata.googlecode.com/svn/trunk/](http://fill-mythvideo-metadata.googlecode.com/svn/trunk/) fill-mythvideo-metadata-read-only


mounted cifs tv show share in fstab to /temp
verified proper permissions
Setup Videos directory in mythtv
mythtv sees the files

opened terminal
ran
sudo perl -MCPAN -e 'install WWW::TV'

and I get a fail to install

Any ideas what is wrong?

I don't want to go past this point without resolving issues and messing somethign up.

If you look at the wiki page, [http://www.mythtv.org/wiki/Fill_mythvideo_metadata.pl]("http://www.mythtv.org/wiki/Fill_mythvideo_metadata.pl") Specifically where it says Perl prerequisites or read the version notes:

```
#version 0.7:
#* Moved away from WWW::TV perl module. Now uses www.thetvdb.com API!
#* New command line arguments:
#	* Take snapshots for movies (don't take IMDB's poster) - "0" for take from IMDB.COM, "1" generate snapshot from file: -MOVIE_SNAP [1/0]
#	* Take snapshots for TV shows (don't take The TV DB's poster) - "0" for take from www.thetvdb.com, "1" generate snapshot from file: -TV_SNAP [1/0]
#* major change in images download.
#* bug fixes
#* Known bug: images are not saved in the ART folder, but next to the video files - which means no images in the MythWeb.


```

You'll see that the WWW:TV perl module hasn't been required since the switch to [www.thetvdb.com](www.thetvdb.com) API. In addition, the wiki shows that no third party perl modules are required by the script at all anymore. All you need to do is download the script and run it with the command line switches modified to your liking. :D

---

### Post by joshoekstra on 2009-06-01
Does anyone have troubles getting some descriptions to load from thetvdb.com?
I've got an episode of;
"NOVA_Alien.from.earth.avi" and I override the metadata link in "NOVA_Alien.from.earth.nfo" containing this:
<thetvdb seriesid="76119" season="36" episode="5"/>
Which the script recognizes and downloads the description for, the description ends with: 

Ever since, scientists have been scrambling to find more information about these "hobbits."

I'm guessing the double quotes harm the script because no data gets added to the DB, is this a known problem? Otherwise I'll open an issue for it :)

---

### Post by utar on 2009-06-01
Don't think the double quotes are a problem as this was fixed a while ago.

Not sure that override is valid through, try:

<thetvdb episodeid="391944"/>

May also be worth running the script with "-N 0 -F [path and filename]" to ensure any metadata is refreshed.


[Edit: just tried this on my system and it doesn't work.  I think your are right about the double quotes causing the issue, however I think the exact problem is that double quotes are the last character.  I would raise a bug report.]

Utar

---

### Post by joshoekstra on 2009-06-02
Opened issue 36 on it.

---

### Post by silverdulcet on 2009-06-07
Is it possible to use an nfo file to override the script for a DVD ripped to a VIDEO_TS folder? I've tried using an nfo file named for the directory containing the VIDEO_TS folder, i.e. /mythtv/videos/Moviename/Moviename.nfo as well as VIDEO_TS.nfo. It seems that the script takes note of the nfo files but does not respect them. Perhaps I'm placing the nfo file in the wrong place?

---

### Post by menny on 2009-06-15
> **joshoekstra said:**
> Opened issue 36 on it.
Issue fixed. Download the latest from [http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl](http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl)

Guys, I haven't had a lot of time lately to take care of the script (which I must say, I have very little problems with it, thanks to the support I got from you guys).

But, I'm ready to hear about problems.
Currently I have one bug open ([issue 35]("http://code.google.com/p/fill-mythvideo-metadata/issues/detail?id=35") from jbman).
Does anyone know of any other problem?
Or is it perfect? :)

---

### Post by jbman on 2009-06-15
I will update the script now and give it another run. 

Cheers

---

### Post by joshoekstra on 2009-06-15
> **menny said:**
> Issue fixed. Download the latest from [http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl](http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl)

Guys, I haven't had a lot of time lately to take care of the script (which I must say, I have very little problems with it, thanks to the support I got from you guys).

But, I'm ready to hear about problems.
Currently I have one bug open ([issue 35]("http://code.google.com/p/fill-mythvideo-metadata/issues/detail?id=35") from jbman).
Does anyone know of any other problem?
Or is it perfect? :)

It works, thanks for fixing it!

---

### Post by jbman on 2009-06-15
Still getting the same issue. I tried running the script with sudo with the same results as well.

---

### Post by menny on 2009-06-16
> **jbman said:**
> Still getting the same issue. I tried running the script with sudo with the same results as well.

It is a hard one.
Let's continue to work on that using the Google's Code issues system on: [http://code.google.com/p/fill-mythvideo-metadata/issues/detail?id=35](http://code.google.com/p/fill-mythvideo-metadata/issues/detail?id=35)

---

### Post by rosarch on 2009-08-29
Just found this and thought I would try it out, downloaded the script and run from command line (not as mythtv user) and got the following:

rosarch@rosarch-desktop:~/Scripts$ ./fill_mythvideo_metadata.pl
syntax error at ./fill_mythvideo_metadata.pl line 830, near "$motech_id =~ s/["
  (Might be a runaway multi-line // string starting on line 827)
BEGIN not safe after errors--compilation aborted at
./fill_mythvideo_metadata.pl line 2708.

Would be grateful if someone could point me in the right direction....

---

### Post by utar on 2009-08-29
Strange.

Try downloading the version in this thread as I know this one works fine and perhaps something has been broken in the one you have:

[http://code.google.com/p/fill-mythvideo-metadata/issues/detail?id=46&can=1](http://code.google.com/p/fill-mythvideo-metadata/issues/detail?id=46&can=1)

BTW when you say you set the permissions what exactly do you mean?  Did you just set the script to be executable?




Utar

---

### Post by menny on 2009-08-29
I saw that you opened an issue about this ([http://code.google.com/p/fill-mythvideo-metadata/issues/detail?id=49](http://code.google.com/p/fill-mythvideo-metadata/issues/detail?id=49)).
Very good.

I'm corrently away from my mythtv machine, so I can't fix it.

In the meantime, you can download previous versions of the script from here: [http://code.google.com/p/fill-mythvideo-metadata/source/browse/trunk/fill_mythvideo_metadata.pl](http://code.google.com/p/fill-mythvideo-metadata/source/browse/trunk/fill_mythvideo_metadata.pl)

Just browse for older versions (box on the right).

Menny.

---

### Post by rosarch on 2009-08-29
Thanks for the quick responses guys, I downloaded the script as advised by utar and it works a treat.

:KS

---

### Post by rosarch on 2009-08-29
I have been having a play with this and have a query.

I seem to be having a problem with getting an image on the main series folders for my TV collection.

Example:

I have a folder called X

under here I have more folders e.g x - 1x01, x - 1x02, x - 1x03 and under each of these folders I have an avi file e.g x - 101.avi.

This is how the data is sorted with the programs I use. Now when I run the script and click on the avi's directly they show the data from tvdb and adds an image as expected to the .avi picture which is a scene from the episode, however the folder immediately above and the main folder for the series have gone blank (they used to have writing on them, x and x - 1x01 etc)

I tried just having the main folder x and then all the series avi's under that and running the script again but the main series folder is still blank, basically I am trying to get it the same as shown by this pic on the wiki - [http://www.mythtv.org/wiki/Image:Mythvideo_tv_show_covers.JPG](http://www.mythtv.org/wiki/Image:Mythvideo_tv_show_covers.JPG) 

For information the series I am using is a very well known series so I am sure there is data available for it.

Sorry if this post is confusing... Just trying to get the best out of a great script :-)

---

### Post by utar on 2009-08-29
Interesting filing system.  So basically you have a folder per episode.

I don't use this set-up myself so I can't comment on if the script works correctly.  However a work around would be to have a folder per season.  Is there any particular reason you have a folder per episode?



Utar

---

### Post by johnnybirdman on 2009-10-26
Mythbuntu 9.10rc:
This is my first time trying the script and it seemed to execute fine.  I looked in the posters, banners, fanart folders and the cover art has been populated for the videos I have.  However, after I scanned for changes in video manager no detail is showing.

Is there something that needs to be done after the script is run?

Thanks,
J.

---

### Post by fenian on 2009-10-26
Video manager is no longer needed,go to MediaLibrary>Watch Videos  select the folder that has your video and hit M (menu) choose scan for changes and it should repopulate your video library.

---

### Post by johnnybirdman on 2009-10-26
> **fenian said:**
> Video manager is no longer needed,go to MediaLibrary>Watch Videos  select the folder that has your video and hit M (menu) choose scan for changes and it should repopulate your video library.

fenian, thanks for the help, however, this does not appear to solve the problem. Another odd thing is that when I do that (scan for changes) it kicks me back to the top level folder. (For example, in Watch Videos I have folders: DVD, TV, and Podcasts)  If I go in any of the folders, TV, and go into, The Office, and Scan, it does nothing and kicks me back to the top level, Watch Videos.

---

### Post by menny on 2009-10-27
@johnnybirdman, it is quite strange.
Please go to: 
[http://code.google.com/p/fill-mythvideo-metadata/issues/list](http://code.google.com/p/fill-mythvideo-metadata/issues/list)
and open an issue about it, so I (and others) will be able to help you.

Include in the issue the followings:
1) how you run the script (using crontab? manually? which parameters do you use?)
2) a run's console output.
3) any other information you noticed.

Thanks,
Menny.

---

### Post by johnnybirdman on 2009-10-27
> **menny said:**
> @johnnybirdman, it is quite strange.
Please go to: 
[http://code.google.com/p/fill-mythvideo-metadata/issues/list](http://code.google.com/p/fill-mythvideo-metadata/issues/list)
and open an issue about it, so I (and others) will be able to help you.

Include in the issue the followings:
1) how you run the script (using crontab? manually? which parameters do you use?)
2) a run's console output.
3) any other information you noticed.

Thanks,
Menny.

Menny,
I will go do that.  
I also noticed that if I manually add metadata and then run the script it strips what I've changed manually.  I'll add that to the issue ticket.
Thanks,
J.

---

### Post by johnnybirdman on 2009-11-04
Menny,
Did a complete re-install of the 9.10 final and the script now works.  Must have been something in 9.10 RC that was funky.

Thanks again,
J.

---

### Post by eljeffe on 2009-12-16
I love this script, but AAAAARRRGH! After getting all of its' goodness on my video files, I archived a recording and discovered that the container type is forced to .nuv. Can this script read nuv files? or am I doing something else wrong?

I DO love this script though. Incredible work.

Thanks

---

### Post by menny on 2009-12-17
The script is handling only the file types specified in the MythTV's MythVideo file-type list (which is configurable).
Look it at the frontend's settings pages.

---

### Post by eljeffe on 2009-12-17
Beautiful.

Thanks for the quick response. That was what I needed to do. Archived the files, renamed to title season episode, that was all it took. Great.

Thanks again for this wonderful script

---

### Post by grygub on 2010-03-16
Thank you for your hard work, the script is fantastic. It does a much better job than the other scripts out there. In a more recent mythtv release they have added storage groups for mythvideo. The script seems to have trouble when i use storage groups by setting my directories in the myth backend settings and not in frontend media settings. Running the script like this it finds no video files. If I use the command line option to specify a folder or make the frontend settings point to the same folder as the group settings the metadata is populated but disappears when i scan for changes. In the documentation they push the jamu script because it is storage group compatible but your script is better in every other way. Have you ever considered adding this feature?

thanks

---

### Post by Chewiesw on 2010-04-16
I keep "losing" the metadata.
 
I am trying to be a little more green and power off my pc's at night or when they are not needed.

The problem I have is that most of my collection is on my windows pc and is mounted by samba shares with utf8 encoding using cifs to my mythbox.After restaring the the boxes all the metadata of videos on the windows shares is missing which is a real pain. The video's on the actual mythbox reatin their data.

Is there a way I can retain this metadata through reboots?

Andrew

---

### Post by dannyboy79 on 2010-04-16
dont know how this script is surviving when jamu.py is AWESOME! it gets all my movies AND tv shows, not just tv shows. it has the capabilities beyond belief. Jamu is the best.

I mention this to all users who have converted to storage groups. i don't believe this script works with SG.

---

