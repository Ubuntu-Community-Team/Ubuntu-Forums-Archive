---
title: "recording a future audio stream, howto?"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by AAM on 2006-11-24
G'day all.

I wish to record the OSOTA live audio stream which occurs every second week at 9:30pm on a Thursday. I have the base Ubuntu 6.06.1 installation with gnome-sound-recorder (g-s-r).

(I know that I can download their OGG file from their website .. I want to learn how to record a future audio stream!)

I am think that something like a CRON job - starting Rhythmbox with the livestream URL attached and then a recorder would probably work. Unfortunately, there appear to be two man/help pages for g-s-r. Man says that there is a --record option, but the help page does not list it, and it doesn't work when appended to a command in the CLI.

So, fellow Ubuntonians, any help on setting up a 'timer' would be very useful and much appreciated,

AAM

---

### Post by Shay Stephens on 2006-11-24
I made a post a while back asking a similar question:
[http://ubuntuforums.org/showthread.php?t=270247&highlight=record+radio](http://ubuntuforums.org/showthread.php?t=270247&highlight=record+radio)

I have not had time to get anything working yet.  So I am hoping someone in the know will see your post :-)

---

### Post by AAM on 2006-11-24
thanks for the reply - good to know that we are not alone in the universe with unique problems!

It seems that Audacity 1.3.2 (beta release at present) has a timner function, but not the current version (1.2.4) in Ubuntu.

Streamripper is worth a look depending on the source you have (doesn't handle WinMedia, RealAudio, Live365) but would work otherwise with *cron*.

streamripper URL -d <dir> -l <seconds> -q

this looks a reasonable statement. The '-q' makes the file take an incremental number to prevent overwriting.

But that only partly helps me! Still want to be able to capture WM and RA.

---

### Post by AAM on 2006-11-24
talk about answering your own questions!

How does this solution look? You can use the arecord command to record the throughput. I have just tried it on audio from an mp3 and from internet radio ..... and it worked!

The command line options allow you to set the duration of recording but not a start time, so *cron* would be useful for that. Here is a command that should work to produce a decent sound file:

**arecord -d3600 -r44100 -c2 /home/aam/soundfile**

This should record 1 hour (d3600 seconds) at 44.1kHz sample rate of dual (2) channel (stereo) and save it to a file called 'soundfile.wav' (the default format) in the /home/aam directory.

Now I wuppose I will flick over to a *cron* forum to find out howto to set this up to start at the right time. The first action will be to start up a suitable program like Rhythmbox or totem and pass it the required URL for the live feed.

How am I doing Mum? OK, for an old fella?

---

### Post by AAM on 2006-11-24
I have now established that I can start both processes from the command line:

**totem <URL>**

works also. Now it is just a matter of putting both commands into *cron* and having them execute sequentially. The *totem* command should be started 0.5-1 minute before needed to allow streaming to get up to speed.

---

### Post by AAM on 2006-11-24
well, I think I have it all set up!

in a terminal window, enter:

**crontab -e**

to edit the crontab file. I entered something like this:

[B]28 9 * * Sun totem <URL> 
29 9 * * Sun arecord -d1860 -r48000 -c2 /home/aam/Desktop/soundfile.wav
[/B]

which says "*at 0928 each Sunday morning, launch totem and access this URL (which provides a radio stream). Then at 0929 each Sunday, record in stereo at 48kHz for 31 minutes and save the recording as a wav file called 'soundfile' on the desktop of a user called 'aam'.*"

arecord will stop automatically, but do I need to stop totem after 32 minutes? I suppose so. I'll investigate that tomorrow - how to terminate totem at the CLI. I have also been trying to have arecord assign a name which increments so that your last file won't be overwritten, but so far no luck. **soundfile-$(date YYMMdd)** doesn't work. Any ideas, anyone?

Good night's work, I'd say!

---

### Post by Shay Stephens on 2006-11-25
In order to rename your audio file to have a time stamp, create a bash script in gedit:

```
#!/bin/bash
#Program to rename a file with a date stamp.

mv /home/aam/Desktop/soundfile.wav /home/aam/Desktop/soundfile-$(date +%Y%m%d).wav
```

Save it as "rename-soundfile" (as an example) somewhere (home directory as another example) and then right click the file and give it execute permissions.  Then add a line in the crontab to run that file. 

```
30 9 * * Sun /home/aam/rename-soundfile
```

It should rename the file a minute after it is done saving it.

soundfile-20061125.wav

Great work by the way, I am working right now on implementing your idea.  Once I get it working, I shall praise your name in the streets :-)

---

### Post by Shay Stephens on 2006-11-25
Well this is odd.  When the audio is recorded and played back, it really distorted.  It sounds like the volume on recording is way to high and clipped (overdriven?).  So there is more of a harsh buzzing sound.  I have tried different settings in the volume control, but nothing touches it.  Very odd.  But at least I am closer than I was a few days ago :-)

---

### Post by Shay Stephens on 2006-11-25
Yayyyyy!
Ok, the raspy distorted sound happens when I play the wav file via totem.  If I play the same file with mplayer movie player, it sounds perfect.  So now I am ready :-)  Going to give it a go and I should know tomorrow if all worked right :D

---

### Post by Shay Stephens on 2006-11-26
I have it working!  My setup was a little different, because I was using firefox to play a radio station.  Turns out that launching a gui app from crontab takes some special formatting.  So what I needed to have happen is open firefox, start recording two minutes later for 3 hours, then rename the file to give it a timestamp.

This is how the crontab looks:
```
#This is how to read the crontab window
#*     *     *     *     *  command to be executed
#-     -     -     -     -
#|     |     |     |     |
#|     |     |     |     +----- day of week (0 - 6) (Sunday=0)
#|     |     |     +------- month (1 - 12)
#|     |     +--------- day of month (1 - 31)
#|     +----------- hour (0 - 23)
#+------------- min (0 - 59)

#Open firefox and load the audio stream at 10:04pm every day
4 22 * * * export DISPLAY=:0 && firefox http://radio.player.url
#Record every night from 10:06 pm for 2:54:00, 16khz, mono, save to desktop
6 22 * * * arecord -d10440 -r16000 -c1 /home/username/Desktop/radio-show.wav
#Rename the audio file by placing a time stamp on it at 1:06am everyday
6 1 * * * /home/username/rename-radio-file
```

The special technique that allows a gui to be ran from crontab is this:
export DISPLAY=:0 &&

that uses the default display to run the gui, just place the command to run the gui app after that. One thing to keep in mind, don't allow the lines to wrap, keep the commands on one line or they will be treaded as separate commands.

The last line of the crontab calls a bash script that will rename the file with a time stamp.  This is what the script looks like:

```
#!/bin/bash
#Program to rename a file with a date stamp.

mv /home/username/Desktop/radio-show.wav /home/username/Desktop/radio-$(date +%Y%m%d).wav

```

You will have to use the right time and url to record your radio stream and customize the path and file name where you want the audio file saved in both the crontab and the rename script.  This example only has a generic path and file name.  After you save the rename script file, right click on it and give it execute permissions.

If you want to record in 48khz stereo instead of 16khz mono, then use this:
arecord -d10440 -r48000 -c2

the -d10440 controls the recording duration in seconds.  If you only want an hour, use -d3600 (60 minutes x 60 seconds).
-r48000 is the sample frequency (48khz)
-c2 is stereo, c1 is mono.

So hear I am, listening to my radio show perfectly recorded for my listening pleasure the afternoon.  A hearty and boisterous thank you to AAM for doing all the heavy lifting for me that made this all possible!!!  Up until your help, I was just grumbling wishing I could do this.  Now I can!!!

I also found a good bit of crontab help from this post by henriquemaia:
[http://ubuntuforums.org/showthread.php?t=185993](http://ubuntuforums.org/showthread.php?t=185993)

---

### Post by jjross on 2006-11-26
Thanks for posting this. This is something I have wanted to be able to do for a long time.
After playing with your script, I have a suggestion for you.
Instead of naming the file to save to
> /home/radio/soundfile.wav
try this
> /home/radio/$(date +%Y%m%d%k%M).wav

and it will give it a different file name every mo,day,hour,and minute that you start the script
The script you wrote to change the file name gave me this idea so I cant take any credit for any original thinking.
Good work and thanks again

---

### Post by Shay Stephens on 2006-11-27
Hmm, I tried it but it didn't work.  So I will try again today to see if I can figure out why.  It would be cleaner to do it without having to resort to the script.

---

### Post by jjross on 2006-11-27
here is what I ran today
> export DISPLAY=:0 && firefox [http://a959.l1975144999.c19751.g.lm.akamaistream.net/D/959/19751/v0001/reflector:44999](http://a959.l1975144999.c19751.g.lm.akamaistream.net/D/959/19751/v0001/reflector:44999)
arecord -d7200 -r16000 -c1 /home/jim/radio/$(date +%Y%m%d%k%M).wav
it worked fine with the exception that it did not put .wav at the end of the file, but I ran it again and it did, so maybe it was just a one time glitch.
Be aware that the date and time commands are csae sensitive.

---

### Post by Shay Stephens on 2006-11-27
Ok, does that date stamp have to be the whole thing?  I only included the year month and day portions.  Could that be why it failed?

---

### Post by jjross on 2006-11-28
shay,
probably not, but if you record 2 in the same day it will overwrite the first one, I added the %k and %M so it would give a different file name every minute.
Try a test run with the code as I have posted and see if it works.

---

### Post by AAM on 2006-12-05
Shay Stephens and jjross,

you guys are awesome! I have been having the same problems as you two - recording is either harsh noise or nothing (consistent with gui not being opened).

I went OS for a week and thought I would get back to the problem when I returned, and here you have solved all the problems. A triumph for collaboration!

I'll now set about getting everything working properly. Then I'll get a HOWTO written for elsewhere in the forum.

Once again, a big thanks to you both.

Would I be right in thinking that 

```
4 22 * * * export DISPLAY=:**0** && firefox http://radio.player.url
```

becomes

```
4 22 * * * export DISPLAY=:**1** && firefox http://radio.player.url
```

if you are using Xgl?

AAM

---

### Post by Shay Stephens on 2006-12-05
> **AAM said:**
> Would I be right in thinking that 

```
4 22 * * * export DISPLAY=:**0** && firefox http://radio.player.url
```

becomes

```
4 22 * * * export DISPLAY=:**1** && firefox http://radio.player.url
```

if you are using Xgl?

AAM

I am not currently using xgl, but I do know you can use any display that you needto, display 0 is just the default display.  So try 1 or 2 or whatever if 0 does not work for you :-)

Glad to hear you are getting some success :D  the whole process has encouraged me a lot.  I am maybe a month away from being able to stop using my dual boot with Windows.

---

### Post by jjross on 2006-12-05
Just a quick comment on the playback sound quality, use anything except TOTEM.
mine sounded as you described with TOTEM, so I tried MPLAYER and it is perfect, VLC works good also.
I also record  with the audio feed coming in thru MPLAYER plugin in Firefox.
I have found that it will record any sound coming thru the sound card, I have hooked up a microphone and can record voice along with what you are recording on the feed.
I also tried some different code to time and date stamp the file and this seems to work best for me
> arecord -d7200 -r16000 -c1 /home/jim/radio/$(date +%Y%m%d-%H%M).wav
the %k seems to have problems with am hours that start with a zero IE:07:00
Also unless you want real good stereo sound and a real large file size you can lower the frequency and set it for mono (c1). 2 hours at the settings quoted above gave me a 109MB file size and pretty good sound quality for talk radio

---

### Post by AAM on 2006-12-06
Thanks for the very useful advice. Your mini-script reduces the number of lines in cron greatly.

I have taken the advice to use vlc (sound file still sounds terrible today), and changed display to 0 to see what happens. Like you I record once a day, so I will need to wait another 22 hours to see if my changes make sense.

AAM

---

### Post by Shay Stephens on 2006-12-06
Does anyone know how to shut down a program?  So let's say cron opens up firefox to play a stream, once the recording stops, how would one shut firefox down automatically?

You can do it if you know the pid, but how do you get that info if the program starts with cron and you are not there to see what the pid is?

---

### Post by AAM on 2006-12-06
I have no idea about the specifics of the command parameters, but couldn't you use another cron job that says something like 
```
4 24 * * * export DISPLAY=:0 && firefox quit
```

---

### Post by Shay Stephens on 2006-12-06
That doesn't work, it opens a new tab, and then opens a quit smoking website hehehe.  But I will look into the firefox options for closing itself.  There may be something there...

---

### Post by Shay Stephens on 2006-12-06
I couldn't find a firefox switch, but I did find that the killall command can close a program based on name instead of pid, which I still can't find a way to determine programmatically yet.  So I have added this to cron:

```
#close all instances of firefox
4 24 * * * killall -q firefox-bin
```

The -q switch just tells it to operate in quiet mode and not complain if firefox-bin is not there to close.

---

### Post by jjross on 2006-12-08
Until now I have only been using the script manually  to record with.
So I thought would do the cron set up,it will start firefox ok but it will not start arecord. 
Here is the script I am running in crontab
> 13 19 * * *  arecord -d21600 -r16000 -c1 /media/hda8/Radio/$(date +kfyi-%m-%d-%H%M).wav
 
Any ideas why it wont run?
If I run the same command in a bash script it works fine

---

### Post by Shay Stephens on 2006-12-09
Try it without the date stamp code.  I can't get it to work with that.  So try this tonight to see if it works:

```
13 19 * * * arecord -d21600 -r16000 -c1 /media/hda8/Radio/kfyi.wav
```

If that works, then all you need to do is run a cron job after the recording stops to rename the file with a time stamp with a bash script.  Here is the script:

```
#!/bin/bash
#Program to rename a file with a date stamp.

mv /media/hda8/Radio/kfyi.wav /media/hda8/Radio/kfyi-$(date +%Y%m%d).wav
```

I am writing this right now while listening to a radio show I recorded automatically yesterday while I was away from the radio :-)

---

### Post by jjross on 2006-12-09
thanks Shay
That makes it work, apparently the time and date stamp is the problem

---

### Post by Shay Stephens on 2006-12-09
I have totem working in edgy.  What I did was to install the gstreamer backend instead of the xine backend.  In synaptic, install totem-gstreamer.  That will also uninstall totem-xine.  When it is done, you should be able to double click the audio stream and hear it properly.

---

### Post by Shay Stephens on 2006-12-09
**To record and listen to an audio stream from a web based radio station**

**In synaptic, install totem-gstreamer. ** 
Installing totem-gstreamer will uninstall totem-xine.  totem-xine does not work well for playback right now.  If you still have trouble listening to the audio file, play it with mplayer or even vlc.

**Setup crontab to play the stream, record it, rename it, and close it**
in the terminal run:
```
crontab -e
```

add this at the bottom of the editor:

```

#Record the radio show everyday
#Open firefox and load the audio stream
04 10 * * * export DISPLAY=:0 && firefox http://your.radio.station
#Record every day from 10:06 am for 2 hours and 54 minutes
06 10 * * * arecord -d10440 -r16000 -c1 /home/your-username/Desktop/radio-show.wav
#Rename the audio file by placing a time stamp on it
01 13 * * * /home/your-username/rename-radio-file
#close all instances of firefox
01 13 * * * killall -q firefox-bin
```

Of course you need to customize the info above.  Specifically the red areas and the times:
#Record the radio show
#Open firefox and load the audio stream
04 10 * * * export DISPLAY=:0 && firefox [COLOR="Red"]http://your.radio.station[/COLOR]
at 4 minutes past 10am, firefox will load the radio station website you enter.

#Record every day from 10:06 am for 2 hours and 54 minutes
06 10 * * * arecord [COLOR="Red"]-d10440[/COLOR] [COLOR="Red"]-r16000[/COLOR] [COLOR="Red"]-c1[/COLOR] [COLOR="Red"]/home/your-username/Desktop/radio-show.wav[/COLOR]
at 6 minutes past 10am it will start recording for 10,440 seconds (2 hours 54 minutes) at 16000 hz (16khz) in mono (c1, c2 for stereo) and save the recording on the desktop.

#Rename the audio file by placing a time stamp on it
01 13 * * * [COLOR="Red"]/home/your-username/rename-radio-file[/COLOR]
This runs a bash script (which will be detailed next) which is saved in the home folder.  The bash script is ran 1 minute after 1pm

#close all instances of firefox
01 13 * * * killall -q firefox-bin
This closes firefox 1 minute past 1pm so the radio station stops streaming.  You don't want to be streaming content off the servers if you are not there to hear it and you are not recording it.  That is not fair to the radio station or the people who want to hear the station themselves.  This may not be the ideal way to close it down, but it is the only way I know of right now.  If anyone knows a better way, we are all ears :-)

**If you want to customize the start times**
```
#This is how to read the crontab window
#*     *     *    *    *  command to be executed
#-     -     -     -     -
#|     |     |     |     |
#|     |     |     |     +----- day of week (0 - 6) (Sunday=0)
#|     |     |     +------- month (1 - 12)
#|     |     +--------- day of month (1 - 31)
#|     +----------- hour (0 - 23)
#+------------- min (0 - 59)
```

If you want to record on only specific days, for example monday-friday, then a crontab line might look like this:
04 10 * * [COLOR="Red"]1,2,3,4,5[/COLOR] export DISPLAY=:0 && firefox [http://your.radio.station](http://your.radio.station)

**The file renaming bash script:**
```
#!/bin/bash
#Program to rename a file with a date stamp.

mv /home/your-username/Desktop/radio-show.wav /home/your-username/Desktop/radio-$(date +%Y%m%d).wav
```

Save that in your home folder as "rename-radio-file" or whatever you decide to call it from the cron job.  Of course you need to customize both of the paths to your particular setup.

And that is it.  Your radio show should be on the desktop waiting for you to listen to it.  This how-to would not have been possible without the help of AAM, henriquemaia, and jjross.  The main info on recording radio took place here:
[http://ubuntuforums.org/showthread.php?t=305858](http://ubuntuforums.org/showthread.php?t=305858)
And additional help specific to crontab can be had here:
[http://ubuntuforums.org/showthread.php?t=185993](http://ubuntuforums.org/showthread.php?t=185993)

---

### Post by Roberto.Argentina on 2007-02-08
Hello, I have a similar problem to this thread, I want to record a show radio at certain time but not from streaming audio but from the line-in jack of the sound card, the command "arecord" is applicable too?

(sorry from my English)

---

### Post by Shay Stephens on 2007-02-08
It should work with any sound coming through the sound system.  If not, check the audio capture settings of the sound mixer to make sure the line-in jack is selected.

---

### Post by AAM on 2007-02-09
Hey Shay! What an effort!

Sorry that I petered out towards the end, but when my kids play with my machine and freeze it, and then the entire OS is knackered, small fixes take a back seat! In addition I have this problem trying to install Ubuntu with an ATI 9600 card and 1440x900 screen (I don't know what is to blame).

So when I get home tomorrow I'm going to set the whole thing up again! Thanks for the credit, although I think you can justifiably call yourself "The Man"! Have another 677 beans! God working with you.

AAM

---

### Post by mister_p_1998 on 2007-08-10
Well,
Ive been waiting over a year to find out how to run a GUI program from crontab! Thanks so much!
I can now run Icepodder and Democracyplayer on a scheduler!
Cheers
Steve

---

