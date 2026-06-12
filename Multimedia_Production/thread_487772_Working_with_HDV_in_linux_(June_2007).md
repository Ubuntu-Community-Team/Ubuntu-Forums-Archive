---
title: "Working with HDV in linux (June 2007)"
date: 2007-06-29
forum: Multimedia Production
---

### Post by Rexbron! on 2007-06-29
**UPDATED 13/08/07:** Changed the guide to reflect new release of dvgrab. For alternative workflows that may work better, see posts in this thread.

To start, I will explain what pyHDV is.  pyHDV is a python module I wrote to automate some of the tasks associated with working with HDV video under linux. Also included is a (semi)functional implementation of the pyhdv module. 

I wrote pyHDV to assist with tasks that one has to do to work with 24p HDV video on linux. 

The script, commandline.py, (I'll come up with a better name for it sometime) does three things currently and soon will have a fourth feature.

Those features are:

1) Capture HDV video through a patched dvgrab.

2) Convert telecined HDV video back to its native 24p.

3) Create low-res proxy files for editing. This feature is to be used in conjunction with the [proxychange.py](http://cvs.cinelerra.org/docs/proxychange.py) and cinelerra.

4) Dump audio from an input file. (Not done yet)

Start by downloading [pyHDV](http://aehunter.net/Files/Ubuntu/pyHDV-0.1.tar.gz) , extracting pyHDV and running 

```
python commandline.py -h
```

This will display all the options for the commandline script

**_Capturing_**

To use pyHDV to capture HDV video, you will need the latest version of dvgrab (3.0).

You can compile from source (Get it [here](http://sourceforge.net/project/showfiles.php?group_id=14103&package_id=95982)) or if you are running gutsy download a binary from [here](http://vv.guelf.free.fr/ubuntu/).

You will also need to install mencoder if it is not already installed:
```
sudo aptitude install mencoder
```

Finally, you will need to add raw1394 permissions to video.

```
cd /etc/udev/rules.d/
sudo cp 40-permissions.rules 40-permissions.rules.bak
sudo gedit 40-permissions.rules
```

Find:

```
KERNEL=="raw1394",                      GROUP="disk"
```

And change it to look like this:

```
KERNEL=="raw1394",                      GROUP="video"
```

Reboot and login.

**NOTE:**Currently the capture code works, but you must manually interupt (ctl-c) it for dvgrab to finish writting the file. I will be working on properly getting the proper behaviour.


_**Inverse Telecine (IVTC):**_

**NOTE:** You only need to do this if your footage was shot in 24p


Once you have your captured footage, review the footage and copy the clips you wish to work on into another folder. This is necessary as currently the file list that the script works on is all the files in the current directory. Also, in a professional workflow, you would only want to work with the takes that are good. This saves time and diskspace.

There are two formats that the script takes for outputting after the IVTC, Ljpeg and Mpeg2.

Ljpeg:

Ljpeg stands for lossless Motion Jpeg. In technical terms it turns the GOP's into all I Frames. The advantage of this format is there is no loss in quality. The downsides are file size and that the files ususally can not be played back in realtime without dropping frames on playback. 

Ljpeg is the default format.

Mpeg2:

The pros of using the mpeg2 is that it saves space. The con is that sync is lost and picture quality is degraded.

**_Proxies:_**

Due to the nature of mpeg2's (long GOP stream), it makes editing with them in programs like Cinelerra undesirable. Everytime you make a cut Cinelerra must re-encode the clip. Also, Cinelerra has difficulty playing back HDV video in realtime without _very_ powerful hardware.

To overcome both problems, one can create proxy files. These are scaled down versions of your original files but are also mjpegs (all I frames), so you do not encounter the re-encoding problems. 

**Note:** Currently, you have to run the script each time for each operation you wish to perform. I am working on making it so that it will string them together. 

Any questions, comments or corrections, just post below.

---

### Post by eugenia_loli on 2007-07-16
The URL for the tarball is broken. I managed to find the correcdt url, but i get this

eugenia@inspiron:~/Desktop/pyHDV$ python commandline.py -h
  File "commandline.py", line 80
    continue
SyntaxError: 'continue' not properly in loop

---

### Post by Rexbron! on 2007-07-16
Crap. I proably uploaded the wrong tarball... I will have that fixed soon.

---

### Post by eugenia_loli on 2007-07-17
Thanks!

 I have a Canon HV20 and needed the pulldown removed, but I found problems with your mencoder commandline you use. A bug report:

The avi/mjpeg video seems to have problems: It has weird sound (or no sound at all) and the wrong aspect ratio. It is producing a 4:3 video, even in the mencoder command line you ask for 16:9.

The mpeg2 version works much better, but it does not produce 23.976 fps (you seem to ask for 24fps - which is NOT the right framerate for this camera), and this can be problematic in some scenes that require precision.

---

### Post by ArtInvent on 2007-07-17
This sounds like a neat utility. I have a Canon HV20, I'm shooting in 24P  and pretty much need exactly what this does to be able to edit in Cinelerra.

Right now I'm using a pretty simple capture script I worked out, described at
  [http://ubuntuforums.org/showthread.php?t=412826](http://ubuntuforums.org/showthread.php?t=412826)

Then, I've been experimenting with various command lines for mencoder to do reverse pulldown. I get some usable clips, but not sure any of them are quite what they ought to be. I look at the results and it seems to me that mencoder's pullup is not necessarily keying on the correct frames. In correct reverse pulldown, as far as I can tell, you either need to manually set the frame to start on, or the app needs to visually analyze the frames to determine this automatically. I don't have any way to do it manually, and I don't think mencoder is sophisticated enough that it would have the automatic function. In short, I am pretty sure using mencoder is not going to give you the right pullup for the HV20 footage. (Well, you'd have a 1 in 5 chance of it starting on the correct frame!)

Also, another problem I've had with mencoder, mentioned by eugenia, is that resulting files sometimes have the correct aspect ratio, but played in certain movie players and editors, they don't. 

I will try and give your script a try though. Thanks for all your efforts. The proxy thing certainly sounds useful, as I have a pretty decent dual core machine with 2 GB ram, and Cinelerra still chokes on HDV.

---

### Post by eugenia_loli on 2007-07-18
Exactly. Mencoder does not remove the right frames -- plus some other problems. I don't think there is any application on Linux right now that can perform the correct inverse telecine on the HV20. In fact, not even Adobe Premiere LE 3.0 removes the right ones. I blogged about the best free ways to do it under several OSes here: [http://eugenia.gnomefiles.org/2007/07/13/canon-hv20-24p-pulldown/](http://eugenia.gnomefiles.org/2007/07/13/canon-hv20-24p-pulldown/)

---

### Post by mariusmuja on 2007-07-25
I think Avidemux does the pulldown removal correctly. You must use two filters for that: Decomb Telecide and Decomb Decimate, in this order. 
Avidemux is a corss-platform application, is available for windows also.

---

### Post by ArtInvent on 2007-07-25
I hadn't tried Avidemux before. It seems promising. I did try a reverse pulldown on the .m2t capture files from the Canon HV20. I got some awfully good results after some experimenting. 

Best results were output to an AVI format using MJPEG compression. Trying the RAW AVI output option was huge MB-wise and resulted in everything orange being blue. Very strange. Anyway, I reason that for editing MJPEG should be easier since it's entire frame rather than long GOP. Raw video doesn't play too smoothly on my machine, the raw data files are just to large.

When I opened my m2t files they had a black bar at the bottom and measured 1088 pixels high rather than 1080. So first I put a crop filter in the stack to take off 8 pixels from the bottom. 

Next, as you suggest, I added the Decomb Telecide with stock presets. Then the Decomb Decimate with stock presets.

Saving this file I got an AVI file that was playable in Movie Player and VLC, but the aspect ratio was wrong at 4:3 rather than 16:9. I looked for various ways to fix this in Avidemux but couldn't find anything. The properties of the original m2t capture file say that the aspect ratio is unknown. Hmm. It seems like what is needed is some way to add a flag of some kind to the file to signal it's aspect ratio. Don't know how to do this. Tried the Resize filters but was unable to get it. I am also wondering if maybe MJPEG is just plain incompatible with non-square pixels. 

Anyway, by setting the video option in either player to force an aspect ratio of 16:9, I was able to watch this avi file - it's gorgeous. Best I've seen out of the camera, the reverse pulldown seems perfect. 

Next, I try pulling this file into Cinelerra. It actually seemed to work, except for the fact that my clip was about 2m30s and it only pulled in about 46 seconds worth of the file. Setting the aspect ratio in the Cinelerra project, it seemed able to correct the aspect. What was pulled in seemed to play back in the composite window pretty nicely, better than any other HD footage I've seen so far. But then Cinelerra seemed to keep locking up so I gave up.

In short, good progress, but still not quite there.

---

### Post by mariusmuja on 2007-07-26
I'm editing my HV20 movies using almost the same process you described above.

The first thing I do is to process the .m2t file with projectx. This removes the B-frames at the beginning of the movie and synchronizes the audio with the resulting video. I found out that if I don't do this, the B-frames get removed by the Avidemux anyway, but the audio is not synchronized with the video ( there is a delay, smaller on some movies, bigger on others, depending on how many B-frames there are in the beginning until the first I-frame). Projectx outputs two files, a .m2v (the video) and a .mp2 (the audio).

Next I open the .m2v and .mp2 files file with avidemux, apply Decomb telecide with stock presets, Decomb decimate with Pulldown dupe removal mode (I think it also works with with stock presets), a crop filter from 1440x1088 -> 1440x1080 and a Mplayer resize filter from 1440x1080 to 1280x720. I export the result as an AVI with  MJPEG codec for video and WAV PCM for audio. This AVI file can be opened with cinelerra without any problem. Make sure you set the correct format in cinelerra (Settings -> Format), especially the Frame rate to 23.976. If the frame rate is set to 29.97 cinelerra will reinsert dupe frames to correct the frame rate.

Cinelerra used to freeze in my case also until I enabled the "Stop playback locks up" option in Preferences, Playback window. Now it works perfectly.

---

### Post by ArtInvent on 2007-07-26
Thanks for the tips, marius, this sounds awesome. Unfortunately I won't have the time to try this all out for a while. But so far I've done a few more mjpeg-avi's with avidemux and they are beautiful. I haven't seen the sound sync problem yet. I just did one five minute file that was composed of a bunch of short takes not more than 8-12 secs each just starting and stopping the camera, even turning it off and on at various points. The reverse pulldown filters seemed to handle it all and find the correct frames throughout.

I do find it hilarious that Cinelerra has is a setting called "Stop playback locks up". This doesn't really sound to me like something you would want to have as an 'option'  :p

One thing: you're downsampling from 1080P (well, almost)  to 720P, why exactly? Because Cinelerra handles this better? 

To tell the truth, I do think that 720P makes good sense as a format (certainly better than 1080i) and I've seen 720p that seems to look about as good as 1080i. Plus 720P24 should have a lot less data to deal with than other HD formats. It does make me wonder why we don't have more prosumer cams that shoot directly in 720P with mjpeg variable frame rates from 24-25-30-50-60 etc. Instead we have this great camera with a weird 1440x1080 interlaced & telecined format that's just a pain to get into easily editable form.

---

### Post by mariusmuja on 2007-07-27
Cinelerra does handle 720P much better, but that's not my primary reason for downsampling to 720P (you could use proxies to edit 1080P with cinelerra). As you said, I find that 720P looks almost just as good as 1080I and with 720P the resulting movies are smaller, play well even older and not not very fast computers. Also currently most HD TVs don't handle 1080P resolutions.

---

### Post by luisbg on 2007-07-29
great work rexbron! my congrats.

luisbg

---

### Post by Rexbron! on 2007-07-30
> **ArtInvent said:**
> Thanks for the tips, marius, this sounds awesome. Unfortunately I won't have the time to try this all out for a while. But so far I've done a few more mjpeg-avi's with avidemux and they are beautiful. I haven't seen the sound sync problem yet. I just did one five minute file that was composed of a bunch of short takes not more than 8-12 secs each just starting and stopping the camera, even turning it off and on at various points. The reverse pulldown filters seemed to handle it all and find the correct frames throughout.

I do find it hilarious that Cinelerra has is a setting called "Stop playback locks up". This doesn't really sound to me like something you would want to have as an 'option'  :p

One thing: you're downsampling from 1080P (well, almost)  to 720P, why exactly? Because Cinelerra handles this better? 

To tell the truth, I do think that 720P makes good sense as a format (certainly better than 1080i) and I've seen 720p that seems to look about as good as 1080i. Plus 720P24 should have a lot less data to deal with than other HD formats. It does make me wonder why we don't have more prosumer cams that shoot directly in 720P with mjpeg variable frame rates from 24-25-30-50-60 etc. Instead we have this great camera with a weird 1440x1080 interlaced & telecined format that's just a pain to get into easily editable form.

It is all specs on paper, targeted at the consumer. What really makes the difference is the quality of the optics. I originally started devling into this area because I was shooting a film and this was the camera I had available to me, but my work was kind enough to lend me the JVC HD100U. It shoots native 720/24p (none of this telecine junk, writes dup frames to tape) and has much higher quality of optics. 

Other HV20 users asked Canon to insert the telecine flag on the mpeg2 TS so that existing NLE's could handle the conversion. The responce was basically that 24p was only to give the "film look" when outputing to a TV and that if you wanted those "Advanced features" that you should buy their more expencive prosumer model. I can dig up the links if you would like, but this is just what I remember off hand.

As for the alternative work flow, I will try it out and see what my results are. If it works better and it is possible to do so, I would consider re-writing pyhdv and possibly throwing a GUI on it.

---

### Post by eugenia_loli on 2007-07-30
Personally, I would not use anything below 1920x1080 because then it would have made sense to buy a cheaper camcorder. Currently, Cinelerra, Kdenlive and other NLEs under Linux have problems loading and editing such big files. You could create proxy files, but that takes a long time, plus the pulldown time needed.

For those who need the pulldown done this way, they could use avidemux2 to do the pulldown and possibly the resize the videos to 1920x1080, and then load the files on Vegas Movie Studio Platinum 8 under Windows, which is the only *consumer-priced* NLE that is actually stable and powerful, that supports 24p.

It does not make sense to do the pulldown and then save using a lossy codec (e.g. mpeg2). My problem with avidemux2, is that it only supports a buggy version of the huffyuy lossless codec. The kind of files it creates are not read by NLEs (I tried it). It seems that the creator of avidemux2 hasn't tested enough his huffyuy implementation.

---

### Post by ddennedy on 2007-07-31
FYI, I am the dvgrab maintainer. The patches for HDV have been applied in CVS with some command line changes to improve usability. There will soon be a dvgrab3 release that includes this. CVS is at [http://sourceforge.net/projects/kino](http://sourceforge.net/projects/kino)

I have also made some changes in MLT, the engine of kdenlive, to handle various HD profiles and more framerates. Next releases of MLT and kdenlive will handle HDV, but not yet 24p. With your hints about avidemux2 filters, I will look into the realtime reverse pulldown requirements within MLT.

Eugenia, the problem we had playing back one your m2t files within ffplay, MLT, and kdenlive was not due to audio codec. Rather, there is something ffmpeg does not like in that one file we were trying. All of the others load fine! I have not yet found what ffmpeg dislikes about that one m2t.

---

### Post by Rexbron! on 2007-07-31
> **ddennedy said:**
> FYI, I am the dvgrab maintainer. The patches for HDV have been applied in CVS with some command line changes to improve usability. There will soon be a dvgrab3 release that includes this. CVS is at [http://sourceforge.net/projects/kino](http://sourceforge.net/projects/kino)

I have also made some changes in MLT, the engine of kdenlive, to handle various HD profiles and more framerates. Next releases of MLT and kdenlive will handle HDV, but not yet 24p. With your hints about avidemux2 filters, I will look into the realtime reverse pulldown requirements within MLT.

Eugenia, the problem we had playing back one your m2t files within ffplay, MLT, and kdenlive was not due to audio codec. Rather, there is something ffmpeg does not like in that one file we were trying. All of the others load fine! I have not yet found what ffmpeg dislikes about that one m2t.

Wow, that is great. I am so happy that progress is happening on this front.

We just need people to blog about it (and keep us updated) so that the information makes it out there. :)

---

### Post by ArtInvent on 2007-07-31
I am now pretty happily editing away on HDV in Cinelerra, which is pretty awesome. Thanks to Rexbron, ddennedy, mariusmuja and eugenia_loli for all the feedback and contributions.

I have settled on a resolution of 1280x720, using avi with mjpeg video and wav pcm audio. (1440x1080 is also doable.)

I set Cinelerra preferences to "Stop playback locks up" being checked as suggested. This was like a magic bullet, suddenly Cinelerra works like a well oiled clock. It has run for hours, and has only crashed a couple of times when asked to load files that it didn't like. Playback of 720p is quite good, very few dropped frames, yet the sound is well synced and it never drops out of real time. Effects like crossfades stay  show in realtime as well. (In 1440x1080, playback is choppier yet still usable.) It is usable as an editor, in other words, at full resolution without proxies on my hardware. I am now able to see that Cinelerra is a pretty powerful NLE. I was never able to use it much before this to really figure out what it can do.

I have seen the out-of-sync audio problem on some clips from Avidemux. I at first had trouble getting the utility ProjectX running to solve this, though I finally did. I include here a workaround in Cinelerra if you can't figure this step out - you can 'nudge' the audio of a track to manually sync with the picture.

So here is my workflow right now in Feisty.

1) The Canon HV-20 is set to capture '24P' footage, but telecined and encoded as standard HDV footage in 1080i.

2) I use test-mpeg2 on the command line to capture m2t (mpeg-2 transport stream) files from the camcorder firewire. I have been capturing about half (30 min) of tape at a time which results in about 5-7 GB files. 

3) Run .m2t clip through ProjectX to fix possible audio sync problems. See details in follow up post.

4) Open clip in Avidemux, setting the output as follows -
[INDENT]Output container: AVI
Video codec: MJPEG, quality 100
Audio codec: WAV, PCM
Video Filters, in order: [/INDENT]
[INDENT][LIST]
[*]crop 8 pixels from bottom, in 1440x1088, out 1440x1080
[*]Decomb Telecide, stock presets
[*]Decomb Decimate, stock presets
[*]MPlayer resize, output 1280x720, Lanczos3 resampling[/INDENT]
[/LIST]
5) It seems that such AVI files larger than ~1.5GB will not be opened by Cinelerra, and also I like to have smaller clips anyway to make editing easier. There is no auto-detection of scenes in Avidemux, but you can divy up the footage and batch it. I set in and out points (A/B) to contain a total of less than 7 minutes of footage for each file. (For 1440x1080, I stick with about 4 minutes per clip.) I save each A/B set to the Joblist. When I have finished divying up the footage file, I have maybe 4 to 8 jobs set for output. I then 'Run all jobs' from the Joblist window. For an hour of footage, this takes about 90-120 minutes on my machine.

6) I can then open Cinelerra and set the project up to match the clips, 1280x720, 23.976 fps, 16:9, etc. I load the clips. I can insert them as needed onto the AV tracks of the project timeline. Editing, transitions, effects, exposure correction, etc. Editing, sweet editing. (mariusmuja has emphasized that **23.976** is the correct framerate, even if it is rounded to 23.97 this may cause Cinelerra to introduce extraneous frames.)

7) If you have been able to fix the audio sync problem using ProjectX, skip this part, though it's a useful trick to know. Finding a clip where the sound is not synced, open the 'nudge' adjustment which is found on each track control panel (left side of the track display in Cinelerra main window. It is a small white triangle.) Set this to a small offset as needed, such as 0.21 sec or something. It is fairly easy to sync the sound visually to someone's lips this way. You can nudge either the video track or the audio tracks, either one seems to work. However, if you're working with multiple clips where the sound is off by different amounts, each clip will have to go on separate tracks as you can only nudge the whole track, not clip by clip.

8. Well, the final test is whether you can render a final edited video as output from Cinelerra. I am happy to say that I rendered my first AVI file today and it was just as intended. 

Very impressive. Can't tell you how happy this makes me. Video was the one last thing I have had to keep a Windows box around for. No more. 

Sure, I look forward to DVGrab3 and streamlining the process more. So keep up the good work, folks, and spread the word. Linux video is emerging from the stone age.

(Note: this post has been edited from it's original version.)

---

### Post by ArtInvent on 2007-08-02
The following is an extra step and it may all seem like a lot of work to figure out, but once you have it down it's not that bad. For working with the Canon HV-20, it results in about the cleanest and most easily editable HDV 24P footage possible, in your choice of either 1080 or 720 res.

********************

mariusmuja previously clued us in to using ProjectX earlier in this thread. It's quite adept at fixing the sound sync problems that may arise from doing reverse pulldown filters using only Avidemux. Apparently the footage files might have extraneous B-frames, whatever those are, and this mucks up the works. ProjectX basically just removes the offending B's and ensures that the sound stays synced. It would be nice if Avidemux could deal with this on its own or had a filter or something, but right now it just doesn't.

As noted previously the basic workflow to prep the footage is 

[LIST]
[*]Capture footage off the camera into an MPEG TS -  .m2t file.
[*]Use ProjectX to separate this file into video (m2v) and audio (mp2) files. These are separate but should be perfectly synchronized.
[*]Use Avidemux to re-combine these files and perform reverse pulldown into .avi file with Cinelerra friendly codecs.
[/LIST]

ProjectX is a rather obscure, though open source, program. It doesn't really do much other than analyzing and fixing certain inconsistencies in mpeg streams, which is what digital tv is broadcast in as well as HDV. It's not in the usual repos, and it's a cross-platform Java program. Obviously you have to have Java runtime installed first. The project web page is at
[http://sourceforge.net/projects/project-x](http://sourceforge.net/projects/project-x)
Though there is not much info there as to actually how to use it. There is a thread on these forums as to how to install it and run it - 
[http://ubuntuforums.org/showthread.php?t=203330&highlight=install+projectx](http://ubuntuforums.org/showthread.php?t=203330&highlight=install+projectx)

It took me a while to get it going, and apparently it doesn't play well with Beryl/Compiz. Anyway, I finally got it running (GUI). It's a very cluttered screen for what it does. I guess it has a lot of options that don't seem to be documented anywhere. To cut to the chase, basically all you do is, near the bottom left of the screen, add your footage file to the 'Filename' list by hitting the plus sign. If you add more than one file to this list, they will all be joined together into one set of two output files (video and audio). So I just do one at a time.

Then you can hit the 'prepare. . .' button. A second screen comes up with the processing options. You can just make sure the default 'demux' button is checked off and hit the big pause/play button. The text info screen will show you the errors in the file it is correcting etc. You should end up with an .m2v video file and an .mp2 audio file.

It also took me a while to figure out how to open both of these files simultaneously in Avidemux. First you open the .m2v video file. Then, in the Audio menu, select Main Audio Track, then Audio Source - Exterior MP3, then you can select the appropriate .mp2 file. 

Proceeding with Avidemux after this is exactly as described previously in this thread, with cropping, de-telecine, and the correct codecs applied, etc.

---

### Post by JayEmm on 2007-08-04
Hi guys,

I am a recent ubuntu convert, have been learning the ways of the free force on a "server" (read not v. important) PC and am now convinced (mainly by a very crashy vista on my dell).

I chose Ubuntu Studio as my variant, as I'm a film student.

I really like the sound of this pyHDV, but I am a bit of a dingbat still when it comes to linux. Could someone give me really stupid, idiot-proof command-line instructions for installing it?

Also... how do I upgrade the current version of dvgrab to the CVS? My current one is 1.8, which I guess is not the CVS which incorporates HDV capture...


Thanks guys,
James Martin.

---

### Post by JayEmm on 2007-08-04
OK, part fixed my own problem

I've updated dvgrab to 2.1 using the usual ./configure make etc

but I can't for the life of me get it to update with the patch, i installed the patch into my install dir then re-installed it with config/make/make install but it still won't appear.

Also.. where can ya get pyHDV from - the link doesn't work!


Thanks guys.

---

### Post by eugenia_loli on 2007-08-07
[http://aehunter.net/Files/Ubuntu/pyHDV-0.1.tar.gz](http://aehunter.net/Files/Ubuntu/pyHDV-0.1.tar.gz)

ArtInvent, can Cinelerra read the Avidemux files if you actually export as HuffYuv instead of MJPEG?

---

### Post by jkwarras on 2007-08-08
Afaik, cinelerra doesn't read huffyuv videos.

[http://cvs.cinelerra.org/soc.php](http://cvs.cinelerra.org/soc.php)

---

### Post by ddennedy on 2007-08-08
update: dvgrab 3.0 with HDV support is released on [http://www.kinodv.org/](http://www.kinodv.org/)
Read the man page for difference between options with the patches.

MLT, the subsystem for kdenlive, v0.2.4 is released with HDV support. kdenlive 0.5 will be out in a matter of days. This, however, does not yet support the reverse pulldown processing. However, I have been reviewing the original source of the avidemux filters (Donald Graft's telecide+decimate) referenced in this thread. Goals for the next major release include these filters as well as "pass-through," which means, if the project input and output are configured the same (e.g. HDV 720p in/out) then it will try not to re-render/encode unedited portions.

---

### Post by ArtInvent on 2007-08-08
I tried HuffYUV early on and couldn't get it to load in Cinelerra. After that I stuck with mjpeg. As the link indicates, Cinelerra-CV is working on supporting this codec but whether that will make it into the next release is unclear.

The attraction obviously with HuffYUV is that it's a lossless codec, and you would avoid re-compressing the image so many times during the workflow. By shooting footage in mpeg2, then recompressing into mjpeg, editing, and finally rendering into presumably some final codec - my workflow at the moment - the final image will have been compressed three times. Plus, the three codecs may be completely different compression schemes. Obviously it would be better to try and eliminate at least the middle re-compression if possible.

There might be a slight amount of inter-frame 'noise' noticeable using mjpeg. It looks a little like movie film grain, but it's really only visible in the moving image. I now make sure to set the mjpeg quality to 100 in Avidemux and that seems to minimize it. 

The wonder is that the image still looks pretty darn good even with the three compressions. Maybe this is partly because we are so used to looking at movie film which has grain. 

I think the reason for the 'grain' is the same reason that mjpeg is easy to edit. Each individual frame is compressed using a jpeg algorithm. The block compression may differ slightly in each frame, so in 120 frames of blue sky with clouds, for instance, you may see this variation visible as noise. mjpeg has less ability to minimize this inter-frame noise.

So this may also be another reason why the HDV (and DVD and digital broadcast TV) uses mpeg-2 compression even though it is harder to edit. A long-group-of-pictures codec compares an entire group of frames and notes the differences between them. This not only makes the compression more efficient, it also naturally blocks this interframe noise. Broad areas of the same color look the same in successive frames, because the data is pretty much the same data.

---

### Post by ArtInvent on 2007-08-08
Fantastic ddennedy. I will probably wait for a deb package or til something is in the repos to try it, since my capture script works well. Question for you - can you recommend a particular repo(s) where a Feisty package might appear earlier rather than later? For dvgrab and kdenlive both.

If kdenlive is going to support hdv - a major step forward. Though you said it will still not support 24p -?

edit - actually, I just looked, and kdenlive 0.5 is in a repo in my Synaptic. Downloading as I write. Cool.

edit - trying to install, mlt failed to install. It's v0.2.3+svn20070720~3v1ubuntu0 (feisty). Synaptic gives the error - 
E: /var/cache/apt/archives/mlt_0.2.3+svn20070720~3v1ubuntu0_i386.deb: trying to overwrite `/usr/share/mlt/packages.dat', which is also in package libmlt0.2.2-data

??

---

### Post by mariusmuja on 2007-08-09
That's great news ddennedy.

I've been trying to see which lossless codecs can be used with cinelerra. So far I've had success only with raw YV12 (YUV 4:2:0). Cinelerra is *much* faster when using this format, for example 1080p in YV12 format works faster that 720p in MJPEG format. The drawback is the larger file sizes, approximately double than with huffyuv and a lot larger (obviously) than with MJPEG.

To convert to YV12 and perform the inverse pulldown I use mplayer:

mplayer input.m2v -vo yuv4mpeg:file=output.yuv -vf pullup -fps 24000/1001 -ao null

where input.m2v is the .m2v file that I obtain by processing the .m2t from the camcorder with projectx.

As I said, using YV12 files in cinelerra works great, but there is an annoying bug: the small thumbnails on the timeline are black, so it's more difficult to jump to the right place in the movie when editing, everything else seems to work fine. It seems that the source of this bug is the fact that cinelerra doesn't use correctly ffmpeg's swscaler functionality. I will look more into this and post back if I find a solution.

---

### Post by jkwarras on 2007-08-09
> **ddennedy said:**
> update: dvgrab 3.0 with HDV support is released on [http://www.kinodv.org/](http://www.kinodv.org/)
Read the man page for difference between options with the patches.


Wow, great news. It's so nice to know that HDV can be edited in linux. Thanks :) 

Sorry, off-topic. I wonder if someone could be interested in making a NLE in linux work directly with mxf DVCPRO HD files (that panasonic P2 HVX200 is using). Mplayer handles them, but only if ffmpeg can decode it (afaik DV, HDV and DV50). Afaik, DVCPRO HD (aka DV100) can't be decode in linux atm.

---

### Post by Rexbron! on 2007-08-10
> **ddennedy said:**
> update: dvgrab 3.0 with HDV support is released on [http://www.kinodv.org/](http://www.kinodv.org/)
Read the man page for difference between options with the patches.

MLT, the subsystem for kdenlive, v0.2.4 is released with HDV support. kdenlive 0.5 will be out in a matter of days. This, however, does not yet support the reverse pulldown processing. However, I have been reviewing the original source of the avidemux filters (Donald Graft's telecide+decimate) referenced in this thread. Goals for the next major release include these filters as well as "pass-through," which means, if the project input and output are configured the same (e.g. HDV 720p in/out) then it will try not to re-render/encode unedited portions.

Wow, things are picking up speed. Nice.

> **ArtInvent said:**
> Fantastic ddennedy. I will probably wait for a deb package or til something is in the repos to try it, since my capture script works well. Question for you - can you recommend a particular repo(s) where a Feisty package might appear earlier rather than later? For dvgrab and kdenlive both.

If kdenlive is going to support hdv - a major step forward. Though you said it will still not support 24p -?

edit - actually, I just looked, and kdenlive 0.5 is in a repo in my Synaptic. Downloading as I write. Cool.

edit - trying to install, mlt failed to install. It's v0.2.3+svn20070720~3v1ubuntu0 (feisty). Synaptic gives the error - 
E: /var/cache/apt/archives/mlt_0.2.3+svn20070720~3v1ubuntu0_i386.deb: trying to overwrite `/usr/share/mlt/packages.dat', which is also in package libmlt0.2.2-data

??

It is unlikely that there will be an SRU for kino, dvgrab or kdenlive, but that does not mean we can't push to get it into gutsy.

See these two bug reports:

[https://bugs.launchpad.net/ubuntu/+source/kino/+bug/77000](https://bugs.launchpad.net/ubuntu/+source/kino/+bug/77000)
[https://bugs.launchpad.net/debian/+source/dvgrab/+bug/131561](https://bugs.launchpad.net/debian/+source/dvgrab/+bug/131561)

As I interperate it, kdenlive 0.5 will support 24p video files, it just will not be able to remove the pulldown on capture. ddennedy correct me if I am wrong. 


As for kdenlive 0.5, it is not listed as released on their main site, so what repo are you pulling that package from? Email the repo maintainer or if it is an Ubuntu package, file a bug report.

Update: Looks like we have a gutsy package available for testing, have a look at the dvgrab bug report. :)

---

### Post by ArtInvent on 2007-09-29
I finally am able to try out Kdenlive in Feisty. It gave errors on trying to install. I finally had to remove my (older) version of MLT and a couple of it's dependent libs. Then installed the later version of MLT, MLT++ , and finally Kdenlive would install and run.

An first it looks promising. It loads my 720p24 deinterlaced AVI's from the Canon HV-20 just fine. I can trim them and add them to the timeline. It will load the original camera footage m2t files but it takes a while, during which it seems maybe hung, but it's not. Moreover, it will also load HuffYUV encoded files made with Avidemux. Cinelerra can't load these files. HuffYUV is basically lossless, so that should beat the mjpeg codec which was the best Cinelerra can handle. 

However, support for 24p is not there. I could set project to HDV 1080i60, but not 24p. The framerate could not be changed manually. The parameters of the preset formats can't be altered. Then I tried to set the project to 720p30 or 720p25 but this caused the program to crash. This seems like a minor fix and hopefully they will address it soon. But until it's fixed I can't really use the program.

Kdenlive looks like it's 95% of the way there so I will be keeping an eye on it. The interface is clean, attractive, simple and logical. It doesn't have as many bells and whistles as Cinelerra, but on the other hand it looks like it's advancing at a more deliberate pace and does a couple things Cinelerra can't.

Next, I tried capturing within Kdenlive, but I've not been able to install the latest DVGrab 3 into Feisty from repos. It looks like both DVGrab and Kdenlive will have fully updated packages available for Gutsy which is just a few weeks off. That will hopefully mean that straight HDV grabbing and editing should be possible in one app (though for us processing 24p footage from the Canon it will still mean jumping through a couple more hoops.)

---

### Post by eugenia_loli on 2007-12-26
Here are three more ways to remove pulldown and encode using the lossless codec Huffyuv, in case you don't want to use mjpeg or ljpeg. I hope that Rexbron! updates hi pyHDV script to include these. For Huffyuv, adjustment of the A/V sync using an audio delay is necessary. Additionally, only mplayer "understands" that the created files are 16:9, KDEnLive requires a patch to get it right (it thinks they are 4:3).

1. This is a two pass method for the lossless Huffyuv codec. The two passes take more time, but they create smaller files. The created files only work with Linux (tested with KDEnLive), the Windows version of Huffyuv can't read these files because they are on a different colorspace (I tried with Sony Vegas, it showed bad colors).

```
mencoder FILENAME.m2t -aspect 16:9 -mc 0 -noskip -fps 30000/1001 -delay -0.222 -oac pcm -vf pullup,softskip,harddup,scale=1440:1080 -ofps 24000/1001 -ovc lavc -lavcopts vcodec=huffyuv:pred=2:format=422P:vstrict=-1:aspect=16/9:vpass=1 -o huff.avi

mencoder FILENAME.m2t -aspect 16:9 -mc 0 -noskip -fps 30000/1001 -delay -0.222 -oac pcm -vf pullup,softskip,harddup,scale=1440:1080 -ofps 24000/1001 -ovc lavc -lavcopts vcodec=huffyuv:pred=2:format=422P:vstrict=-1:aspect=16/9:vpass=2 -o huff.avi
```

2. Same as above, but with only one pass, faster encoding, but bigger ifles.

```
mencoder FILENAME.m2t -aspect 16:9 -mc 0 -noskip -fps 30000/1001 -delay -0.222 -oac pcm -vf pullup,softskip,harddup,scale=1440:1080 -ofps 24000/1001 -ovc lavc -lavcopts vcodec=huffyuv:pred=2:format=422P:vstrict=-1:aspect=16/9 -o huff.avi
```

3. This one uses prediction=0, which creates "smaller" Huffyuv files, that are compatible with both the Windows and Linux Huffyuv version. I would recommend you go with this version if you want to use Huffyuv.

```
mencoder FILENAME.m2t -aspect 16:9 -mc 0 -noskip -fps 30000/1001 -delay -0.222 -oac pcm -vf pullup,softskip,harddup,scale=1440:1080 -ofps 24000/1001 -ovc lavc -lavcopts vcodec=huffyuv:pred=0:format=422P:vstrict=-1:aspect=16/9 -o huff.avi
```

---

### Post by gigoligno on 2008-01-24
I need to convert HDV video to images (so far, I use mplayer), but the output images have the incorrect resolution of 1440x1080 instead of 1920x1080px. 
I'd appreciate very much if somebody could give me a hint how this is done..

I read in the video with dvgrab 3.0, resulting in a .m2t file.
```

dvgrab -f hdv

```

mplayer 1.0pre8-3.3.5 plays the file in the correct format (1920x1080), but gives strange output saying something about a detected format of 1440x1080. 

```

Playing dvgrab-001.m2t.
TS file format detected.
DEMUX OPEN, AUDIO_ID: -1, VIDEO_ID: -1, SUBTITLE_ID: -2,
PROBING UP TO 2000000, PROG: 0
VIDEO MPEG2(pid=2064)AUDIO MPA(pid=2068) NO SUBS (yet)!  PROGRAM N. 0
Opened TS demuxer, audio: 50(pid 2068), video: 10000002(pid 2064)...POS=403824, PROBE=2000000
VIDEO:  MPEG2  1440x1080  (aspect 3)  25.000 fps  25000.0 kbps (3125.0 kbyte/s)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 1440 x 1080 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1440 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1440x1080 => 1920x1080 Planar YV12
aspect: Warning: no suitable new res found!
A:   2.6 V:   2.6 A-V:  0.003 ct:  0.040  43/ 43 56%  3%  3.3% 1 0
Exiting... (Quit)

```

However, when I try to output images (e.g., jpg) using mplayer, the resulting images have a resolution of 1440x1080px.

```

mplayer -vo jpeg -nosound dvgrab-001.m2t

MPlayer 1.0pre8-3.3.5 (C) 2000-2006 MPlayer Team
CPU:               Intel(R) Pentium(R) 4 CPU 3.20GHz (Family: 15, Model: 6, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.

Playing dvgrab-001.m2t.
TS file format detected.
DEMUX OPEN, AUDIO_ID: -2, VIDEO_ID: -1, SUBTITLE_ID: -2,
PROBING UP TO 2000000, PROG: 0
VIDEO MPEG2(pid=2064)NO AUDIO!  NO SUBS (yet)!  PROGRAM N. 0
Opened TS demuxer, audio: ffffffff(pid -2), video: 10000002(pid 2064)...POS=403824, PROBE=2000000
VIDEO:  MPEG2  1440x1080  (aspect 3)  25.000 fps  25000.0 kbps (3125.0 kbyte/s)
jpeg: Parsing suboptions.
jpeg: Progressive JPEG disabled.
jpeg: Baseline JPEG enabled.
jpeg: Suboptions parsed OK.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 1440 x 1080 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 1440 x 1080 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
No accelerated colorspace conversion found
SwScaler: using unscaled Planar YV12 -> RGB 24-bit special converter
VO: [jpeg] 1440x1080 => 1920x1080 RGB 24-bit
jpeg: . - Output directory already exists and is writable.
TS_PARSE: COULDN'T SYNC4%  0.0% 0 0
V:   3.0  54/ 54 49% 404%  0.0% 0 0

Exiting... (End of file)

```

---

### Post by Rexbron! on 2008-01-24
> **gigoligno said:**
> I need to convert HDV video to images (so far, I use mplayer), but the output images have the incorrect resolution of 1440x1080 instead of 1920x1080px. 
I'd appreciate very much if somebody could give me a hint how this is done..


No, that is the correct resolution for HDV video. HDV (and all DV) does not use square pixels.

---

### Post by gigoligno on 2008-01-24
> **Rexbron! said:**
> No, that is the correct resolution for HDV video. HDV (and all DV) does not use square pixels.
Thanks for the answer. However, I am not sure if I understood your answer correctly. 
Is your statement that the resolution of 1440x1080px for the conversion is correct? 
If so, why is the video played in 1920x1080px then (and seem to be the "right" resolution)? Do you say that 1440x1080 is the actual resolution and is just artificially blown up to 1920? Hence I should take my 1440px images and blow them up (e.g., by interpolation)?

---

### Post by gigoligno on 2008-01-24
Ok, got it now -- since the pixels are not square when recorded, but square when displayed (after grabbing), the format ist 1440x1080 (physical number of pixels) instead of 1920x1080. So, I have to supersample the images to get the same format..

---

### Post by Rexbron! on 2008-01-24
Take a look at [http://en.wikipedia.org/wiki/HDV#Resolution_and_aspect_ratio](http://en.wikipedia.org/wiki/HDV#Resolution_and_aspect_ratio)

---

### Post by kokachev on 2008-02-21
Guys.
Do you have any A-V sync problems, while transoding to lower resolution avi files 1080i m2t files from HV20 NTSC?
I try to create proxy files, with 720x540 resolution and mjpeg codec. To make story shorter below is my command line:
```
mencoder dvgrab-022.m2t -mc 0 -noskip -ovc lavc -lavcopts vcodec=mjpeg -vf scale=720:540 -oac pcm  -o dvgrab-022.avi
```
If I remove -mc 0 -noskip options, then I receive "Duplicate frames " for every 10th frame up to frame 151. After that frame - everything is fine (A-V sync is correct),  but for first 150 frames I have A-V desync. 

And I have one more question: is there any other command line tool like projectx, that can demux audio from m2t file.
Thanks!

---

