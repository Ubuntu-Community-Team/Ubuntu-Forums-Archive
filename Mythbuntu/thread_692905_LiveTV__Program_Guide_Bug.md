---
title: "LiveTV / Program Guide Bug"
date: 2008-02-10
forum: Mythbuntu
---

### Post by uncle hammy on 2008-02-10
I have been dealing with the bug where trying to launch the program guide crashes live tv.  Sometimes, it works fine (the guide), sometimes it freezes the video entirely, and sometimes the current stream keeps playing, but you are completely locked in it (no keystrokes respond).

I am using the most current weekly builds (0.20.2+fixes 15775), NVidia 7600GS, AMD64 3200+, 1.5Gigs Ram.

I have tried all the suggested fixes, such as disabling thread priority, etc and none have any effect.

Anyways, I was noticing that the guide always works just fine while viewing a recorded program.  The big difference I have noticed is a) the show is paused before the guide is entered b) There is no preview window of the show in the guide from recorded tv.

I am a linux newbie, period, so I don't have the ability to do anything developer wise.  However, could these bits of info, offer some sort clue to the solution of the guide in live tv bug?  Perhaps pausing the stream and taking out the preview window before trying to render the guide?

MythTV s working fantastic for me, and my hat goes off to everyone that ever had anything to do with this project!  This one little annoyance is livable (I just disabled the guide keybinding for livetv), but fixing it would sure be nice.

---

### Post by volkswagner on 2008-02-11
This has been confirmed video driver related.  Are you using restricted drivers?  After enabling mine I get no crash but the current station does not properly display.

---

### Post by uncle hammy on 2008-02-11
I am using the NVidia restircted drivers.  They were selected and installed as part of the mythbuntu installation...NVidia_new.  

I have also used sudo apt-get and/or the updater from Myth Control Center to install all updates....would NVidia drivers be included in that?

---

### Post by volkswagner on 2008-02-11
You may want to search your specific video card to see what other users have installed.  Be sure to back up your xorg.conf file prior to making any changes.  This will allow you to early revert back.  You may want to give Envy a try.  It can make things easy.

---

### Post by uncle hammy on 2008-02-11
Well, I don't know what part changed, but...

I initially installed Mythbuntu using the "Gudied install" which made one big ext3 partition.  I then started reading about using xfs for the recordings drive.  Since it's such a new box, and we had almost nothing of importance on it yet, I decided to start over while I still easily could.  This time I manually made /lib/var partition xfs with a clean install.  I applied all the updates, and now I have had no guide issues yet.  I spent about 30 minutes in live tv just hitting guide, exiting and hitting again....over and over.

Could be the clean install, could be an update, could be the xfs file system, could be just not enough time to crash yet :)...I dunno, but so far no crashes.

---

### Post by uncle hammy on 2008-02-11
I take that back, it just crashed :(.  Seems to be more prevailent on certains channels.

Envy frightens me.  I tried it when I first set out on this project, and it just stalled about half way through the installation, and royally screwed things up.

---

### Post by volkswagner on 2008-02-11
I had the same situation.  I think my problems began when I changed the setting in the guide setup to allow browse mode, or allow select to change the channel.

---

### Post by uncle hammy on 2008-02-11
OK, I checked the nvidia drivers that were installed and it was something like version 100.  I bit the bullet and installed envy and let it do it's thing, and I know have version 169.  Immediately, I noticed that with the new drivers, it recognized the native resolution of my tv as 1080i, as opposed to the 720p the old drivers did!

Anyways, I need to do a bit of tweaking to get my GUI to match the new 1920x1080 resolution, but checking with guide on the channels that it seemed to crash all the time, so far so good.

I'll keep you posted.

---

### Post by uncle hammy on 2008-02-12
Well, this is great.  Last night, everything installed fine via Envy.  I bumped my resolution down to 720p, hit apply, and everything still fine.  This morning, the screen is all scrambled, and I had to restart.

After restarting, I was set back to 1080i, and the restricted drivers manager indicates nvidia drivers are not enabled.  I enabled them, and now everytime I boot up, I get the "Low graphics mode" warning, and basically everything sucks.  I tried restoring my original backed up xorg.conf file, with no change.

Now what?

EDIT...

I uninstalled the driver with envy, but everything was still messed up, so I reinstalled the driver with Envy.  Everything seemed fine, I rebooted a few times, and it kept using the NVidia driver at 1080i.  So, I dropped my resolution to 720p again (I get a little better response on the tv at this) and this time clicked 'Apply' AND 'Save to configuration'.  Rebooted a couple times, and so far it's keeping the settings, though I have lost vnc wit hthe "No password configured for VNC auth" error.  We'll see how it goes.  Little nervous about it right now.

---

### Post by uncle hammy on 2008-02-22
Just an update to this..

I have played around a lot lately with XvMC (both on and off), and interlacing filters.  At first, I was using XvMC, because HD was "jerky" without it.  Though, I recently discovered that for some odd reason, if I start a recording or Live TV, and pause it for 2 seconds, then proceed, the jerkiness is gone entirely....go figure that one out.

Anyways, I am now using the lib mpeg and BOBx2, and as long as I pause and go at the start, everything is beautiful.  I have noticed far fewer issues by not using XvMC as well.  Which brings me to the guide bug...

By not using XvMC, the guide is FAR more reliable.  I have yet to actually crash.  However, sometimes the guide doesn't come up, the box still responds to keystrokes though.  Every once in a while though, I hit guide, it doesn't come up, so I hit Esc, and then instead of exiting out of LiveTV, it actuall logs me out all together.  I end up at the Ubuntu login screen, with a message saying that my user will log in in 30 seconds, at at the end of the 30 seconds, it logs in, Mythfrontend starts, and I'm back in business.  Strange huh?

---

