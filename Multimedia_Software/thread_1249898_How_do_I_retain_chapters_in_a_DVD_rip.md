---
title: "How do I retain chapters in a DVD rip?"
date: 2009-08-25
forum: Multimedia Software
---

### Post by jmail524 on 2009-08-25
Hi everyone.

I would like to rip my DVD collection to my hard drive for quick access without having to find the DVD, put it into the player and wait for the #$*$!# FBI/Interpol/etc warning to go by before I can start watching the DVD that I PURCHASED with MY MONEY. (Sorry if I'm a little cranky.)

Becuase I'm concerned with the quality of the rip I have been using AcidRip and set it to "copy", not re-encode, the DVD to a ".mpg" file.  The problem is that I lose the chapter marks in the process.  The mpg file plays as a single chapter.  I have looked through AcidRip's options (to the best of my abilities) and I can't find any options to retain the chapter markers.  After doing some research on the web, I think I have found that the ".mpg" file container doesn't have chapter capabilities.

So I turned to the program Handbrake because it supports the ".mkv" file container.  Research on mkv indicates that it supports any video/audio codec and chapter markers.  But, Handbrake will not just copy the MPEG2 stream into the mkv container with out re-encoding it to some other format (ie, H.264, XviD, FFMEP (MPEG-4)).

So now I ask the grand collective of these forums.  Is there a way for me to rip a DVD (without re-encoding the video/audio streams) and putting it into the mkv (or any other suitable continer) while retaining the chapter markers from the DVD.  It could be an GUI app, CLI or even a Windows app that I can run under WINE.

Thanks.
Brian.

---

### Post by tubasoldier on 2009-08-25
Perhaps you could try k9copy and use it to keep the DVD structure in tact. It can copy exactly what is on the disk or only the chapters you want.

---

### Post by jmail524 on 2009-08-26
Hi tubasoldier,

Thanks for the quick reply.  I took you suggestion and tried K9Copy.  That did exactly what I needed. Thanks.

For anyone who might care, here is the procedure I used to create a ".mkv" file with chapters using a bit-perfect rip from a DVD. (I hope this is correct. Doing this from memory.)

1) Start-up the K9Copy application and insert the DVD you wish to rip.

2) Configure K9Copy to copy strems through FFMPEG.
    a) Click on the "Configure k9copy" button in the top menubar.
    b) Go into the MEncoder section.
    c) Under the "Video Codecs" tab, click on the (+ Add) button near the bottom left of the screen.  This creates a new profile.
    d) For the line "label", type in a name for the new settings profile. (I called it "MKV Copy".)
    e) Under the "one pass" setting, enter "-vcodec copy". (This is FFMPEG's copy video stream function and doesn't re-encode the video.)
    f) Near the bottom of the window, change the "encoder" setting to "ffmpeg".
    g) Next click on the "Audio codecs" tab.
    h) Again, at the bottom left click on (+ Add) to create a new profile.
    i) Under the line "label", type in a name for the new settings profile. (I used "MKV Copy" again)
    j) Under the "options" setting, enter "-acodec copy". (This FFMPEG's command to copy the audio stream, not re-encode it.)
    k) Again, at the bottom of the window change the "encoder" setting to "ffmpeg".
    l)  Now click on the (OK) button to save the changes and return to the main K9Copy window.

3) With the DVD you want to copy already in the drive.  At the top of the screen, change the "input device" option to point to the drive that has you DVD. (This probably only applies to machines with more that one DVD drive.)

4) Click the "Open" button in the main menubar to read the contents of the DVD.

5) Now select the chapters, audio tracks, etc in the main selection window that you want included in your ripped file.

6) Now change the encoding options to copy the video and not re-encode it.
    a) To the center-right of the screen, set "Encoder" to "ffmpeg".
    b) Under the "Video" tab, select the newly created video profile. (In my case "MKV Copy".)
    c) Now go under the "Audio" tab and again select the new profile. (Again, in my case "MKV Copy". I don't know if any of the other settings under the "Video" and "Audio" tabs have any effect on the process, I just left them alone.)

7) Now click on the "Create MPEG-4" botton in the top menubar.
    a) At the bottom of the save window, change the "Filter:" to "Matroska (*.mkv)" (That is the only container that worked for me when using MPEG2 with chapters.)
    b) Browse to the location you want to save the file and give it a name.
    c) At last, click on the (Save) button to start the process (and watch the video frames just fly by.)

Hopefully you eventually get a message that says titles have been successfully encoded. You should now have a file on your computer that retained the original chapter information from the DVD with a perfect 1:1 copy of the video and audio streams.  (Not every video player can select chapters, I use VLC and it work pretty well.)

Best of luck and thanks.
Brian

---

### Post by sawyer11 on 2009-08-26
With this [dvd converter]("http://www.applemacvideo.com/mac-video-converter-pro.html#119") you could check the titles and chapters you want to rip or not.

---

### Post by randywilharm on 2009-08-27
VLC can work with .mkv files too. I just did it today
with the capture option.

---

### Post by jmail524 on 2009-08-27
Hi sawyer11,

I looked at the DVD converter program you mentioned.  It looks like it is only available for Mac's.  I am unsure about the feasibility of running Mac software under Linux. (I use the WINE project, which allows me to run almost all of my Windows software, but I am unaware of a Mac API "emulator" for Linux.)

Hey randywilharm,

I was unaware that chapter markers were retained with the capture option of VLC.  This is a moot point for me however, because VLC always crashes on me when I try to capture. (I have had this problem over 4 versions of Ubuntu and 2 versions of VLC under Windows. Just bad karma I guess.)

I do appreciate both of the suggestions.

I have found another alternative (possibly).  There is an app call MakeMKV that has a beta version for Linux available. (You must compile it yourself.)  It seems to act similarly to what I was doing throught K9Copy, but a bit more streamlined.  I just got done compiling it and have tested it out on one DVD, so far so good. I'll play around with it and try to report back later.

Thanks.
Brian

---

### Post by lisati on 2009-08-27
I'm thankful for the success reported with k9copy, not having used it much. (I do most of my DVD & video stuff with assorted tools in Windows, including DVDshrink, which can reauthor and retain chapters and almost feel like a traitor to Ubuntu when I do so)

---

### Post by Mister.Vash on 2009-08-28
I noticed you mentioned earlier, "Becuase I'm concerned with the quality of the rip"

Have you thought of ripping to an iso output?  If you have enough space to do that, your not going to loose anything.  It's basically copying the entire disk to a file without changing he data.  You can play the iso files directly in to a lot of the software players, vlc, etc. The pluses are that it's actually what is on the disc, the downside is the size. - Just bringing up another option if you weren't aware of doing it that way

---

### Post by jmail524 on 2009-08-28
Hello Mister.Vash,

I thought about ripping the DVDs to ISO files.  The problem with that comes from how I want to organize and use the files.  For instance,  I rip each episode of a TV series DVD into a separate file because I have a frontend application that catalogs and play the files. (I know I'm being picky.)

Actually, this new MakeMKV ([http://www.makemkv.com](http://www.makemkv.com)) application I found seems to do the trick.  It allows me to rip each episode to a separate MKV file and it retains the chapter information plus multiple audio tracks.  Right know the linux version is in beta and you have to build it from source yourself,  but it seems to work without any problems. (Although I have only ripped about 2 DVDs so far: a TV show and a concert.)

Thanks.
Brian

---

### Post by gatecrasher on 2009-10-09
I'm not seeing any of the ffmpeg references that you describe in your k9 configuration howto. Which version are you using? Thanks!

---

