---
title: "giPlayer : a wrapper for get_iplayer"
date: 2010-09-14
forum: Multimedia Software
---

### Post by mr bob on 2010-09-14
Hi I've written a little python/gtk GUI wrapper for get_iplayer (the command line utility to download BBC programmes).

If anybody would like to try the beta version, I have created a deb package and you can download it from:

[http://sourceforge.net/projects/giplayer/files/]("http://sourceforge.net/projects/giplayer/files/")

The source is also on sourceforge if you wish to play about with the code and the GTK user interface too. I wrote it as a small project to try out my first python code.

---

### Post by ron999 on 2010-09-14
Hi
Thanks for this.
It's working OK for me with 9.10 Karmic Koala.
Just the job. :D

---

### Post by mr bob on 2010-09-14
That's great! :D

---

### Post by nickmcg on 2010-12-20
Sorry mr bob, unsatisfied dependency in 10.10

Dependency is not satisfiable: python-gnome2-desktop (>= 2.16) 

It looks like the package has been renamed python-gnomedesktop!

Cheers

Nick

---

### Post by mr bob on 2010-12-20
Thanks for letting me know. I will try and have a look at that over Xmas.

---

### Post by mr bob on 2010-12-20
OK. I think I have fixed the dependency bug with version 0.31beta.

Thanks for flagging it and if possible let me know if it works for you.

---

### Post by Remix_88 on 2010-12-21
Hi,

Very nice UI. One suggestion for you :-)

I can start downloading one programme and while it downloads I can start downloading another programme. Both programmes continue to download correctly but the progress meter goes a bit crazy. Any chance you can display the download progress for each program separately?

---

### Post by mr bob on 2010-12-21
Thanks Martin.

I may consider making that change in a later version. 

Funnily enough the application was only designed to download one program at a time and the ability to search and download while another programme is still downloading is a bit of an unintended feature.

Another work around is to open an instance of giPlayer for each programme you wish to download simultaneously. That is a bit annoying if all the programmes you wish to download are in the same search but it does have the advantage of displaying the progress correctly for each download.

---

### Post by conal on 2011-01-23
I like this! Well done! It works (almost) perefectly on my x86 linux mint setup. Only hitch it the window gets stuck at 99.9% 'post-processing', but I just close it.

If I could get it working on my power-pc macs then I'd be stoked as the iplayer site is pretty useless with these.

Best

Conal

---

### Post by mr bob on 2011-01-24
Thanks for the positive feedback. :D

---

### Post by Fullofhope on 2011-03-28
A great idea, but I have a problem.
When I download a radio program I get a file called nameofprogram.partial.aac.flv
Try as I may, I can do nothing with this file. Even ffmgeg gives me "unknown format".
Needless to say I have tried about every audio or video player or editor you can think of.
And I've downloaded two different programs at different times in case  it was an artifact.
By the way, TV programs work OK, its just radio progs that are a problem.
This is quite frustrating. Any suggestions?

---

### Post by mr bob on 2011-03-28
Hi fullofhope,

When a radio (or tv) file is downloaded it will take the form nameofprogram.partial.fff.flv, where fff is the format. This is usually "aac" for radio or "mp4" for tv.

When the download has completed it then renames the file to nameofprogram.fff.

It seems your radio download has failed to complete for some reason. It could be a number of reasons.

giPlayer is a graphic user interface wrapper for get_iplayer. It could be either program that is causing the problem.

Can you tell me:
1) Does the giPlayer progress bar complete and disappear?

2) Click on Help->About. From the About dialog, can you tell me which version of get_iplayer it is using? The latest is version 2.78.

3) Try downloading a radio program using get_iplayer on its own by entering this into a terminal:

```
get_iplayer --type radio "name of program"
```

Where "name of program" is substituted with the program you wish to download. This will return a list of possible programs beginning with a 5-figure code. If the code is (for example) 12345, then download with this line:

```
get_iplayer --get 12345
```

Let me know if this download completes correctly. The download will be in whichever folder the terminal is pointing to (probably your user folder).

---

### Post by Fullofhope on 2011-03-29
Thank you Mr Bob for your reply.
Does the progress bar complete? Yes.
Version I'm using? 0.3 Beta
Downloading with terminal? Yes, it works that way.
I downloaded another program today with your gui and this time it worked fine! No 'partial' and no 'flv', and it can be pulled into Audacity, just as required. Things often work when someone is looking.

So in future if the gui won't do it, the terminal will. Thank you for that.

Now, what about the downloaded files I already have? They are long gone from iplayer. I've tried all sorts of renaming strategies, so far to no avail. Is there anything I can do about them?
Thanks for help thus far!

---

### Post by mr bob on 2011-03-29
Glad it is working for you now.

As for your previous downloads the simple answer is renaming alone won't work. However you can easily convert the flv downloaded file to whatever it is containing using ffmpeg.

So type this in a terminal (if it is a radio download):

```
ffmpeg -i nameofprogram.partial.aac.flv -acodec copy nameofprogram.aac
```

If you do not have ffmpeg installed type this into the terminal to install it:

```
sudo apt-get install ffmpeg
```

It will ask for your password.


For a fuller explanation:
############################################
get_iplayer downloads programmes in a Flash Video container file (flv). So if it is a radio programme in aac format, then the download will be a Flash Video Container file (flv), containing an aac audio file.

When the download completes, get_iplayer extracts the aac from the container file (flv) and then deletes the flv.

If get_iplayer fails to complete the download, you are left with an flv container instead of the required file.
############################################

---

### Post by Fullofhope on 2011-03-31
Thanks Mr Bob, I tried what you said.
I had to rename the file back to what it had been in the first place. Can't remember whether it had been mp3 or aac but anyhow I tried both. Every time it gives me Unknown Format, see below.
Looks like I've lost these files, but in future I'll be more aware of what to look for.
Thanks for trying to fix this,
Best wishes.


ffmpeg -i bc1.partial.mp3.flv -acodec copy bc1.aac
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
bc1.partial.mp3.flv: Unknown format

---

### Post by jrussell88 on 2013-01-02
Thanks for what looks like a very handy utility Rob. I've been using get_iplayer for a while, but the syntax can be trying and I hope Giplayer will simplify the process, however I'm having difficulty getting it to work properly.

I'm running Ubuntu 12.04 with get_iplayer 2.80 and giplayer 0.31 beta.

When I press the Radio button, program titles starting with numbers and letters up to 'Cl...' are listed. Nothing after that. If I put the name of a program into the search box and press radio, whether or not I've already listed programs, it only searches those up to 'C'. 

For example searching for 'Today' yields nothing. 

Entering the BBC code for a programme also doesn't find the programme, as it appears only to search the titles. Although Giplayer lists 'Episode' and 'Channel' it doesn't search these fields. 

It appears to be a fault that it doesn't search the full list of programmes, and it would be a great improvement if it could find programmes by searching these fields and the programme id. Many programmes cover different topics each week which are identified in the 'Episode' field, rather than the name of the programme.  

Thanks for  any help you can give with this!

John

OK I worked out that if I run 'get_iplayer --type=radio' it updates the list of programmes which Giplayer shows. So pressing the radio or TV buttons doesn't actually send the query to get_iplayer or update the saved list. 

Perhaps it would be a useful enhancement to add this functionality.

---

### Post by mr bob on 2013-01-02
> **jrussell88 said:**
> When I press the Radio button, program titles starting with numbers and letters up to 'Cl...' are listed. Nothing after that. If I put the name of a program into the search box and press radio, whether or not I've already listed programs, it only searches those up to 'C'. 

For example searching for 'Today' yields nothing. 

Entering the BBC code for a programme also doesn't find the programme, as it appears only to search the titles. Although Giplayer lists 'Episode' and 'Channel' it doesn't search these fields. 
Thanks for  any help you can give with this!

John

Hi John,

Sorry to hear your version of giPlayer isn't working. That is a very unusual problem that I've not heard before. 

Clearly it was working when I programmed it and it is currently working correctly on my version. The only thing I can suggest is to try again on another day and if it is still not working try reinstalling it. 

Otherwise I am sorry I can't help, as I am not in a position to support the project at the moment.

Mr Bob

---

