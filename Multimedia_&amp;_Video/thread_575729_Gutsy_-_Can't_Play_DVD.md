---
title: "Gutsy - Can't Play DVD"
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by Cirrocco on 2007-10-14
I hope I got this in the right forum...

I've been fighting with this for a few days now.
I can't play a DVD in Gutsy (the beta version for anyone looking back at this after official release)

I fire up Totem and get:
```
Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.
```

I've installed the w32codecs, the xine plugins, the ubuntu restricted kit, vlc (I know it's a separted player, but it doesn't work either).

I tried easyubuntu, but it insta-crashes after asking for my password.

I'm tapped out.
I don't know what's wrong.
I don't want to go back to edgy - I love this OS.

any pointers?

---

### Post by carlinuxlearner on 2007-10-14
Same problem, I don't know how to get Totem to work, I just installed Kaffeine, and it works.

C@RL

---

### Post by janbockaert on 2007-10-14
same here. where is libdvdcss in the repo's?

---

### Post by AvixK7 on 2007-10-15
I'm having the same problem, libdvdcss3 is installed but neither totem nor xine ( my prefered dvd player) will work. everything is properly installed as far as I know...

---

### Post by Cirrocco on 2007-10-15
is there such thing as dvdlibcss3?  I thought it only went to 2.

I'm having a bit of confusion over what xine and gstreamer are.
it seems that totem will hook into one or the other.
are they the backend engine for decoding DVDs?

---

### Post by Perpetual on 2007-10-19
Any resolution to this.  I just found that my 7.10 Final will not play DVD's and all is installed...

Edit: just walked back through the multimedia how-to with no success.   Installed gxine and it won't play them either.  Frustrated now :(

---

### Post by agisfox on 2007-10-19
I have the same problems with DVD playback, but not dvd-ripping; both Thoggen and iriverter can rip dvds fine.  Thoggen shows the preview frames too, and it uses gstreamer like totem does so it's not a plugins issue as far as I can tell.

Edit:
VLC works for me now though, just not Totem which gives the plugins error.

Edit 2:
Totem will play the VOB files if I open them manually, however, it just can't open the disk.

So it looks like I have a different problem.

---

### Post by Perpetual on 2007-10-19
I am at a loss at this point.  I have tried everything, uninstalled and walked back through it again.  Nada.  I suppose I will install VLC Player (although I think it's my least favorite).  Will see if VLC works right now...

Edit: VLC works.

---

### Post by agisfox on 2007-10-19
Ok, as per Bugzilla Bug #344415 the "Open DVD" menu part of Totem doesn't actually work:

[http://bugzilla.gnome.org/show_bug.cgi?id=344415](http://bugzilla.gnome.org/show_bug.cgi?id=344415)

---

### Post by Perpetual on 2007-10-19
> **agisfox said:**
> Ok, as per Bugzilla Bug #344415 the "Open DVD" menu part of Totem doesn't actually work:

[http://bugzilla.gnome.org/show_bug.cgi?id=344415](http://bugzilla.gnome.org/show_bug.cgi?id=344415)

It's funny you said that.  I noticed when I put a disc in, totem opens and the disc plays....without video.  I can hear it.  Can't see anything.  Stop it, start it and it fails.

From Bug Tracker

[i] Comment #8 from Alex Ruddick  (points: 1)
2007-10-10 16:26 UTC [reply]

Another workaround is to open and close the DVD drive, which should start Totem
and begin playing.

Rather annoying bug, but it's possible to live with it.[/i]

Yeah but I have no video, just sound.  Another problem also??

---

### Post by msubzwari on 2007-10-19
I had the same problem.  
Could not make it work in totem until I changed from totem-gstreamer to totem-xine.  
Now DVD playback is fine.

---

### Post by liveforfunnow on 2007-10-22
> **msubzwari said:**
> I had the same problem.  
Could not make it work in totem until I changed from totem-gstreamer to totem-xine.  
Now DVD playback is fine.

so, gstreamer is broken in gutsy? I have the problem where Totem opens, but sound only - no video. VLC just chokes (no playback whatsoever when I use any of VLC's menus). I can play .avi files just fine. 

is there any possibility of getting this to work with the gstreamer engine?

---

### Post by Perpetual on 2007-10-22
> **liveforfunnow said:**
> so, gstreamer is broken in gutsy? I have the problem where Totem opens, but sound only - no video. VLC just chokes (no playback whatsoever when I use any of VLC's menus). I can play .avi files just fine. 

is there any possibility of getting this to work with the gstreamer engine?

I ended up using Totem-xine.  I inquired on bugzilla.gnome ([http://bugzilla.gnome.org/show_bug.cgi?id=344415](http://bugzilla.gnome.org/show_bug.cgi?id=344415)) with no response as of yet.  Although, VLC worked for me from the start.  I just don't care for VLC, have never found it to have very good quality playback.

---

### Post by Quadcore on 2007-10-22
I had the same problem, so I reinstalled mplayer from source and now it works perfect..

---

### Post by rapsball4 on 2007-10-22
Also trying to get DVD playback on my 64-bit Gutsy.  Not working in any media player right now.

---

### Post by Cariboo1938 on 2007-10-22
Just a comment in general....
I'm wondering what the problem is with playing DVDs...
I joint the Ubuntu Community in 2006  installing Dapper, then followed the upgrade to Edgy, now running Feisty and each time, it took me days and weeks to get a DVD player running. Right now in Feisty, VLC media player is working so, so.....if I put a DVD in, it still does not start automatically, but OK, I can live with that....
Now again, Gutsy installations still have this problems with that.

---

### Post by frostie on 2007-10-23
System>Preferences>Removable Drives and Media then 'Multimedia' tab.

---

### Post by frostie on 2007-10-23
What just worked for me was a suggestion in Launchpad:

[https://answers.launchpad.net/ubuntu/+source/totem/+question/12582](https://answers.launchpad.net/ubuntu/+source/totem/+question/12582)

ie:

sudo apt-get install libdvdread3 libxine1-ffmpeg

I am runnning totem-xine btw, libdvdread was already installed anyway but the libxine install kickstarted dvd play in Totem.

---

### Post by pfred on 2007-10-25
The repositories are new for Gutsy and might not be working for you guys. Add the Gutsy medibuntu repository to get *libdvdcss* and *w32codecs*.

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

I hope this helps. I also found that changing the Totem backside to Xine instead of Gstreamer worked. Just search for Xine in Synaptic and choose to install xine. Gstreamer will be replaced.

---

### Post by theorganloft on 2007-10-25
I am just glad to know that it was not me.  I also tried almost everything to get it to  work.

I noticed it the first day I installed Gutsy.  I have faith that it will get fixed.  I do not want to give up my Gutsy to watch a bootlegged movie. :lolflag:

I am going to try VLC player  until this gets resolved.

---

### Post by C00P88 on 2007-10-26
For those that were able to play a dvd using VLC: Is there anything else that needs to be installed/configured to get a DVD to work? I've tried mplayer, xine, totem-xine, and VLC. Synaptic shows I have libdvdcss2, libdvdnav4, and libdvdread3 installed. I also went to the medibuntu site and installed the whole repository for gutsy

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```


and installed the w32codecs (I read somewhere I needed them)

```

sudo apt-get install w32codecs
```

This morning I could get sound to play, if I opened VLC and then tried to play the DVD on Totem. Now, I get the "The source seems encrypted...Are you trying to play....without libdvdcss?" message. 

When I try to play on VLC I get "Unable to open 'dvdsimple:///dev/hda". 

So what's the secret? :confused:

---

### Post by Chuckaluphagus on 2007-10-26
I can get DVDs to play back in Mplayer only.  On Feisty, I could play DVDs in Totem, Mplayer, Gxine, VLC etc.  I did a clean install for Gutsy and I've installed libdvdcss2, libdvdnav4, libdvdread3, w32codecs, all of the available gstreamer plugins.  Totem-gstreamer tells me I don't have the appropriate plugins to play a DVD, totem-xine gives a slightly more terse message that tells me the same thing, in essence.  VLC doesn't even give me an error message, it just either fails playback or closes out.

I'm wondering what changed between 7.04 and 7.10?  Enabling DVD playback on previous versions has always been a two-minute procedure, it seems to have gotten much harder.

---

### Post by features on 2007-10-27
I have very similar problems - MPlayer is garbled, even though I have libdvdcss2 etc installed, and my VLC just crashes with this error when playing DVDs:

```
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
libdvdread: Can't allocate memory for file read!
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:214: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)

```

Will try totem-xine now :)

---

### Post by Sean Babu on 2007-10-27
I love Ubuntu, GG even more than FF, but I don't understand why this has to be so complicated.

On FF, after MUCH struggle I was able to play VCDs and DVDs in MPlayer. I never got anything to play in Totem.

On GG, right after the upgrade nothing played, but after I rebooted, VCDs played in MPlayer but DVDs didn't. I am however now able to play DVDs in VLC, but the picture is not that great. (It might be the disc, though.) Again, nothing works in Totem.

I have yet to be able to figure out how to play multi-track VCDs in any player.

I'll have to try some of the other suggestions in this thread, but it's hard to justify spending the time experimenting essentially to enable a function for goofing off.:(

---

### Post by Sean Babu on 2007-10-27
Just installed glxine and totem-xine. Nothing plays on them. Oh well. I'm sure it will get fixed eventually.

---

### Post by BoardDWorld on 2007-10-27
Same problem here, everything is installed and now ALL related packages have been reinstalled. No go... Feisty was fine in this area, just click and go!

---

### Post by Dimitriid on 2007-10-27
first network and now this? This is just pathetic how can gutsy be such a piece of garbage and everybody keeps praising it?

---

### Post by tonyshangrila on 2007-10-27
Eventually got this to work.  Here are the steps that I took after reading this thread from the start:
Was not working w/ totem-gstreamer
switched to totem-xine, wouldn't work either
wouldn't work w/ VLC

added medibuntu repository, installed w32codecs and libdvdcss2.  already had libdvdnav4 and libdvdread3.  This worked!

Just for fun, switched back to totem-gstreamer to see if that would work, too-- no go.  So, now I have:
totem-xine
w32codecs
libdvdcss2
libdvdnav4
libdvdread3

... and I have playback in Movie Player or VLC.  Don't have any other players installed.

---

### Post by C00P88 on 2007-10-27
I'm so jealous.

---

### Post by gwoodard on 2007-10-27
Here's what I learned; most of the people probably think that the "DVD" Codecs are ready when installed but (as most of you and myself included) did not think to restart the computer after dvd codecs installed (wine is very similar to this approach for some reason)

Rundown:
Install Gutsy (or other Ubuntu version)
Restart PC
Update (if any)
May seem like a joke but restart PC
Install DVD Codecs (Ubuntuguide and Synaptic manager)
Restart PC
Play a dvd to see if it works (it did for mine ((after trial and error)))

---

### Post by Perpetual on 2007-10-27
I don't know if we should be blaming Ubuntu for this when there is an open Gnome bug regarding Totem that was the problem I was having...

[http://bugzilla.gnome.org/show_bug.cgi?id=344415](http://bugzilla.gnome.org/show_bug.cgi?id=344415)

Then again, these may be 2 different issues entirely.

---

### Post by DeadToad on 2007-10-27
You need to REINSTALL livdvdcss2 to get VLC and MPlayer to play DVDs.

livdvdcss2 is NOT in any repository, I searched til the cows came home and could not find it.
It IS here: [http://download.videolan.org/pub/lib...2.9-1_i386.deb](http://download.videolan.org/pub/lib...2.9-1_i386.deb)

Just click the link, then (do NOT save it) "open" it with the default selection.
Then click "install software", and let it finish.
After that, VLC and MPlayer will play your DVDs real nice.
Have fun.
DeadToad

---

### Post by DeadToad on 2007-10-28
HOW TO GET VLC AND MPLAYER TO PLAY DVDs
(the Step-by-Step method, nothing left out!)

Installation instructions for libdvdcss2 and w32codecs in Ubuntu, to play DVDs in MPlayer and VLC:

To add libdvdcss2 and win32codecs to your Ubuntu installation, you have to add the Medibuntu package repository to your /etc/apt/sources.list file.

To do this, you have to:
1. Edit the file /etc/apt/sources.list using either of the following commands in a terminal:
gksudo gedit /etc/apt/sources.list to open it in the GUI text editor
or
sudo vim /etc/apt/sources.list to open it in the Vim command line text editor

2. Add the following lines to add the Medibuntu repository to the file:

## Medibuntu - Ubuntu 7.10 &#8220;gutsy gibbon&#8221;
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free

If you are running Feisty or some other release, other than gutsy, replace the word &#8220;gutsy&#8221; in the three lines above with the name of the release you are using.

3. Import the gpg key for the Medibuntu repository to ensure that the packages are installed without warnings/errors regarding trust:
To do this, run the following command from the terminal:
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

4. Now update the local list of packages to get the list of packages from the newly added Medibuntu repository:
In a terminal execute the following command:
sudo apt-get update

5. Now you can install libdvdcss2 and w32codecs using the following command:
sudo apt-get install libdvdcss2 w32codecs

Close terminal window.

6. To install/reinstall VLC Media Player:
Open Synaptic (System -> Administration -> Synaptic Package Manager).
Type your password.
Click Settings -> Repositories.
Under "Ubuntu Software" check the first four items, making sure you have the "universe" repository checked.
Do NOT check "source code".
Under "Third-Party Software" check all items.
Under "Updated/Ubuntu Updates" check all items.
Click "Close", twice if necessary.
Now back at the Synaptic Package Manager main window:
Click "Search".
Type "vlc".
Click "Search" button.
"vlc" will be shown in the left window.  left-click it once to highlight it.
In the right window, click on these additional files: vlc-plugin-esd and mozilla-plugin-vlc, then click "Mark for installation" for each file.
(libdvdcss2 which will be installed later, as it is NOT in a repository).
Click "Apply".
Click "Apply" again, if necessary to begin download.
After "Changes applied", click "Close".
Close "Synaptic Package Manager" window.

7. Now, you just need to REINSTALL livdvdcss2 to get VLC and MPlayer to play DVDs:
livdvdcss2 is NOT in any repository, I searched til the cows came home and could not find it.
It IS here: [http://download.videolan.org/pub/lib...2.9-1_i386.deb](http://download.videolan.org/pub/lib...2.9-1_i386.deb)

"libdvdcss2_1.2.9-1_i386.deb"

Just click the link, then "open" it with the default selection (do NOT save it).
Then click "install software", and let it finish.
After that, VLC and MPlayer will play your DVDs real nice.
Have fun.
DeadToad

---

### Post by features on 2007-10-28
Yeah, I forgot to reboot after installing libdvdcss.  Why?  because this is *Linux*...if I can install a graphics driver (ATI, no less...) without having to reboot, I don't see why I should have to, to play DVD's :D - and I don't think I've ever had to up until now, either, though I'm probably wrong there ;)

In short I now have:

VLC and MPlayer working, OKish (they don't like being moved around, and it looks pretty funny if you rotate the cube while in fullscreen mode).
Totem-Xine or -Gstreamer are just as crap as they always have been, and won't play DVD's

---

### Post by C00P88 on 2007-10-28
> 7. Now, you just need to REINSTALL livdvdcss2 to get VLC and MPlayer to play DVDs:
livdvdcss2 is NOT in any repository, I searched til the cows came home and could not find it.
It IS here: [http://download.videolan.org/pub/lib...2.9-1_i386.deb](http://download.videolan.org/pub/lib...2.9-1_i386.deb)

Is the above supposed to be li**v**dvdcss2 or li**b**dvdcss2? Also, the link results in an error 404- Page Not Found.

li**b**dvdcss2 is listed in synaptic.

And I have yet to play a DVD. I'm done for awhile.

---

### Post by DeadToad on 2007-10-28
> **C00P88 said:**
> Is the above supposed to be li**v**dvdcss2 or li**b**dvdcss2? Also, the link results in an error 404- Page Not Found.

li**b**dvdcss2 is listed in synaptic.

And I have yet to play a DVD. I'm done for awhile.

---

Sorry for the mistype, it is "libdvdcss2".
I can't believe that link is now Dead!
Even though libdvdcss2 is listed in synaptic, it needs to be reinstalled; that was my case.

If you need the "libdvdcss2_1.2.9-1_i386.deb" file, it can be found here (right now), I just googled it and this link is working: 
[http://files.filefront.com/libdvdcss2+129+1+i386deb/;6575747;/fileinfo.html](http://files.filefront.com/libdvdcss2+129+1+i386deb/;6575747;/fileinfo.html)

---

### Post by Sean Babu on 2007-10-28
I looked in Synaptic and saw that I already had libdvdcss2 installed.

Installing, reinstalling, and tweaking every possible setting isn't very "it just works." Again, this shouldn't be so complicated.

If anyone does find out the underlying problem as to why the various applications seem to work arbitrarily for some people and not for others, please do let us know.

---

### Post by DeadToad on 2007-10-28
The videolan link has been changed, here is the new one:
[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2-dev_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2-dev_1.2.9-1_i386.deb)
Just "open" it, do NOT save it.  Then click "install software".
DVD playback should work then.

---

### Post by moeFinley on 2007-10-28
Finally got it working.  Installed all the above but you must restart.  Very strange!

This is still a bug as Gutsy is supposed to install all this automatically.  It's a real shame as this is the one of the first things people new to Linux point out, no MP3 and DVD support.

---

### Post by C00P88 on 2007-10-28
Ok, I tried the link, got an error stating 
> 
Error: Dependency is not satisfiable: libdvdcss2

So I went back through all the steps, when I got to step 3, the result is:

> gpg: No valid OpenPGP data found

wtf?

Edit: I just went into Synaptic, it said it could not download info from all repositories, specifically the ones regarding medibuntu. Hmm.

---

### Post by hoppingsnail on 2007-10-28
Ubuntu and computer-novice reporting with my struggles to play my Monty Python and the Holy Grail DVD on Gutsy. :)  This is my first post too so... hi!

libdvdcss2 sure is elusive today, isn't it?  I tried the links in this topic, but none of them worked.  I found it somewhere through google.  I won't post the link because that seems to be bad luck, with all the other links that were posting going down. ;)

Anyway, I followed all the steps (installing the codecs, reinstalling libdvdcss2, restarting the computer) and I got VLC up and running.  Totem does not play them, though.  That is, Totem does not work for me when you select the dvd from the menu, but it partly works when it autostarts.  It plays the film, but there are no menus.  It sounds a lot like the bug Perpetual linked to ([http://bugzilla.gnome.org/show_bug.cgi?id=344415](http://bugzilla.gnome.org/show_bug.cgi?id=344415))  The screen also looks "squished" for some reason.  I set the DVD  to autostart when the DVD is inserted with VLC instead through the System-Prefs-Removable Media menu.  

So, short version:

1) Followed the steps in this topic from Dead Toad and others.
2) Installed codecs, re-installed libdvdcss2
3) Restarted computer.

Results

1) VLC works fine.
2) Totem will auto-start, but will not play dvd from menus.  When it plays a film in widescreen, the film gets more "squished" than it should.  Title menus not accessible, forward/back chapter buttons do not work.  Most of this is straight from [http://bugzilla.gnome.org/show_bug.cgi?id=344415](http://bugzilla.gnome.org/show_bug.cgi?id=344415).

I like the default movie player... but I guess I'll have to stick with VLC for now.  At least it works.

---

### Post by nsti on 2007-10-28
I actually do have Totem fully functional now in v7.10. Follow these insructions

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I also followed the instructions from the Beginning Ubunbu Linux (Apress) to change Totem to Totem-Xine. ( Pages 377 - 378 ) Once these were accomplished the DVDs snapped to and run as expected.

That did the trick for me.

Jack

> **Perpetual said:**
> I am at a loss at this point.  I have tried everything, uninstalled and walked back through it again.  Nada.  I suppose I will install VLC Player (although I think it's my least favorite).  Will see if VLC works right now...

Edit: VLC works.

---

### Post by newmo on 2007-10-28
>  Error: Dependency is not satisfiable: libdvdcss2


 I had same error message.

So I did

>  sudo apt-get remove libdvdcss2


I then used the package in** post #36** above rather than the later official videolan one posted.

(I didn't choose open - but that's probably irrelevant)

This also gave an error message about newer package being available from official sources but I was able to ignore this and install (I did an install and reinstall) and then I restarted and yes it is now working as far as I can see.

All a bit nuts but thanks to Dead Toad for  the  instructions for getting it fixed.

My only difference is using the the second of the three links for the libdvdcss2 package

> If you need the "libdvdcss2_1.2.9-1_i386.deb" file, it can be found here (right now), I just googled it and this link is working:
[http://files.filefront.com/libdvdcss.../fileinfo.html](http://files.filefront.com/libdvdcss.../fileinfo.html)

This is all a bit annoying as I asumed the tested version for gutsy had been sorted out and installed with the Ubuntu restricted package that I had downloaded on day one.

I am now using this unofficial old version that for whatever reason seems to work (though the source is a complete mystery to me - so my machine is probably now a spambot :-))

Joys of Linux I guess.

---

### Post by DeadToad on 2007-10-28
Yes, Step #3 does give errors messages.  But, ignore them and continue down the yellow brick road.
There are 2 versions of the libdvdcss2.deb file available.
They are:
libdvdcss2_1.2.9-1_i386.deb [http://files.filefront.com/libdvdcss2+129+1+i386deb/;6575747;/fileinfo.html](http://files.filefront.com/libdvdcss2+129+1+i386deb/;6575747;/fileinfo.html)
and 
libdvdcss2-dev_1.2.9-1_i386.deb [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2-dev_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2-dev_1.2.9-1_i386.deb)

I used the first one. 

Both of the last two links I posted are still active.
Just click "Open" the file with the default program, do not "Save" it.  Then click "Install Software".  Let it finish.  Then it should work.

I compiled the "How-To" instructions from 3 other posters comments from various sites, then did research on my own, and then found the libdvdcss2 files using Google.  After 2 hours around midnight, I could play DVDs.

I have both Totem MPlayer and VLC Media Player working perfectly.  Except Totem freezes after about 30-45 minutes of playing.
So, I use VLC.  It works flawlessly.
Hope this helps.
Good luck.
DeadToad

---

### Post by Mostlyharmless42 on 2007-10-28
> **tonyshangrila said:**
> Eventually got this to work.  Here are the steps that I took after reading this thread from the start:
Was not working w/ totem-gstreamer
switched to totem-xine, wouldn't work either
wouldn't work w/ VLC

added medibuntu repository, installed w32codecs and libdvdcss2.  already had libdvdnav4 and libdvdread3.  This worked!

Just for fun, switched back to totem-gstreamer to see if that would work, too-- no go.  So, now I have:
totem-xine
w32codecs
libdvdcss2
libdvdnav4
libdvdread3

... and I have playback in Movie Player or VLC.  Don't have any other players installed.

I did all of this and it worked, the only detail that was left out is that in my case it required a restart.  At first i thought it didn't work, but I restarted and now it works.

---

### Post by RAV TUX on 2007-10-28
> **Mostlyharmless42 said:**
> I did all of this and it worked, the only detail that was left out is that in my case it required a restart.  At first i thought it didn't work, but I restarted and now it works.

I get this:

```
ravtux@CafeLinux:~$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Ign http://medibuntu.sos-sts.com gutsy Release.gpg
Ign http://medibuntu.sos-sts.com gutsy/free Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://medibuntu.sos-sts.com gutsy/non-free Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release
Ign http://medibuntu.sos-sts.com gutsy Release
Hit http://us.archive.ubuntu.com gutsy-updates Release
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://us.archive.ubuntu.com gutsy/main Packages
Ign http://medibuntu.sos-sts.com gutsy/free Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Ign http://medibuntu.sos-sts.com gutsy/non-free Packages
Ign http://medibuntu.sos-sts.com gutsy/free Sources
Ign http://medibuntu.sos-sts.com gutsy/non-free Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Err http://medibuntu.sos-sts.com gutsy/free Packages
  404 Not Found
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Err http://medibuntu.sos-sts.com gutsy/non-free Packages
  404 Not Found
Err http://medibuntu.sos-sts.com gutsy/free Sources
  404 Not Found
Err http://medibuntu.sos-sts.com gutsy/non-free Sources
  404 Not Found
Fetched 3B in 1s (2B/s)
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/gutsy/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/gutsy/free/source/Sources.gz  404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/gutsy/non-free/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
ravtux@CafeLinux:~$      
```

---

### Post by mc4man on 2007-10-29
gotta lose the sos-sts stuff
```
Hit http://packages.medibuntu.org gutsy/free Packages
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://archive.ubuntu.com gutsy-updates/main Sources
Hit http://archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Sources
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://archive.ubuntu.com gutsy-security/main Packages
Hit http://archive.ubuntu.com gutsy-security/restricted Packages
Hit http://packages.medibuntu.org gutsy/non-free Packages
Hit http://archive.ubuntu.com gutsy-security/main Sources
Hit http://archive.ubuntu.com gutsy-security/restricted Sources
Hit http://archive.ubuntu.com gutsy-security/universe Packages
Hit http://archive.ubuntu.com gutsy-security/universe Sources
Hit http://archive.ubuntu.com gutsy-security/multiverse Packages
Hit http://archive.ubuntu.com gutsy-security/multiverse Sources
Fetched 192B in 1s (176B/s)

```
in sources
```
Medibuntu.
deb http://packages.medibuntu.org/ gutsy free non-free
```

---

### Post by DeadToad on 2007-10-29
Some changes to Step 6, new links in Step 7, and added Step 8.
I just installed Linux Ubuntu Gutsy Gibbon v7.10 on another desktop, following this "how-to" and VLC and Totem MPlayer play DVDs flawlessly.

6. To install/reinstall VLC Media Player:
Open Synaptic (System -> Administration -> Synaptic Package Manager).
Type your password.
Click Settings -> Repositories.
Under "Ubuntu Software" check the first four items, making sure you have the "universe" repository checked.
Do NOT check "source code".
Under "Third-Party Software" check all items.
Under "Updated/Ubuntu Updates" check the first two items.
Click "Close", twice if necessary.
Now back at the Synaptic Package Manager main window:
Click "Search".
Type "vlc".
Click "Search" button.
"vlc" will be shown in the left window.  left-click it once to highlight it.
In the right window, click on these additional files: vlc-plugin-esd and mozilla-plugin-vlc, then click "Mark for installation" for each file.
(libdvdcss2 which will be installed later, as it is NOT in a repository).
Click "Apply", twice if necessary to begin download.
After "Changes applied", click "Close".
Close "Synaptic Package Manager" window.

7. Now, you just need to REINSTALL livdvdcss2 to get VLC and Totem MPlayer to play DVDs:
"libdvdcss2_1.2.9-1_i386.deb" is here: 
[http://files.filefront.com/libdvdcss2+129+1+i386deb/;6575747;/fileinfo.html](http://files.filefront.com/libdvdcss2+129+1+i386deb/;6575747;/fileinfo.html)
(This is the version that works).
If not found, google "libdvdcss2_1.2.9-1_i386.deb" for an active link.

libdvdcss2-dev_1.2.9-1_i386.deb is here: [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2-dev_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2-dev_1.2.9-1_i386.deb)
or here: [http://downloads.videolan.org/pub/videolan/libdvdcss/1.2.9/deb/](http://downloads.videolan.org/pub/videolan/libdvdcss/1.2.9/deb/)
or here: [http://www.free-dvd.org.lu/libdvdcss/debian/](http://www.free-dvd.org.lu/libdvdcss/debian/)
(This version does not work).
If not found, google "libdvdcss2-dev_1.2.9-1_i386.deb" for an active link.

Just click the link, then "open" it with the default selection (do NOT save it).
Then click "Install Package", and let it finish.
After that, VLC Media Player and Totem MPlayer will play your DVDs.

8. Reboot computer, then run Update Manager again for additional updates (libdvdread3):
System/Administration/Update Manager.
===
DeadToad

---

### Post by Mateo on 2007-10-31
The problem is that with totem-xine, it won't player /dev/video0  which is the TV card location.  but totem-gstreamer will...

---

### Post by wjston on 2007-11-04
I couldn't get DVD playback working in Gutsy until I installed Xine-ui. Forget about Totem-xine, it just complains about not having the proper codecs.

---

### Post by TNT220 on 2007-11-09
OK, I'm a total newbie when it comes to Linux, and have had both the network,usb and Totem cannot find plugin error..

I finally got totem to work with playing dvd, and here is what I did.. but I cannot explain why it works..

installed 
totem-xine
libdvdcss2
libdvdnav4
libdvdread3

I also tried the gstreamer-options and set it to the X.org with no xv

Since that didn't hekp i decided to try gxine which gave me the "xine engine error: no demuxer found"..

I then in synaptics installed everything libxine related (except dev stuff) and tried again.. now the video started, but was totally green... on [http://www.xinehq.de](http://www.xinehq.de) I then found the switch to run gxine with gxine -V XShm and now the video played.

Then I started totem and now it suddenly played my dvd perfectly... 

maybe someone can tel me why it works.... I'm just happy that it does..

---

### Post by marco123 on 2007-11-09
All I do as part of my install routine is try to play all my video/music type files and install the codecs when prompted, then:

If your on 32bit just run:  sudo /usr/share/doc/libdvdread3/install-css.sh

If 64bit you will need to run this command first: "sudo apt-get install debhelper build-essential fakeroot "     then run the above command.

This has worked on about 7 or 8 different installs in a row for me.:)  Everyone seems to be making it as hard as possible.:confused:

EDIT:  I use ogle to play DVDs with full menus.

---

### Post by thousandrobots on 2007-11-10
i was briefly having the same problem as everyone else here, but in the end, i think all you really need to do is:

- install the ubuntu-restricted-extras [as described on the wiki]("https://help.ubuntu.com/community/RestrictedFormats")
- sudo apt-get install totem-xine
- sudo apt-get install vlc
- reinstall libdvdcss2 with "sudo apt-get libdvdcss2"
- sudo apt-get install libdvdread3 libxine1-ffmpeg 
- sudo /usr/share/doc/libdvdread3/install-css.sh

i did not have to reboot.

i did this on a brand new install of gutsy, and it worked -- i put in a dvd and it started playing in totem. the menus didn't work, but they do in VLC. this is with crap integrated graphics chipset and an external dvd burner. also, vlc users, don't forget to make sure you are typing the right device name into your "open disc" dialog box. /dev/scd1 or /media/cdrom0 or whatever.

---

### Post by Irish_spartan1775 on 2007-11-10
I think this is my first post on this forum.

I was having a hell of a time playing dvd's since making the permanent switch to linux.  this forum helped fix my problem.

i love VLC

---

### Post by monkeytech on 2007-11-10
this one command is what did the job after i thought i tired everything.. on fresh install of gusty with extra's xine installed

sudo /usr/share/doc/libdvdread3/install-css.sh

if you are having problems try that one command may be whats needed..


cheers to the above poster for pointing this out

---

### Post by Rog-Mahal on 2007-11-11
I'm having problems with this as well. I appear to have all the correct dvd codecs, libdvdread, libdvdcss, xine, vlc, ALL of it.

Yet, when I attempt to play a dvd, I get the following error:

```
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/roger/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000132
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00005051
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000053fe
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000053fe)!!
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00371e7b
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x00371e7b)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00371e7f
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x00371e7f)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0037c37d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0037c381
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x0037c381)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0037e580
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x0037e580)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0037e584
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x0037e584)!!
libdvdread: Elapsed time 1
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 7
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.

```

Can anyone make sense of this? I'd really appreciate some help, this is really frustrating.

---

### Post by Presto123 on 2007-11-11
I'm just wondering myself if I can get ALL dvd's to play. Certain ones just buck, but others play beautifully. I'm thinking it's company specific. Am I right?

---

### Post by hogwartsnigel on 2007-11-11
I'm afraid I can't help. But just wanted to say that this thread has got me up and running on the DVD front at least playing, back up 9-5 etc...thanks to all concerned your help is SO appreciated..now to find a good swf authoring tool like 3dfa..
Thanks

Nigel

---

### Post by amiga_os on 2007-11-11
Every gstreamer codec installed
Every xine codec installed
All this installed:
libdvdread3
libdvdcss2
sudo /usr/share/doc/libdvdread3/install-css.sh (tried playing video before and after update by medibuntu - i.e. tried using at least two different versions of the libdvdcss2 package, one from this command, and one from medibuntu)
libdvdnav4
libxine1-ffmpeg
totem-xine
vlc
mplayer
gxine
xine-ui
using medibuntu

Still cannot play dvds.  Having used Ubuntu since Dapper - DVD playback has gone seriously downhill and seriously backwards in Gutsy.  I have done every single trick in teh book that I have learnt after over a year of using Ubuntu, and I can't get my wife's laptop to play our dvds.  This is atrocious.

How many open source video projects does there have to be?  How many open source libraries are trying to provide the same functionality?  And yet - when will I simply be able to buy a dvd, stick it in my laptop, and click play on my computer?

The only thing I *can* do is rip dvds.  So - here's the irony - the css encryption system has forced me to copy my own dvds that I bought legally, and have no intention of pirating.  I've never needed to use a dvd-ripper before, and now I must.

---

### Post by Brian Dempster on 2007-11-12
I had the same problem, None of my DVDs would play.
I installed gxine and now most players are working.
See
[http://www.xinehq.de/index.php/download](http://www.xinehq.de/index.php/download)
I used the terminal.
# apt-get install xine-ui
# aptitude install gxine

I like gxine and Kaffeine.
I hope this helps others.:KS

---

### Post by zorkerz on 2007-11-17
No DVD playback: Could it have anything to do with 64 vs 32 bit systems? It seems some people are having success doing the same things that do not work for others.

---

### Post by Tom Mann on 2007-11-17
Guys I think I may have a lead:

I'm running my audio through Freebob (through Jack)

JackCtl shows the first two outputs from totem to connect to freebob output 1&2 when playing avi.

DVD seems to ignore the settings and route all 6 outputs from totem to freebob. - however the audio only comes through output 2&3. I only have output on the right channel. routing output 3 from totem to output 1 on freebob enables the other channel.

Hope this helps.

Tom

---

### Post by NTolerance on 2007-11-19
> **thousandrobots said:**
> i was briefly having the same problem as everyone else here, but in the end, i think all you really need to do is:

- install the ubuntu-restricted-extras [as described on the wiki]("https://help.ubuntu.com/community/RestrictedFormats")
- sudo apt-get install totem-xine
- sudo apt-get install vlc
- reinstall libdvdcss2 with "sudo apt-get libdvdcss2"
- sudo apt-get install libdvdread3 libxine1-ffmpeg 
- sudo /usr/share/doc/libdvdread3/install-css.sh

i did not have to reboot.

i did this on a brand new install of gutsy, and it worked -- i put in a dvd and it started playing in totem. the menus didn't work, but they do in VLC. this is with crap integrated graphics chipset and an external dvd burner. also, vlc users, don't forget to make sure you are typing the right device name into your "open disc" dialog box. /dev/scd1 or /media/cdrom0 or whatever.

This got totem-xine working for me.  Thanks.  As a point of interest I did not need to run the install-css.sh script.

Edit:  Install libdvdnav4 to get working menus.  :cool:

---

### Post by mdpalow on 2007-11-19
For those of you still having problems with this - see the link in my signature at the end of my posting.

My script will install the proper DVD and Codecs files and in a couple minutes your DVD player will most likely be playing movies and you won't have to reboot as I never had to and I tested my code on three computers running Ubuntu 7.10 (32 and 64 bit versions). I even wrote the script to work with Ubuntu 7.04 just in case you're running that instead.

There has already been feed back from users saying it's worked when nothing else they did seemed to work.

Give it a shot and I think you'll be playing your DVD movies shortly after if there's nothing wrong with your hardware, which in MOST cases I think is unlikely ....

Good luck...

---

### Post by neotasic1 on 2007-11-21
> **mdpalow said:**
> For those of you still having problems with this - see the link in my signature at the end of my posting.

My script will install the proper DVD and Codecs files and in a couple minutes your DVD player will most likely be playing movies and you won't have to reboot as I never had to and I tested my code on three computers running Ubuntu 7.10 (32 and 64 bit versions). I even wrote the script to work with Ubuntu 7.04 just in case you're running that instead.

There has already been feed back from users saying it's worked when nothing else they did seemed to work.

Give it a shot and I think you'll be playing your DVD movies shortly after if there's nothing wrong with your hardware, which in MOST cases I think is unlikely ....

Good luck...

Thanks dude, been chasing my tail trying to get gxine to play DVD's the last 2 days since fresh install of Gutsy.  (Had it working fine in Feisty using Gxine)  Followed all the tutorials and advice etc - no joy.  (Can't find input plugin error)

Used your script - changed my settings in System>Preferences>Removable Drives and Media Multimedia tab so the command reads /usr/bin/totem - hey presto. Load a DVD and totem opens.  Select the disk from the menu and away it goes.  Mine is a 64bit Gutsy install for info. If others have the same experience I would recommend you get this post stickied.
BTW gxine still doesn't work, but I am more than happy to use totem instead.  Thanks again.

---

### Post by mdpalow on 2007-11-21
Glad to hear it !

Would love to have it 'Stickied,' so others wouldn't spend so much time trying to get a DVD to play on their computer. Maybe you could suggest it. :)

Sure it's nice to know how to do it yourself, but for some - just having a DVD work is good enough without having to know how or why.

bfn...

---

### Post by jromer on 2007-11-21
this solution solved all my problem. (was mentioned by a previous poster in this thread...)

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

i.e.
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine
sudo /usr/share/doc/libdvdread3/install-css.sh

this apparently installs totem-xine and uninstalls totem-gstreamer (the default movie player)...and does some other things...I don't pretend to know 

I also just noticed that all this is well documented in the help menu under "Playing DVD's" 

I still don't understand why totem-gstreamer is the default player if it doesn't consistently work playing DVD's (known bug issues as mentioned in previous posts), shouldn't totem-xine be the default player? (But obviously there must be a reason.)

The confusing thing for me was that during my first attempt at playing a DVD on Gutsy, I believe I got a popup box asking me to install codecs (which I chose to do) and some DVD functionality was working. (In fact, I thought everything was ok.) But then some DVD's wouldn't launch the "movie player", and I couldn't get totem-gstreamer to play dvd's from HD, and I couldn't get it to "Open New DVD", and the time-slider wouldn't work properly either. All these issues were solved by changing from totem-gstreamer to totem-xine. (as instructed above.)

---

### Post by mdpalow on 2007-11-21
By law, the OS cannot include the Codecs files to play an encrypted DVD 'out of the box.' If you remember, when you installed Windows - you couldn't play a DVD either unless you had loaded Nero or some other proprietary s/w package that made it possible to view DVDs. 

I think a lot of people don't put 1+1 together with Windows 'cause most people right away install Nero or have something pre-installed for them that allows them to watch a DVD. That's a general comment btw and not directed at you jromer. :)

EDIT: One last thing. I think you must have installed some other files because your installs mentioned above appear to be missing some files that would also be needed.

---

### Post by Mr.Beast on 2007-11-22
Just wanted to say a big thanks, 
I was having this problem as well and following these instructions allowed totem to play no problems.

cheers guys, your'e the best.

---

### Post by bw44 on 2008-01-06
> **mdpalow said:**
> Glad to hear it !

Would love to have it 'Stickied,' so others wouldn't spend so much time trying to get a DVD to play on their computer. Maybe you could suggest it. :)

Sure it's nice to know how to do it yourself, but for some - just having a DVD work is good enough without having to know how or why.

bfn...
The first time I got DVDs to work on my desktop without benefit of your procedure. It was a great learning experience and I'm sure some users will always want to to "do it themselves."  But to get DVDs to play on my newly acquired laptop, I used QuickStart and it worked flawlessly (on a computer which had given me lots of other headaches in the wireless networking and sound departments).  The only thing to mention is that downloading the codecs themselves can take a long, long time (at least in my case it did).

The reason your post may not be "sticked" is that it doesn't spell out (descriptively) what it's doing, so if you ever stop "supporting" QuickStart, users will be thrown back on their own devices and will not have learned anything they can carry with them.  (Of course they could always study the script!)

Many thanks!

---

### Post by stefcep on 2008-01-11
you need w64codecs and non-free-codecs installed from synaptic

---

### Post by TangoRom on 2008-01-12
Toad,

Spent about 2-3  hrs to get this done. jesus, I'm exhausted :) Finally, it's working beautifull. I read almost all posts regarding this issue. The tricky part was getting that lib file from google  to work by re-installing it. I'm using VLC and watched DVD (queensryche - mindcrime at the moore :P) without any problem.

thx

LINUX ROCKS !!!

---

### Post by photismos on 2008-02-03
[http://ubuntuforums.org/showthread.php?p=4264688#post4264688](http://ubuntuforums.org/showthread.php?p=4264688#post4264688)

I'm just a newb but I managed to get Gutsy to play my DVDs finally...

"in a nutshell" I basically switched over to Xine taking Alexander's advice (see the post I cite in this reply above) and then installed this libdvdcss...voila!  Never been happier for today anyway...  =D   

[http://downloads.videolan.org/pub/libdvdcss/1.2.9/deb/](http://downloads.videolan.org/pub/libdvdcss/1.2.9/deb/)

hope this might be useful to somebody...

---

### Post by BMWolfgang on 2008-02-15
hello,
I would like to pass on what has worked for me, I use Gutsy after an upgrade, installed all the "given" files that come with medibuntu, including the libdvdcss2 . No player would play any DVD.
Then, browsing through this thread, I took the recommendation of post# 36 from DeadToad (thank you, how do I do this officially ?)  and downloaded and try to install, got a message, a newer version is installed (same number !!).
So I uninstalled my "new" version and installed the downloaded one, same name    libdvdcss2_1.2.9-1_i386.deb, from Jan 2007, and voila, all players, Kaffeine, Xine, Totem play my DVD.
Obviously, there exist different versions with the same name (or is this a compilation issue) and it seems that medibuntu supplies the wrong version for gutsy.
This is my conclusion and please correct me if I am wrong, always learning.
Then I would not know of how to tell "medibuntu" about this if they might need to be told.

My Kubuntu is fun again
No more microsoft, I had stopped smoking, life is good.

Wolfgang

---

### Post by marck119 on 2008-03-20
hey i made my dvd work. just download all the libdvd.dev  repo's on synaptic, then on add/ remove install the ubuntu and kubuntu restricted extras...
that worked for me

---

### Post by mattalexx on 2008-03-21
> **carlinuxlearner said:**
> Same problem, I don't know how to get Totem to work, I just installed Kaffeine, and it works.

C@RL

Wow, I can't believe this worked! Thank you for the suggestion, carlinux!

EDIT: Wait, I just got through the previews, but the movie wouldn't play. Here's the error:

"
The source can't be read.

Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (Error opening vtsN=3, domain=2.)
"

---

### Post by asilaydyingdl on 2008-03-21
Hey all, I don't  know if you have solved the trouble yet because I am waaay too tired to read everything, but here is what I did to solve the problem of DVDs and CDs in Linux, step by step:

[http://ubuntuforums.org/showthread.php?p=4556700](http://ubuntuforums.org/showthread.php?p=4556700)

Goodnight!

---

### Post by asilaydyingdl on 2008-03-21
P.S.  Using my steps, you will have an all-in-one media player for Linux as a result.

---

### Post by pfeels on 2008-03-23
> **asilaydyingdl said:**
> Hey all, I don't  know if you have solved the trouble yet because I am waaay too tired to read everything, but here is what I did to solve the problem of DVDs and CDs in Linux, step by step:

[http://ubuntuforums.org/showthread.php?p=4556700](http://ubuntuforums.org/showthread.php?p=4556700)

Goodnight!


Takes forever to research this stuff and turns out to be an easy fix ... Put this stuff below in your Terminal, just the italicized stuff,\ along with the links


      Ubuntu 7.10 "Gutsy Gibbon":

      *sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list*


Then, add the GPG Key:

*wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update*


With the entire Medibuntu repository

If you have added the entire Medibuntu repository, you just need to install the package using APT:

*sudo apt-get install libdvdcss2*

---

### Post by Applegeek on 2008-03-25
YAHOO!!!!

I finally got mine going.  It had nothing to do with Totem, Xine, libdvdcss2 or any of that rot...

[http://www.getautomatix.com/forum/index.php?showtopic=1767&mode=threaded&pid=5506](http://www.getautomatix.com/forum/index.php?showtopic=1767&mode=threaded&pid=5506)

This was on my new HP dv2740se notebook - and you have to apt-get install regionset, then run regionset to set the region on the DVD player.  If you're in the US/CAN use region 1, otherwise google DVD Region Codes for your area.

If the region isn't set, you'll crystal-clear messages from Totem like "Are you trying to run without libdvdcss".  And GXine will tell you it has a "NAV packet error".  And VLC just closes.  And MPLayer just hangs the machine completely.  

Apparently these apps need to be updated to detect a DVD with a region code that hasn't been set yet...in any case, I hope this helps someone!

---

### Post by timetoballj on 2008-03-25
i am new to all this and need some step by step help with the same problem and when i try to find it in the terminal it said error cant find i am using a acer laptop aspire 5610z

---

### Post by timetoballj on 2008-03-25
every time i get errors when it comes to the libdvdcss2

---

### Post by Applegeek on 2008-03-26
Dang..I thought I had this fixed.

Now my Gutsy-AMD64 HP laptop will play some DVD's.  But if I plug in Disney's "Spirited Away" for example, what happens in GXine is I get a "Corrupted/Encrypted Datastream Error".  Totem-Xine will just go black, and VLC will attempt to play the DVD in fits and jerks about 2 seconds at a time.

But other commercial DVD's will play OK and menus work.

It looks like all the codecs are installed...libdvdcss2 is there, libdvdread3 is there, etc.

I ran the Quickstart script and Automatix scripts to see if that would do anything different, but no effect.

What am I missing here???   This is my Daughter's Laptop and her birthday is in 2 days, and I'm trying to get all of this setup for her...

---

### Post by Applegeek on 2008-03-28
Looks like several Disney DVD's don't play...Is there some magical way to get these to play?

---

