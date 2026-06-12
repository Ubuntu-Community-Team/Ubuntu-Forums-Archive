---
title: "[SOLVED] nuvexport divx/xvid/mpg formats"
date: 2008-12-05
forum: Mythbuntu
---

### Post by MartinusEx on 2008-12-05
Hi,
I'm a little lost about the definitions and what nuvexport actually does:

[I]I'm walking through the process of getting Mythbuntu to transcode and cut recordings, so I can burn some on a DVD.
The orginal transcode job generates nuv files.
nuvexport now is obviously the  way to transcode the recordings for output to DVD and PSP or whatever.[/I]
[LIST]
[*]nuvexport seems "only" to support to transcode to divx or xvid.
[*]What is now the difference divx/xvid vs mpg?

[*]Could nuvexport be set to produce mpg instead of divx or xvid (if this is necessary anyway)

[*]Is there any background information available on nuvexport?
[*]A description how it works principially?

[*]How are ffmpeg or mencoder related to nuvexport?(These are the encoders, so **what does nuvexport actually do**?)
[/LIST]

thanks a lot for any information available

Martinus

---

### Post by SiHa on 2008-12-05
There's quite a good guide for nuvexport here:
[http://ubuntuforums.org/showthread.php?t=346778](http://ubuntuforums.org/showthread.php?t=346778)

I use nuvexport (using transcode, converting to Xvid) for any recordings I want to keep long-term, or to chuck on a flash drive and take to work to watch at lunch-time.

Running nuvexport from the comand line, simply```
nuvexport
```

Will cause it to prompt you for your required settings - I'm fairly sure there's an MPEG2 output (required for DVD) - and it will give you a chance to see what's available and fine-tune your settings.

If you are recording DVB transmissions, then they should be stored as MPEG2 streams anyway, have you tried Mythtv's in-build 'lossless transcoding' to simply remove the bits inthe cutlist, then use something like DeVeDe to create the DVD .iso

To answer your final point, nuvexport is simply a wrapper script for mencoder, ffmpeg & transcode. The amount of available switches and options for these is bewildering and nuvexport just simplifies their use, bringing the three transcoders together with a unified interface / syntax.

---

### Post by MartinusEx on 2008-12-05
Hi SiHa,
nice to read you :-))
thanks up to here.
> **SiHa said:**
> 

If you are recording DVB transmissions, then they should be stored as MPEG2 streams anyway,...



[INDENT][I]Jep,I'm using a DVB-S card.
This seems to be raw stream stored, I get lots of warnings when running these files through project-x.
Under windows, the project-x exits with memory overflow and I have to use ffmpeg before I can use project-x
[/I]
My goal is to 
[LIST]
[*]cut out unwanted parts (as you mentioned)
[*]make the files somewhat more handy (at least down to 2,5GB is my aim)for storage and
[*]have them available to burn to DVD.
[/LIST]

The cutting is the problem up to now, nothing really worked out.

For DVD authoring I tried tovid which works out nice and DVDAuthor which I haven't had the time to get into up to now.[/INDENT]

> **SiHa said:**
> 

..., have you tried Mythtv's in-build *'lossless transcoding'* to simply remove the bits inthe cutlist, then use something like DeVeDe to create the DVD .iso


All I'm currently aware of is 
[LIST]
[*]the automatic transcoding which can be programmed when programming the recording in FE in advance and 
[*]the transcoding job that can be started from mythweb.
[/LIST]

These both seem to produces nuv-files.
Actually I'm not sure what you are talking about.
I need to have a look in the possibilities for setting these actions up (I hope the wiki gives enough information on that
issue)

[LIST]
[*]Is the lossless transcoding one of the actions mentioned above?
[*]How can I invoce that if not?
[/LIST]
rgds and thanks

Martinus

---

### Post by SiHa on 2008-12-06
[B][Windows Warning]
****
If you are easily offended by non-linux talk - move on - nothing to see here.
****
[/Windows Warning][/B]
> Under windows, the project-x exits with memory overflow and I have to use ffmpeg before I can use project-x

I can help you there. There seems to be a problem with the commony available versions of the ProjectX Win32 executable, in that it is compiled with only a small memory size (32 MB, I think) so if it requires more than this you get an overflow.

The way round it is to grab the compiled .jar (not the .EXE) from somewhere like here [http://www.oozoon.de/main_en.html](http://www.oozoon.de/main_en.html).

Make sure you have the Java Runtime Engine (JRE) installed. Extract the above into a directory - I found it needed to be immediately off the root dir, then create a shortcut to it with the following command line:
```
C:\WINDOWS\system32\java.exe -Xmx128m -jar c:\projectx\ProjectX.jar
```

This will run it with 128MB memory space, and should stop the overflow errors.

**Back to MythTV.**

> Quote:
Originally Posted by SiHa  

[QUOTE]..., have you tried Mythtv's in-build 'lossless transcoding' to simply remove the bits inthe cutlist, then use something like DeVeDe to create the DVD .iso 

All I'm currently aware of is 
the automatic transcoding which can be programmed when programming the recording in FE in advance and 
the transcoding job that can be started from mythweb. 

These both seem to produces nuv-files.
[/QUOTE]

Lossless transcoding can be setup in the recording profiles:

Setup -> Setup -> TV Settings -> Recording Profiles -> Transcoders.

You can add new transcoders, but I found they didn't show up in the list of available jobs - a bug that needs filing?. What I've done is, edited the 'High Quality' transcoder, towards the bottom of the first page, there is a check box 'Lossless Transcoding', select it, and then select 'Finish'.

Now if you go back to the Watch Recordings menu, select a recording and arrow-right to bring up the context menu, scroll down to job obtions, select transcode, then select High Quality. As there's no actual transcoding taking place, this should run pretty quickly. When the job has finished you should find you still have an .mpg file that has had the cutlist. (I am assuming uo know how to use 'Edit' to create the cutlist?).

You should now be able to use Tovid to make your DVD.

---

### Post by MartinusEx on 2008-12-12
Hi SiHa,
later is better than never:
Thnaks for your reply .

> **SiHa said:**
> [B][Windows Warning]
****
If you are easily offended by non-linux talk - move on - nothing to see here.
****
[/Windows Warning][/B]

I can help you there. There seems to be a problem with the commony available versions of the ProjectX Win32 executable, in that it is compiled with only a small memory size (32 MB, I think) so if it requires more than this you get an overflow.

The way round it is to grab the compiled .jar (not the .EXE) from somewhere like here [http://www.oozoon.de/main_en.html](http://www.oozoon.de/main_en.html).

Make sure you have the Java Runtime Engine (JRE) installed. Extract the above into a directory - I found it needed to be immediately off the root dir, then create a shortcut to it with the following command line:
```
C:\WINDOWS\system32\java.exe -Xmx128m -jar c:\projectx\ProjectX.jar
```

This will run it with 128MB memory space, and should stop the overflow errors.


thanks on that, I didn't mean to talk windows, it just sprang to my mind. Nevertheless I'll try that.


[QUOTE=SiHa;6320849][B][Windows Warning]
Lossless transcoding can be setup in the recording profiles:

Setup -> Setup -> TV Settings -> Recording Profiles -> Transcoders.
...

This one is up and running.
I was irritated by only beeing able to choose from mpg4 or rtjpg.
And in fact, i created a converter "test" which doesn't show up in the  menu.
But the as i said editing  "high quality" to be lossless did the job.

thanks a lot so far

(Yes I found the way to edit recordings)
MythTV/MythBuntu has an overwelming mass of features, so that I never will be able to make full use of it :-))

Martinus

---

