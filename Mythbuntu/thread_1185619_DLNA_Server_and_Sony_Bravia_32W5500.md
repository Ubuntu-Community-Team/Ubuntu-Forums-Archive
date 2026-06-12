---
title: "DLNA Server and Sony Bravia 32W5500"
date: 2009-06-12
forum: Mythbuntu
---

### Post by rojjjjjjj on 2009-06-12
I have recently purchased a new Sony Bravia LCD TV which has inbuilt DLNA functionality to link to a server and access Photo's and Music.

I have also been running Mythbuntu for several years and thought that it would be a simple enough process for the TV to find the Mythbuntu server and access the resources however this was not the case.

The TV can find the Mythbuntu Media server but cannot access any resources.

I then tried to find other DLNA media servers to try out on Mythbuntu.

This excellent link provided me with some options:

[http://www.rbgrn.net/content/21-how-to-choose-dlna-media-server-windows-mac-os-x-or-linux](http://www.rbgrn.net/content/21-how-to-choose-dlna-media-server-windows-mac-os-x-or-linux)

I set about installing 

Fuppes
Media Tomb
Twonky Media
Ushare

Only Twonky was able to be found and accessible. 

After some more searching I found a small project MiniDLNA which after checking out the code and compiling works like a charm.

I am posting here to ask what peoples experiences of DLNA Servers and from what seems to be a compliant server seems to offer very different results.

I would also be keen to see Mythbuntu include a DLNA server that I could make use of.

Many thanks

---

### Post by tvbox on 2009-06-14
hi!

I'v got the same tv box. And also have almost the same problem. Minidlna is not working.
It is not found by the tv.

How did you make it work?

pls help me

thx in advance

---

### Post by tvbox on 2009-06-14
ushare and mediatomb is found but not supported... and minidlna seems to be running, but not found by the tv at all .

---

### Post by joshoekstra on 2009-06-14
Whack, installed minidlna and ran it with ./minidlna -f configfile -d and after setting the right dirs for sharing it show up on my 40W5500.

I had some trouble that minidlna was found but it only shared a std dir and not the configured dirs but this was corrected by stopping minidlna, removing /tmp/minidlna/files.db and restarting minidlna.
Wish mythtv could be made compatible with DLNA, cause that's where my media with metadata lives.

---

### Post by tvbox on 2009-06-14
what kind of files did you share with your tv?
(jpg, mp3, for avhcd - mp4? mts?)

---

### Post by tvbox on 2009-06-14
cannot see dlna server via tv box,
but minidlna's running
what do you think? how can i solve this problem?
and another question, how can you watch avhcd formats via minidlna?

thx in advance

./minidlna -f /etc/minidlna.conf -d
[2009/06/14 17:08:53] minidlna.c:619: warn: Starting MiniDLNA version 1.0.13.
[2009/06/14 17:08:53] minidlna.c:652: warn: Creating new database...
[2009/06/14 17:08:53] scanner.c:740: warn: Scanning /home/tv/Pictures
[2009/06/14 17:08:53] minidlna.c:696: warn: HTTP listening on port 49153
[2009/06/14 17:08:53] scanner.c:808: warn: Scanning /home/tv/Pictures finished (3 files)!
[2009/06/14 17:08:53] scanner.c:740: warn: Scanning /home/tv/Music
[2009/06/14 17:08:53] scanner.c:740: info: Scanning /home/tv/Music/Tosca - Delhi
[2009/06/14 17:08:53] scanner.c:808: warn: Scanning /home/tv/Music finished (12 files)!
[2009/06/14 17:08:53] scanner.c:740: warn: Scanning /home/tv/Videos
[2009/06/14 17:08:53] metadata.c:521: debug: Parsing video bd-twty.CD01.avi...
[2009/06/14 17:08:53] metadata.c:648: debug: Container: 'avi' [bd-twty.CD01.avi]
[2009/06/14 17:08:53] metadata.c:789: debug: Stream 0 of bd-twty.CD01.avi is 688x384 XViD
[2009/06/14 17:08:53] metadata.c:521: debug: Parsing video bd-twty.CD01.mp4...
[2009/06/14 17:08:53] metadata.c:648: debug: Container: 'mov,mp4,m4a,3gp,3g2,mj2' [bd-twty.CD01.mp4]
[2009/06/14 17:08:53] metadata.c:779: debug: No DLNA profile found for MP4/AVC/SD file bd-twty.CD01.mp4
[2009/06/14 17:08:53] metadata.c:784: debug: Stream 0 of bd-twty.CD01.mp4 is h.264
[2009/06/14 17:08:53] metadata.c:521: debug: Parsing video test.mp4...
[2009/06/14 17:08:53] metadata.c:648: debug: Container: 'mov,mp4,m4a,3gp,3g2,mj2' [test.mp4]
[2009/06/14 17:08:53] metadata.c:779: debug: No DLNA profile found for MP4/AVC/SD file test.mp4
[2009/06/14 17:08:53] metadata.c:784: debug: Stream 0 of test.mp4 is h.264
[2009/06/14 17:08:53] metadata.c:521: debug: Parsing video test.mts...
[2009/06/14 17:08:54] metadata.c:648: debug: Container: 'mov,mp4,m4a,3gp,3g2,mj2' [test.mts]
[2009/06/14 17:08:54] metadata.c:779: debug: No DLNA profile found for MP4/AVC/SD file test.mts
[2009/06/14 17:08:54] metadata.c:784: debug: Stream 0 of test.mts is h.264
[2009/06/14 17:08:54] scanner.c:808: warn: Scanning /home/tv/Videos finished (16 files)!
[2009/06/14 17:08:54] inotify.c:182: debug: Add watch to /home/tv/Music/Tosca - Delhi

---

### Post by joshoekstra on 2009-06-14
jpg, mp3 works without a hitch
mpg(2)(DVB-T and PVR-recordings) work
mp4 don't seem te be picked up(by either minidlna or TV) and I don't have mts or avhcd-files as far as I know.
ts don't work either.
I'm not sure if .mp4 files do get picked up at all by minidlna but it seems to respond better than WMP 11

---

### Post by tvbox on 2009-06-14
could you show me your config file? I don't know why... may tv cannot find minidlna server:(it finds mediatomb and ushare --but cannot connect them).

---

### Post by joshoekstra on 2009-06-14
I started with the std config and it showed up immediately on the TV.
Later on I only added some directories.
How do you start minidlna?

---

### Post by tvbox on 2009-06-14
./minidlna -f /etc/minidlna.conf -d

---

### Post by joshoekstra on 2009-06-14
hmmm, that's the same way I do it.```
# port for HTTP (descriptions and SOAP) traffic
port=8200

# set this to the directory you want scanned.
# * if have multiple directories, you can have multiple media_dir= lines
# * if you want to restrict a media_dir to a specific content type, you
#   can prepend the type, followed by a comma, to the directory:
#   + "A" for audio  (eg. media_dir=A,/home/jmaggard/Music)
#   + "V" for video  (eg. media_dir=V,/home/jmaggard/Videos)
#   + "P" for images (eg. media_dir=P,/home/jmaggard/Pictures)
#media_dir=/opt
media_dir=A,/bigdisk/MP3
media_dir=V,/bigdisk/Film
media_dir=V,/bigdisk/video
# set this if you want to customize the name that shows up on your clients
friendly_name=Eau Rouge 

# this should be a list of file names to check for when searching for album art
# note: names should be delimited with a forward slash ("/")
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# set this to no to disable inotify monitoring to automatically discover new files
# note: the default is yes
inotify=yes

# set this to yes to enable support for streaming .jpg and .mp3 files to a TiVo supporting HMO
enable_tivo=no

# default presentation url is http address on port 80
#presentation_url=http://www.mylan/index.php

# report system uptime instead of daemon uptime
system_uptime=no

# notify interval in seconds. default is 30 seconds.
notify_interval=900

# serial and model number the daemon will report to clients
# in its XML description
serial=12345678
model_number=1
```
Is my config, only thing changed = media_dir and friendlyname.
```
Only thing that can be important is that I used the following command in the past to make mythtv work(which I couldn't)
route add -net 239.0.0.0/8 eth0
```
But that shouldn't matter anymore since I rebooted the machine and another thing I did was search on the TV via setting network and then so on..

EDIT: I guess you got it working gathering from your post [here]("http://ubuntuforums.org/showpost.php?p=7456311&postcount=5")?

---

### Post by lxowle on 2009-06-14
Hi there,

I have the same TV, and I'm trying to setup minidlna. Following your instructions, I've got it up and running, but I can get it to display any pictures or videos. However, it can find and play my mp3's which is a great start.

However, it is almost as if the video and picture aspects of minidlna aren't running - if I put a jpeg into a mp3 directory (these folders are found by the TV in pictures, audio and video) it doesn't show up at all under the pictures menu on the tv.

---

### Post by lxowle on 2009-06-14
OK - I've found that when I restart minidlna, it is actually restarting (for example, I can change the friendly_name). However, it never changes the folders it looks in for media - this is stuck with settings I used the very first time I ran the program. Is there some file somewhere (apart from the config file) that I can delete to fix this?

---

### Post by lxowle on 2009-06-14
Well, I sort of have it running now. By adding a new media folder to the config file, and then copying content into it, it is picked up on the tv. So far, I can only display mpg's recording from a PVR, but this is not too bad. Thanks to all for the above posts.

---

### Post by BigStan23 on 2009-06-19
Same thing happened to me.  It stores all it's temp files in /tmp/minidlna.  If you go and delete everything out of that directory (rm -rf /tmp/minidlna), it will rescan everything.

> **lxowle said:**
> OK - I've found that when I restart minidlna, it is actually restarting (for example, I can change the friendly_name). However, it never changes the folders it looks in for media - this is stuck with settings I used the very first time I ran the program. Is there some file somewhere (apart from the config file) that I can delete to fix this?

---

### Post by lxowle on 2009-06-29
Thanks for the advice above - with it I've got minidlna working pretty well, especially now I know where the tmp files are stored. I want to thank everyone who contributed to this thread - I've never compiled software from source before, but following all instructions here and documentation that came with minidlna I'm up and running.

I have another question. Some of my videos work, and some don't. Has anyone found a way of reliably ripping dvds so that they are accessible via dlna to the Sony Bravia 32W5500? I know this must be possible, but I haven't figured it out yet.

---

### Post by lxowle on 2009-06-29
Ah, it is actually straightforward. Just a simple rip using acidrip where the audio and video codecs are set to "copy" and the container format is set to "mpeg" works. 

The first time I tried this it didn't work, but that was just a case of minidlna not updating my videos directory. By killing it, deleting the tmp files and restarting it, the videos were found by both the minidlna and the tv.

This is pretty cool, I wouldn't really have expected that this would work as well as it does.

---

### Post by craigchambers on 2009-06-30
Acidrip is the way I did it too.  I've been successfully using MiniDLNA for about 2 months now, and it look like others on here have worked out the same foibles as me (e.g. the temp folder issue).  
I have found that the latest releases are broken on my Ubuntu machine.
I am using an older version for now, and periodically trying the latest version. 
I have attached the version that works for me to this thread.

/Craig

---

### Post by atomota on 2009-07-01
Thanks a lot, minidlna is great and streams nicly to my TV (Sony Bravia). 

But it just works if I execute the daemon from a root shell but not by booting it via the init process (Ubuntu 9.04).

I used the script  linux/minidlna.init.d.script (you'll find it in the cvs root dir) for starting and stopping the appropriate daemon process by copying it to /etc/init.d/minidlna

Afterwards I setup init.d by executing: sudo update-rc.d minidlna defaults 99

It  works properly if I execute it in console by the root user: /etc/init.d/minidlna start 

But when the system re-boots and init.d executes the same script then a segementation fault is caused :-(

I tried the most recent CVS version and also the posted one above->same result.

Was anybody able to use minidlna by starting it via init.d? Maybe there is a need of a particular environment variable?

---

### Post by craigchambers on 2009-07-01
> **atomota said:**
> Was anybody able to use minidlna by starting it via init.d? Maybe there is a need of a particular environment variable?

I have the same problem, and there's an issue about this raised on the Sourceforge forum.  Justin Maggard, the developer, does not use Ubuntu and cannot reproduce the problem.

I looked around and one suggestion I saw for this problem with another process was to preface the command in the startup script with 'nohup'.  I haven't tried it and I have no idea if it would work with miniDLNA.  My server is still on Intrepid and so still uses init.d scripts, but I have seen somewhere that Jaunty uses a different startup mechanism to sysvinit called upstart. I've not looked into it on my Jaunty PC though, so this may be incorrect.

/Craig

---

### Post by atomota on 2009-07-02
I tried to start minidlna's process via nohup. This way seems to cause another segementation fault. But your comment about upstart is quite interesting! As far as I understand Jaunty looks like systemvinit regarding /etc/init.d 
But the real trigger is done by upstart's scripts which are located in /etc/event.d and which just invoke scripts located in /etc/init.d

Nevertheless I was not able to fix this. A poor man's solution would be to start minidlna after a user login (executing via ~/.profile or ~/.bashrc) but that is really not satisfying for a server solution :-(

Any suggestions?

---

### Post by craigchambers on 2009-07-02
> **atomota said:**
> But the real trigger is done by upstart's scripts which are located in /etc/event.d and which just invoke scripts located in /etc/init.d

I think that this is only the case for backwards compatibility with sysvinit.  From what I read each of those scripts in /etc/event.d are run when the triggering condition is met.  In the case of the rc2 script there's a check that presumably upstart is aware of for a change to run level 2, and on that happening it basically says to run the /etc/init.d/rc 2 script (thereby seeming to be using standard sysvinit).  

It seems that you could also drop in a script for another app (e.g. miniDLNA) into here rather than in /etc/init.d/ if you knew the syntax for upstart.  Unfortunately there aren't any examples in there at present to help with this. 

Starting, stopping, restarting manually seems to be done via the command initctl (e.g. sudo initctl start minidlna).  

The script below is what I now have in /etc/event.d/minidlna but it doesn't work, either from start-up or via the command above: 
```
# miniDLNA upstart script
#
# This task runs miniDLNA.  it's currently a work in progress

#description	"miniDLNA start-up script"
#author		"Craig Chambers"

start on runlevel 2 
start on runlevel 3 
start on runlevel 4 
start on runlevel 5 

stop on runlevel 0 
stop on runlevel 1 
stop on runlevel 6 r

respawn
exec /usr/sbin/minidlna -f /etc/miniupnpd/minidlna.conf

```
I know that miniDLNA requires the network to be up in order to start and this is what Justin thinks may be the issue with the init.d script. When the script above is run manually, this is definitely the case, so I've no idea why my new script doesn't work.
I'm hoping someone with more experience of this might tell me where I've gone stupidly wrong.

/Craig

---

### Post by atomota on 2009-07-03
> **craigchambers said:**
> I know that miniDLNA requires the network to be up in order to start and this is what Justin thinks may be the issue with the init.d script. When the script above is run manually, this is definitely the case, so I've no idea why my new script doesn't work.


I verified the network dependency by writing a little helper script called "minidlna-debug.sh" to wrap the actual minidlna command:
```

#!/bin/bash                                                                                                      
                                                                                                                 
ping -c 1 ubuntuforums.org > /dev/null                                                                           
net=$?                                                                                                           
now=`date`                                                                                                       
                                                                                                                 
if [ $net == 0 ]; then                                                                                           
  echo "$now info: network is available"                                                                         
else                                                                                                             
  echo "$now error: network has not been initialized"                                                            
fi                                                                                                               
                                                                                                                 
/usr/sbin/minidlna -f /etc/minidlna.conf

```Subsequently I used upstart for starting minidlna and replaced the "exec" part by the following line

```

...
exec /opt/minidlna/minidlna-debug.sh >> /var/tmp/minidlna-debug.log 2>&1 
...

```The debug log "/var/tmp/minidlna-debug.log" will tell you that there is no network connection followed by an error message about the segmentation fault always when 'upstart' is used for starting. And it does not matter if you boot or use the command line by calling: 
>initctl start minidlna

Afterwards I wrote an analog wrapper call within systemvinit compatible section.
By using the systemvinit compatible script, you'll realize that starting the service via command line 
>etc/init.d/minidlna start
results in a successfull network connection and NO segmentation fault.
But booting by the same systemvinit config results in NO network connection followed by a segementation fault.

So I have no idea why upstart and the systemvinit compatible mechanism do not behave the same regarding the service start by command line and the (missing) network connection. 

But I think that my tests are good enough to show that there is an association between the missing network connection and the subsequent segmentation fault.

Other services like sshd and smbd also depend on a network connection and despite of that they start properly although no user login is done before. How am I able to boot minidlna after having a proper network connection? Or how should minidlna's daemon (initialization) be configured so that it behaves like the daemons mentioned before?

Achim

---

### Post by t0mmy_d on 2009-07-05
Hi, new to these forums & am trying to setup a DLNA server on Jaunty to work with my Sony Bravia.  Mini DLNA seems to be the one people are suggesting, but I can't find it!  There aren't any files available to download on the SourceForge project pages.  Can anyone help?

---

### Post by atomota on 2009-07-05
> **t0mmy_d said:**
> Hi, new to these forums & am trying to setup a DLNA server on Jaunty to work with my Sony Bravia.  Mini DLNA seems to be the one people are suggesting, but I can't find it!  There aren't any files available to download on the SourceForge project pages.  Can anyone help?

On MiniDLNA 's project page you'll find advise about how to get the projects fresh source code after clicking the "Develop" tab. There will be a tool mentioned "Concurrent Versions System" (CVS) which you should install first. Then you'll be able to download the latest source code.

You should install CVS via your preffered package manager, eg. synaptic, apt-get or aptitude.

After downloading the source code via CVS you should read the INSTALL file for further instructions. If you think your system meets all preconditions then start a "make". If not, you'll maybe have to install some further packages and start "make" again... 

Good Night, and Good Luck ;)

Achim

---

### Post by craigchambers on 2009-07-05
Tommy, you have to use cvs to download the source files.  The procedure is listed on the Sourceforge pages, under the Develop tab.
```
cvs -d:pserver:anonymous@minidlna.cvs.sourceforge.net:/cvsroot/minidlna login

cvs -z3 -d:pserver:anonymous@minidlna.cvs.sourceforge.net:/cvsroot/minidlna co -P modulename
```
I use the following command which downloads everything to your current folder:
```
cvs -z3 -d:pserver:anonymous@minidlna.cvs.sourceforge.net:/cvsroot/minidlna co -P *
```

You may need to do the login command first, though I don't think that I have done this since the first time I downloaded it.

I actually posted a zip containing a CVS dump that I downloaded in early April (Latest versions don't work for me) earlier in this thread.

Regards,
Craig

---

### Post by t0mmy_d on 2009-07-07
I think I'm being really stupid here, but I've never had to install anything outside of apt-get.  Whenever I run "make" it always ends with this error: 
[INDENT]*** No rule to make target `-lexif', needed by `minidlna'. Stop
[/INDENT]Does that mean I'm missing something? (this is using the files Craig uploaded on the other page, the download didn't work for me)  I get a similar error whenever I try to "make" install any other software package I've tried (such as gmediaserver)

---

### Post by craigchambers on 2009-07-07
Tommy, I'm no expert so I'm not sure about your exact problem.  Have you read the INSTALL file and ensured that you meet the dependencies?

- libexif
- libjpeg
- libid3tag
- libFLAC
- libvorbis
- sqlite3
- libavformat (the ffmpeg libraries)
- libuuid

I had to Google some of these to find the correct packages to install with Synaptic (or apt-get).  Finally, you will need to ensure that you have a compiler (gcc and/or g++ (I'm not sure, so make sure you have them both!)), and 'make' also installed.  Hopefully that's it :-)

/Craig

---

### Post by t0mmy_d on 2009-07-08
I've tried to install these softwares but I'm having some problems.

- libexif -  installed libexif12 off apt-get
- libjpeg - configured & "make" worked OK
- libid3tag - installed libid3tag0 off apt-get
- libFLAC - installed libflac8 off apt-get
- libvorbis - Installed OK
- sqlite3 - installed OK
- libavformat (the ffmpeg libraries) -  installed libavformat off apt-get
- libuuid - installed through apt-get

Even after all this, running "make" still doesn't work, I get the error (the files are in a folder on my desktop if that makes any difference):

```
./genconfig.sh
-e 
ERROR!  Cannot continue.
-e The following required libraries are either missing, or are missing development headers:

-e libavcodec libavformat libavutil libvorbis libid3tag libexif libjpeg libuuid libsqlite3 

make: *** [config.h] Error 1

```

---

### Post by craigchambers on 2009-07-09
Ah, I think I see the issue... You need to install the 'Dev' versions of all those dependencies.  These versions contain all the code required to build them into other programs.  I'm no programmer, so it slipped my mind when I said to install the utilities!

Hopefully we're getting there...

/Craig

---

### Post by t0mmy_d on 2009-07-09
We are indeed getting closer, now I am only missing libuuid.  I've tried searching for the "dev" package, but it doesn't seem to exist.  To be on the safe side I tried installing all the libuuid packages I could find (libuuid1,  libuuidm-ocaml-dev, libuuid1-dbg, libuuid-perl)

---

### Post by atomota on 2009-07-09
Hi Tommy,

Did you try to install "uuid-dev"?

Achim

---

### Post by t0mmy_d on 2009-07-13
I hadn't...did that and the make worked...but I can't seem to run minidlna, get the "command not found" error

---

### Post by stedy6 on 2009-07-14
You need to type: ./minidlna -f minidlna.conf -d   
The '-d' force minidlna to run in terminal.  
./minidlna for display help tekst

---

### Post by t0mmy_d on 2009-07-15
Thanks for all of your help, got it working at last, but only for photos & music.  It just wasn't liking video files though.

...then I stumbled upon a beta version of a Java-based PS3 Server...and that works straight out of the box with transcoding and no hassle!  Its also apparently cross-compatible with Windows.

---

### Post by craigchambers on 2009-07-20
Hi Tommy,

Good for you.  I'm glad you found something that works for you.  It's horses for courses I guess.  
I run my server 24/7 without a GUI, so I don't think a Java based solution that works on Windows is likely to work for me.  

/Craig

---

### Post by lxowle on 2009-07-24
For those of you having trouble running minidlna at start-up - did you try using the ubuntu GUI for the job (System->Preferences->Startup Applications)?

That's what I use and it works fine - even after a standby etc.

---

### Post by craigchambers on 2009-07-25
Hi lxowle,

That might help some folks, but the start-up app seems to be a part of Gnome.  I'm running my server headless, so generally no x-session is running.

Cheers,
Craig

---

### Post by MoRoBoShi on 2009-07-31
Hi to all,
I'm tring to configure a minidlna server on intrepid.
I installed minidlna in post#18 from craigchambers (many thx for files) but I'm not able to play any video I see nothing under video folders...

Anyway my questions are:
 is someone able to stream an mpg to the tv?
 Is it possible i miss something during installation of minidlna?

Unluckily streaming is not working
..........so i try to play a little .mpg file from  USB and it works!
....Recently I try to play a 600MB mpg file from USB and it doesn't work...:-(

Do someone know which are specification for video files supporded by Bravia?

Ooops...I forget.. my tv is a 46w5500 (hoping that basically is  similiar to 32w5500 if not identical, except for size..)

---

### Post by MoRoBoShi on 2009-07-31
Hi to all,
I'm tring to configure a minidlna server on intrepid.
I installed minidlna in post#18 from craigchambers (many thx for files) but I'm not able to play any video I see nothing under video folders...

Anyway my questions are:
 is someone able to stream an mpg to the tv?
 Is it possible i miss something during installation of minidlna?

Unluckily streaming is not working
..........so i try to play a little .mpg file from  USB and it works!
....Recently I try to play a 600MB mpg file from USB and it doesn't work...:-(

Do someone know which are specification for video files supported by Bravia?

Ooops...I forget.. my tv is a 46w5500 (hoping that basically is  similiar to 32w5500 if not identical, except for size..)

---

### Post by rojjjjjjj on 2009-07-31
Hi, I have found that for video's the PS3 Media Server Project has a great solution that allows the transcoding of AVI and other video formats to be DLNA compatible formats for streaming.

The projects latest builds provide support for the Sony Bravia  W range as well as new support for XBMC clients as well as PS3's.

The project uses mencoder, ffmpeg and mplayer to provide the support and the media center was immediately recognised by my Sony Bravia TV.

I hope this helps. The PS3 Media Server just requires the installation of the Sun JRE and then launches from a script file. Its very impressive.

---

### Post by craigchambers on 2009-08-03
> **MoRoBoShi said:**
> Hi to all,
I'm tring to configure a minidlna server on intrepid.
I installed minidlna in post#18 from craigchambers (many thx for files) but I'm not able to play any video I see nothing under video folders... 
No problem on the file - but Justin Maggard has now provided an official binary on the Sourceforge pages ([https://sourceforge.net/projects/minidlna/](https://sourceforge.net/projects/minidlna/)) that is probably better.  Otherwise you could try to get the sources and build for yourself :-)

> Anyway my questions are:
 is someone able to stream an mpg to the tv?
I have .mpg files working on my W5500 (straight copies from a DVD using AcidRip)
> Is it possible i miss something during installation of minidlna?
What exactly did you do to install?  Have you set the paths in the config file?
> Do someone know which are specification for video files supported by Bravia?
Basically, whatever the Sony digital Camcorders use.  i.e. MPEG 2 (.mpg with MPEG-PS video and AC3 audio - this is what you get if you rip a DVD); AVCHD (.m2ts with H264 (AKA AVC) video and AC3 Audio) and one other format of their camcorders that I can't remember!

/Craig

---

### Post by FlemmingJ on 2009-08-24
> **joshoekstra said:**
> Whack, installed minidlna and ran it with ./minidlna -f configfile -d and after setting the right dirs for sharing it show up on my 40W5500.

I had some trouble that minidlna was found but it only shared a std dir and not the configured dirs but this was corrected by stopping minidlna, removing /tmp/minidlna/files.db and restarting minidlna.
Wish mythtv could be made compatible with DLNA, cause that's where my media with metadata lives.

please "joshoekstra" or some one else, tell me how to install minidlna - seems to be working for 40v5500, right.

regards and thanks Flemming

---

### Post by craigchambers on 2009-08-26
> **FlemmingJ said:**
> please "joshoekstra" or some one else, tell me how to install minidlna - seems to be working for 40v5500, right.

regards and thanks Flemming

What exactly are you struggling with Fleming?  Have you downloaded the source and can't build it? Or are having trouble with the binaries?
miniDLNA works on my 40W5500, I think that the DLNA client is the same in the V series.

/Craig

---

### Post by FlemmingJ on 2009-08-26
> **craigchambers said:**
> What exactly are you struggling with Fleming?  Have you downloaded the source and can't build it? Or are having trouble with the binaries?
miniDLNA works on my 40W5500, I think that the DLNA client is the same in the V series.

/Craig

I can't build it I'm affraid. Please provide a step-by-step guide.

thanks a lot

Flemming

---

### Post by craigchambers on 2009-08-28
> **FlemmingJ said:**
> I can't build it I'm affraid. Please provide a step-by-step guide.

thanks a lot

Flemming

I suggest that if you don't know how to build it you just use the binaries on the sourceforge pages.  It should save you a lot of trouble.  I have tried them previously and they work on my server, so hopefully you will have no problems with them.

The .tar.gz file has the binary and config in the correct folder hierarchy.  Once they are in the same place on your system, edit the config file so that the correct media locations are in it then run it with:
/usr/sbin/minidlna -f /etc/minidlna.conf

HTH.
/Craig

---

### Post by FlemmingJ on 2009-08-28
> **craigchambers said:**
> I suggest that if you don't know how to build it you just use the binaries on the sourceforge pages.  It should save you a lot of trouble.  I have tried them previously and they work on my server, so hopefully you will have no problems with them.

The .tar.gz file has the binary and config in the correct folder hierarchy.  Once they are in the same place on your system, edit the config file so that the correct media locations are in it then run it with:
/usr/sbin/minidlna -f /etc/minidlna.conf

HTH.
/Craig

I will try that - wasn't aware of the existence of binaries.

thanks

Flemming

---

### Post by FlemmingJ on 2009-08-28
> **craigchambers said:**
> I suggest that if you don't know how to build it you just use the binaries on the sourceforge pages.  It should save you a lot of trouble.  I have tried them previously and they work on my server, so hopefully you will have no problems with them.

The .tar.gz file has the binary and config in the correct folder hierarchy.  Once they are in the same place on your system, edit the config file so that the correct media locations are in it then run it with:
/usr/sbin/minidlna -f /etc/minidlna.conf

HTH.
/Craig

hi Craig

It's working on my Bravia 40V5500 - and very fast I must say.

best regards

---

### Post by stedy6 on 2009-08-28
> **craigchambers said:**
> 
respawn
exec /usr/sbin/minidlna -f /etc/miniupnpd/minidlna.conf
[/code]I know that miniDLNA requires the network to be up in order to start and this is what Justin thinks may be the issue with the init.d script. When the script above is run manually, this is definitely the case, so I've no idea why my new script doesn't work.
I'm hoping someone with more experience of this might tell me where I've gone stupidly wrong.
/Craig


I tried the init.d on a ubuntu server whit Webmin, past the code directly into webmin's Edit Action in the Bootup and Shutdown configuration, for a custom made "bootup and shutdown action". it actual works.... 
I found the script where placed in rc2.d , rc3.d and rc5.d named 99minidlna by Webmin. 
 
I guess there Is something whit user privileges thats cause the script to fail on ubuntu systems. Webmin runs every proses as root.  
 
I have never reported this as a bug, but I have noticed for many(all??) cvs version of minidlna I have tested that when I start it as a regular user then i cause one error: 
 
nn@desktop:~/workspace/minidlna$ ./minidlna -f minidlna.conf -d 
[2009/08/29 00:19:22] daemonize.c:76: error: Unable to open pidfile for writing /var/run 
 
So if ubuntu dont run inti.d scripts as root then the init.d script cant manage to create the pidfile?? 
 
start)  log_daemon_msg "Starting minidlna" "minidlna" 
        start-stop-daemon --start --quiet --pidfile /var/run/minidlna.pid --startas $MINIDLNA -- $ARGS $LSBNAMES 
        log_end_msg $? 
        ;; 


also reported at: [https://sourceforge.net/forum/message.php?msg_id=7594235](https://sourceforge.net/forum/message.php?msg_id=7594235)

---

### Post by FlemmingJ on 2009-08-31
> **FlemmingJ said:**
> hi Craig

It's working on my Bravia 40V5500 - and very fast I must say.

best regards

BTW: it seems like Bravia 40V5500 only supports MPG's. Is that a fact. I have a bunch of AVI's. How do I make them visible on the TV-set.

thx & regards Flemming

---

### Post by joshoekstra on 2009-08-31
> **FlemmingJ said:**
> BTW: it seems like Bravia 40V5500 only supports MPG's. Is that a fact. I have a bunch of AVI's. How do I make them visible on the TV-set.

thx & regards Flemming
That's a fact, recoding 2 mpeg will show them. PS3 mediaserver apparantly does that, recoding on the fly. It will use some processing power though...

---

### Post by FlemmingJ on 2009-09-01
> **joshoekstra said:**
> jpg, mp3 works without a hitch
mpg(2)(DVB-T and PVR-recordings) work
mp4 don't seem te be picked up(by either minidlna or TV) and I don't have mts or avhcd-files as far as I know.
ts don't work either.
I'm not sure if .mp4 files do get picked up at all by minidlna but it seems to respond better than WMP 11

hi again

It seems like MiniDLNA only supports MPEG2, MP3 and JPG. I can't find a list of supported mediatypes though. Do you know is there is such a list.
Specificilly I am looking for AVI and ISO support.

regards Flemming

---

### Post by craigchambers on 2009-09-01
> **FlemmingJ said:**
> BTW: it seems like Bravia 40V5500 only supports MPG's. Is that a fact. I have a bunch of AVI's. How do I make them visible on the TV-set.

thx & regards Flemming

There's a wealth of information in this very thread.  I have posted this information at least twice...
e.g post #42 
> Basically, whatever the Sony digital Camcorders use. i.e. MPEG 2 (.mpg with MPEG-PS video and AC3 audio - this is what you get if you rip a DVD); AVCHD (.m2ts with H264 (AKA AVC) video and AC3 Audio) and one other format of their camcorders that I can't remember!

Unfortunately, the 5500 series has very minimal codec and container support and your AVI files are not supported.  I wish that they were too!

/Craig

---

### Post by joshoekstra on 2009-09-03
> **FlemmingJ said:**
> hi again

It seems like MiniDLNA only supports MPEG2, MP3 and JPG. I can't find a list of supported mediatypes though. Do you know is there is such a list.
Specificilly I am looking for AVI and ISO support.

regards Flemming

It's not that miniDLNA doesn support it, it's the W5500 that doesn't because of DSP that was chosen for it. If you're looking for avi-support PS3 mediaserver might help, ISO I'm not to sure about, depends what's exactly on it.
My manual tells me something about the media-types, but right now too lazy to search for it ;)

---

### Post by MoRoBoShi on 2009-09-05
> **craigchambers said:**
> No problem on the file - but Justin Maggard has now provided an official binary on the Sourceforge pages ([https://sourceforge.net/projects/minidlna/](https://sourceforge.net/projects/minidlna/)) that is probably better.  Otherwise you could try to get the sources and build for yourself :-)


I have .mpg files working on my W5500 (straight copies from a DVD using AcidRip)

What exactly did you do to install?  Have you set the paths in the config file?

Basically, whatever the Sony digital Camcorders use.  i.e. MPEG 2 (.mpg with MPEG-PS video and AC3 audio - this is what you get if you rip a DVD); AVCHD (.m2ts with H264 (AKA AVC) video and AC3 Audio) and one other format of their camcorders that I can't remember!

/Craig

Craig... this helps me a lot!! Thank for every suggestion!!!!!

Video Streaming is working Now!! !:lolflag:iabadabadù!

---

### Post by stedy6 on 2009-10-07
> **atomota said:**
> Was anybody able to use minidlna by starting it via init.d? Maybe there is a need of a particular environment variable?


This issue seams like it is solved now, -i run Ubuntu 8.10
  sudo cp  minidlna.init.d.script  /etc/init.d/minidlna
  sudo chmod +x /etc/init.d/minidlna
  sudo update-rc.d minidlna defaults
  to remove the startup schript then : sudo update-rc.d -f minidlna remove

---

### Post by mnmzuiderwijk on 2009-10-14
yersterdag installed minidlna (only get the minidnla and the conf file)
Doe the copy thing and did the settings in the conf file eb start the program.
(sorry for my english)
Yust start the program in debug mode and see the the TV (sony 4500) response on the screen. But the program das nog search or make a database. I het 3 files in the directory (MPG, MP3, JPG) But is saing no files on the TV.
There is a connection but no files. Indexing das nog work.
What I am doing wrong?

---

### Post by mnmzuiderwijk on 2009-10-14
> 
What I am doing wrong?
 
Found it. Must do a option -R (minidnla -R) for rebuild the database.
The sony 40Z4500 dat not support video (Yet?) Only photos and music.
It works great.

---

### Post by mihaki on 2009-10-18
> **stedy6 said:**
> This issue seams like it is solved now, -i run Ubuntu 8.10
  sudo cp  minidlna.init.d.script  /etc/init.d/minidlna
  sudo chmod +x /etc/init.d/minidlna
  sudo update-rc.d minidlna defaults
  to remove the startup schript then : sudo update-rc.d -f minidlna remove
-------


In my case (Ubuntu 8.04) that was not enough... minidlna didn't start properly this way. I couldn't find
log messages though, but I guess it was "no network connection" related problem.
After reading update-rc.d manual, I came up with the following solution:

sudo update-rc.d minidlna defaults 98 2

Now minidlna starts properly - I guess the last two numbers specify the priority of the process
in the scheduler (98 means that process starts late t.i. after the network is up). 2 would mean
that process ends early.

Another point... we know that minidlna (although it works flawlessly - at least for me) is still kind of in it's beta stage. I am not sure anyone can guarantee it is bullet-proof against hacker attacks (or is it?).
Of course it will usually run behind broad-band router. But still I think it would be prudent to think about security. I am very new to this field and so I would like to ask what everyone thinks...

Do you think it is safe to run it as root (or even as me (user) )?
What & how is the best way to run minidlna?

I'd be very grateful for some oppinions.

---

### Post by craigchambers on 2009-10-18
> **mihaki said:**
> -------
After reading update-rc.d manual, I came up with the following solution:
sudo update-rc.d minidlna defaults 98 2


Thanks for this. I'm also using Hardy and have trouble with restarts.  I'm going to give it a try.  

> **mihaki said:**
> -------
I am not sure anyone can guarantee it is bullet-proof against hacker attacks (or is it?).
<snip>I'd be very grateful for some oppinions.

My server has two NICs, one for the internal network, and one for the external.  I only bind MiniDLNA to the internal network, so it shouldn't be even available externally.  
I also run a firewall (UFW, configured with GUFW) on my server and only allow access to miniDLNA's ports from my internal subnet.  If you're worried about attacks to services on your machine, then it's worth considering setting up a firewall on it.

Regards,
Craig

---

### Post by mihaki on 2009-10-18
My server has two NICs, one for the internal network, and one for the external.  I only bind MiniDLNA to the internal network, so it shouldn't be even available externally.  
I also run a firewall (UFW, configured with GUFW) on my server and only allow access to miniDLNA's ports from my internal subnet.  
------
Thanks for the advice. In my case the entire subnet is connected to the broad-band router directly. I guess your solution is a lot better... I'll look into it one of these days.


If you're worried about attacks to services on your machine, then it's worth considering setting up a firewall on it.
------
Well, it's not that I am really worried about the attacks. After all, I don't have that many secrets that could be stolen;). 

I am rather interested in the subject from 'academical' point of view - I'd like to learn a few good security practices.

For instance, I have been fooling around with IRC server the other day and I noticed that it always runs as user called 'irc'. Then I read somewhere that in this way - if someone actually managed to hack it - it would still only have irc's privileges (t.i. minimal?). So I've been wondering... what if I run minidlna as unprivileged minidlna user? Has someone actually tried to do it? Or is it worth the effort?

---

### Post by joshoekstra on 2009-10-19
I use minidlna with a 'normal' user, no problem whatsoever.

Has anyone tried to run mythtv 0.22 with the W5500? It's supposed to be working for some Samsung TV's now by changing a header or something. I was hoping it would work for the bravia as well, but cannot go to 0.22 RC1 now because of exams.

---

### Post by craigchambers on 2009-10-19
> **mihaki said:**
> ------
I am rather interested in the subject from 'academical' point of view - I'd like to learn a few good security practices.


As you say, running all services with limited permissions is good practise.  MiniDLNA will run as a regular user provided that you are not trying to use it on a restricted port (i.e. one below 1024).
Good practise for security would always include the use of a firewall.  

There is nothing wrong with the set-up that you have BTW, there is really no need to put two NICs in your machine.  Mine is this way because I host services externally from this machine.  Your router offers protection because presumably it uses NAT to share one external address (either static or dynamic).  This is simply the same role that my server has in my network, hence my absolute requirement for a firewall on that machine.
[Link to more info on NAT]("http://www.dslreports.com/faq/9787")

Hope that helps.

/Craig

---

### Post by mihaki on 2009-10-22
Hi Craig!

Thanks for your explanation. It surely helps me udnerstand my network a bit more:). 

> **mihaki said:**
> -------


sudo update-rc.d minidlna defaults 98 2

Now minidlna starts properly - I guess the last two numbers specify the priority of the process
in the scheduler (98 means that process starts late t.i. after the network is up). 2 would mean
that process ends early.



Well, I guess my celebration was a bit premature. I have been playing with minidlna some more and I realized, that with the above setting minidlna starts correctly in about 60% - 70% of reboots. Otherwise it doesn't start at all! 

I searched a bit and I came up with a theory... I think the problem is simply this: minidlna requires active network connection in order to start. However network, although it probably starts before minidlna command is called, my need some more time in order to go active (waiting for DNS server to approve IP, etc.). Setting init.d priority very low may help a bit. However it may still happen that minidlna will be started before net-interface is completely set.

To solve this problem I 'slightly' modified (merged it with the contents of this thread) my minidlna's init.d script. This script will now ping a gateway address to check if net is up. If ping returns 0, minidlna will be called. If not, 5s delay is inserted and ping is retried. Retry is up to 10 times (usually 2 are enough). This will of course prolong the boot-time. But since I am not planning to restart my server box that often, this is not too big problem for me. 

script: [ATTACH]132694[/ATTACH]

I am still testing this script but so far there have been no problems - minidlna starts 100%. It's my 1st serious-looking script so if anyone cares to give a comment or fix something I did wrong, I'll be very grateful.

---

### Post by Gilron on 2009-11-20
> **joshoekstra said:**
> I use minidlna with a 'normal' user, no problem whatsoever.

Has anyone tried to run mythtv 0.22 with the W5500? It's supposed to be working for some Samsung TV's now by changing a header or something. I was hoping it would work for the bravia as well, but cannot go to 0.22 RC1 now because of exams.

I have tried MythTV 0.22 (Mythbuntu 9.10) with V5500 and it doesn't seem to work. TV cannot find server at all.

--G

---

### Post by craigchambers on 2009-11-20
I have tried to install MythTV on several occasions (the last time about 2 weeks ago), but attempting to get it to work with my Hauppauge DVB-S2 card has always failed, despite ample FAQs and walkthroughs on the subject. My experience of Myth is pretty much entirely negative.

/Craig

---

### Post by joshoekstra on 2009-11-20
Errr, what does this have to do with DLNA? ;)
If you open a new topic on the mythbuntu-forum a lot of people can provide some assistance, especially if you open with the hardware you use, what you tried, what you encountered as errors and son on.

So open a new topic and let yourself be assisted in solving your problems.

---

### Post by Gilron on 2009-11-23
Has anyone been able to stream AVCHD material from minidlna server to Sony TV (5500 series, or any)? I have tried with various different settings but my TV does not show any .m2ts or .mts files I have in my minidlna shared folder. MPEG2-PS works perfectly, but according to marketing material it should also support AVCHD.

So far I've tried woth both Level 4.0 and Level 4.1 encodings with AC3 audio (5.1) and without any audio. Muxing has been done with tsMuxeR into m2ts stream. I have not tried if they work through USB.

--G

---

### Post by craigchambers on 2009-11-25
> **Gilron said:**
> Has anyone been able to stream AVCHD material from minidlna server to Sony TV (5500 series, or any)? --G

There's a bug reported on this on the SourceForge site.

[https://sourceforge.net/tracker/index.php?func=detail&aid=2881371&group_id=243163&atid=1121519](https://sourceforge.net/tracker/index.php?func=detail&aid=2881371&group_id=243163&atid=1121519)

/Craig

---

### Post by laakkus on 2009-12-04
i've just ran into ps3 mediaserver (beta)
it has support for my bravia (40w5500). i'm quite happy with it. needs little extra to stream some stuff, but this forum gives nice advice too. (+link to dl)
 
[http://ps3mediaserver.org/forum/viewtopic.php?f=2&t=3217](http://ps3mediaserver.org/forum/viewtopic.php?f=2&t=3217)

---

### Post by Antoniya001 on 2009-12-06
I just wanted to say THX. to stedy6, mihaki and the rest. Got it to work on Xubuntu 9.10 for my Samsung B650. I actually posted a larger / more detailed description / how to  on my blog so I would remember later on.
 
_[COLOR=#800080][http://www.audiodude.nl/?p=84](http://www.audiodude.nl/?p=84)[/COLOR]_
 
For those still in trouble. Hope it helps.
 
Arjan[]("http://www.audiodude.nl/")

---

### Post by surveyorsteve on 2009-12-08
Hi All, I've followed all the instructions and I think miniDlna is running via Startup Applications but my TV won't see the server. TV network connection appears OK, I'm not sure where else to look. Any suggestions?

---

### Post by craigchambers on 2009-12-14
Hi Steve,

1) Have you tried just starting the server without the start-up script?  Can your TV see the server if you start it with:
/usr/sbin/minidlna -f /etc/minidlna.conf

2) Have you changed any of the settings in the conf file to match your local system?

3) Do you by any chance have 2 NICs?  MiniDLNA has a setting to define which subnet it is visible on.

I wouldn't start with the start-up script until I know that the server is working from a manual start.

Cheers,
Craig

---

### Post by surveyorsteve on 2009-12-15
Hi Craig, thanks for the reply.

TV can't see if started manually, I have edited the config file and I only have one NIC (onboard network). I'll keep having a play with it and let you know. It's probably something blindingly obvious.

Regards
Steve

---

### Post by stedy6 on 2009-12-20
Do you have a firewall active? if so you have to open port 8200 on your server

---

### Post by surveyorsteve on 2009-12-21
The TV found the PC!! Thank you. Not sure exactly what I did but it is something to do with a firewall. I'll explore more after work tonight. Cheers.

---

### Post by joepz on 2009-12-30
> **laakkus said:**
> i've just ran into ps3 mediaserver (beta)
it has support for my bravia (40w5500). i'm quite happy with it. needs little extra to stream some stuff, but this forum gives nice advice too. (+link to dl)
 
[http://ps3mediaserver.org/forum/viewtopic.php?f=2&t=3217](http://ps3mediaserver.org/forum/viewtopic.php?f=2&t=3217)

Hi, just bought me a W5500 and looking into this DLNA topic.
Every now and again people are pointing to the ps3 mediaserver. But not a lot of response.

Is MiniDLNA preferred? And why?
To me MiniDLNA seems pretty complicated to get it to work and even then only mpeg2 movies are recognized.
What is the downside of ps3 media server?

Reading the entire thread I will give the ps3 mediaserer a try and will let you know my findings. Hopefully I do not have to turn to MiniDLNA in the end ;)

Joep

---

### Post by stedy6 on 2009-12-31
I have made a PPA out of minidlna, I don't know if I am able to make a proper release package. The ppa is patched whit latest playlist support...

 [https://launchpad.net/~stedy6/+archive/stedy-minidna]("https://launchpad.net/%7Estedy6/+archive/stedy-minidna")
 deb [http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu](http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu](http://ppa.launchpad.net/stedy6/stedy-minidna/ubuntu) karmic main


the only thing you have to change no is the /etc/minidlna.conf after installation

---

### Post by craigchambers on 2010-01-04
> **joepz said:**
> 
To me MiniDLNA seems pretty complicated to get it to work and even then only mpeg2 movies are recognized.

Video codec support is provided by the TV.  What I presume you are referring to is that miniDLNA doesn't transcode other video formats to those supported by the TV.  I believe this is planned for the future, though I'm not certain.

> **joepz said:**
> 
What is the downside of ps3 media server?Joep

It doesn't run as a daemon without a GUI and hence is no good for standard server installations.  It also has a rather large overhead as it requires Java.  miniDLNA has a small footprint that is even suitable for NAS devices.

I didn't find PS3 Media server easy to use, and it will only run on my main PC, which is not always on.  It's a question of choice.

/Craig

---

### Post by Earthshine on 2010-01-06
All, have a quick question - does anyone know if there are ports other than the configurable one listed in the minidlna.conf that minidlna uses?

I want to keep my iptables up , but for the life of me can't get anything to see minidlna unless I turn iptables off.

Running Ubuntu 9.04.
Here are the rules I've tried and currently have:

#PS3 Minidlna
#iptables -A TRUSTED -i eth0 -p tcp -m tcp --source 10.0.1.0/255.255.255.0 --dport 8200 -j ACCEPT
#iptables -A TRUSTED -i eth0 -p udp -m udp --source 10.0.1.0/255.255.255.0 --dport 8200 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 8200 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 8200 -j ACCEPT

Thanks in advance

---

### Post by craigchambers on 2010-01-11
> **Earthshine said:**
> All, have a quick question - does anyone know if there are ports other than the configurable one listed in the minidlna.conf that minidlna uses?

I think that 1900 udp is used for multicast broadcasts to find all local  upnp (and probably DLNA) devices.

HTH,
Craig

---

### Post by joepz on 2010-01-20
> **craigchambers said:**
> Video codec support is provided by the TV.  What I presume you are referring to is that miniDLNA doesn't transcode other video formats to those supported by the TV.  I believe this is planned for the future, though I'm not certain.



It doesn't run as a daemon without a GUI and hence is no good for standard server installations.  It also has a rather large overhead as it requires Java.  miniDLNA has a small footprint that is even suitable for NAS devices.

I didn't find PS3 Media server easy to use, and it will only run on my main PC, which is not always on.  It's a question of choice.

/Craig


Hi Craig,
Now trying to get miniDLNA to work. Indeed PS3 is not easy to use. As I am a newbee things do not go smooth. I am not sure if/when miniDLNA is running.

I downloaded the 2 files from sourceforge and kept them in the original folder structure.
I do the following in terminal to get it run manually (before using start-up facility)

*****************************************
joep@joep-desktop:~/minidlna/usr/sbin$ ./minidlna -f etc/minidlna.conf -d
Error reading configuration file etc/minidlna.conf
Usage:
    ./minidlna [-d] [-f config_file]
        [-a listening_ip] [-p port]
        [-s serial] [-m model_number] 
        [-t notify_interval] [-P pid_filename]
        [-w url] [-R] [-V] [-h]
******************************************

As you can see it is not able to read the configuration file. Do I need to move the file or change the start-up command?

Thanks a lot,
Joep

---

### Post by joepz on 2010-01-20
> **joepz said:**
> Hi Craig,
Now trying to get miniDLNA to work. Indeed PS3 is not easy to use. As I am a newbee things do not go smooth. I am not sure if/when miniDLNA is running.

I downloaded the 2 files from sourceforge and kept them in the original folder structure.
I do the following in terminal to get it run manually (before using start-up facility)

*****************************************
joep@joep-desktop:~/minidlna/usr/sbin$ ./minidlna -f etc/minidlna.conf -d
Error reading configuration file etc/minidlna.conf
Usage:
    ./minidlna [-d] [-f config_file]
        [-a listening_ip] [-p port]
        [-s serial] [-m model_number] 
        [-t notify_interval] [-P pid_filename]
        [-w url] [-R] [-V] [-h]
******************************************

As you can see it is not able to read the configuration file. Do I need to move the file or change the start-up command?

Thanks a lot,
Joep

Got it to run/execute. DLNA server now shows up in UPnP Inspector :D
Will let you know further progress (if interested).

Cheers

---

### Post by craigchambers on 2010-01-21
> **joepz said:**
> Got it to run/execute. DLNA server now shows up in UPnP Inspector :D
Will let you know further progress (if interested).

Cheers

Glad to hear you got it working.

Your initial problem may have been the following:
>  ./minidlna -f etc/minidlna.conf -d

It should be:
```
./minidlna -f /etc/minidlna.conf -d
```
Note the / before etc/minidlna.conf

You were asking it to find the config file in etc/ in your current folder (e.g. ~/minidlna/usr/sbin/etc/).  

/Craig

---

### Post by joepz on 2010-01-23
Thanks Craig,

Still have to get used to 'browsing' folder structures in terminal.
As I said I have got it running now, my TV sees it, but I have a hard time to define the path/folder for my TV to pick up.

I have a secondary harddrive (internally) containing all my media. It is called 'data'. In Ubuntu I have mapped it to the standard 'media' folder in order to be able to access it. But would the 'dlna server' use this mapping? Looks like it doesn't.

In the Config file I have tried:

media_dir=/data/
media_dir=/media/data/

But no folders show up.

Any advice?
Thanks a lot!
Joep

---

### Post by Tungdykaren on 2010-01-24
> **joepz said:**
> Thanks Craig,

Still have to get used to 'browsing' folder structures in terminal.
As I said I have got it running now, my TV sees it, but I have a hard time to define the path/folder for my TV to pick up.

I have a secondary harddrive (internally) containing all my media. It is called 'data'. In Ubuntu I have mapped it to the standard 'media' folder in order to be able to access it. But would the 'dlna server' use this mapping? Looks like it doesn't.

In the Config file I have tried:

media_dir=/data/
media_dir=/media/data/

But no folders show up.

Any advice?
Thanks a lot!
Joep


Joep, try writing like below:

media_dir=**X**,/data/  <--Where **X** should A for audio, V for video and P for images

Take care!

---

### Post by craigchambers on 2010-01-25
> **Tungdykaren said:**
> Joep, try writing like below:

media_dir=**X**,/data/  <--Where **X** should A for audio, V for video and P for images

Take care!

There shouldn't be any need to set the types available.  Setting specific types is optional.  The setting in the default config is:
media_dir=/opt

Joepz: Can you navigate to /media/data/ in the command line?  If you can then it should be OK in miniDLNA.  If not, then you need to find the correct path.
One thing that may be worth doing is to delete anything in /tmp/minidlna/ before you start it again.  It may be fixed but there used to be an issue where the database used by miniDLNA didn't update on restart.

Cheers,
Craig

---

### Post by xsilvergs on 2010-03-01
Hi I seem to have most bits running, I just need to buy the TV now but have a question regards mounting of drives.

I have a network drive which has three partitions and I mount each one manually in terminal thus:
ut listall
sudo ut attach <id from listall> /dev/nbd0
sudo mount /dev/nbd0 /media/sc101_Music

and repeat for the two remaining positions.

Is there a way to automatically attach and mount using the fstab file or similar?

Thanks.

---

### Post by joepz on 2010-03-01
> **xsilvergs said:**
> Hi I seem to have most bits running, I just need to buy the TV now but have a question regards mounting of drives.

I have a network drive which has three partitions and I mount each one manually in terminal thus:
ut listall
sudo ut attach <id from listall> /dev/nbd0
sudo mount /dev/nbd0 /media/sc101_Music

and repeat for the two remaining positions.

Is there a way to automatically attach and mount using the fstab file or similar?

Thanks.

Hi Xsilvergs,

I followed these instructions:

[http://mesanna.com/2009/02/02/how-to-mount-a-partition-automatically-in-ubuntu-linux/](http://mesanna.com/2009/02/02/how-to-mount-a-partition-automatically-in-ubuntu-linux/)

Works like a charm.

I've got my DLNA server running too finally.
But... opening a 2,5 Mb picture/photo takes about a second. Slow slow slow. Can't imagine to stream a movie properly. Or using it regularly to browse my photo archive.
So... 
What did I do?
I bought me a mediaplayer Mede8er!

Much much better. Added 1.5 Tb disk in it and have it work as a NAS as well.

:p

Good luck to you all!
Joep

---

### Post by xsilvergs on 2010-03-01
Hi joepz, thanks for reply. I seem to have a problem though.

I mounted the drives thus
sudo ut attach <id from listall> /dev/nbd0
sudo mount /dev/nbd0 /media/sc101_Music

but they do not appear in fdisk -l

Here is part of my fstab

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb5 	/media/Music ntfs defaults 0 0
/dev/sdb6	/media/Pictures ntfs default 0 0

# sc101 Toaster
/dev/nbd0	/media/sc101_Digipics ext3 defaults,errors=remount-ro,users,users_xattr,user 0 0
/dev/nbd1	/media/sc101_Music ext3 defaults,errors=remount-ro,users,users_xattr,user 0 0
/dev/nbd2	/media/sc101_Video ext3 defaults,errors=remount-ro,users,users_xattr,user 0 0
```

But it does not mount the drives

Q1: Why do the drives from my SC101 not appear in fdisk -l?
Q2: Can you give more help please?

Thanks

---

### Post by joepz on 2010-03-01
Hi,

I have to admit I am a bit of a nitwit still. Doing my best to learn.

I only now see you talk about 'network drives' (and not an internal secondary hard drive). I am not sure if Messana's 'how to' also works for network drives. Possibly ask her directly? She always responds.

Sorry I am not of help.
Cheers, Joep

---

### Post by nickrout on 2010-03-02
> **xsilvergs said:**
> Hi joepz, thanks for reply. I seem to have a problem though.

I mounted the drives thus
sudo ut attach <id from listall> /dev/nbd0
sudo mount /dev/nbd0 /media/sc101_Music

but they do not appear in fdisk -l

Here is part of my fstab

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb5 	/media/Music ntfs defaults 0 0
/dev/sdb6	/media/Pictures ntfs default 0 0

# sc101 Toaster
/dev/nbd0	/media/sc101_Digipics ext3 defaults,errors=remount-ro,users,users_xattr,user 0 0
/dev/nbd1	/media/sc101_Music ext3 defaults,errors=remount-ro,users,users_xattr,user 0 0
/dev/nbd2	/media/sc101_Video ext3 defaults,errors=remount-ro,users,users_xattr,user 0 0
```

But it does not mount the drives
presumably the attach command needs to be given before the mount command, you may need to set up your own script to do this on boot. Put it in /etc/rc.local> 
Q1: Why do the drives from my SC101 not appear in fdisk -l?

According to this [http://code.google.com/p/sc101-nbd/wiki/QuickStartGuide](http://code.google.com/p/sc101-nbd/wiki/QuickStartGuide) you can't partition a disk on a sc101 except in windows.

---

### Post by xsilvergs on 2010-03-03
Hi nickrout.

I set it up in Windows and then changed the partitions to ext3. It all works fine except for mounting the drives.

I have tried this:
```
#!/bin/bash
# ut-mount-all.sh
# Author: Steven Norder
# Email: info@zeropain.com
# Website: http://www.zeropain.com/wiki
# Date: 06-08-2008
# Description: Automaticly find and mount SC101 Partitions
# Version 0.01

### Config Start
MOUNTDIR=/media
UT=/sbin/ut
FS=ext3
FSOPTIONS=noatime
### Config End

echo -n "Checking if nbd needs to be loaded... "
if [ -e /dev/nbd0 ]
then
        echo "Loaded"
else
        echo "Not Loaded. \nTrying to Load Now..."
        modprobe nbd
fi

n=0
partitionsfound=`ut listall | sed -nr '/^([A-Z0-9]*)-([A-Z0-9]*)-([A-Z0-9]*)-([A-Z0-9]*)-([A-Z0-9]*)\s*(\S*)\s*([0-9]*\.[0-9]*\.[0-9]*\.[0-9]*)\s*([0-9]*)$/p'`

echo "Partition Id\t\t\t\tLabel\tIP\t\tSize\tNBD\tMount Point"
echo "$partitionsfound" |
while read partid label ipaddress size
do
        n=$(($n+1))
        echo -n "$partid\t$label\t$ipaddress\t$size"
        $($UT attach $partid /dev/nbd$n)
        echo -n "\tnbd$n"
        mkdir -p /$MOUNTDIR/$label
        mount -t $FS -o $FSOPTIONS /dev/nbd$n /$MOUNTDIR/$label
        echo "\t$MOUNTDIR/$label"
done
exit 0
```

from [http://code.google.com/p/sc101-nbd/wiki/QuickStartGuide]("http://code.google.com/p/sc101-nbd/wiki/QuickStartGuide") 
but I get errors:
```
Checking if nbd needs to be loaded... Loaded
Partition Id\t\t\t\tLabel\tIP\t\tSize\tNBD\tMount Point
\t\t\tusage: ut OPTIONS
\tnbd1mount: wrong fs type, bad option, bad superblock on /dev/nbd1,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

\t/media/

```

which I don't really understand yet. Can anybody see why ut-mount-all.sh doesn't work under Ubuntu 9.10?

Thanks

---

### Post by xsilvergs on 2010-03-03
Hi nickrout.

I set it up in Windows and then changed the partitions to ext3.

I have trying this:

```
#!/bin/bash
# ut-mount-all.sh
# Author: Steven Norder
# Email: info@zeropain.com
# Website: http://www.zeropain.com/wiki
# Date: 06-08-2008
# Description: Automaticly find and mount SC101 Partitions
# Version 0.01

### Config Start
MOUNTDIR=/media
UT=/sbin/ut
FS=ext3
FSOPTIONS=noatime
### Config End

echo -n "Checking if nbd needs to be loaded... "
if [ -e /dev/nbd0 ]
then
        echo "Loaded"
else
        echo "Not Loaded. \nTrying to Load Now..."
        modprobe nbd
fi

n=0
partitionsfound=`ut listall | sed -nr '/^([A-Z0-9]*)-([A-Z0-9]*)-([A-Z0-9]*)-([A-Z0-9]*)-([A-Z0-9]*)\s*(\S*)\s*([0-9]*\.[0-9]*\.[0-9]*\.[0-9]*)\s*([0-9]*)$/p'`

echo "Partition Id\t\t\t\tLabel\tIP\t\tSize\tNBD\tMount Point"
echo "$partitionsfound" |
while read partid label ipaddress size
do
        n=$(($n+1))
        echo -n "$partid\t$label\t$ipaddress\t$size"
        $($UT attach $partid /dev/nbd$n)
        echo -n "\tnbd$n"
        mkdir -p /$MOUNTDIR/$label
        mount -t $FS -o $FSOPTIONS /dev/nbd$n /$MOUNTDIR/$label
        echo "\t$MOUNTDIR/$label"
done
exit 0
```

from [http://code.google.com/p/sc101-nbd/wiki/QuickStartGuide]("http://code.google.com/p/sc101-nbd/wiki/QuickStartGuide") and will report back.

Thanks

---

### Post by craigchambers on 2010-04-07
Yay - I am now able to stream HD content (though I'm unable to FFwd/Rew) on my Bravia 40W5500 from miniDLNA on my server.  

It's not the simplest thing to get working.  Here are the issues I found:

1) You need a working miniDLNA set-up (of course).

2) Files must be in a format that the TV is happy with.  For AVCHD this means (from my limited testing) .m2ts containers with H264 High profile level 4.0 video and AC3 (dolby digital) sound.  I converted a .mkv file using TsMuxer (available on multiple platforms) and changed the video level to 4.0 while doing so.

3) The Bravia TVs don't support the DLNA standard DLNA_PN field (or so I've read).  I had to use an SQL statement to modify the database entries (in /tmp/minidlna/files.db).  I used the 'sqlitebrowser' app from the repositories
```
update details set
dlna_pn="AVC_TS_MP_HD_AC3_T;SONY.COM_PN=AVC_TS_HD_24_AC3_T;DLNA.ORG_OP=01;DLNA.ORG_CI=0"
where path like "%M2TS";
```
This will change the setting for all .m2ts files and the '24' in there is specifically the video frame rate, so if you have some at different frame rates, you may need to be more granular in your approach.
I'm hoping that the dev might sort this out as it's the worst part of the job!

I'm sure that this isn't exhaustive, for example I think that .ts as an extension is also OK and I haven't tried 1080i or 1080p video.

Hope this helps someone,
Craig

---

### Post by Jingo on 2010-07-18
Thanks for the info.

Could you please post the settings you're using to transcode your movies into x264 and the settings for tsmuxer?

I am actually looking for some good and easy settings to convert DVDs and BDs into some Sony Bravia ex500 compatible format (maintaining quality). Preferable x264. I need subtitles working, and think burning into the stream is the only way.

---

### Post by TackyTiger on 2010-07-26
> **Jingo said:**
> Could you please post the settings you're using to transcode your movies into x264 and the settings for tsmuxer?

The following works for me on Ubuntu 8.04 using mencoder 2:1.0~rc2-0ubuntu13.1+medibuntu1 and tsMuxeR 1.10.6, playing on a Sony Bravia KDL40EX703U TV.

```

#!/bin/sh

IN_FILE="test.avi"
OUT_FILE="test.m2ts"
VIDEO_BR=5000
AUDIO_BR=192
FPS=25

mencoder $IN_FILE -ovc x264 -x264encopts pass=1:bitrate=$VIDEO_BR:nob_adapt:bframes=1:level_idc=40**:subq=6:partitions=all:8x8dct:me=umh** -of rawvideo -oac copy -o /dev/null
mencoder $IN_FILE -ovc x264 -x264encopts pass=2:bitrate=$VIDEO_BR:nob_adapt:bframes=1:level_idc=40**:subq=6:partitions=all:8x8dct:me=umh** -of rawvideo -oac copy -o tmp.264
mencoder $IN_FILE -ovc copy -oac lavc -lavcopts acodec=ac3:abitrate=$AUDIO_BR -of rawaudio -o tmp.ac3
echo 'MUXOPT --no-pcr-on-video-pid --new-audio-pes --vbr  --vbv-len=500\nV_MPEG4/ISO/AVC, "tmp.264", fps='$FPS', insertSEI, contSPS, ar=As source\nA_AC3, "tmp.ac3"' > tmp.meta
tsMuxeR tmp.meta $OUT_FILE
rm tmp.264 tmp.ac3 tmp.meta divx2pass.log

```The settings in bold are optional, they may improve the quality, but to be honest I can't really tell the difference. If you're transcoding from WMV you'll also need -ofps $FPS -vf harddup.

On the subject of getting minidlna to start on boot, I tried adding the following to iface eth0 section of /etc/network/interfaces "up /etc/init.d/minidlna restart || true". While it works when doing a /etc/init.d/networking restart, I had no luck on boot.

---

### Post by Jingo on 2010-07-27
@TackyTiger

Thanks, transcoding.... Hope it works with ex500 and minidlna.

---

### Post by Jingo on 2010-07-28
Thanks for the script, playing fine.

Had to change the dlna_pn according to craigchambers. Had to use "24" even though the FPS are 25.

I'm unable to forward and rewind. Did anyone resolve this?
Mpeg2 stream (vobs) can forward and rewind, so its not a problem with the tv or minidlna!?

---

### Post by Archie369 on 2010-07-30
Guys, i'm from Russia and i find resolve of this problem! i have 40w5500 Bravia tv, try to use XBMC, Twonky, and others, but the simplyst way, to show and explerer folder's on you TV-set is:
1. Install the latest WINE app
2. Go to the [http://www.homemediaserver.ru/page1.php](http://www.homemediaserver.ru/page1.php) (this is russian site, if you don't undersant please go to this link and download Home Media Server software, it is FREE!) [http://www.homemediaserver.ru/files/114/setup_ms.exe](http://www.homemediaserver.ru/files/114/setup_ms.exe)
3. Install this software (double click)
4. you have desktop link, double click on this and select SONY TV 1920x1080
i don't know, but may be this software have english language:)
But work perfectly

---

### Post by Jingo on 2010-07-30
I somewhat solved the ffw(fast forward) and rw (rewind) situation.

minidlna dlna_pn field
instead of
```
update details set
dlna_pn="AVC_TS_MP_HD_AC3_T;SONY.COM_PN=AVC_TS_HD_24_AC3_T;DLNA.ORG_OP=01;DLNA.ORG_CI=0"
where path like "%M2TS";
```

I did
```
update details set 
dlna_pn="MPEG_TS_SD_EU;DLNA.ORG_OP=01;DLNA.ORG_CI=0"
where path like "%M2TS";

```

Pause/play works again, ffw and rw works partly. Only ffw and rw only updates frame once in a while rendering it imposible to know how far it has forwarded!?

---

### Post by holland141 on 2010-12-03
> **craigchambers said:**
> 

2) Files must be in a format that the TV is happy with.  For AVCHD this means (from my limited testing) .m2ts containers with H264 High profile level 4.0 video and AC3 (dolby digital) sound.  I converted a .mkv file using TsMuxer (available on multiple platforms) and changed the video level to 4.0 while doing so.



Hi Craig

I was sent to this post via the response to [http://www.readynas.com/forum/viewtopic.php?f=22&t=48189&p=276356#p276356](http://www.readynas.com/forum/viewtopic.php?f=22&t=48189&p=276356#p276356). I wonder if you can help?

I'm trying to see AVCHD .m2ts files on my new Sony 40NX803. These files have been generated via my Sony Camcorder - and indeed I can see them via the USB stick and also in the local Sony Centre they streamed one of my files from their store PC to the same TV model. Thus I assume the file is OK i.e. it is a level 4.0 video - whatever that is ;)

So - it would seem to be a problem with the DNLA server. From what I can see you are using miniDNLA - correct? I am using ReadyDNLA on my Netgear NAS.  

Is this where I need to focus my attention (in your opinion)

Thanks in advance

Steve

---

### Post by craigchambers on 2011-03-20
> **holland141 said:**
> Hi Craig

I was sent to this post via the response to [http://www.readynas.com/forum/viewtopic.php?f=22&t=48189&p=276356#p276356](http://www.readynas.com/forum/viewtopic.php?f=22&t=48189&p=276356#p276356). I wonder if you can help?
Thanks in advance
Steve

Just picked this up... Don't know if you solved your problem, but you may have more luck with an upgraded version of the DLNA server on the NAS.  I don't know too much about how you do this, but ReadyDLNA is essentially miniDLNA (the developer is the same Netgear employee).  

Your other option is to try to fix the entries in the database that ReadyDLNA uses.  Info on this is available in the thread above.

/Craig

---

### Post by nickrout on 2011-07-04
> **coldwilson2011 said:**
> 1 Make sure all you media devices are connected together through home networking.

2 Make sure all the deviced are DLNA-certified.

If you still have problems, check your web.

What a strange post. Of course no one is going to expect no networked devices to work via dlna.

Also just because ServerX and PlayerY are dlna certified, it doesn't mean they will work together. ServerX may serve mpeg2 in a mpeg-ts wrapper but PlayerY wants h.264 in a mkv wrapper.

There are numerous aspects of dlna spec that are not consistently interpreted across different manufacturers and devices.

It's a royal mess, as this thread shows.

---

### Post by craigchambers on 2011-07-13
> **nickrout said:**
> Also just because ServerX and PlayerY are dlna certified, it doesn't mean they will work together. ServerX may serve mpeg2 in a mpeg-ts wrapper but PlayerY wants h.264 in a mkv wrapper.

There are numerous aspects of dlna spec that are not consistently interpreted across different manufacturers and devices.

It's a royal mess, as this thread shows.

Seconded.  The certification should always allow for playback of JPG, WAV (PCM), MP3 and MPEG2, but in reality very little is interoperability tested.  Usually when a new device comes out, either the renderer or the server manufacturer has to issue a software update because the two don't work together.  Given that the renderer is usually (in my experience) a major CE manufacturer, that leaves it to the server vendor to fix.

BTW, PlayerY could not be certified as a DLNA video renderer in your example above unless it supported the ts file from ServerX.  That of course is no guarantee that a ts video will play from one to the other, just that both are certified to do so!

/Craig

---

### Post by glymph on 2011-08-29
In case anyone is still having trouble with media servers on DLNA-compatible devices, this application may help; it's not open source as far as I can tell, just free:

[http://www.serviio.org/](http://www.serviio.org/)

It appears to work extremely well (once the files are appropriately indexed), and I'm very happy with it - I can watch files with the AVI extension (not sure what codec, but it probably varies) on my Sony Bravia KDL-40EX403 TV served from an ASUS Eee 901 netbook running Ubuntu 10.10 with only occasional pauses in transcoding (it uses ffmpeg).

Hope this helps, 

Dom

---

