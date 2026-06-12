---
title: "Sound gets lost in Firefox flash applications over time"
date: 2009-12-16
forum: Multimedia Software
---

### Post by wickstopher on 2009-12-16
Hi, there.  I have a strange problem.  I recently did a fresh install of Karmic 9.10 (32-bit version), and everything is working great, except for this.  I'll be whiling away, browsing the interwebs via Firefox, when seemingly at random, flash applications (YouTube, pbskids.org, anything using flash) will have stopped putting out any sound.  Actually, this tends to happen more often when I step away from the computer for some time, leaving firefox open, and then get back to it later.  I then quit Firefox, and it won't allow me to start back up again, saying that Firefox is still running.  The only way to get around this is as such:

1) sound in Flash stops working
2) Quit firefox
3) Open Terminal
4) pgrep firefox
5) sudo kill [PID#]
6) restart firefox, sound in Flash works again

Needless to say, this is a clunky workaround for the problem.  Anyone else have this issue and can offer up a fix?  Thanks!

---

### Post by redhotMonk on 2009-12-16
I have this same problem. Upgraded to 9.10 from 9.04. All my sounds work fine except for after awhile I have to kill firefox to get sound for flash.

My flash video also has choppy video in fullscreen. This problem was fixed when I upgraded to 9.10 but now it's doing it again. I have no idea if this is related to the audio problem.

---

### Post by wojox on 2009-12-16
For all my Firefox and Flash needs: [URL="http://ubuntuforums.org/showthread.php?t=1193567"] Firefox optimization and troubleshooting thread
[/URL]

---

### Post by AgenT on 2009-12-17
I had a problem where Flash would cause 95-100% CPU usage in Firefox and other browsers. The movie would first stop having sound then would freeze altogether. Closing the tab where the flash movie was playing would not help. Only restarting the browser helped.

The solution?

I had timidity installed, from before my upgrade to 9.10. Timidity steals the soundcard which produces problems. After removing timidity, the problem went away. Now I get 30-40% CPU and after the movie finishes playing, it drops to CPU usage before playing the movie!

For those having any PulseAudio problems, **READ OVER THE [SIZE=3]_[KARMIC CAVEATS]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")_[/SIZE] WIKI**!

---

### Post by purecharger on 2009-12-17
I also lose sound from Firefox+flash over time. Its annoying to have to quit the browser and kill the process when I have a bunch of tabs open.

Any suggestions for troubleshooting this? I'm not even sure where to look.

---

### Post by wickstopher on 2009-12-19
> **AgenT said:**
> I had a problem where Flash would cause 95-100% CPU usage in Firefox and other browsers. The movie would first stop having sound then would freeze altogether. Closing the tab where the flash movie was playing would not help. Only restarting the browser helped.

The solution?

I had timidity installed, from before my upgrade to 9.10. Timidity steals the soundcard which produces problems. After removing timidity, the problem went away. Now I get 30-40% CPU and after the movie finishes playing, it drops to CPU usage before playing the movie!

For those having any PulseAudio problems, **READ OVER THE [SIZE=3]_[KARMIC CAVEATS]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")_[/SIZE] WIKI**!


Well, I don't have timidity installed, so that's not the problem.  Not sure if it's a PulseAudio thing or not, because all other audio functions normally it's ONLY the audio in flash in firefox.

---

### Post by DilbertCa on 2009-12-21
I am also seeing this problem.  I have a recent (~2 years) ASUS motherboard with
Intel Core2Duo processor.  I do not have "timidity" installed.  I tried the tip suggested
by [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567), doing:
        sudo apt-get remove swfdec-mozilla
        sudo apt-get remove mozilla-plugin-gnash
        sudo apt-get remove adobe-flashplugin
        sudo apt-get remove flashplugin-nonfree
        sudo apt-get install flashplugin-nonfree
Sound on flash videos was working fine after this procedure, but sound is failing 24 hours
later.  Sound works with Ogg-Vorbis files at Wikipedia---this seems to be a flash-only problem.  Restarting firefox resolves the issue, but is obviously a cumbersome solution.

Any further suggestions?  Thanks.

---

### Post by wickstopher on 2009-12-21
> **DilbertCa said:**
> I am also seeing this problem.  I have a recent (~2 years) ASUS motherboard with
Intel Core2Duo processor.  I do not have "timidity" installed.  I tried the tip suggested
by [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567), doing:
        sudo apt-get remove swfdec-mozilla
        sudo apt-get remove mozilla-plugin-gnash
        sudo apt-get remove adobe-flashplugin
        sudo apt-get remove flashplugin-nonfree
        sudo apt-get install flashplugin-nonfree
Sound on flash videos was working fine after this procedure, but sound is failing 24 hours
later.  Sound works with Ogg-Vorbis files at Wikipedia---this seems to be a flash-only problem.  Restarting firefox resolves the issue, but is obviously a cumbersome solution.

Any further suggestions?  Thanks.

I have very similar components.  ASUS P5NE-SLI and Core 2 Duo 2.66 GHz.  I somewhat doubt that it's a hardware issue.

---

### Post by tike012 on 2009-12-22
Ah, a still-active thread.

So, I've been experiencing this "bug" since way before Karmic.  To me, it's obviously a problem with Flash + Firefox causing a memory leak that'll cut off sound if left alone too long.  The question is just how to fix it... and there I am lost =(

---

### Post by DilbertCa on 2009-12-22
> **tike012 said:**
> So, I've been experiencing this "bug" since way before Karmic.  To me, it's obviously a problem with Flash + Firefox causing a memory leak that'll cut off sound if left alone too long.  The question is just how to fix it... and there I am lost =(

For what it's worth, I was _not_ experiencing it with Feisty.  It's something new with flash, firefox, or the new sound architecture.  Was hoping Firefox 3.5.6 would fix it but no such luck.  Sound seems to go away overnight.  Not sure about the memory leak theory;  it seems just as plausible that some process is coming along overnight and interfering with some settings that firefox is depending on.

("They mostly come at night---mostly.")

---

### Post by BobvanderPoel on 2010-01-03
I've been having the same problem! So, I think we are not alone.

I'm wondering if anyone has tried to delete the existing firefox profile and start building the various cache files, plugins, etc. and figuring out which one is the problem? I'd hate to do this ... my firefox is just too configured! 

Any other ideas. This is truly a pain!

I've checked various "fix firefox" threads, etc. and it appears to me that it's just the folk on this thread with the problem. Odd.

Oh, and easier than getting the PID to kill firefox, just do a "killall firefox" ... assuming you've not got multiple copies running :)

---

### Post by BobvanderPoel on 2010-01-06
Since there are no new posts on this thread ... I assume that either:
 - no one knows the answer, 
 - no one cares about the problem,
 - the 3 or 4 people reporting the problem are the only ones having the problem,
 - the same 3 or 4 people are the only ones which notice the problem.

Sorry, it's been a long day and I just had to restart my firefox to get flash audio for the 5th time today.

---

### Post by DilbertCa on 2010-01-07
> **BobvanderPoel said:**
> Since there are no new posts on this thread ... I assume that either:
 - no one knows the answer, 
 - no one cares about the problem,
 - the 3 or 4 people reporting the problem are the only ones having the problem,
 - the same 3 or 4 people are the only ones which notice the problem.

Sorry, it's been a long day and I just had to restart my firefox to get flash audio for the 5th time today.

I think it's a combination of the fact that no one reading this forum knows the answer and
that this is the wrong forum.  This really ought to be a bug report for firefox.  There's no
reason to believe that it is Ubuntu-specific.  Anyone have a pointer to a firefox bug report
of this issue?

---

### Post by aktorun on 2010-01-07
exactly same problem.

my on-board sound card work perfectly with Amarok (for instance) but no sound with Firefox+Flash

MoBo : Asus P5Q Pro
On-board Sound Card : Realtek ALC1200
Kernel : 2.6.31-17-generic  x86_64 GNU/Linux
Firefox : 3.5.6

---

### Post by BobvanderPoel on 2010-01-11
I was hoping that I might have a fix ... installed firefox 3.6 yesterday. Works great! But, after leaving it running overnight my flash audio was dead again.

I'm getting more and more convinced that the problem is not with firefox, but a combination of flash and the new pulseaudio and my sound card (Maudio 24/96).

I'd love to help track down the problem but really have no idea of what to do to help.

---

### Post by platosearwax on 2010-01-13
I have no answer but I can confirm that it is not just Firefox.  I get the exact same thing happening when using Chrome.  It works fine for a while but if left alone for a time I have no sound in flash.  The good thing about Chrome is you don't have to kill it like Firefox.  

I am guessing it is a Flash/Pulse problem.  I had fits with Pulse in the new Karmic but everything works now except for the Flash problem.

---

### Post by oakbox on 2010-01-14
Count me as another person experiencing this issue.  It happened very recently (starting from january 13th for me), so possibly something to do with a recent update.

No audio problems in Exaile or other audio applications.  It's not just youtube video either, any flash video craps out.  I have tried it in Opera and Firefox with the same results.

Argh!

- Richard

---

### Post by wickstopher on 2010-01-14
Recent updates seem to have resolved the issue on my end.  I'll have to wait a few days to be absolutely sure, but can anybody else confirm this?

---

### Post by ichudov on 2010-01-14
I have EXACTLY the problem described in the first post of this thread. I have to KILL firefox in order to get rid of it and to restore sound!

---

### Post by ichudov on 2010-01-14
I am trying now to disable 

    load-module module-suspend-on-idle 

in file /etc/pulse/default.pa 

I will report my results.

---

### Post by MOHCTP on 2010-01-15
I have exactly the same problem -- sound is fine in all apps and FireFox, but leave the computer running overnight, and the next day the sound on YouTube is gone.

For what it's worth, it's not just FireFox, but also Chrome, and now also Opera (yes, there are Chrome and Opera for Linux now).  I don't think the problem is FireFox, it's very clearly Adobe Flash that sucks.  The only thing FireFox could have done better is give you an ability to kill the plug-in without restarting, or at least be able to quit normally when this happens, instead of hanging and having to be killed.
BTW, Opera allows to you exit, takes a little while, but does exit without external intervention, and does restart fine.

I've had this problem on 9.04, and upgraded to 9.10 for one reason only -- in hopes of fixing this annoying bug.  No such luck. 

P.S. I don't have any third party software installed, and my audio is an external cheapo USB card, because the machine is a rack server with an Intel server mobo.

---

### Post by wickstopher on 2010-01-15
Well, never mind, I suppose I spoke to soon.  Problem is still in effect.

---

### Post by FMaz008 on 2010-01-15
I also have this problem since the very first version of Ubuntu I've tried.
I've Ubuntu on 3 computer (2 AMD, 1 Intel), one of my AMD computer have a dedicated sound card.

All of them, on all Ubuntu version I've tried, have this problem.
It's really anoying.


Also, after some random time, I have another weird problem playing any king of video: I only have 3 second of play time, after that, the video "pause", flash or any other form of streaming; it doesn't matter.

I'm not trying to start 2 problems on the same topic, but I thought this might be linked.

---

### Post by ichudov on 2010-01-15
Reporting on my earlier post...

Editing /etc/pulse/default.pa and disabling module-suspend-on-idle 
did me no good.

I am back to square 1.

i

---

### Post by BobvanderPoel on 2010-01-16
In desperation I installed a newer flash (10.1.beta2) ... I was so hopeful ... nope. Problem is still there!

There has to be a fix for this???

BTW, I read somewhere else (I think) that once flash is started it continues to run. Could it be that it's overflowing something in the pulse buffers? Just a thought.

---

### Post by Stronze on 2010-01-17
ubuntu - 9.04

im having almost the same issue.

if i play ANY videos in FireFox, it kills my sound on the whole computer.
i installed chrome and i have the same issue.

i try and play a flash video and all i get is static type sound, then i try to play a movie and there is NO sound.
i gotta restart to restore sound on the computer.
restarting does play a *beep* 

now if i have a movie playing and try to play a Fire Fox video via flash, movie sound works fine but still gets static. but if i dont have a movie paused then all sound is lost.

i must assume its an update.
worked in the states then i deployed to iraq and no sound after a few rounds of updates.

---

### Post by ratcheer on 2010-01-20
I just want to report that I am having the same problem (no audio with Flash in Firefox - the video portion plays fine). I have a Creative Audigy 2 ZS sound card.

Flash audio was working fine until yesterday. I got the stupid urge to upgrade ALSA from 1.0.20 to 1.0.22.1 (which is supposed to fix a lot of bugs). I know, "If it ain't broke, don't fix it." I already said it was stupid.

ALSA only upgraded to 1.0.21. I don't know why (and I have posted about it in the ALSA upgrade script thread). Sound is working perfectly when playing media files, audio CD's, and movie DVD's. Just not Flash videos in Firefox.

Tim

---

### Post by ratcheer on 2010-01-20
I have tried three things, neither worked. 1) I installed the latest Flash plug-in, 10.0.42.34, directly from the Adobe website; 2) I uninstalled and reinstalled Firefox 3.5.7; 3) I installed Opera 10.5 alpha. Flash videos play in both, but no sound in either. So, this does **not** appear to be a Firefox problem, exclusively.

Next, I am going to try Google Chrome.

Tim

---

### Post by ratcheer on 2010-01-20
Google Chrome is the same - no audio in Flash videos. :(

Tim

---

### Post by BobvanderPoel on 2010-01-20
I really don't know for sure ... but I think there are 2 threads here:

1. Flash audio doen't work in firefox/etc.

2. Flash audio stops working firefox after some time has elapsed.

I'm not sure, but I think they are 2 different issues.

---

### Post by joshzam on 2010-01-26
> **BobvanderPoel said:**
> I really don't know for sure ... but I think there are 2 threads here:

1. Flash audio doen't work in firefox/etc.

2. Flash audio stops working firefox after some time has elapsed.

I'm not sure, but I think they are 2 different issues.

Well, sign me up for your #2. Same as everyone else who has described this. Audio stops, close Firefox, kill Firefox, restart Firefox, audio works. No rhyme or reason as to why or when it happens. Grrr...

I've got Firefox 3.5.7 on Karmic, and these are my installed plugins (DivX Web {layer 1.4.0.233, QuickTime Plug-in 7.2.0, Shockwave Flash 10.0 r42, VLC Multimedia Plugin, and Windows Media Player Plug-in 10)

---

### Post by BobvanderPoel on 2010-02-02
In total desperation I pulled my soundcard (M-Audio Audiophile) in my computer and started to use the sound on the motherboard. Well, that's not it either ... complete different sound cards, same problem. Oh well, needed to dust the inside of the computer anyway :)

---

### Post by platosearwax on 2010-02-02
I just now realized that I haven't had this problem for more than a week or so.  I think my Firefox is updated to the latest, but this happened for me in Chromium as well.  I think there were also updates to pulse audio and alsa this last week and that may be it.  Either way, I am hoping that this thing is solved, even though I have no idea why.

---

### Post by platosearwax on 2010-02-03
And typically I spoke too soon.  Happened today in Firefox.  I have no idea what this is but I am guessing it's a flash problem (which would make sense since other than on Windoze flash is pretty buggy).

---

### Post by groundpounder on 2010-02-05
I left Ubuntu for Debian a while back after Ubuntu stopped supporting the older hardware in my desktop.  I just bought a new Dell laptop though, and I have installed Karmic (64 bit) on that.  I have the exact same problem in my Debian desktop and my new Karmic laptop, but that problem is somewhat different than what's reported here.  I experience no issues at all with Firefox on either machine.  Opera however is another story.  After a while, the sound either stops working (most of the time on the laptop) or comes out all garbled (half the time on the desktop) AND using the mouse to play a flash game or to operate the controls on a Flash media player (i.e. youtube), the actual spot that sees the mouse click is actually a couple inches to the left and below where the mouse pointer is shown on the screen.  Again, that is only in Opera, and on both Karmic and Debian.  I have not had either problem in Firefox (or iceweasel on Debian).

---

### Post by martinezlc99 on 2010-02-05
I have been following this thread for awhile now in hopes of a solution.  

For me the problem is that flash and pulseaudio do not seem to want to work together:

- whenever I am listening to youtube, I cannot use any listen to pulseaudio applications;
- the converse is true, if I am using a pulseaudio app (notably rhytmbox, movie player, and pidgin...which I use all the time), then flash will not play sound.

I have to kill Chrome/Firefox/Swiftfox/Namoroka (tried them all) to get flash to play music.  

If I uninstall pulseaudio, then the problem goes away, but I cant use some applications.  

Not sure what I have to add (I am pretty new to linux), but those are the symptoms I have noticed.

---

### Post by syllogism_ on 2010-02-06
I get this issue with both the Opera web browser and Firefox. I'm going to try uninstalling pulseaudio.

---

### Post by mavrick13927 on 2010-02-06
I have the same or very similar problem
Kubuntu 8.04 LTS
FireFox 3.0.17
Flash 10 r42

I started experiencing this problem a few weeks back after upgrading to 10 r42.

Playing back a video, I get no sound until the video is ~1/3 over, then I get a short burst of audio as if playing a cassette on fast forward, then the audio goes into a loop, playing a second worth of audio over and over.  The immediate fix to stop audio loop is close tab.  To get audio working again requires:
close Firefox
ps aux|grep fox
kill PID
Restart Firefox

---

### Post by groundpounder on 2010-02-08
> **mavrick13927 said:**
>  then I get a short burst of audio as if playing a cassette on fast forward, then the audio goes into a loop, playing a second worth of audio over and over.  

After reading this, it sounds exactly like what I'm getting sometimes, usually with Opera on Debian (I described it above as just "garbled").  Sometimes even after closing the tab, the audio loop continues on for as much as another minute or two.

---

### Post by Yowzaboodle on 2010-02-11
Bringing this thread back to the original issue...has anyone found any more info on the complete loss of sound over time in flash applications? After much searching, this is the only forum where I've found any indication that anyone else was experiencing the problem (in my case, started with fresh install of Karmic; happens in both Firefox and Chrome). Does anyone with more Linux experience than myself know where or how to file a bug report on the issue, or how to find out whether one has perhaps already been filed?

---

### Post by chuckwoodchip on 2010-02-13
You folks are not alone.  I have been having this problem for at least 6 months.  The common (and most suspicious) aspect of this problem is that when firefox is first started, everything is fine.  Then, after an undetermined amount of browsing, any flash media will return with the most unsettling reverberating sound. 
I have followed every lead with no success. The lack of interest from the highest techie levels leaves me to believe that we have stumbled upon the contested ground of a turf war. 
I have been loading chrome just to have a way to play flash media but chrome doesn't have firefox's sophistication.  Maybe someday, when the offending code becomes obsolete and is replaced through upgrades, we will suddenly hear flash without fear and apprehension.[COLOR=#000000][FONT=Times New Roman][FONT=Arial][/FONT][/FONT][/COLOR]

---

### Post by jestal on 2010-02-16
I'm having the same issue where my mp3's work, and so do the system event sounds.

I just appear to be missing the sound from Youtube videos, or other streaming video.

I upgraded from 9.04? (i think) to 9.10.
That's when the problem started.

Hardware is Dell Inspirion E1705.

---

### Post by natrixgli on 2010-02-16
I have this problem frequently. If Firefox or Chrome are left idle after watching Flash content, eventually the audio stops working. Typically I have to close Firefox by brute force with "killall -9 firefox" and then restart it. Usually Firefox gives me the "Well this is embarrasing..." error message upon restarting.

I recently had to explain to my newly converted boss on why this workaround is necessary for something she regards as trivial and "always worked fine when I had Windows..." It was not fun since she'd recently been griping about how OpenOffice.org makes all her Word docs look like garbage.

I agree this should be filed on Launchpad, but early indications from this thread suggest that it would get rejected and blamed either on Adobe or Mozilla, followed by remarks on how I don't know how to report bugs properly. I've seen that before with similar bugs and I am not in the mood for a scolding right now.

Maybe later. ;)

-n8

---

### Post by VertexPusher on 2010-02-17
Uninstall PulseAudio and see if the problem goes away.
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse
```
If that doesn't help, you can get PulseAudio back by entering this:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by jms830 on 2010-02-17
Sign me up. I have the same problem where flash stops working over a period of time. Happens in firefox, chrome, or epiphany if you leave them open long enough. Then you have to restart the browser. I have been trying to fix this problem for probably a year but haven't found anyone who has the same issue until now. Just recently it's gotten severe. I can't watch more than a minute video before it cuts out.

---

### Post by bmomjian on 2010-02-17
What has me confused is why this has not been solved, though it has been reported months ago.  Obviously it is easy to reproduce, and a stuck process is even left around for debugging, so why has no one been able to fix this?

---

### Post by simoniux on 2010-02-22
The same problem as for everybody here. Upgraded to Ubuntu 9.10 from 9.04. In addition, followed the steps in this tutorial to fix potential PulseAudio problems: 
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Sound stops working in flash after some time. Sound continues to work fine everywhere else. Have to kill Firefox to make flash work again. As somebody noted, once flash starts ALSA plug-in, the plugin continues to run (as can be seen on the list of applications in the playback tab in pavucontrol), but probably that is normal.

---

### Post by FMaz008 on 2010-02-23
I could also add that if you have multiple browser, the bug is not global:

I open firefox, I watch some flash video. The problem occur.
I keep firefox openned, (because I don't want to loose my 18 tabs), and I open Opera.
The video will work under opera.

That said, I've not yet experienced the problem on Opera, but I never use opera for enought long to say if it's because the bug is not present in different browser, or because I don't let it occur.

My feeling is that it's a Flash related bug, not a firefox one.

---

### Post by BobvanderPoel on 2010-02-27
Interesting that you can open Opera while FF is not working for flash and get it running. Yes, tried and that's working.

So, I tried opening a 2nd instance of FF to see if that would work. Nope, no joy. I should try as a different user on a 2nd virtual terminal ... probably work just fine.

Not sure what we're proving here ... other that something is broken.

Does anyone know if it's possible to open flash links in FF by forcing the link to use opera or chrome?

---

### Post by FMaz008 on 2010-02-27
I was just watching a video, and the sound stopped WHILE the video played.
Reloaded the page: no sound.
Tryed another video: no sound
Closes + re-openned the browser: sound is back.

---

### Post by leprasmurf on 2010-03-06
I am also having this problem.  If firefox is left open too long, flash sound stutters (each second of the sound will play about 5+ times before playing the next).  Once this occurs, the only method I know of to fix is to kill firefox (pkill firefox).  Funnily enough, as mentioned previously, I can open epiphany and flash works just fine.  I haven't tried running just opera or epiphany for a night to see if it happens still, but that'll be my next step.

oh, and one other thing.  If I look at a feed in google reader that has alot of embedded flash, firefox will crash.

---

### Post by pterosky on 2010-03-17
I got the same problem with Firefox in Ubuntu 9.04 (Jaunty Jackalope) -- after a while sound stops working, while watching a  Flash movie. I have audacious running in the background, but paused.

There is a pulseaudio process that I can't kill when this happens, perhaps a clue?

---

### Post by S Man on 2010-03-17
Same problem here. Rhythm Box would work fine but all my flash applications would stop working over a period of time, especially in Firefox.

---

### Post by spottedhog on 2010-03-17
I am the same as leprasmurf.  I have Kubuntu 9.10 installed.

> If firefox is left open too long, flash sound stutters (each second of the sound will play about 5+ times before playing the next).

While the problem is happening in Firefox, I can open other browsers to the exact same web page and all is fine.

To fix it, I close Firefox and then open again.

Last night I watched maybe 4 hours of YouTube videos and left the computer on with Firefox open.  In the morning, the sound on a flash video in Firefox was as described above.

I just found this...

A temporary HotFix for Firefox:
> Just go to Tools -> Addons and disable flash. Once it's disabled, re-enable it and refresh the page. Everything is back to normal and you don't have restart firefox.

---

### Post by platosearwax on 2010-03-23
I can tentatively report that the problem seems to go away if I disable visual effects.  I have an older Nvidia card which has some other problems with effects anyway (terminals come up invisible, showing what is behind them; super user passwords screens when opening synaptic are blank but functional; can't use any type of dock or screen applets; drop down autocomplete in Firefox rarely works) so it isn't that big a deal to turn off the effects, makes the computer slightly more functional.  Though less pretty!

I'll report back if I still have problems with effects off.

---

### Post by auh2o on 2010-03-23
I've never had this problem before, but after today's Ubuntuzilla update to 3.6.2 it started happening to me. If I restart Firefox, the sound comes back, but will disappear again after a little while.

---

### Post by vikasap on 2010-03-25
Has anyone reported this as a bug in ubuntu or firefox flash plug-in ? If not, may be we need to do that first to get some attention on the problem.

---

### Post by auh2o on 2010-03-26
Well guess what; the problem disappeared for me again. But as to why, I have no explanation.

---

### Post by corykendall on 2010-03-26
I lose it over time as well.  

Here's a quick script to restart firefox... in case anyone hasn't written one yet :)

I'm relatively new to scripting, so let me know if I can do this better.

kill -9 `ps auxxx | grep firefox | grep usr | awk '{print $2}'` >/dev/null 2>&1 
firefox >/dev/null 2>&1

---

### Post by BobvanderPoel on 2010-03-26
I've been using the trick posted by another user, above. Just go to Tools->Add-ons->Plugins and disable Shockwave flash and immediately enable it. No need to stop firefox, etc. Then reload the page with the flash. Simplier than killing/restarting firefox.

Hopefully in the next firefox with plugin isolation things will be okay :)

---

### Post by vikasap on 2010-03-26
@BobvanderPoel

Ok , that trick kills my firefox. So , it is no better than the script. :)

---

### Post by BobvanderPoel on 2010-03-26
> **vikasap said:**
> @BobvanderPoel

Ok , that trick kills my firefox. So , it is no better than the script. :)

Odd. It seems the many folk are having a "similar but different" problem with this issue. I just tired it on my system: Firefox 3.6.2 (real FF, not ubuntufox), nvidia video (not sure if that makes a difference or not), ubuntu 9.10. Best thing I can suggest is to try it ... if it works, it's a "free fix". Otherwise use one of the other solutions.

It sure would be nice to have the problem FIXED!

---

### Post by Ububtubobl on 2010-04-05
Downloading the latest version of Java through the Synaptic manager solved that problem for me.

---

### Post by lavi17 on 2010-04-11
I'm having the exact the problem i've a similar thread running in debian forums, there too didn't get any solution, has anyone here in this comm, managed to sort out this thing..... hope to get a reply here, atleast y it is happening....

---

### Post by UserSince2003 on 2010-04-12
This procedure worked for me:
[http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/)

---

### Post by lavi17 on 2010-04-12
> **UserSince2003 said:**
> This procedure worked for me:
[http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/)
Hi i've tried whats been mentioned in that link, hope it works fine... well thanks for your post.... :)

---

### Post by lavi17 on 2010-04-12
> **UserSince2003 said:**
> This procedure worked for me:
[http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/)

Hi, well i'm back to point zero, the prb is still there... leave browser running for sometime there is no sound for sometime after that instead of sound can hear some noise as if some casette got stuck in the casette player. This not only about youtube but any site that uses flash animation, online song playing sites that use flash players to play the sound ...

---

### Post by GadiCohen on 2010-04-12
I'll mention a slight addition to the 'quick reload' of plugin "solution".  This should help in the cases where it didn't work, and is much quicker than killing and reloading all of firefox.  Of course, it still doesn't solve the actual problem.

1) Run the Pulse Audio Manager [Alt-F2 and 'paman' OR click on the PA icon on the panel and select 'Manager').  Go to Clients -> "ALSA plug-in [firefox-bin]" -> Properties -> Kill

2) In Firefox: Tools -> Add-ons -> Plugins -> Shockwave Flash -> Disable (and then Enable straight afterwards).

The new part is of course step 1.  Which points to the actual problem.  Usually when you close a tab with Flash, you'll see in paman that the client disconnects.  When the problem is evident, even with the tab/window closed, the client connection is still open.

So, the problem is that Flash is not releasing the connection, thereby blocking all audio from Firefox (including from other Flash instances) until you do the steps above.

---

### Post by lavi17 on 2010-04-12
> **GadiCohen said:**
> 

1) Run the Pulse Audio Manager [Alt-F2 and 'paman' OR click on the PA icon on the panel and select 'Manager').  Go to Clients -> "ALSA plug-in [firefox-bin]" -> Properties -> Kill


Hi, i'm not having pulse audio, i'm having esound-common, do i have to uninstall esound-common in order to install pulse-audio?

---

### Post by GadiCohen on 2010-04-12
> **lavi17 said:**
> Hi, i'm not having pulse audio, i'm having esound-common, do i have to uninstall esound-common in order to install pulse-audio?

Sounds right to me.  PulseAudio has become pretty standard these days, works well, and is backwards compatible with esound (esound clients can connect to it without any changes).  Plus you have a lot more control and features.

Although failing that, if there's no way to kill off individual client connections to esound, I'm sure you could restart your esound server at the same time you disable/enable flash, as far as making this problem more bearable until Adobe eventually fix it (and who knows when that could be).

---

### Post by nealmcb on 2010-04-20
I had this problem of flash audio ceasing to work while using chrome.  I'm running karmic 9.10, using google-chrome-beta                    5.0.342.9-r43360 and flashplugin-nonfree 10.0.45.2ubuntu0.9.10.1

For me it worked to just find the process running flash and kill it.  E.g. 

$ ps ax | grep flash

lists something like this:

16503 ?        SNl    0:11  /opt/google/chrome/chrome --type=plugin --plugin-path=/usr/lib/flashplugin-installer/libflashplayer.so --lang=en-US --plugin-data-dir= ....

Then pick out the process id and use it like this

$ kill 16503

My youtube video box changed to a puzzle piece looking unhappy, but reloading the page got me a working flash player.  Oddly enough, I no longer see a flash plugin process - I would have expected it to spawn a new one....

---

### Post by nealmcb on 2010-04-20
See also these pages for help diagnosing and reporting sound problems:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

And finally, note that the root problem here is use of the "nonfree" flash package.  So encourage web sites to use web standards like html5 for video and audio playing, rather than proprietary stuff like flash.  Or encourage Adobe to open source their flash player :)

See e.g. [http://www.technologyreview.com/web/24844/?a=f](http://www.technologyreview.com/web/24844/?a=f)
and
[http://www.linux-mag.com/cache/7734/1.html](http://www.linux-mag.com/cache/7734/1.html)

---

### Post by Yellow Pasque on 2010-04-20
> **martinezlc99 said:**
> For me the problem is that flash and pulseaudio do not seem to want to work together:

- whenever I am listening to youtube, I cannot use any listen to pulseaudio applications;
- the converse is true, if I am using a pulseaudio app (notably rhytmbox, movie player, and pidgin...which I use all the time), then flash will not play sound.
[http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by DilbertCa on 2010-04-25
> **nealmcb said:**
> I had this problem of flash audio ceasing to work while using chrome.  I'm running karmic 9.10, using google-chrome-beta                    5.0.342.9-r43360 and flashplugin-nonfree 10.0.45.2ubuntu0.9.10.1

For me it worked to just find the process running flash and kill it.

Yes!!  Thank you!  I should have thought to look for a flash process, but didn't.   This procedure works and doesn't cause a browser hang as it does to disable the plug-in.

---

### Post by wickstopher on 2010-05-23
Well, this problem is gone for me in Lucid. :)

---

### Post by platosearwax on 2010-05-23
> **wickstopher said:**
> Well, this problem is gone for me in Lucid. :)

Hmmmm...just yesterday installed Lucid so we'll see if that fixes it for me as well.

---

### Post by platosearwax on 2010-05-25
Seems to be totally gone for me in Lucid as well.  In fact, for the first time ever, I don't really have any video issues since installing Lucid (of course I have effects off and use Metacity for compositing, but even doing that before still gave me problems).

---

### Post by BobvanderPoel on 2010-05-25
Ummm, me too. Firefox seems stable after installing Lucid. Give it a bit of time ... one thing I did need to do was to get the nvidia drivers from nvidia.com. The ones in the lucid depositories just gave me the slowest and high-cpu-usage I've ever seen. Version 195-36-24 seems to be very nice with my 8400GS.

---

### Post by platosearwax on 2010-05-25
> **BobvanderPoel said:**
> Ummm, me too. Firefox seems stable after installing Lucid. Give it a bit of time ... one thing I did need to do was to get the nvidia drivers from nvidia.com. The ones in the lucid depositories just gave me the slowest and high-cpu-usage I've ever seen. Version 195-36-24 seems to be very nice with my 8400GS.

Oh, yes.  My system (I have an old Nvidia 6600) won't even give me a recognizable screen with default drivers or the ones in the repository.  I installed them from Nvidia like I have always had to but this time I have no issues at all.  I don't even get that embedded flash stuttering and flickering problem.  

I'm really happy with Lucid so far.

---

### Post by blazini on 2010-06-02
I've had the same problems with sound and flash, but did get it fixed. 

[http://ubuntuforums.org/showthread.php?t=1412153]("http://ubuntuforums.org/showthread.php?t=1412153")

....will pretty much take care of all the issues with flash sound (at least for me it did). I The only issue, which probably isn't an issue for most is that the only option that shows up in alsamixer is "pulse". I was trying to get 5.1 sound working so I undid this and my flash problems came back. I've given up on 5.1 for the time being so back I go.

---

### Post by Whizzospace on 2010-06-08
I've had the audio dropout and accompanying video playback 'speed-up" bug after a few minutes of running any Flash video. Like many here, I have been chasing this since since initial installation. 

I think I tried every possible fix listed in this thread: non-standard Nvidia drivers, ALSA tweaking, fresh Flash install. When I finally 'broke' Firefox, and it failed to run, I did a reinstall through the package manager. Haven't had any problem with any Flash vid since.

---

### Post by Whizzospace on 2010-06-12
One other change: after I uninstalled ALSA, I reinstalled a different app in the software manager "Gnome ALSA Mixer" versus "ALSA Mixer." Seems more stable over the past three days.

I noticed two Flash updates in the recommended patches today, but am worried about wrecking what finally seems like working Flash audio.

---

### Post by llawwehttam on 2010-06-12
I used to get this problem but after the recent flash updates it seems to have gone.

---

### Post by platosearwax on 2010-06-22
Well, this is irritating.  I had no problem once I upgraded to Lucid, flash worked fine.  Even when a new flash was installed recently everything was fine.  But suddenly today the problem crops up again, with the same thing, no sound, need to quit Firefox and then kill the process.

The only thing I can think at this point is that there was recently an update to pulse audio, which may be the actual sticking point at least on my system.  

I thought this was fixed....

---

### Post by Whizzospace on 2010-10-19
I finally gave up troubleshooting sound issues after a couple of months. I looked in the Pulse Audio list of sound cards that work with that audio software suite. 

Found a cheap Creative Sound Blaster Audigy SE 7.1 card. Works perfectly out of the box. 

So far, no Flash sound issues, no standard Movie Player audio dropouts, no Pulse Audio stream interruptions.

---

### Post by platosearwax on 2010-10-19
I almost forgot about this thread because I have had no problems at all for a long time.  Not exactly sure why or even when the problem resolved itself.  It may be related to the fact that I installed the Firefox extension that makes sure you have the proper flash version.  Whatever it is, I have no sound issues.

---

