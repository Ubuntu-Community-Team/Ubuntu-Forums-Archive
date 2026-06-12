---
title: "Moving recordings to videos"
date: 2010-05-02
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-05-02
I have a number of movies that I've recorded, which currently reside in the recordings section of my Myth system.

I would like to be able to move them to the videos section (which is on a second hard drive with a lot more room than the hard drive the recordings are on), ideally so that the system still knows what the movie is called so that I can do an IMDB lookup to fill in all the metadata (although presumably this is not too much of a PITA to do manually if I can't keep the metadata?)

I see that this question has been asked before on these forums, although [that thread]("http://ubuntuforums.org/showthread.php?t=649183") is over 2 years old so I was wondering if things have moved on since then.

It would also be nice to be able to get rid of any adverts in the movies at the same time, although that's definitely a nice-to-have feature rather than essential.

Any hints or tips? Is there an easier way to do this than simply copying the movies manually to the relevant directory and manually adding back the metadata?

I'm using Mythbuntu 9.10.

Thanks
NM

---

### Post by kja999 on 2010-05-02
Well, not sure if there are any new tools as I still do a similar process.

Mark the adverts from within myth, run the transcode to cut them out, find the .mpg file and copy it to video location.
No extra conversions necessary as the resulting file seems to play everywhere ok for me (linux only).

---

### Post by klc5555 on 2010-05-02
The copied file will play, but will need a frame index for myth to be able to jump forward/backward in it. This can be done generally with mythtranscode (with --mpeg2 --buildindex --video) or sometimes mythcommflag (--rebuild) being run on the file in its new, copied location.

---

### Post by bergersau on 2010-05-06
The best way I've found is to set up the nuv2mkv script as a user job.
Get the script here.
[http://web.aanet.com.au/~auric/?q=node/6]("http://web.aanet.com.au/~auric/?q=node/6")

You'll need to hand edit the script to set up it's defaults to suit you. Then chmod +x it to make it executable and add the script to the MythTV user jobs. [http://www.mythtv.org/wiki/User_Jobs]("http://www.mythtv.org/wiki/User_Jobs")

Then edit the ad's out [http://www.mythtv.org/wiki/Removing_Commercials]("http://www.mythtv.org/wiki/Removing_Commercials").

Then run the user job on the recording.

nuv2mkv will honor the cut points list, import IMDB/TMDB meta data as appropriate and store the finished file in your movies folder and add it to the database.

---

### Post by NautiusMaximus on 2010-05-08
OK, thanks for those suggestions, I'm now making progress.

I have successfully managed to edit out the adverts by following the instructions in the link you gave.

I did that by transcoding using the built-in MythTV tools, which seemed to work OK. The file size shrank more than I thought it would given that I'd set the transcoding to lossless. It's obviously going to shrink a bit given that I'm editing out adverts, but the transcoded version wasn't much more than about half the file size of the original. Is that normal behaviour?

However, I couldn't get the nuv2mkv script to work. I set it up as a user job, and then it appeared in the jobs menu on the front end. But when I tried to run it, nothing happened. Here is something from the backend log which I suspect is probably relevant:

```
2010-05-08 15:40:50.242 JobQueue: Started Copy to videos for "Austin Powers: International Man of Mystery" recorded from channel 9384 at Sun Jan 25 23:05:00 2009
ldd: missing file arguments
Try `ldd --help' for more information.
strings: '': No such file
strings: '': No such file
2010-05-08 15:40:51.418 JobQueue Error: User Job 'mythnuv2mkv.sh --jobid=593 --copydir=media/disk2/mythtv/videos --chanid=9384 --starttime=20090125230500' failed.
```

Any ideas what might be going wrong here?

It's actually not the end of the world if I can't get this script to work, as it's reasonably easy to copy the file manually and download the metadata manually, but it would be nice if it could be done automatically.

BTW, if there is a simpler alternative to mythnuv2mkv, that would be fine. It seems to convert the file format, which I rather feel is unnecessary. The original .mpg file plays just fine in the Videos function.

---

### Post by laffinet on 2010-05-09
Each mythnuv2mkv job produces a log file, you should check that for more information about why it failed.

Logfiles are located in /var/tmp/

One of the advantages of the mythnuv2mkv script is that the resulting files are a lot smaller than the original mythtv mpeg files (depending on what settings you use). So it might be worthwhile persisting.

Once you have it set up as a user job it's really easy to use.

---

### Post by NautiusMaximus on 2010-05-16
> **laffinet said:**
> Each mythnuv2mkv job produces a log file, you should check that for more information about why it failed.



Ah, thanks for that. That log was considerably more helpful, and I seem to be making progress, although I'm not there yet.

The log said that it couldn't find the program mencoder. I found a program with that name in Synaptic package manager, installed it, and tried again.

This time, I get the error message "ERROR Can't find program convert". Sadly, there doesn't seem to be a program in Synaptic called "convert".

Any ideas what to try next?

Since I'm really not bothered about transcoding, and want the script simply to move the file and handle the metadata, I'm toying with the idea of editing the script to take out all the bits that do the transcoding and just leave me with the bits I want. However, I have almost zero experience of writing shell scripts. Is that plan worth considering, or am I almost guaranteed to screw it up if I'm not intimately familiar with shell scripts? I have done a bit of programming in other languages in the Windows world, but am a bit of a newbie when it comes to all things Linux.

---

### Post by laffinet on 2010-05-16
From the mythnuv2mkv website:
```
For all contypes

mythtranscode. - UBUNTU: mythtv-transcode-utils (multiverse) 
perl. http://www.perl.org/ - RPM: perl - UBUNTU: perl (main) 
mplayer http://www.mplayerhq.hu/design7/news.html - RPM: mplayer - UBUNTU: mplayer (multiverse or non-free(medibuntu)) 
mencoder http://www.mplayerhq.hu/design7/news.html - RPM: mplayer - UBUNTU: mencoder (multiverse or non-free(medibuntu)) 
wget http://www.gnu.org/software/wget/ - RPM: wget - UBUNTU: wget (main) 
ImageMagick http://www.imagemagick.org/script/index.php - RPM: ImageMagick - UBUNTU: imagemagick (main) 
bc - RPM: bc - UBUNTU: bc (main) 
For avi

mp3lame http://www.mp3dev.org - RPM: lame & lame-devel - UBUNTU: lame & liblame0 (multiverse) 
For mkv and mp4 contypes

x264 http://www.videolan.org/developers/x264.html - RPM: x264 (http://atrpms.net/) - UBUNTU: x264 (multiverse) 
faac http://sourceforge.net/projects/faac/ - RPM: faac & faac-devel (http://atrpms.net/) - UBUNTU: faac & libfaac0 (multiverse) 
faad2 http://sourceforge.net/projects/faac/ - RPM: faad2 & faad2-devel (http://atrpms.net/) - UBUNTU: faad & libfaad0 (universe) 
For mkv contype

mkvtoolnix http://www.bunkus.org/videotools/mkvtoolnix/ - RPM: mkvtoolnix - UBUNTU: mkvtoolnix (universe)
(For NTSC mkvmerge V2.2.0 or later).
There is a bug report for mkvmerge 2.5.1 https://www.bunkus.org/bugzilla/show_bug.cgi?format=multiple&id=338
V1.43 and latter should auto add the below workaround.
It has a workaround of running "mkvmerge" as "LANG=C mkvmerge"
If you get the following error
Error: The locale could not be set properly. Check the LANG, LC_ALL and LC_MESSAGES environment variables.
Change
mkvmerge --default-duration 0:${FPS}fps --aspect-ratio 0:${ASPECT} --title "$TITLE" \
to
LANG=C mkvmerge --default-duration 0:${FPS}fps --aspect-ratio 0:${ASPECT} --title "$TITLE" \ 
For mkv,ogg contype

vorbis-tools http://www.vorbis.com/ - RPM: vorbis-tools - UBUNTU: vorbis-tools (main) 
For mp4 contype

MP4Box http://gpac.sourceforge.net/index.php - RPM: gpac (http://rpmfusion.org/) - UBUNTU: gpac (multiverse) 
Optional

mediainfo - http://mediainfo.sourceforge.net/en - Can tell if input is progressive and so auto remove the deinterlace filter if added. 

```

This is all the software you have to have installed in order for the script to work. Install all these and try again.

You can just use a terminal and copy everything into the same line
```
sudo apt-get install mythtv-transcode-utils perl mplayer 
```etc. etc.

---

### Post by NautiusMaximus on 2010-05-29
OK, I have a solution to this now.

I never did get the nuv2mkv script to work. Presumably it can work under some circumstances, but not under the ones in which I was attempting to use it. As stated previously, I didn't feel any need for the transcoding feature, and the main thing I wanted was to copy the media file to the movies directory while maintaining something of the metadata.

I spent an hour or two reading about how to write bash scripts, and came up with a fairly simple script that seems to do the job, and then set it up as a user job so that it can easily be accessed from the frontend. What it does is it copies the media file from the recordings directory to the videos directory, and renames the file with the name of the movie. That's it. It doesn't look up the metadata, but that is very easy to do once the file is in the videos folder, so I'm not too worried about that (although if anyone would like to suggest how to amend the script to make it download the metadata automatically, that would be welcome). It also saves a log file so you can see if it's been successful.

I attach a copy of the script in case anyone is interested.

---

