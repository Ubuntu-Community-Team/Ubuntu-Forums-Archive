---
title: "Mythbuntu Upgrade - Mythtranscode Advice"
date: 2013-03-11
forum: Mythbuntu
---

### Post by se99paj on 2013-03-11
I've recently gone through a clean upgrade of Mythbuntu - I think the best advice I have is that if you want to upgrade in the future make sure that you upgrade frequently, I can't remember what build my old version was but I couldn't reuse the same database in 0.26, in the end I decided to wipe the recordings completely and start from scratch, my videos are in a separate partition so they were easy to update.

Anyway, I have a process where I transcoded recordings that I wanted to keep using nuvexport/mencoder and moved them to the videos folder, the videos were transcoded to AVI files using the Xvid codec, the results were quite good.

After the upgrade I tried to use the same process, but it didn't work, when using Nuvexport Mythtranscode kept finishing early.
I then tried to just use mythtranscode I experimented with Mpeg4 compression but had issues with the cut videos, I also experimented with just mpeg2 but had a permanent "Deadlock detected" errors.

After reading up on this it sounds like there is an issue with Mythtranscode and 0.26.

I've now gone back to 0.25 and mythtranscode seems to be working alright, I managed to do some initial testing with Mpeg4 the output files were smaller but not by much and the quality was quite poor.

It would be useful to know how other people use transcoding, do most people just cut the commercials and use lossless to keep the files, most discussion boards seem to say that storage is cheap so why not.

My concern is that if I compare the old video files with the new ones I'm going to have then the file sizes are going to be huge whereas the old ones had a small filesize and the quality was quite good.

---

### Post by klc5555 on 2013-03-11
> **se99paj said:**
> I've recently gone through a clean upgrade of Mythbuntu - I think the best advice I have is that if you want to upgrade in the future make sure that you upgrade frequently, I can't remember what build my old version was but I couldn't reuse the same database in 0.26, in the end I decided to wipe the recordings completely and start from scratch, my videos are in a separate partition so they were easy to update.

Anyway, I have a process where I transcoded recordings that I wanted to keep using nuvexport/mencoder and moved them to the videos folder, the videos were transcoded to AVI files using the Xvid codec, the results were quite good.

After the upgrade I tried to use the same process, but it didn't work, when using Nuvexport Mythtranscode kept finishing early.
I then tried to just use mythtranscode I experimented with Mpeg4 compression but had issues with the cut videos, I also experimented with just mpeg2 but had a permanent "Deadlock detected" errors.

After reading up on this it sounds like there is an issue with Mythtranscode and 0.26.

I've now gone back to 0.25 and mythtranscode seems to be working alright, I managed to do some initial testing with Mpeg4 the output files were smaller but not by much and the quality was quite poor.

It would be useful to know how other people use transcoding, do most people just cut the commercials and use lossless to keep the files, most discussion boards seem to say that storage is cheap so why not.

My concern is that if I compare the old video files with the new ones I'm going to have then the file sizes are going to be huge whereas the old ones had a small filesize and the quality was quite good.

I cut the commercials, use lossless to keep the files, and buy additional storage when necessary. I've not upgraded to 0.26 largely because of the mythtranscode problems. But even on 0.25 and earlier, the "Deadlock detected!" error is a fairly frequent mythtranscode issue, particularly when cutting HD recordings. The "workaround" described for "Deadlock detected!" in the mythtranscode wiki is frankly useless, and so for "Deadlock detected!" files, I cut commercials and save the files using Avidemux. Not ver. 2.54 or 2.55, which I think are still included for Ubuntu 12.04/12.10, but rather the recently released Avidemux 2.61, which appears to be the first version that can cut and remux HD recordings correctly.

---

### Post by se99paj on 2013-03-12
How do you cut commercials and then run a lossless transcode? do you use the --mpeg2 option in mythtranscode or do you have a transcoder setup with lossless transcoding (Or are these basically the same thing just staretd differently?)

I thought it might be easier to document what I'm trying to achieve and then hopefully someone can tell me if my approach isn't very practical.

I would like to save recordings that I want to keep in my Videos library (I've done this for videos but I'm also interested in looking at TV Shows), so initially the requirement would be to save the file using the title as the filename but if I use tv shows I'll also need to look at including the season into the output directory/filename.
In the past my approach has been to run nuvexport, convert to Xvid and save in the videos directory, after the upgrade I couldn't nuvexport to work and tried just using mythtranscode.

**Option 1 Mythtranscode**
Using mythtranscode I was able to save movies into the movies directory, I'm pretty sure this was using lossless transcoding but I'll need to check. The filename was the movie title which worked correctly, but this approach won't work with tv shows as I don't think I can pull the season information from Mythtv into the job script and therefore I can't construct a directory/filename that meets the metadata requirements.

**MythvidExport**
I did come across the Mythvidexport script last night which looked like it does everything I need, i.e. moves films and tv shows into the videos folder and you can chance the structure being used, it looks like they are moved using the storage groups which is a bonus. But I'm not really a python expert and the instructions on the wiki page are not very detailed, also I'm not sure if Mythvidexport transcodes the file and removes commercials or if it just moves the original.

**Nuvexport**
I've given Nuvexport another go and it works, I'm guessing this is because I'm not on 0.25 instead of 0.26, I'm going to play around with the settings to try and get a compression/format that I'm happy with. The ideally I would like the same quality as the recorded version but with a reduced filesize, I'll probably be playing the videos on my tv or tablet. My only concern with Nuvexport is that there are so many different options that I don't know which one I should use, i.e. should I use Xvid or H264, AVI or MP4.

---

### Post by klc5555 on 2013-03-12
I'll set up cutlists manually in mythfrontend for shows I wish to save, since automatic commercial detection in mythtv cannot be relied upon. Then I'll run a bash script (which I've set up as a user job) which 1) runs mythtranscode with the --mpeg2 and --honorcutlist options 2) takes the original recording and moves it to a *.old file 3) takes the *tmp file that mythtranscode produced and moves it to the original filename 4) rebuilds the frame index for the newer, shorter "original" file (mythtranscode with the --mpeg2 and --buildindex options), and 4) deletes the now-obsolete cutlist for the new "original" file.  It's essentially the following script, but with the unreliable flagging and cutlist generating sections removed: [http://www.mythtv.org/wiki/Script_-_RemoveCommercials](http://www.mythtv.org/wiki/Script_-_RemoveCommercials) Another bash script set as a cron monthly removes all the left over *.old and *.tmp files from the recording directories after a reasonable period.

If the newer, cut recording has a problem (extremely rare) I still have the *.old file for a while to troubleshoot from, and if necessary restore. If, however, mythtranscode bombs completely (much more common) I have to use a secondary method to trim commercials from material I wish to save. Formerly this method was nuvexport transcoding down to an avi. But avi is obsolete, the files have a 4 Gig size limit, and I really hate throwing data away by using a lossy transcoding method. When I originally tried avidemux for lossless saving after commercial cutting, I was disheartened by the discovery it couldn't handle H264 very well, and couldn't cut the audio tracks in HD recordings at all. However, coming back to it recently, I was very pleased to discover that these flaws were fixed in avidemux 2.61, and I could cut and save (using its mpeg2-ps muxer) all the HD recordings that mythtranscode had died on in recent months. I had a fair backlog to work through.

I've never used MythvidExport. But the script appears to move the file and preserve the cutlist information, not transcode.

---

### Post by se99paj on 2013-03-19
So I thought I'd provide some feedback on how I got on.

After trawling the internet for a solution I decided to use Nuvexport but with my own Bash script, technically it isn't my own script as I used this script as a guide: [http://www.mythtv.org/wiki/Nuvexport#Automating_The_Process](http://www.mythtv.org/wiki/Nuvexport#Automating_The_Process)

Also, for any newbies out there I'd say don't be afraid about getting your hands dirty writing your own scripts, it probably seems daunting at first, but is easier than it looks.

The script is very simple (It needs to be as I wrote it) but basically it uses the tv show season and episode information to create a new folder if it doesn't exist, then runs nuvexport to transcode the file.

The few things I noticed are:

1.) I can't seem to Mythtv to convert to MP4 via a user job, it works fine as an Xvid so I need to do some more research on this.
2.) Some of the documentation regarding user jobs doesn't seem to be uptodate, for example it is possible to use the Season and Episode value as fields in a user job but this isn't covered in the documentation. Who updates the documentation? is it something that I could do or should it stick with the devs?

---

