---
title: "No DVD playback - tried everything?"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by David_1cog on 2007-06-18
I cannot play DVDs on my Dell Inspiron 6400 / E1505, Intel 945GM integrated graphics laptop.  When I insert a DVD playback begins, but the screen remains black with an occasional flicker / stutter of an image.  I hear some audio, but it skips and crackles.

I've spent *days* researching and trying all recommended solutions I can find - install libdvdcss2 + w32codecs + libdvdread3, enable DMA (which I can't because my DVD is connected as SCSI).  I've tried multiple media players.

I'm pretty sure I've tried everything recommended at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) + [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats).

It's an Ubuntu / Linux-specific problem as the same machine (Dell Inspiron 6400 / E1505, Intel 945GM integrated graphics) plays DVDs OK on Vista (hopefully soon to be wiped off!).

Any suggestions very gratefully received.

---

### Post by rapolas on 2007-06-18
> **David_1cog said:**
> 
It's an Ubuntu / Linux-specific problem as the same machine (Dell Inspiron 6400 / E1505, Intel 945GM integrated graphics) plays DVDs OK on Vista (hopefully soon to be wiped off!).


I have the same machine and everything works fine, so probably you did something to settings or maybe uninstalled something what is necessary to play dvd...

---

### Post by rabbit83 on 2007-06-18
Have you tried different DVD's? I had DVD's that showed the same behaviour as yours, due to the copy protection. After removing the copy (and in this case, play-) protection, the DVD's worked fine.

---

### Post by justin whitaker on 2007-06-18
Which player are you using?

---

### Post by David_1cog on 2007-06-18
> **rapolas said:**
> I have the same machine and everything works fine, so probably you did something to settings or maybe uninstalled something what is necessary to play dvd...

Quite possibly - I've had to do a lot of hacking to get wireless working, screen resolution working, mouse working, etc..  I'll reinstall Ubuntu as a last resort if this thread doesn't produce an answer.

> **rabbit83 said:**
> Have you tried different DVD's? I had DVD's that showed the same behaviour as yours, due to the copy protection. After removing the copy (and in this case, play-) protection, the DVD's worked fine.

I've tried several DVDs (all legit / shop bought).  How did you remove the copy / play protection?  Isn't that what libdvdcss2 does?

> **justin whitaker said:**
> Which player are you using?

I've tried several ... Totem, VLC, mplayer.  

I just tried using k9copy to rip the contents to mpeg4 - that seemed to work but playing the AVI file produced same results as the original DVD.  I then tried ripping to ISO - same result as AVI.

:-?

---

### Post by rabbit83 on 2007-06-18
> **David_1cog said:**
> 

I've tried several DVDs (all legit / shop bought).  How did you remove the copy / play protection?  Isn't that what libdvdcss2 does?



It should be, yes. But somehow, creating a backup with k9copy worked, while playing the DVD didn't.

---

### Post by David_1cog on 2007-06-18
Did you see that I have tried ripping with k9copy, although I've only tried sections of the DVD, not an entire backup.  As the sections don't work, I don't expect a full DVD backup would be any different.  Besides, I want to find a solution so that I can play my DVDs without to rip every single one!

P.S.  I just tried mplayer again and it reported gstreamer packages missing.  I've installed those and now the sound is perfect, but still no video display.

---

### Post by David_1cog on 2007-06-20
OK, I've stumbled on the solution - install 'gstreamer0.10-plugins-bad'.  That was all I needed.

Thanks for all the replies.

---

### Post by David_1cog on 2007-06-20
> **David_1cog said:**
> OK, I've stumbled on the solution - install 'gstreamer0.10-plugins-bad'.

I've just done a little digging to find out why I missed this package when I'd followed the instructions.  It looks like [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) instructions for 7.04 is missing the step of installing the 'gstreamer0.10-plugins-bad' package, although the instructions for 6.04 and 6.10 do tell you to install it.

I've asked in the discussion ([https://help.ubuntu.com/community/RestrictedFormats/Talk](https://help.ubuntu.com/community/RestrictedFormats/Talk)) if the article should be updated.

---

### Post by Ultra Magnus on 2007-06-20
Hi. I have a similar problem - on the same computer - I have downloaded all this stuff including gstreamer0.10-plugins-bad - I can get VLC to play the dvd but the video is really jumpy and unwatchable - any other ideas?

---

### Post by David_1cog on 2007-06-20
The problem has returned for me.  

I uninstalled some of the media players I had installed (gxine, mplayer, XMMS) and the same symptoms appeared - jumpy, unwatchable playback.  I re-installed them and still the same problem.  I tried uninstalling / re-installing 'gstreamer0.10-plugins-bad ' but that did not fix it.

Back to square one. :(

---

### Post by mikedoth on 2007-06-21
I am also having the same problem.

Two days ago I installed DVD playback in Totem on three machines, they all worked perfect for the first day. That night I shut them all down and the next day after work I booted them all up and found DVD playback was broken. I was especially pissed when VLC player (my holly grail of media players) was also broken. I can only asume it is Gstreamer related.

Tonight i'm going to uninstall Gstreamer.

---

### Post by freshmeatz on 2007-06-21
hmm you have the file libdvdread? and other lo's that go with it as dep's

---

### Post by mikedoth on 2007-06-21
**SOLUTION**

Rollback css file ([http://ubuntuforums.org/showthread.php?t=475213&highlight=libdvdcss+rollback+dvd&page=2](http://ubuntuforums.org/showthread.php?t=475213&highlight=libdvdcss+rollback+dvd&page=2)).
sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by David_1cog on 2007-06-23
> **mikedoth said:**
> **SOLUTION**

Rollback css file ([http://ubuntuforums.org/showthread.php?t=475213&highlight=libdvdcss+rollback+dvd&page=2](http://ubuntuforums.org/showthread.php?t=475213&highlight=libdvdcss+rollback+dvd&page=2)).
sudo /usr/share/doc/libdvdread3/install-css.sh

Not a solution for me. :(

Maybe part of the problem: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110636](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110636), although that wouldn't explain why I got it working earlier.

I've now done a clean install of Feisty (third time this week).  I've installed all gstreamers, libdvds, win32codecs, etc. that I can find mentioned.  Problem persists.  Grrr.

**I've just discovered that the problem is not restricted to DVD playback for me** - any video (avi,mpeg,mov,qt,mp4,wmv) suffers the same problem and in any media player.  Am I missing CODECs?

---

### Post by David_1cog on 2007-06-23
Found this: [https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/65165](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/65165)

I've now got video (avi, mpeg, etc.) playback working in mplayer (change Preferences ... Video ... driver to X11 instead of default XMGA) and VLC (Prefs ... Output Modules ... X11).  They still don't play DVDs though.

I'm about beaten on this.

---

### Post by uconvert on 2007-06-23
Same thing happend to me!

I'm really upset.:(

 I persuaded five friends to try Feisty and they are fumin! The worst part is having it set up right and then having an update mess it up. Shades of Microsoft?

 I have Dapper on my Desktop and its fine, so its a Fesity only bug. for now I am unistalling Feisty and reinstalling Dapper on my laptop. Dapper is STABLE - the only drawback is Firfox 1.5 instead of Firefox 2

If anyone finds a genuine permanent solution, I am up to giving it a try!

Thanks for letting me vent (sorry)

Don

---

### Post by rapolas on 2007-06-24
I had the same problem, but then I installed video card drivers and now everything is just fine.

---

### Post by David_1cog on 2007-06-24
> **rapolas said:**
> I had the same problem, but then I installed video card drivers ...

How did you do that?

---

### Post by David_1cog on 2007-06-24
OK, I've found the culprit - Beryl / Compiz.  Switch to Metacity windows manager and DVDs play ([http://ubuntuforums.org/showpost.php?p=2741054&postcount=7](http://ubuntuforums.org/showpost.php?p=2741054&postcount=7)).

To recap: the solution / workaround for me is to use X11 video output in VLC (this allows playback of video files with Beryl running), and turn off Beryl to watch DVDs.

I'll try and find a full solution at the Beryl + Compiz forums now.

---

### Post by stoske on 2007-06-26
I have the same problem.

I have x800xl aiw graphic card. 

When I am using  Beryl or Compiz I cannot watch movies, there is only a sound. Switching to Metacity and video works just fine.

I installed fresh Ubuntu 7.04 and Beryl and everything worked instantaneously.

First time I tried to install driver but then I was unable to start Beryl.

I hope that there is some solution for this video problem.

---

### Post by uconvert on 2007-06-27
OK~

I took my Ubuntu only laptop and downgraded to Ubuntu 6.06LTS. Then I followed the enable DVD playback procedure on this How To: [http://www.cs.cornell.edu/~djm/ubuntu/](http://www.cs.cornell.edu/~djm/ubuntu/)

It works great with no problem. My Test DVD's are Gone in 60 Seconds (redux) and Hamlet (Ethan Hawke).

Then I took my Dual-Boot Laptop and did a fresh install of Feisty and used the same procedure and get error, asking if I'm trying to play a DVD w/o libdvdcss2.

What's going on with Feisty? 

Open-source video drivers don't work on my Compaq Presario 1500; I have to do the dpkg-reconfigure xserver-xorg procedure for Feisty, otherwise I get stuck with a split-screen.

Truthfully I  don't play DVDs but I can't recommend Feisty as an XP replacement w/o DVD playback!

Still looking for a solution!

Don

---

### Post by paradoxni on 2007-06-27
try  sudo /usr/share/doc/libdvdread3/install-css.sh

youll need libdvdread3 package installed first thou: sudo apt-get install libdvdread3

---

### Post by uconvert on 2007-06-29
Didn't work.:(

---

### Post by uconvert on 2007-07-11
I FIXED IT!:)


I forgot that I switched my CDRW/DVD-ROM Drive to a DVD RAM Drive. 

Apparently it shipped with the region code set to 0 - I found a useful utility called regionset

Changed region to 1 and just watched Crouching Tiger Hidden Dragon - plays beautifully!

Hope this helps others!


Good thing I have too much time on my hands!

My apologies to FEISTY - it's not you it's me!

Don

---

### Post by galileon on 2007-07-19
watchout with that regionset thingy, it can only be used 5 times! after that you have to get a new dvd drive!

> **mikedoth said:**
> **SOLUTION**

Rollback css file ([http://ubuntuforums.org/showthread.php?t=475213&highlight=libdvdcss+rollback+dvd&page=2](http://ubuntuforums.org/showthread.php?t=475213&highlight=libdvdcss+rollback+dvd&page=2)).
sudo /usr/share/doc/libdvdread3/install-css.sh

YOU ARE MY HERO!!!!!!!!!!!!!!!!

---

