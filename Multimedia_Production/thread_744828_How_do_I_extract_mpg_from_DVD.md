---
title: "How do I extract mpg from DVD?"
date: 2008-04-04
forum: Multimedia Production
---

### Post by elvinatom on 2008-04-04
Hello Forum,
I searched the forum and googled for quite some time to no eval ...
I've got a bunch of DVD iso files and I'm running severely out of space, so I decided to ditch the extras and menus and keep only the title that contains the actual movie (with all languages and subtitles).  There seems to be a lot of advise for DVD to divx, mpg4, etc, but an easy solution for a simple title extraction to mpg I couldn't find.  I'm not scared of cli - in fact I prefer it, but any "simple and quick" solution would be great.  Does anybody know a program that gets the job done?

Btw, I tried k9copy and it works great to rip DVD to iso, but when I rip a title to ... well ... anything, it fails every time after a few seconds (just jumps from 3% to 96% and then hangs there forever).  If I could get that to work, that would be cool.

Thanks in advance!

---

### Post by aeiah on 2008-04-04
you should be able to use acidrip to do it. usually its used to encode to xvid, x264 etc but im pretty sure you can rip to mpeg without re-encoding.

you can view the command line that acidrip will use for the file and modify it as you please for multiple files. avid rip does have a queue function, but i dont think you can select more than one input, so the queue is only useful for ripping episodes etc

---

### Post by hurtstotalktoyou on 2008-04-04
DVD Decrypter works great in Wine, as long as you set it to NT 4.0 compatibility mode.  Although I've never attempted this myself, you *should* be able to demux the A+V streams in IFO mode, and then recombine them as MPEG PS in Avidemux.

This is actually a pretty good question for a HOWTO thread.  I think I'm going to check this out further and then get back to you.

---

### Post by elvinatom on 2008-04-05
thank you, hurtstotalktoyou ...
I actually have the means to do it with tmpgenc on my wifes winxp box, but I'm seeking a linux solution for it as I want to move away from Billy's "stuff" and "stuff" that builds on it.  I appreciate you input though and yes, I loved dvd decrypter at the time.

aeiah,
that's a good starting point - will definitely look into it this weekend.

Just an update on my research for whoever seeks the same goal as me.  Since vobs contain the actual mpg-stream but have a 1GB limit, I did some testing with almost complete success - concatenate them:
```
cat vts01_1.vob vts01_2.vob vts01_3.vob vts01_4.vob vts01_5.vob > extracted_movie.mpeg
```
Works great, all audio tracks and subtitles and whatnot, but there are some issues with playback - for example ...
total duration of the move is displayed as 40 hour or 1.06 hour depending on player.
player sometimes exits (crashes?) while seeking.
I think there might be an issue related to the recombination, or maybe the vobs have simply a structure of their own that need to be modified to fit ".mpg / .mpeg" files.  I'm not sure yet but I keep investigating.

---

### Post by hurtstotalktoyou on 2008-04-05
Well, there is something else you can try--again, with DVD Decrypter as the key.

You may not actually have to rip mpegs.  If you rip individual VOB files, you may be able to treat them the same as mpegs in dvdauthor, or whatever other authoring software you use.

In DVD Decrypter, go to Mode and select IFO.  Then go to Tools > Settings > IFO Mode and select File Splitting by Chapter.  Then decrypt each title, and you'll get a separate VOB for each chapter.

Then see if dvdauthor can handle those VOBs.

---

### Post by hurtstotalktoyou on 2008-04-05
Okay, I just tested it and it *does* work.  You do not need to extract an mpg stream from the VOBs.  Instead, you can just rip VOBs, split as you like them, and recombine them using dvdauthor into a custom DVD.  These instructions are written in ultra-newbie style so that this thread can benefit future viewers.

Here's how to do it:

1.  You've got to install some software, first.  In Synaptic Package Manager, make sure the following packages are installed:  dvdauthor, wine, mkisofs, and brasero.

2.  Install [SetupDVDDecrypter_3.5.4.0.exe](http://fileforum.betanews.com/sendfile/1011845169/1/SetupDVDDecrypter_3.5.4.0.exe) in Wine.

3.  Change the DVD Decrypter compatibility mode to NT 4.0.  If you don't know how to do this, just follow these instructions:  Go to Applications > Wine > Configure Wine > Applications and click on "Add Application..."  Navigate to drive_c/Program Files/DVD Decrypter/ and open DVDDecrypter.exe.  This will send you back to the Wine configuration window, where you must click on the DVDDecrypter.exe file you just added to the list.  Change the "Windows" option from "Global settings" (or whatever it happens to say by default) to "Windows NT 4.0".  Then just click "OK" to exit.

4.  Run DVD Decrypter.  Go to the "Mode" menu and select "IFO".

5.  Go to Tools > Settings > IFO Mode, and where it says "File Splitting" (or sometimes just "File Splitt") select "by chapter".  Click "OK" to exit that window.

6.  In the Input tab, find and highlight the title you wish to extract.

7.  Click on the Stream Processing tab and check the "enable stream processing" box.  Do not select "demux" or "raw"--just keep it on the "direct stream" option.  However, you should unselect all but just one audio and video streams.  Sometimes there will only be one of each, in which case you can probably skip this step.

PLEASE NOTE:  You could probably skip step #7 even if you have multiple A/V/subtitle streams.  However, I have not tested this, personally, so it could lead to problems.  Feel free to play with that.

8.  Go to File and click on "Decrypt" (or just click the big button in the lower left corner).  When the VOBs are done decrypting, exist DVD Decrypter.

9.  Open Terminal and cd to the directory you just ripped to.  This will be something like "cd ~/.wine/drive_c/DVDTITLE/VIDEO_TS".  Make sure you are actually in the VIDEO_TS folder, and not just the DVDTITLE folder.

10.  In Terminal, type the following commands:

> dvdauthor -o ~/Desktop/dvd/ -t firstvob.VOB secondvob.VOB thirdvob.VOB

dvdauthor -o ~/Desktop/dvd/ -T

mkisofs -dvd-video -o ~/Desktop/discimage.iso ~/Desktop/dvd

Please note you will need to know what those VOB filenames actually are.  You can find out by typing "dir" in terminal after you cd to the VIDEO_TS folder.  Also note that all terminal commands are [case sensitive](http://en.wikipedia.org/wiki/Case-sensitive).

This will create a burnable disc image of the new title on your desktop.

11.  Run Brasero (Applications > Sound & Video > Brasero Disc Burning Application), select "Burn image", and tell it to burn the discimage.iso file you just made.

That should do it.

---

### Post by vanadium on 2008-04-05
I am not sure whether you will that significantly gain disk space by "cleaning" your DVDs from the menus and extras. You will be doing a lot of effort to gain perhaps 10-15% disk space. In contrast, transcoding to mpeg4 (xvid) would reduce your disk usage by a factor of at least 4, keeping near DVD quality if you encode properly.

That said, I have a suggestion for your current procedure. You could use vobcopy instead of dvddecryptor to extract the VOBs. It is also a command line tool that allows to extract a single title from the dvd to a single vob file. As an added benefit, you would be working with only Linux and free software.

---

### Post by hurtstotalktoyou on 2008-04-05
> **vanadium said:**
> I am not sure whether you will that significantly gain disk space by "cleaning" your DVDs from the menus and extras.  You will be doing a lot of effort to gain perhaps 10-15% disk space. 

Oh, it would probably be less than that.  I bet out of a 4.7GB DVD less than 50MB is menu data.  No, I think what he wants to do is reauthor DVDs without losing quality, and without wasting time waiting on the CPU to transcode.

Also, menus can be damned annoying.  When I make custom DVDs, I *never* use menus.  I just want something I can pop in my DVD player and watch from beginning to end.

> In contrast, transcoding to mpeg4 (xvid) would reduce your disk usage by a factor of at least 4, keeping near DVD quality if you encode properly.

That said, I have a suggestion for your current procedure. You could use vobcopy instead of dvddecryptor to extract the VOBs. It is also a command line tool that allows to extract a single title from the dvd to a single vob file. As an added benefit, you would be working with only Linux and free software.

Vobcopy would definitely be worth learning, but I don't think it can break encryption on commercial DVDs.  Or can it?

---

### Post by vanadium on 2008-04-06
vobcopy does use CSS descrambling if the libraries are installed on your system.

---

### Post by hurtstotalktoyou on 2008-04-06
> **vanadium said:**
> vobcopy does use CSS descrambling if the libraries are installed on your system.

Please explain.  If this is true, I would like to make the switch so that I can use native Linux software instead of a Windows app in Wine.

---

### Post by vanadium on 2008-04-07
If you can play commercial encrypted DVD in Ubuntu, then also vobcopy or any other tool that uses libdvdread will be able to decrypt them. Also mplayer can be used, but the command line syntax is more complex.

---

### Post by hurtstotalktoyou on 2008-04-07
> **vanadium said:**
> If you can play commercial encrypted DVD in Ubuntu, then also vobcopy or any other tool that uses libdvdread will be able to decrypt them. Also mplayer can be used, but the command line syntax is more complex.

I cannot play commercial DVDs in Ubuntu.

---

### Post by liveB on 2008-04-07
deleted

---

### Post by arman.haghi on 2008-04-08
> **elvinatom said:**
> Hello Forum,
I searched the forum and googled for quite some time to no eval ...
I've got a bunch of DVD iso files and I'm running severely out of space, so I decided to ditch the extras and menus and keep only the title that contains the actual movie (with all languages and subtitles).  There seems to be a lot of advise for DVD to divx, mpg4, etc, but an easy solution for a simple title extraction to mpg I couldn't find.  I'm not scared of cli - in fact I prefer it, but any "simple and quick" solution would be great.  Does anybody know a program that gets the job done?

Btw, I tried k9copy and it works great to rip DVD to iso, but when I rip a title to ... well ... anything, it fails every time after a few seconds (just jumps from 3% to 96% and then hangs there forever).  If I could get that to work, that would be cool.

Thanks in advance!

Hey Mate,

I use DVD::RIP, have had great results and its easy to use.

I'm quite sure it was available through Synaptic, but incase here's the website:

[http://exit1.org/dvdrip/](http://exit1.org/dvdrip/)

I generally tend to use Xvid and a 2pass encode. Let me know if this is of use/ you have other questions.

Cheers,

Arman.

---

### Post by Prefader on 2008-04-08
Transcode (apt-get install transcode) does this quite well.

```
tccat -i /dev/dvd -T [titlenumber],-1 -L >out.vob
```

You can substitute any mounted iso (sudo mount -o loop /path/to/disc.iso /path/to/mount/point) for the dev node.

---

### Post by elvinatom on 2008-04-11
Thank you all for your helpful advise, I'll work my way through them to get the most convenient solution that works for me ...

BTW, I do gain quite some space by discarding the "extras" on many DVDs; I have many commercial DVD9s that contain a 5Gig movie - thats 4Gigs less right there, but I actually consider now to transcode a few big ones to some mpg4 format, as the resolution doesn't look all that great on my 720p TV, even in un-re-encoded playback.

So, does anyone know why k9copy fails as mentioned on page1?

---

