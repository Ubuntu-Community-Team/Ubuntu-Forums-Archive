---
title: "how to go back to my old setup? upgrade sucks"
date: 2008-03-13
forum: Mythbuntu
---

### Post by gsrcrxsi on 2008-03-13
so i upgraded to myth 0.21, not really knowing. my updater told me i had important updates, so i installed them. well after, i can no longer watch DVD's i cant rip DVD's i lost my themes (i had it on retro and its gone now) i just want everything back the way it was. easy way to downgrade/reverse the process?

---

### Post by murbanci on 2008-03-13
you can get your dvds working again my removing mythdvd and upgrading mythvideo.

---

### Post by gsrcrxsi on 2008-03-13
ok, mythvideo is somehow conflicting with mythdvd. what the hell? i install one, and it uninstalls the other, i install the other and it uninstalls the first. ugh this is frustrating. please tell me im not the only one having this problem.

---

### Post by gsrcrxsi on 2008-03-13
ok, removed mythdvd, i guess they integrated it into mythvideo? wish they would make the update take care of things like this so that it doesnt break stuff...

im almost satisfied with the upgrade. what happened to the retro theme? after the upgrade, im left with GANT, blootube, and blue, and all three suck. how do i get my other themes back?

---

### Post by JPurdy on 2008-03-14
I also ran into upgrade nightmares (still dealing with them w/ my DVB tuner card that I accidentally deleted and cannot re-install).

The themes is actually pretty easy.  Like you, I disliked the new standard themes (I personally like Mythbuntu-wide).  To get 'em back, it's pretty easy: just go into Synaptic and do a search for mythtv-theme.  There in the results, you'll see 'em all.  Just check the ones you want and then apply your selections.  After it's done, those themes will be available in your Settings > General > Appearance.

---

### Post by superm1 on 2008-03-14
All of the themes are in apt.  Look for them.

---

### Post by thatkidandy on 2008-03-14
Your best bet is to just apt-get install everything that isnt working, notably mythvideo. I'm guess that not all of the plugins updated from 0.20 to 0.21 so the communication is broken (this is what happened to me). Themes are also easy to install and set up again once you realize the change.

---

### Post by DJ-Power on 2008-03-14
Since the upgrade I have got some problems too. I have got everything working ok as far as themes and TV tuner, I can now play my videos again after installing Mythvideo so thats good. What has happened though is a bit strange, when I  play DVD's if they are in 5.1 then I get the dolby surround through my Technics amp fine. But if they are Dolby digital and only stereo I am not able to get any sound. This all was working fine before the upgrade and I am a little stumped as to why it isnt working now. Any ideas??

Regards
DJP :)

---

### Post by volkswagner on 2008-03-14
I had to change my spdif setting from max of "5.1" to "stereo" to get any sound.  There may be a bug for the 5.1 max setting?

---

### Post by Calash on 2008-03-14
mythbuntu-control-centre lets you add the themes you want back.

I had the MythDVD vs MythVideo issue as well, finally figured out just to leave it on Video and everything is working well.

---

### Post by DJ-Power on 2008-03-14
> **volkswagner said:**
> I had to change my spdif setting from max of "5.1" to "stereo" to get any sound.  There may be a bug for the 5.1 max setting?

Yes I had to set mine to stereo as well but I still get no sound if the DVD is in Dolby digital stereo I only get sound if it is in Dolby 5.1.

Regards
DJP :)

---

### Post by ctpaterson on 2008-03-22
Hey folks,

Are there some command-line instructions for restoring some of the lost behaviour that come from the latest upgrade?  My mythbox (gutsy) outputs to my analog TV, and is controlled pretty much via remote-control and ssh (ie, making changes in control centre is quite an ordeal).  I do my updates via "sudo apt-get upgrade".

If "Go to System->Preferences etc." is all there is; then I'll haul out the extra equipment, but I'm hoping not.

I've noticed the following changes in my setup:
- Retro (which I was using) is gone
- News Feeds no longer works (I press "OK" on the remote; nothing happens)
- Image Gallery no longer works
- Editing a recording doesn't work as expected (was tied to Retro)
- On-screen info on Live TV is gone (was tied to Retro)
- Channel changing on Live TV isn't quite working

This is just what I have noticed.

I don't want to seem ungrateful; love Myth and it's free after all...but after spending the day wrestling with an errant graphics card and freaky nic problems on my brother-in-law's computer -- this was a pretty lousy way to end the day.

Cheers.

---

### Post by ctpaterson on 2008-03-22
> **ctpaterson said:**
> Hey folks,

Are there some command-line instructions for restoring some of the lost behaviour that come from the latest upgrade?  My mythbox (gutsy) outputs to my analog TV, and is controlled pretty much via remote-control and ssh (ie, making changes in control centre is quite an ordeal).  I do my updates via "sudo apt-get upgrade".

If "Go to System->Preferences etc." is all there is; then I'll haul out the extra equipment, but I'm hoping not.

I've noticed the following changes in my setup:
- Retro (which I was using) is gone
- News Feeds no longer works (I press "OK" on the remote; nothing happens)
- Image Gallery no longer works
- Editing a recording doesn't work as expected (was tied to Retro)
- On-screen info on Live TV is gone (was tied to Retro)
- Channel changing on Live TV isn't quite working

This is just what I have noticed.

I don't want to seem ungrateful; love Myth and it's free after all...but after spending the day wrestling with an errant graphics card and freaky nic problems on my brother-in-law's computer -- this was a pretty lousy way to end the day.

Cheers.

Okay...I was annoyed enough that I went and got a keyboard and mouse and fumbled with the connectors in the back until I could use them.  I went into the control centre, launched synaptic, and did the search for "mythtv-theme retro".  Checked, installed, re-configured.  Okay.

...and if you think that was fun on an analog TV...man I need glasses...

The problems I listed above seem to have retreated along with the return of the retro theme; with two notable exceptions:

- Image Gallery is still not working
- News Feeds is still not working

Symptoms are that the machine does not respond when I select the menu item.  I should mention that my photos are on the same drive as my videos (which are there, and no problems); and that the "Weather" menu item is working; so I do not suspect my internet connection.

Any help would be greatly appreciated.

Oh, and while we're at it.  I screwed myself by blindly going to .21 via "sudo apt-get upgrade" didn't I?

Cheers.

---

### Post by laga on 2008-03-23
> **ctpaterson said:**
> 
...and if you think that was fun on an analog TV...man I need glasses...


No, you need VNC or ssh -X ;)

> 
- Image Gallery is still not working
- News Feeds is still not working


What does /var/log/mythtv/mythfrontend.log say?

---

### Post by ctpaterson on 2008-03-23
> **laga said:**
> No, you need VNC or ssh -X ;)



What does /var/log/mythtv/mythfrontend.log say?

I rebooted the machine to try and get a log without a lot of flotsam in it.  There definitely seem to be some issues with the gallery and newsfeed plugins...as well as some others that I didn't notice for lack of use.

> 
ICE default IO error handler doing an exit(), pid = 6180, errno = 0
Starting mythfrontend.real..
2008-03-23 08:51:28.212 Current Schema Version: 1160
2008-03-23 08:51:28.213 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-03-23 08:51:28.213 Enabled verbose msgs:  important general
2008-03-23 08:51:30.117 Total desktop dim: 1024x768, with 1 screen[s].
2008-03-23 08:51:30.118 Using screen 0, 1024x768 at 0,0
2008-03-23 08:51:30.118 Switching to square mode (Retro)
2008-03-23 08:51:30.140 Using the Qt painter
2008-03-23 08:51:30.503 Joystick disabled.
2008-03-23 08:51:31.066 Loading from: /usr/share/mythtv/themes/Retro/base.xml
2008-03-23 08:51:31.082 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-23 08:51:31.102 Key Down,Return is bound to multiple actions in context TV Playback.
2008-03-23 08:51:31.140 Registering Internal as a media playback plugin.
/usr/lib/mythtv/plugins/libmytharchive.so: undefined symbol: _ZN19ConfigurationDialog8addChildEP12Configurable
2008-03-23 08:51:31.202 MythPlugin::Init() dlerror:
2008-03-23 08:51:31.202 Unable to initialize plugin 'mytharchive'.
/usr/lib/mythtv/plugins/libmythcontrols.so: undefined symbol: _ZN14MythScreenType12ParseElementER11QDomElement
2008-03-23 08:51:31.219 MythPlugin::Init() dlerror:
2008-03-23 08:51:31.219 Unable to initialize plugin 'mythcontrols'.
2008-03-23 08:51:31.240 Registering MythDVD DVD Media Handler as a media handler ext()
2008-03-23 08:51:31.240 Registering MythDVD VCD Media Handler as a media handler ext()
/usr/lib/mythtv/plugins/libmythflix.so: undefined symbol: _ZN10MythDialog11deleteLaterEv
2008-03-23 08:51:31.243 MythPlugin::Init() dlerror:
2008-03-23 08:51:31.243 Unable to initialize plugin 'mythflix'.
/usr/lib/mythtv/plugins/libmythgallery.so: undefined symbol: _ZN10MythDialog11deleteLaterEv
2008-03-23 08:51:31.264 MythPlugin::Init() dlerror:
2008-03-23 08:51:31.264 Unable to initialize plugin 'mythgallery'.
/usr/lib/mythtv/plugins/libmythgame.so: undefined symbol: _ZN19ConfigurationDialog8addChildEP12Configurable
2008-03-23 08:51:31.275 MythPlugin::Init() dlerror:
2008-03-23 08:51:31.276 Unable to initialize plugin 'mythgame'.
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2008-03-23 08:51:31.704 Registering MythMusic Media Handler 1/2 as a media handler ext()
2008-03-23 08:51:31.704 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
/usr/lib/mythtv/plugins/libmythnews.so: undefined symbol: _ZN10MythDialog11deleteLaterEv
2008-03-23 08:51:31.718 MythPlugin::Init() dlerror:
2008-03-23 08:51:31.718 Unable to initialize plugin 'mythnews'.
/usr/lib/mythtv/plugins/libmythphone.so: undefined symbol: _ZN19ConfigurationDialog8addChildEP12Configurable
2008-03-23 08:51:31.731 MythPlugin::Init() dlerror:
2008-03-23 08:51:31.731 Unable to initialize plugin 'mythphone'.


I guess the first thing I'd do is "sudo apt-get remove" them, unless anyone has a better idea.

Happy Easter, all.

Cheers.

---

### Post by ctpaterson on 2008-03-23
> 
I guess the first thing I'd do is "sudo apt-get remove" them, unless anyone has a better idea.


I tried a remove/install on a plugin I didn't care about (game).  No luck.

---

### Post by Sirkent on 2008-04-09
This is to do with your client and server installations of MythTV being different versions. I just had this problem myself. For some reason one of my boxes had updated to a newer version. I went into Synaptic and then 'repositories' and unticked 'Recommended updates'. Then I uninstalled mythtv and re-installed and the problem was gone, as now I was using the same version on both machines.

---

### Post by laga on 2008-04-09
> **Sirkent said:**
> This is to do with your client and server installations of MythTV being different versions. I just had this problem myself. For some reason one of my boxes had updated to a newer version. I went into Synaptic and then 'repositories' and unticked 'Recommended updates'. Then I uninstalled mythtv and re-installed and the problem was gone, as now I was using the same version on both machines.

Unless I'm missing something, your database was likely upgraded to the schema used in 0.21. If that happened, you should restore the backup that was created when upgrading. I can't remember right now where that is placed, maybe someone else knows. Or 'locate mythconverg' might help.

---

### Post by ctpaterson on 2008-04-09
> **Sirkent said:**
> This is to do with your client and server installations of MythTV being different versions. I just had this problem myself. For some reason one of my boxes had updated to a newer version. I went into Synaptic and then 'repositories' and unticked 'Recommended updates'. Then I uninstalled mythtv and re-installed and the problem was gone, as now I was using the same version on both machines.

I've only got the one myth box, in my case - just one installation.  I'm still coasting along without a number of features (image gallery, news feeds), and without remedies I can employ, I had resigned myself (and the missus) to live with the problems until 8.04 was released at the end of this month.  Employing a reinstall to "fix" the problem, will leave me at the same decision.

---

