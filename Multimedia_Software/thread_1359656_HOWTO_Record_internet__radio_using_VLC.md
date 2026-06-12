---
title: "HOWTO: Record internet  radio using VLC"
date: 2009-12-19
forum: Multimedia Software
---

### Post by bheemboy on 2009-12-19
I had to dig through several posts to set up automated recording of my favorite internet radio show. So I hope this may of help to someone besides me.

This can be done with a single command using VLC:
1. Create a script file 'recordmyshow.sh', with the following content.
```
#!/bin/sh
NOW=$(date +"%b-%d-%y")

cvlc --run-time=7200 http://kqed-ice.streamguys.org:80/kqedradio-ch-e1 --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/<user>/myshow-$NOW.mp3}" vlc://quit ;

```

cvlc is the commandline version of vlc
use --run-time to indicate the duration of the show in seconds
Replace the url to the radio station of your choice and dst to the path you desire. That's it

2. Mark the file as executable
```

chmod +x recordmyshow.sh

```

3. Schedule the recording in cron.
  a. Launch the cron
```

crontab -e

```

  b. Put the schedule in it
```

00 18 * * 06 /home/<user>/recordmyshow.sh

```
My favorite show is at 6 pm every Saturday.

---

### Post by USB_NL on 2009-12-19
Thanks

Is this possible with video asf files?

---

### Post by bheemboy on 2009-12-20
The url I used is feeding mp3. I am not sure about asf. If you give me the link I can try...

---

### Post by tubunu on 2010-01-02
I would like to schedule a live stream of WPLJ radio station. Here's the address:

```
mmsh://citadelcc-wplj-fm.wm.llnwd.net/citadelcc_WPLJ_FM?MSWMExt=.asf
```

I can't seem to figure out how to do it. Any help would be much appreciated! Thanks.

---

### Post by USB_NL on 2010-01-04
> **tubunu said:**
> I would like to schedule a live stream of WPLJ radio station. Here's the address:

```
mmsh://citadelcc-wplj-fm.wm.llnwd.net/citadelcc_WPLJ_FM?MSWMExt=.asf
```I can't seem to figure out how to do it. Any help would be much appreciated! Thanks.
I will follow this thread too:popcorn:

---

### Post by mc4man on 2010-01-04
> would like to schedule a live stream of WPLJ radio station
Change the mux to asf
ex.
--sout "#duplicate{dst=std{access=file,mux=asf,dst=/home/doug/nj1.wma}"

---

### Post by tubunu on 2010-01-04
THANK YOU bheemboy for a great script and THANK YOU mc4man for great advice. It works perfectly! :)

---

### Post by pixiebob on 2010-02-18
hi everybody i need to record radio with this adress:
[http://www.ouifm.fr/player/metafile/Ouifm-hautdebit-wmp.asx](http://www.ouifm.fr/player/metafile/Ouifm-hautdebit-wmp.asx)
_what is the command with cvlc_?.
i know how do with mplayer but i need to use only vlc:
thanks

---

### Post by pixiebob on 2010-02-18
i found solution myself.
i use wget to download adress radio.after i open the file asx downloaded with kwrite for example and i see the real adress that i can use to record with cvlc

---

### Post by pc10pc on 2010-06-05
i modified the code to this 
```
#!/bin/sh


vlc --run-time=10800 http://www.live365.com/cgi-bin/play.pls?stationid=319909&now=1157978043165&token=53ddde2191ce2a16d9a3d1f10e1cf672-3012110080400000&AuthType=NORMAL&bitrate=256&SaneID=81.187.66.150-1156155723215&membername=&session=kxlu2%3A0&tag=live365&filename.pls --sout "#duplicate{dst=std{access=file,mux=mp3,dst=/home/paul/mfn.mp3}" vlc://quit ;
```
to record a show on KXLU which uses .pls format. i changed cvlc to vlc just for testing.
when i execute the .sh file, vlc starts and plays the stream just fine, but no recording takes place. i am able to manually save the stream using the media>convert/save dialogue.
can anyone show me where i'm going wrong? the link for the stream is
```
http://www.live365.com/cgi-bin/play.pls?stationid=319909&now=1157978043165&token=53ddde2191ce2a16d9a3d1f10e1cf672-3012110080400000&AuthType=NORMAL&bitrate=256&SaneID=81.187.66.150-1156155723215&membername=&session=kxlu2%3A0&tag=live365&filename.pls
```

---

### Post by mc4man on 2010-06-05
you could try this instead (otherwise I'm not sure you can use "access=file"

```
cvlc --run-time=10800 http://www.live365.com/play/319909? --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/paul/mfn.mp3}" vlc://quit ;
```

---

### Post by pc10pc on 2010-06-06
that works fine, thanks for your help!
:guitar:

---

### Post by pc10pc on 2010-06-07
ah, a slight hitch has arisen for me on the cron side of things.
i used Gnome schedule to set up the cron, and had to select 'x application' as the behaviour in order for VLC to start up on schedule. However, though VLC starts and connects to the stream it wont write the saved .mp3 file.
any thoughts on this?


EDIT
using the one time scheduler works fine, but recurring does not. strange...

---

### Post by robstwd on 2010-06-27
hi, just wanted to add my vote of thanks for the script. Just spent the last few hours getting it working using Ruby => works an absolute treat! Much appreciated bheemboy.

The Ruby system command gets 2 command line arguments for URL of station (details stored in a YAML file) and duration, as per the following:```
system "cvlc --run-time=#{@duration} #{@url} --sout '#duplicate{dst=std{access=file,mux=raw,dst=/home/rob/Music/Radio/#{@outputfile}.mp3}' vlc://quit ;"
```

---

### Post by fachtofer on 2010-07-10
Just felt compelled to add, a big thanks for this thread.. I've been looking for something like this, was using Streamtuner but I wanted automation. 

Linux never ceases to amaze me with the possibilities..

---

### Post by jlabomb on 2010-07-24
I have been trying to get this to work but when I run my script it just plays the radio station and the recording is no where to be found. This is what the terminal displays

> james@james-desktop:~$ /home/james/Desktop/recordmyshow.sh
VLC media player 1.0.6 Goldeneye
/home/james/Desktop/recordmyshow.sh: line 4: --sout: command not found
james@james-desktop:~$ [0x2672048] dummy interface: using the dummy interface module...
[0x7ff85c002cc8] pulse audio output: No. of Audio Channels: 2


Here is my script

        > #!/bin/sh
    NOW=$(date +”%b-%d-%y”)

    cvlc --run-time=3600 [http://216.235.94.11/play?s=johnnycashradio&d=live365&r=0&membername=&session=johnnycashradio:0&AuthType=NORMAL&app_id=live365%3AMozilla5.0X1&SaneID=69.73.10.60-1279803603216522&ftm=0.671473454218358](http://216.235.94.11/play?s=johnnycashradio&d=live365&r=0&membername=&session=johnnycashradio:0&AuthType=NORMAL&app_id=live365%3AMozilla5.0X1&SaneID=69.73.10.60-1279803603216522&ftm=0.671473454218358) --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/james/music/JCradio/test.mp3}" vlc://quit ;


I have changed it several times but the way with the least errors. The radio station I am trying to record is here

[http://216.235.94.11/play?s=johnnycashradio&d=live365&r=0&membername=&session=johnnycashradio:0&AuthType=NORMAL&app_id=live365%3AMozilla5.0X1&SaneID=69.73.10.60-1279803603216522&ftm=0.671473454218358]("http://216.235.94.11/play?s=johnnycashradio&d=live365&r=0&membername=&session=johnnycashradio:0&AuthType=NORMAL&app_id=live365%3AMozilla5.0X1&SaneID=69.73.10.60-1279803603216522&ftm=0.671473454218358")


Any help would be great. Thanks.

---

### Post by ron999 on 2010-07-24
Hi **jlabomb**
I think your link's no good.:(
Try your script with this link insted:-
> [http://216.235.94.11/play?s=johnnycashradio](http://216.235.94.11/play?s=johnnycashradio)

```
cvlc --run-time=3600 http://216.235.94.11/play?s=johnnycashradio --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/james/music/JCradio/test.mp3}" vlc://quit ;
```

Then look in the **/home/james/music/JCradio** folder

---

### Post by jlabomb on 2010-07-24
Thanks. That did the job. I don't know why the link didn't work because I could hear the audio when I ran the script. Anyway I have one more question. Is there a command to auto name the file either by a number or time and date? Thanks again this will be great for me.

---

### Post by ron999 on 2010-07-24
**jlabomb**
In your command, instead of file name **test.mp3**
Try something like this:-
**JohnnyCash-$(date +"%b-%d-%y").mp3**

---

### Post by mc4man on 2010-07-24
What's sorta interesting about that site is the podcasts are of much better quality - the stream you're recording is 96k, 20500. Can't tell if the external player on the site is using the lower or higher quality mp3's

> I don't know why the link didn't work because I could hear the audio

There was to much 'info' in that link - vlc would 'stop' after getting the stream so no --sout

As a hint - sometimes play a link in vlc, then as it's playing go - tools  - codec info.. and see what url is displayed in vlc (location

---

### Post by jlabomb on 2010-07-24
Great you guys are a big help. Just one last question, can I also stamp the time on that file name? If I record 2 shows in one day it will overwrite the previous file.

I had seen that shorter link in vlc but I wasn't sure which one to use in the script but now I know to pull that one out of vlc. Thanks again for all the help.

---

### Post by ron999 on 2010-07-24
Try this for your file name:-
**JohnnyCash-$(date +"%b-%d-%y--%H:%M").mp3**
or this:-
**JohnnyCash-$(date +"%b-%d-%y--%H:%M:%S").mp3**

Those times will be shown as GMT though.(Maybe).

---

### Post by SoFl W on 2010-07-24
I am a little late to this conversation but I found this the other day...

[Schedule streaming audio recordings in Ubuntu]("http://www.instructables.com/id/Schedule-Streaming-Audio-Recordings-in-Ubuntu/").

---

### Post by jlabomb on 2010-07-24
That did it Ron999. I just wanted to be able to schedule more than one a day. Thanks again.

---

### Post by shantiq on 2011-07-30
ok guys need some help here trying to use script and so far failing what am i missing???




> vlc --run-time=9 [http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls](http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls)  “#duplicate{dst=std{access=file,mux=mp4a,dst=/home/shantiq/Womad_3-$NOW.mp4}” vlc://quit ;


but now it cannot find the file   why is that?

>  vlc --run-time=9 [http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls](http://www.bbc.co.uk/radio/listen/live/r3_aaclca.pls)  “#duplicate{dst=std{access=file,mux=mp4a,dst=/home/shantiq/Womad_3-$NOW.mp4}” vlc://quit ;VLC media player 1.2.0-git Twoflower (revision 1ee61ad)
[0x72f110] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x784740] main playlist: stopping playback
[0xd3a890] access_http access: Raw-audio server found, m4a demuxer selected
[0xd5d920] packetizer_mpeg4audio demux packetizer: AAC channels: 2 samplerate: 44100
[0x78d9e0] filesystem access error: cannot open file /home/shantiq/“#duplicate{dst=stdaccess=file” (No such file or directory)
[0xd8b090] main input error: open of `file:///home/shantiq/%E2%80%9C%23duplicate%7Bdst%3Dstdaccess%3Dfile%E2%80%9D' failed
[0xc23a20] filesystem access error: cannot open file /home/shantiq/“#duplicate{dst=stdmux=mp4a” (No such file or directory)
[0xe40780] main input error: open of `file:///home/shantiq/%E2%80%9C%23duplicate%7Bdst%3Dstdmux%3Dmp4a%E2%80%9D' failed
[0xb0a280] filesystem access error: cannot open file /home/shantiq/“#duplicate{dst=stddst=/home/shantiq/Womad_3-.mp4” (No such file or directory)
[0xd755e0] main input error: open of `file:///home/shantiq/%E2%80%9C%23duplicate%7Bdst%3Dstddst%3D/home/shantiq/Womad_3-.mp4%E2%80%9D' failed
[0x7e4c40] dummy demux: command `quit'


realized i had not used ```
--sout
```   but when i do it does not even start


a bit confused

---

### Post by ron999 on 2011-07-30
> **shantiq said:**
>  but when i do it does not even start


a bit confused


Hi
That HD 320Kbps aac stream is ADTS coming from an RTMPE server.
Even though VLC will play it, I'm not sure how to save it (other than use the red button).

For this job I can use **get_iplayer** instead.
It uses RTMPDump to save the stream.

Details are here:- [http://pastebin.com/gJv3QvZa]("http://pastebin.com/gJv3QvZa")

And in the attachment is 20 seconds worth.

---

### Post by shantiq on 2011-07-30
thank you Ron as usual a fount of knowledge

got earlier program today with red button for Womad nice 320kbps

probably will stick with that then if there is no way to control the time on get-iplayer

```
get_iplayer --get --force --type=liveradio --stop 20 "http://www.bbc.co.uk/mediaselector/4/gtis/?server=cp60703.live.edgefcs.net&identifier=Special_Event1_UK@s6485&kind=akamai&application=live"
```


works a charm too:)

---

### Post by ron999 on 2011-07-30
> **shantiq said:**
>  if there is no way to control the time on get-iplayer

```
get_iplayer --get --force --type=liveradio [SIZE="4"][COLOR="Red"]--stop 20[/COLOR][/SIZE] ....
```


works a charm too:)
........

---

### Post by shantiq on 2011-07-30
der:KS   who is dumb?
   shan  is dumb  
 thank you   --stop 9000 will sort me out     cheers

---

### Post by Langstracht on 2011-08-05
I hope all you helpful guys are still around cos I sure could use your help.

My problem seems to be with "vlc://quit".

If I leave it in the .sh file it executes immediately - i.e. supposedly goes through all the preceding commands but closes down (quits) before anything happens.

If I take it out everything is fine (open, find, play/record & stop).  But, of course, I'm left with vlc still there.

I hope the above is clear.  And I hope someone can help.

TIA

---

### Post by shantiq on 2011-09-21
hi guys very useful thread here thank you :KS


trying to record highest sound quality classical radio station in europe
NRK alltid klassisk which broadcasts online at 384kbps
but finding a little hitch here    any ideas?


> cvlc --run-time=40 [http://lyd.nrk.no:80/nrk_radio_klassisk_wma_h](http://lyd.nrk.no:80/nrk_radio_klassisk_wma_h) --sout "#duplicate{dst=std{access=file,mux=asf,dst=/home/shantiq/nrrrrrrk.wma}" vlc://quit ;


and i get this on terminal


> cvlc --run-time=40 [http://lyd.nrk.no:80/nrk_radio_klassisk_wma_h](http://lyd.nrk.no:80/nrk_radio_klassisk_wma_h) --sout "#duplicate{dst=std{access=file,mux=asf,dst=/home/shantiq/nrrrrrrk.wma}" vlc://quit ;
VLC media player 1.2.0-git Twoflower (revision 1ee61ad)
[0x6c5de0] dummy interface: using the dummy interface module...
[0x6a2970] main playlist: stopping playback
[0x6cc380] access_mms access error: [COLOR="Red"]cannot read data 2[/COLOR]
[0x6f8550] access_mms access error: cannot connect to 10.103.0.72:80
[0x9d3f70] main input error: open of `mmsh://10.103.0.72:80/nrk_radio_klassisk_wma_h?MSWMExt=.asf' failed
[0x9d3f70] main input error: Your input can't be opened
[0x9d3f70] main input error: VLC is unable to open the MRL 'mmsh://10.103.0.72:80/nrk_radio_klassisk_wma_h?MSWMExt=.asf'. Check the log for details.
[0x7440f0] dummy demux: command `quit'

---

### Post by shantiq on 2011-09-21
also here


trying to run the script in combination with cron    ( can one do that /? )


> 45 11 * * 3  cvlc --run-time=3600 [http://mp3.live.tv-radio.com:80/francemusique/all/francemusiquehautdebit.mp3](http://mp3.live.tv-radio.com:80/francemusique/all/francemusiquehautdebit.mp3) --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/shantiq/france_musique_aujourdhui-$NOW.mp3}" vlc://quit ;


but it does not start.  is it simply not possible to combine both; or does someting need be modified in the lines i am using

ps   I am feeding the cron info through mousepad which works with other timed recordings

---

### Post by mc4man on 2011-09-21
> **shantiq said:**
> hi guys very useful thread here thank you :KS


trying to record highest sound quality classical radio station in europe
NRK alltid klassisk which broadcasts online at 384kbps
but finding a little hitch here    any ideas?

You are using http in the command - that should be 

cvlc --run-time=40  [COLOR="Blue"]mmsh[/COLOR]://lyd.nrk.no:80/nrk_radio_klassisk_wma_h ect.

---

### Post by shantiq on 2011-09-21
thank you mc4man   it works and gives me this **but works !**


> [COLOR="DarkRed"]cvlc --run-time=40 mmsh://lyd.nrk.no:80/nrk_radio_klassisk_wma_h --sout "#duplicate{dst=std{access=file,mux=asf,dst=/home/shantiq/nrrrrrrk.wma}" vlc://quit ;[/COLOR]
VLC media player 1.2.0-git Twoflower (revision 1ee61ad)
[0xf56de0] dummy interface: using the dummy interface module...
[0xf686b0] access_mms access error: cannot read data 2
[0xfb78a0] dummy demux: command `quit'




do you or anyone else have any idea on the [**other one** with cron]("http://ubuntuforums.org/showpost.php?p=11271698&postcount=32")

---

### Post by mc4man on 2011-09-21
> **shantiq said:**
> also here


trying to run the script in combination with cron    ( can one do that /? )

but it does not start.  is it simply not possible to combine both; or does someting need be modified in the lines i am using

ps   I am feeding the cron info through mousepad which works with other timed recordings
What you're calling a script is just the command, you'd do fine if you create an actual script for THIS stream & then in your crontab just /path/to/scriptname
You can refer back to post one for this - though for Ex. the mp3 stream
use this for your script, name it something unique & simple (1 word),  then  make executable - 

```
#!/bin/bash
NOW=$(date +"%b-%d-%y")
cvlc --run-time=3600 http://mp3.live.tv-radio.com/francemusique/all/francemusiquehautdebit.mp3 --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/shantiq/france_musique_aujourdhui-$NOW.mp3}" vlc://quit ; 
```

Then your crontab would be - 
```
45 11 * * 3 /path/to/scriptname
```
For every stream you want to auto record then create a new script as above, just alter the cvlc command to suit

---

### Post by shantiq on 2011-09-22
ok thanx for that   that shows me how to not confuse script and command


so i saved a document called frmusique.sh in home folder


> #!/bin/bash
NOW=$(date +"%b-%d-%y")
cvlc --run-time=36 [http://mp3.live.tv-radio.com/francemusique/all/francemusiquehautdebit.mp3](http://mp3.live.tv-radio.com/francemusique/all/francemusiquehautdebit.mp3) --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/shantiq/france_musique_aujourdhui-$NOW.mp3}" vlc://quit ;



made it executable



entered 

```
10 9 * * * frmusique.sh

```

in my cron page to test

and got nothing ...     what might you think am not seeing / understanding ?

---

### Post by mc4man on 2011-09-22
> **shantiq said:**
>  

```
10 9 * * * frmusique.sh

```

in my cron page to test

and got nothing ...     what might you think am not seeing / understanding ?

You need to full path the script so if it was sitting loose in your  home folder then  - 

```
10 9 * * * /home/shantiq/frmusique.sh
```

You may want to create a folder for scripts or a bin folder in home - in any event do the _full path_ in crontab

---

### Post by shantiq on 2011-09-22
i have a script folder 


but i did this as the full path to script folder did not work


so i placed it in home folder


and with or without full path nothing happens still :KS

---

### Post by mc4man on 2011-09-22
Well 1st confirm the script itself runs  - d. left click on and choose 'run in terminal' or open a terminal & run it. (just Drag & Drop your script into the terminal, click on terminal to return focus, press enter

Tried your last one here, no issue, - was started from cron - see screen, in 2nd one it's the test2 entry

---

### Post by shantiq on 2011-09-22
thanx for your time mc4


i ran

```
shantiq@shan:~$ #!/bin/bash
shantiq@shan:~$ NOW=$(date +"%b-%d-%y")
shantiq@shan:~$ cvlc --run-time=36 http://mp3.live.tv-radio.com/francemusique/all/francemusiquehautdebit.mp3 --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/shantiq/france_musique_aujourdhui-$NOW.mp3}" vlc://quit ;
VLC media player 1.2.0-git Twoflower (revision 1ee61ad)
[0xa49630] dummy interface: using the dummy interface module...
[0xa62000] mux_dummy mux: Open
[0xa67690] access_http access: Raw-audio server found, mp3 demuxer selected
[0xa4cf50] dummy demux: command `quit'
shantiq@shan:~$ 

```




as you see perfect


i think it might be a path issue   ??

could otherwise maybe be :  i keep my .cron file in my home folder and edit it through mousepad which has not been a problem with other cron jobs ?

---

### Post by mc4man on 2011-09-22
gotta go to work - anyway I use nano to do crontab (crontab -e in terminal
Would have rather seen you run the script itself, not just the commands in it.

Ex. - 
> doug@doug-XPS-M1330:~$ [COLOR="Blue"]/home/doug/bin/test2[/COLOR] 
VLC media player 1.2.0-git Twoflower (revision 1.2.0~~git20110916+r874)
[0x983a948] dbus interface: listening on dbus as: org.mpris.MediaPlayer2.vlc
[0x983b1e8] dummy interface: using the dummy interface module...
[0x9859128] mux_dummy mux: Open
[0x98592f0] access_http access: Raw-audio server found, mp3 demuxer selected
[0x986f540] idummy demux: command `quit'


---

### Post by shantiq on 2011-09-22
run this way you mean?

```
cd Desktop/SCRIPTS-BashConvert-DO.NOT.DELETE
shantiq@shan:~/Desktop/SCRIPTS-BashConvert-DO.NOT.DELETE$ ./frmusique.sh
VLC media player 1.2.0-git Twoflower (revision 1ee61ad)
[0x2569ec0] dummy interface: using the dummy interface module...
[0x2569510] mux_dummy mux: Open
[0x256cee0] access_http access: Raw-audio server found, mp3 demuxer selected
[0x2579a00] dummy demux: command `quit'
shantiq@shan:~/Desktop/SCRIPTS-BashConvert-DO.NOT.DELETE$ 

```


works fine    but not as yet  with cron and crontab

---

### Post by shantiq on 2011-09-23
also now running this script


```
#!/bin/bash
NOW=$(date +"%b-%d-%y")
cvlc --run-time=3600 http://195.10.10.210/rtve/radio3.mp3 --sout "#duplicate{dst=std{access=file,mux=raw,dst=/home/shantiq/elefanteRTVE-$NOW.mp3}" vlc://quit ;
```

with crontab


```
17 14 * * *    /home/shantiq/Desktop/SCRIPTS-BashConvert-DO.NOT.DELETE/elefantesRTVE3.sh
```


and it does not start but the script works perfectly **on its own** so it is a kink with cron although cron runs this


> 0 22 * * 0   get_iplayer --get --force --type=liveradio --stop 3600 "http://www.bbc.co.uk/mediaselector/4/gtis/?server=cp60703.live.edgefcs.net&identifier=Special_Event1_UK@s6485&kind=akamai&application=live"  && sudo shutdown -h +15


0 23 * * 2,3,4   get_iplayer --get --force --type=liveradio --stop 5400 "http://www.bbc.co.uk/mediaselector/4/gtis/?server=cp60703.live.edgefcs.net&identifier=Special_Event1_UK@s6485&kind=akamai&application=live"  && sudo shutdown -h +45


**perfectly!**



so it is an issue between script and cron on my system


any offers???

---

### Post by mc4man on 2011-09-23
How about something a bit simpler to test - 
```
mkdir scripts
```
Move elefantesRTVE3.sh into the scripts folder - lose the .sh extension
Then in your crontab - 
```
17 14 * * *    /home/shantiq/scripts/elefantesRTVE3
```

---

### Post by shantiq on 2011-09-23
ok did that still nada :KS

---

