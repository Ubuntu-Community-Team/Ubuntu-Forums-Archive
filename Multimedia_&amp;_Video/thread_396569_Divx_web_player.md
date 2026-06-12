---
title: "Divx web player"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by Mattimus on 2007-03-29
Hey guys, I am kinda new to the linux world (got rid of windows once the ignorance wore off) and I have a question about online videos....

I don't have any problems with most formats on the web as firefox seems to have plugins for most everything but divx videos.....
what I want to know is if anyone here has a solution for viewing divx video through firefox....maybe another program I could install....

---

### Post by sdowney717 on 2007-03-29
mplayer plugin

---

### Post by Mattimus on 2007-03-30
I suppose that would lead to a second question.....
I already have mplayer plugin installed, but to no avail with the divx movies (only online that is)
so here is my question....how do you get mplayer set for the divx plugin?.....I looked in my about: plugins and I don't even have a section for divx 

any takers?

---

### Post by Mattimus on 2007-03-30
okay....I guess I do need to clarify a little bit....some divx video will play.....but some won't
ex....
[http://download.divx.com/BrowserPlugInBeta2/BrowserPlugIn_Beta2_Sample4.html](http://download.divx.com/BrowserPlugInBeta2/BrowserPlugIn_Beta2_Sample4.html)

---

### Post by Dayylin on 2007-04-27
bump

I too have the issue. I can play any video but divx format and unfortunately, a lot of what I need to play is divx. Anyone found a work around?

---

### Post by josephus on 2007-04-28
i was having the same problem.  make sure you have the mozilla-mplayer plugin installed from the repo.   it includes two files needed for making mplayer play divx within firefox
```

/usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
/usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
```

for some reason my firefox doesn't seem to see these files until i move into the /usr/lib/firefox/plugins directory.  i don't know why this is the case since i've always thought it searched through both directories (if someone could explain this to me).

once i move these files and restart firefox i can see divx in the about:plugins page

(i can't play the videos on the link that was provided above, but i think that is because it is pointing to a broken link - can see the other videos on the divx.com page)

---

### Post by treris on 2007-05-01
Thanks Josephus, 

that solved my problem, they were indeed in the mozilla folder, but not in the firefox folder for some reason or another

---

### Post by ecornes on 2007-05-07
You don't have to move the divx plugins, just make a symbolic link to the plugins as you do when you install java.  In the firefox plugin directory enter ln -s /usr/lib/mozilla/plugins/[plugin files]

---

### Post by Skylara on 2007-05-14
> **ecornes said:**
> You don't have to move the divx plugins, just make a symbolic link to the plugins as you do when you install java.  In the firefox plugin directory enter ln -s /usr/lib/mozilla/plugins/[plugin files]

Hey there.  I'm having the same problems, so I tried your instructions above:

I used "sudo," entered my password, and it said permission denied.  Here's the terminal text:

> kitten@green-desktop:/usr/lib/firefox/plugins$ ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
ln: creating symbolic link `./mplayerplug-in-dvx.xpt' to `/usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt': Permission denied
kitten@green-desktop:/usr/lib/firefox/plugins$ ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
ln: creating symbolic link `./mplayerplug-in-dvx.so' to `/usr/lib/mozilla/plugins/mplayerplug-in-dvx.so': Permission denied

I am a new Linux/Ubuntu user.  By new I mean really really new.  I installed Dapper from the Official Ubuntu Book CD I got for Mother's Day Saturday evening, upgraded to Edgy, installed Wine and World of Warcraft and got everything running nicely, but that's about the extent of my experience.

Do you have to be logged in as a super-user?  If so, I thought that's what "sudo" did?

Or maybe I'm doing something wrong that is easy to fix and staring me right in the face?  And I have to use the terminal -- I can't just copy them from the files because I don't have permission and I'm not sure how to get around that either.

Any help would be wonderful!

---

### Post by josephus on 2007-05-14
how are you using sudo?  in your quoted text i don't see the sudo command?

```
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
```

---

### Post by Skylara on 2007-05-14
> **josephus said:**
> how are you using sudo?  in your quoted text i don't see the sudo command?

```
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
```

From page 144 of The Official Ubuntu Book:
 
> When you have authenticated yourself to sudo you will not be asked for the password again for another 15 min.

I took that to mean I only had to use sudo once, to log in, and then was good to go for 15 min.  I didn't realize you must use it before each command.  You didn't see sudo in my copied text because I had used it earlier and was asked for my password, then entered the command to make the link and mistyped it.. so you just saw the two I typed correctly.

Anyhow, without going off-topic of this thread, that means anytime you do a command that affects root-user files, you must use sudo, even though you only log into it once?

Edit: The two files are in the Firefox plugins folder now, so the linking worked.  Thanks!  **But** I still cannot get divx movies to stream.  The site I go to has links to shows/movies/music videos.  You find the one you want and click on it and it opens a small browser window with the player embedded in it.  I can play ones that use Flash just fine, but Divx still refuses to work.  I've used the steps here and am not sure what else I am missing.

Let me know if you need any system specs or anything else that can help.

---

### Post by josephus on 2007-05-14
every time you want to do something requiring root access you have 'sudo + command'.  the fifteen minutes just means that it won't keep asking you for the password each time after the first.

if you are doing a lot of things that require root, then sudo + command can get a little bit tiring.  in those cases you can create a terminal shell logged in as root using the command

```
sudo -i 
```
or
```
sudo bash
```

---

### Post by josephus on 2007-05-14
if you point your browser to about:plugins do you see the divx plugin?

also which website are you trying?  does stage6 work for you?

[http://stage6.divx.com/](http://stage6.divx.com/)

---

### Post by Skylara on 2007-05-14
> **josephus said:**
> if you point your browser to about:plugins do you see the divx plugin?

also which website are you trying?  does stage6 work for you?

[http://stage6.divx.com/](http://stage6.divx.com/)

I have attached a screenshot showing the two DivX-related plugins.

The site I am trying is [http://tv-links.co.uk]("http://tv-links.co.uk").  I have been using it for some time on my Windows XP laptop, but was hoping to get it working for this desktop.

I actually found a How-To relating to my exact problem:   [HOWTO: Watch Stage6 DIVX movies]("http://ubuntuforums.org/showthread.php?p=2654954#post2654954") but the How-To has been unable to resolve the issue either.

I have posted to there as well to see if the author can help... and no, I can't see the Stage 6 stuff.  That's pretty much the only problem I have.. as far as I know, I can view any other formats.

---

### Post by josephus on 2007-05-14
what happens when you try playing the file from the command line (this is the ocean's 13 trailer)

```
mplayer http://divx-484.vo.llnwd.net/stage6vid/1207629.divx
```

---

### Post by Skylara on 2007-05-14
> **josephus said:**
> what happens when you try playing the file from the command line (this is the ocean's 13 trailer)

```
mplayer http://divx-484.vo.llnwd.net/stage6vid/1207629.divx
```

I get the following code back:

```
kitten@green-desktop:~$ mplayer http://divx-484.vo.llnwd.net/stage6vid/1207629.divx
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3400+ (Family: 15, Model: 47, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Creating config file: /home/kitten/.mplayer/config

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing http://divx-484.vo.llnwd.net/stage6vid/1207629.divx.
STREAM_HTTP(1), URL: http://divx-484.vo.llnwd.net/stage6vid/1207629.divx
Resolving divx-484.vo.llnwd.net for AF_INET6...
Couldn't resolve name for AF_INET6: divx-484.vo.llnwd.net
Resolving divx-484.vo.llnwd.net for AF_INET...
Connecting to server divx-484.vo.llnwd.net[208.111.157.68]: 80...
STREAM_ASF, URL: http://divx-484.vo.llnwd.net/stage6vid/1207629.divx
Resolving divx-484.vo.llnwd.net for AF_INET6...
Couldn't resolve name for AF_INET6: divx-484.vo.llnwd.net
Resolving divx-484.vo.llnwd.net for AF_INET...
Connecting to server divx-484.vo.llnwd.net[208.111.160.39]: 80...
size_confirm mismatch!: 17990 8265
Error while parsing chunk header
Failed, exiting.
STREAM_HTTP(2), URL: http://divx-484.vo.llnwd.net/stage6vid/1207629.divx
Resolving divx-484.vo.llnwd.net for AF_INET6...
Couldn't resolve name for AF_INET6: divx-484.vo.llnwd.net
Resolving divx-484.vo.llnwd.net for AF_INET...
Connecting to server divx-484.vo.llnwd.net[208.111.157.68]: 80...
Cache size set to 320 KBytes
Cache fill:  0.00% (0 bytes)   


Exiting... (End of file)
kitten@green-desktop:~$ 
```

And thanks for helping with this!

---

### Post by josephus on 2007-05-14
which version of ubuntu do you have installed? 32/64 bit?

---

### Post by Skylara on 2007-05-14
> **josephus said:**
> which version of ubuntu do you have installed? 32/64 bit?

How can I check that?  I installed Edgy as an update from Dapper and used the System > Admin > Update Manager to install it, so I honestly don't know.

---

### Post by josephus on 2007-05-14
post the output of

```
uname -a
```

---

### Post by josephus on 2007-05-14
can you play divx files that are already downloaded to your computer?

if you don't have a divx file handy, try downloading the trailer first

```
wget http://divx-484.vo.llnwd.net/stage6vid/1207629.divx
mplayer 1207629.divx
```

---

### Post by Skylara on 2007-05-14
> **josephus said:**
> post the output of

```
uname -a
```

```
kitten@green-desktop:~$ uname -a
Linux green-desktop 2.6.17-11-386 #2 Tue Mar 13 23:30:30 UTC 2007 i686 GNU/Linux
kitten@green-desktop:~$ 
```

> **josephus said:**
> can you play divx files that are already downloaded to your computer?

And I can.  I also went back to the DivX site and was able to play from their site this time, so I thought maybe it was just a glitch.  I went back to tv-link.co.uk and tried to play Flowers in the Attic again and it still doesn't work.

I'm looking around on that site now to see if I can find other DivX movies/shows to see if it repeats with any DivX shows from that site, or if it's just that movie.  I'll update when I find another and see what happens.

---

### Post by Skylara on 2007-05-14
Well, under [Cartoons > Family Guy]("http://tv-links.co.uk/show.do/2/143") they list next to the episodes which are hosted by VEOH (uses Flash) and which are hosted by Stage 6 and I can't play any of the Stage 6 ones.  

I guess the problem is limited to their site and any of the fixes offered in this thread and the How-To will enable most DivX playback except for the Stage 6 stuff at tv-links.co.uk.  Not sure what to do about that... if it's something I can do on my end with my player and Ubuntu.. or if it has to do with the way they link to the streaming video.

---

### Post by josephus on 2007-05-14
yeah, i'm not really sure what the problem is.  the main error message 'size_confirm mismatch' isn't turning up many hits.   you might want to try uninstalling and reinstalling mplayer using synaptic, and if that fails try compiling mplayer from source

also if you can't get mplayer to work with divx you should remove plugin. as it stands now firefox has two plugins handling divx.

---

### Post by Skylara on 2007-05-14
> **josephus said:**
> yeah, i'm not really sure what the problem is.  the main error message 'size_confirm mismatch' isn't turning up many hits.   you might want to try uninstalling and reinstalling mplayer using synaptic, and if that fails try compiling mplayer from source

also if you can't get mplayer to work with divx you should remove plugin. as it stands now firefox has two plugins handling divx.

Thanks again for your help.  I'll try the uninstall/reinstall and compiling, if needed and see what happens.

---

### Post by schnupi on 2007-05-17
thanks so much! its all workin now.. i hate using totem. its such a paaaain. 

btw. i used it for swiftfox. for those using swiftfox wondering why it doesnt work.. copy those two files into /opt/swiftfox/plugins/

---

### Post by JJFO on 2007-05-28
I got the web player working, but i still cant rewind of skip forward, can anyone else do this?

---

### Post by il-luzhin on 2007-05-29
I still can't get the plugins to show up.  Is this a 64-bit limiltation?

---

### Post by shellex on 2007-07-06
I've been following this thread for some time now and it seems like the Stage6 Player is working on the Stage6-Site with the Mplayer-Plugin. However, has anyone played any Stage6-Videos over tv-links.co.uk?

The problem with the tv-links.co.uk vids is that they don't redirect directly to the stage6.divx.com server, but to an url on the same server where - I figure - the location header is changed to the desired url. The thing is: they might check some other stuff before redirecting you to the stage6 video like the referrer or other session data to verify that you came from tv-links.co.uk and that you are not just crawling their database or whatnot. I tried to open the embedded video link with a spoofed referrer (the popup's url) but this resulted in a 404-site.
I just wanted to remind you that it might not be a problem with linux, mplayer, vlc, firefox or so on, but a protection trick from tv-links.co.uk. Can anyone verify or disprove this theory?

---

### Post by jinxjinx on 2007-07-08
anyone got any ideas?????

---

### Post by andnobodyslept on 2007-07-10
I second this opinion about tv-links, mainly since I can get a few stage6 videos to work, and then some will just sit there initializing with mplayer for ever. My recommendation is just to hit the dead link link and hope that someone will get around to checking it. The only thing is that I have yet to check out the same link using windows, so it is still possible that it might just be a linux divx thing.

---

### Post by jinxjinx on 2007-07-10
they all work on a mac. so it must be a linux thing....

---

### Post by andnobodyslept on 2007-07-10
Actually I think it is more the fact that I am finding the occasional dead link, since I would say close to 90% of all the stage6 videos are now working for me. It sometimes takes a while for it to initialize and start buffering (up to and over a minute) but they are all buffering (though that took some work to get right) and playing beautifully. Basically, for me I just installed mplayer, removed every other plugin, made the link to usr/lib/firefox/plugins and made sure that all divx movies were pointed to mplayer, including right clicking on the mplayer window and enabling divx support. For tv-links I suggest that you set your min cache to around 5000 and the min cache percent to 0, so the player doesn't keep restarting and rebuffering, also take off pause video when hidden.

---

### Post by jinxjinx on 2007-07-10
what did you do exactly?

Im using the media player plugin and when i click the little icon to open the movie in totem (i guess that is the same as mplayer) it tells me location not found...for most stage 6 links from tvlinks.

it works fine from the stage 6 website.

---

### Post by andnobodyslept on 2007-07-10
First don't use media player plugin, just
```
sudo aptitude install mozilla-mplayer
```

Allow it to install the rest of mplayer (at least that is what I did)

Change the default player for divx to mplayer Edit-->Preferences-->Content Tab-->Manage


Make sure that mplayer is in the right folder, see the first and second page of this thread
[http://ubuntuforums.org/showthread.php?t=396569&highlight=divx+stage6+tv-links]("http://ubuntuforums.org/showthread.php?t=396569&highlight=divx+stage6+tv-links")
Mainly post 6 and 10

Then get rid or the totem plug-in
```
sudo aptitude remove totem-mozilla
```

restart firefox

Go to tv-links, open a video that is on stage6, mplayer should come up, then right click the mplayer box Configure, check enable divx support, uncheck Pause Video when hidden.

I then had some problems with the buffering, mainly it would buffer for a few seconds, then play for a few seconds and then stop and start buffering from the beginning, only to start the video from the beginning again. I got around this by once again going into the configure panel setting the minimum cache size to around 5000 (guess it would depend on your connection speed) and the min cache percentage to 0. Restart firefox and so far I haven't had any problems, sometimes it takes a bit to start buffering, but never more than a minute or two. 


If this doesn't work, don't hold me to it, I got it working through three days of searching the forums, googling and plain stupid luck, so this might not work for you since I did a lot of testing and banging my head into the table to get it. Post if you do have questions, you might jog my memory about something I forgot. Trust me, I'm no super-user, I just tried everything until this worked.

Good luck
Ian

---

### Post by jinxjinx on 2007-07-10
thanks for the help!
 i can get some movies to work now...
but there usually black and white ones...
does euro trip work for you?

[http://tv-links.co.uk/show.do/4/5147](http://tv-links.co.uk/show.do/4/5147)

---

### Post by andnobodyslept on 2007-07-10
I gave it a try and no luck, etiher something is missing or the video has been removed at stage6. My guess is on the video was removed, but if you get it to work, PM me with your fix.

---

### Post by grayhammer on 2007-07-20
I noticed something odd about tv-links and stage6 videos.  If I refresh the page I am on before I try to launch a video, the video plays every time.  If I don't refresh, the video player launches, but nothing plays.  So if you're having trouble watching stage6 videos at tv-links, try closing the video playback window, refreshing the links page and try the video again.  This works for me and I am using totem-gstreamer, of all things.

---

