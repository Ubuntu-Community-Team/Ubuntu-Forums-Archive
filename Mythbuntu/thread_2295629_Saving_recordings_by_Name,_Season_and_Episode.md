---
title: "Saving recordings by Name, Season and Episode"
date: 2015-09-20
forum: Mythbuntu
---

### Post by hollywoodpete on 2015-09-20
I have been using Myth for about a year and am trying to find a painless way to save my recordings as Name SxxExx.filetype. Currently they are saved by a convoluted set of numbers. I have used the Direct Download on Mythweb but it is very slow. If there is a faster conversion tool that can be automated, I would be forever greatful.

---

### Post by khPWXxF on 2015-09-22
Does mythlink.pl get close to what you want?
Phil

---

### Post by hollywoodpete on 2015-09-23
> **khPWXxF said:**
> Does mythlink.pl get close to what you want?
Phil

It may, unfortunately I need to learn a lot more about using the CLI to make it work. I am hoping for a point-and-click solution

---

### Post by vidtek on 2015-09-30
> **hollywoodpete said:**
> I have been using Myth for about a year and am trying to find a painless way to save my recordings as Name SxxExx.filetype. Currently they are saved by a convoluted set of numbers. I have used the Direct Download on Mythweb but it is very slow. If there is a faster conversion tool that can be automated, I would be forever greatful.

I use the archive facility in Mythtv, it doesn´t do episodes and series very well, but it creates a folder with the programme title and the gobbledgook numbers.mpg in that folder.  you can then run that .mpg file in another frontend programme like VLC.

Tony

---

### Post by philip7 on 2015-10-07
I've tried to do something similar in the past using multiple approaches, ideally producing a filename that could be understood by Kodi.

Unfortunately I've never been successful with anything that is perfect, there was always an issue that caused a problem, for example Mythlink is great until you want to delete the recording, you'll only delete the symlink no the actual recording.

If you have any success please let me know.

---

### Post by vidtek on 2015-10-07
> **philip7 said:**
> I've tried to do something similar in the past using multiple approaches, ideally producing a filename that could be understood by Kodi.

Unfortunately I've never been successful with anything that is perfect, there was always an issue that caused a problem, for example Mythlink is great until you want to delete the recording, you'll only delete the symlink no the actual recording.

If you have any success please let me know.

I use KDE so when I need to delete the actual recordings, it&#347; quite painless to do a twin pane with meld and tie up the symlink to the actual file and delete both.  Never tried Kodi so am clueless as to what that is/does, presumably a frontend viewer?  I use mythweb on other machines ipads etc., all I need is included in the Myth package.
 
The gobbledegook filenames used in Mythtv always contain the recorded date, so doing it by hand it&#347; still fairly easy, just use your file admin programme to sort by date.

Tony

---

### Post by aelfric55 on 2015-10-08
Season and episode number seem to be only sporadically provided by xml data providers. If, however, you can get by with Series title and Episode title, you don't need anything more sophisticated than the "cp" command, which you would incorporate in a user job.

That is, a user job command along the lines of:```
cp %DIR%/%FILE% /PATH/TO/STORAGE/DIRECTORY/"%TITLE%"-"%SUBTITLE%"-%FILE%
```should do the trick, where the storage directory is a place mythtv has write-access to. The file should end up with a name like "title-episode-numericaltimechannelstamp.mpg" I'd think you'd want to keep the time/channel stamp portion, so that in case you re-record the episode you still have unique filenames. The quotes are necessary in case your show title/subtitle has a character that can't normally be in a filename without escaping, like the apostrophe in "O'Reilly",or spaces.

I use a command similar to this as part of a user job that automatically transcodes down the evening's news & business shows I like and loads them onto a thumb drive I take with me on the bus the next morning.

---

### Post by vidtek on 2015-10-09
> **aelfric55 said:**
> Season and episode number seem to be only sporadically provided by xml data providers. If, however, you can get by with Series title and Episode title, you don't need anything more sophisticated than the "cp" command, which you would incorporate in a user job.

That is, a user job command along the lines of:```
cp %DIR%/%FILE% /PATH/TO/STORAGE/DIRECTORY/"%TITLE%"-"%SUBTITLE%"-%FILE%
```should do the trick, where the storage directory is a place mythtv has write-access to. The file should end up with a name like "title-episode-numericaltimechannelstamp.mpg" I'd think you'd want to keep the time/channel stamp portion, so that in case you re-record the episode you still have unique filenames. The quotes are necessary in case your show title/subtitle has a character that can't normally be in a filename without escaping, like the apostrophe in "O'Reilly",or spaces.

I use a command similar to this as part of a user job that automatically transcodes down the evening's news & business shows I like and loads them onto a thumb drive I take with me on the bus the next morning.

Aelfric55's suggestion is an elegant solution to our problem with Mythtv&#347; gobbledegook filenames, you really have to love linux, many paths to the same end.

Thank you for this, sometimes we get so caught up with scripts and complicated ways of doing things, we overlook the simple ways, I´ll definitely try this one myself.

Tony

---

### Post by deadflowr on 2015-10-09
> **philip7 said:**
> I've tried to do something similar in the past using multiple approaches, ideally producing a filename that could be understood by Kodi.

Unfortunately I've never been successful with anything that is perfect, there was always an issue that caused a problem, for example Mythlink is great until you want to delete the recording, you'll only delete the symlink no the actual recording.

If you have any success please let me know.

Do you have *kodi-pvr-mythtv* installed?
It's an add-on package that will add  TV option that will connect to your mythbackend.
It acts quite similar to a normal mythtvfrontend, but inside kodi.
(It reads the files just as the frontend would, and will do anything you would do with a frontend, like delete)
more: [http://kodi.wiki/view/MythTV_PVR](http://kodi.wiki/view/MythTV_PVR)

---

### Post by hollywoodpete on 2015-10-10
> **deadflowr said:**
> Do you have *kodi-pvr-mythtv* installed?
It's an add-on package that will add  TV option that will connect to your mythbackend.
It acts quite similar to a normal mythtvfrontend, but inside kodi.
(It reads the files just as the frontend would, and will do anything you would do with a frontend, like delete)
more: [http://kodi.wiki/view/MythTV_PVR](http://kodi.wiki/view/MythTV_PVR)

I use Kodi as my frontends which is why I want to rename the video file. The current naming system by myth is not recognized by the Kodi frontends.

---

### Post by philip7 on 2015-10-12
I can recommend using the Mythtv add-on for Kodi, it was the only way to be sure all the recordings would appear in Kodi.

The only downside was the interface, it isn't quite as good as Mythtv, but I've got used to it overtime.

---

### Post by philip7 on 2015-11-16
Not sure if you're still looking at this but I looked at this again using Mythvidexport ([https://www.mythtv.org/wiki/Mythvidexport.py](https://www.mythtv.org/wiki/Mythvidexport.py)) and have had more success.

You need to make sure all the necessary metadata (InetRef, Season, Episode, Subtitle)  is correct for the recording, you also will need to change the format for tv shows so they work for Kodi. I can give you my config details if you're interested.

---

### Post by vidtek on 2015-11-16
> **philip7 said:**
> Not sure if you're still looking at this but I looked at this again using Mythvidexport ([https://www.mythtv.org/wiki/Mythvidexport.py](https://www.mythtv.org/wiki/Mythvidexport.py)) and have had more success.

You need to make sure all the necessary metadata (InetRef, Season, Episode, Subtitle)  is correct for the recording, you also will need to change the format for tv shows so they work for Kodi. I can give you my config details if you're interested.

I was unable to get Aelfric55's simple solution to work for me, so thanks for this I'll have a go and report back here.

Tony.
edit:
Not had much success with this either, if you can you post your config I'll try again with that. 
Tony

---

### Post by philip7 on 2015-11-22
This is how I get the script working so the filenames work well with Kodi:

1.) Take the Mythvidexport script from here: [https://www.mythtv.org/wiki/Mythvidexport.py](https://www.mythtv.org/wiki/Mythvidexport.py), you can put it anywhere you like I have mine in the mythtv home folder
2.) Change the tv format to this "%TITLE%/%TITLE% s%SEASONPAD%e%EPISODEPAD% - %SUBTITLE%" and the movie format to this "%TITLE% %YEAR%"
3.) Then run this as a userjob /SCRIPT LOCATION/Mythvidexport.py --chanid %CHANID% --starttime %STARTTIME% --listingonly

The only issues I have at the moment are:
1.) Some user jobs fail, from what I can tell you need to make sure the metadata for the recording is correct (Title/Subtitle/Season/Episode/InetRef).
2.) There some shows that use a colon (:) symbol - this causes a problem with the filenames, I haven't had a look at the script but fairly sure it would be an easy change.

Let me know if you have any problems

---

