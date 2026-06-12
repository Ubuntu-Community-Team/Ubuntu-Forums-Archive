---
title: "[SOLVED] Screen blanks while watching recordings, etc"
date: 2007-10-25
forum: Mythbuntu
---

### Post by bblboy54 on 2007-10-25
I've been using MythBuntu for a while and love it.  Since Ubuntu 7.10 officially released I decided to apt-get upgrade all of the machines in my mythbuntu network (1 backend, 2 frontends).  Since doing the upgrade both of my front end machines (each with identical hardware) are screen blaning after about 10 mins while watching TV or recordings.  This is, of course, frustrating as I have to sit by the keyboard and tap num lock every time this happens.  Buttons on the remote control don't seem to bring the screen back on and it does not power down the monitor.  I've also noticed that the mouse cursor will appear on the screen a few seconds before the screen blanks so I am assuming the upgrade enabled a screen saver in the GUI but since I havent installed the desktop enviornemtns (which I have no need for), I dont have any controls for adjusting these.

Has anyone else experienced this problem?  Any quick fix?

For reference, my front end machines are using Intel PIII Server boards with the 815 chipset.  Each have 512MB of RAM and use the on-board video.  This issue didnt happen until I did the most recent update.  Also for reference, I upgraded a little over a month ago and didnt have this issue as far as I saw so it's probably something that changed within the last month or so.

---

### Post by napsilan on 2007-10-25
try 
```

gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false

```

Might have to su to mythtv to do get it to stick for that user.  

Before I knew the command line, I did it by setting the mythtv user password to something I knew, ssh-ing as mythtv, running gnome-screensaver-preferences (with X forwarding), then re-locking the mythtv password.

If that doesn't work, perhaps adding this to xorg.conf would help
```

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

```

---

### Post by bblboy54 on 2007-10-25
It looks like adding that code to the end of /etc/X11/xorg.conf and restarting fixed the problem.  Using the gconf command that you gave me didn't seem to do anything.

This is probably something that needs looked at in the distro.  Has anyone else experienced this?  I'll open a report on launchpad and link back to this thread.

---

### Post by bblboy54 on 2007-10-25
> **bblboy54 said:**
> It looks like adding that code to the end of /etc/X11/xorg.conf and restarting fixed the problem.  Using the gconf command that you gave me didn't seem to do anything.

This is probably something that needs looked at in the distro.  Has anyone else experienced this?  I'll open a report on launchpad and link back to this thread.

Actually, strike that..... as soon as I posted that and went back to watching my program, it blanked again.  Any other ideas?

---

### Post by bblboy54 on 2007-10-25
[https://bugs.launchpad.net/mythbuntu/+bug/157158](https://bugs.launchpad.net/mythbuntu/+bug/157158)

I opened bug 157158 on launchpad

---

### Post by napsilan on 2007-10-25
did you run gconftool as the mythtv user, or as your user?

---

### Post by bblboy54 on 2007-10-25
> **napsilan said:**
> did you run gconftool as the mythtv user, or as your user?

I did "sudo su mythtv" before running it so that it would run as the mythtv user.

---

### Post by superm1 on 2007-10-25
Um.... things aren't done as the mythtv user in the final of mythbuntu.  They are done as your normal user.

---

### Post by bblboy54 on 2007-10-26
It appears that this only does happen when you apt-get upgrade one of the alpha releases of mythbuntu.  I found an easy solution to make this not happen:

```

chmod a-x /usr/bin/gnome-screensaver

```

This makes X unable to start the screen saver and, so far, I havent seen any indication that any components have an issue with this.

---

### Post by hades_6_6_6 on 2007-10-29
> **bblboy54 said:**
> This makes X unable to start the screen saver and, so far, I haven't seen any indication that any components have an issue with this.
I don't want to deactivate screen-saver for ever, just when I'm watching a movie. Does somebody have a better solution?

---

### Post by napsilan on 2007-10-29
If you are just concerned with the screensaver during movies, and not TV recordings, you can add &#8722;stop-xscreensaver to the mplayer command

---

### Post by superm1 on 2007-10-29
This option is by default included in the configuration file within /etc for mplayer in the final release.  It can be added otherwise to the config file in ~/.mplayer

---

### Post by bblboy54 on 2007-10-29
> **hades_6_6_6 said:**
> I don't want to deactivate screen-saver for ever, just when I'm watching a movie. Does somebody have a better solution?
 As indicated by the bug report, this is not a bug but is the result of upgrading from an alpha version.  I wouldn't look for any solutions to this issue since there is the possibility of other things on the system wanting to break later.

---

### Post by hades_6_6_6 on 2007-10-30
> **bblboy54 said:**
> As indicated by the bug report, this is not a bug but is the result of upgrading from an alpha version.
I've made a **fresh install** of Gusty release. I've never made any kind of upgrade/update. And still I have this issue.
I'll update your bug report

---

### Post by superm1 on 2007-10-30
Speak more to where this is happening to you?  During LiveTV/Recordings?  During menus? During an external video player?  Is it a slow fade, or a sudden black out?

---

### Post by hades_6_6_6 on 2007-10-30
> **superm1 said:**
> Speak more to where this is happening to you?  During LiveTV/Recordings?  During menus? During an external video player?  Is it a slow fade, or a sudden black out?
watching a movie with VLC. Sudden black out after ~10 minutes. Audio's still playing.
Screen comes back as soon as I touch the mouse.

---

### Post by superm1 on 2007-10-30
> **hades_6_6_6 said:**
> watching a movie with VLC. Sudden black out after ~10 minutes. Audio's still playing.
Screen comes back as soon as I touch the mouse.
We have no workarounds for VLC itself put in mythbuntu.  I had thought VLC has gnome screensaver support however.  Perhaps it doesn't?


Try another playback software maybe?

---

### Post by Test_Dummy on 2007-11-05
Apparently there is an issue with gnome-screensaver in Ubuntu 7.10 (not trapping keys or some such).

[http://www.linuxsecurity.com/content/view/130446/](http://www.linuxsecurity.com/content/view/130446/)

I was going to test the latest software updates (noticed them on my laptop this morning) and see how they affected the screensaver behavior.

I was running Fiesty and Myth 0.20.0 with the gnomescreensaver-patch and everything was working fine - with the exception of MythGame. Screensaver always kicks in when playing with joystick - doh!

I upgraded to Gibbon and Mythtv 0.20.2 (which has the screensaver-patch included) and lo and behold, the screensaver kicks in when watching Live TV, Videos, DVDs, etc.

I like the new Movie Times plugin (although alignment is off in widescreen) and weather is working once again.

---

### Post by Test_Dummy on 2007-11-06
Nope, no such luck. I upgraded to Gutsy on Friday (11/2) which already had the compiz security patch.

The gnome-screensaver-command --poke built into Myth apparently no longer inhibits the screensaver.

Any ideas?

---

### Post by Test_Dummy on 2007-11-06
Checked to be sure that gnome-screensaver-command --poke still works (sure enough it does). Myth must not be calling the deactivation routine any longer.

#include <iostream>
#include <cstdlib>

int main()
{
   while (true)
   {
      if (std::system(0))
      {
         std::cout << "Hokey-Pokey" << std::endl;
         std::system("gnome-screensaver-command --poke);
      }
      sleep (300);
   }

   return 0;
}

---

### Post by superm1 on 2007-11-06
There has been no such changes to the Myth packages in the archives.  Are you using weekly builds?  If so, perhaps try to revert back to the archive packages in case this broke in 0.20-fixes.

---

### Post by DaveDH on 2007-11-16
Why does the title of this say [SOLVED]?

Just want to add that I'm having the same problem here since updating to Gutsy.  I've diabled screensaver, and checked power settings (which are off).

Screen still goes blank (immediately, no fade) after the ~10 mins period.

The most irritating is while I'm watching movies in Totem Movie Player, but it happens whenever the computer is idle.

My only difference since upgrading to Gutsy is that I'm now running an ATI restricted video driver (as Gutsy told me it was available) - plus I installed X-desktop (or something - new to Linux!) to give me desktop Visual Effects.

Possibly a different issue, but still screen related - Function F4 won't switch to external output now to send the display to my projector.  Any suggestions?

---

### Post by titaniumlou on 2007-11-17
I'm having the same problems, although I don't have Myth installed on my machine at all.

I upgraded from Feisty a week or so ago and have these same problems where the screen blanks out after watching a video for about 10 minutes.

I've tried going into the screensaver preferences since I noticed the default time for blanking the screen was set to 10 minutes there, but changing that hasn't had any effect.

Anyway, I'd appreciate any help folks might be able to offer.

Thanks!

---

### Post by superm1 on 2007-11-17
> **titaniumlou said:**
> I'm having the same problems, although I don't have Myth installed on my machine at all.

I upgraded from Feisty a week or so ago and have these same problems where the screen blanks out after watching a video for about 10 minutes.

I've tried going into the screensaver preferences since I noticed the default time for blanking the screen was set to 10 minutes there, but changing that hasn't had any effect.

Anyway, I'd appreciate any help folks might be able to offer.

Thanks!
Folks you have to specify what apps are doing this to you.  This thread is marked solved because the poster's issue has been resolved.

---

### Post by DaveDH on 2007-11-18
> **superm1 said:**
> Folks you have to specify what apps are doing this to you.  This thread is marked solved because the poster's issue has been resolved.

Hi superm1,  this is happening in *all* apps, but of course is most annoying when watching a movie (for me that would be in Totem Movie Player).

I have tried what is suggested earlier without success, and I have tried the suggestions from here: [http://www.shallowsky.com/linux/x-screen-blanking.html](http://www.shallowsky.com/linux/x-screen-blanking.html) but they didn't help either.

I think [SOLVED] should be removed, as the issue from the original poster was never resolved, as (s)he says in #4 - [http://ubuntuforums.org/showpost.php?p=3630059&postcount=4](http://ubuntuforums.org/showpost.php?p=3630059&postcount=4)

Any other suggestions are most welcome.  I have only seen problems in moving to Gutsy so far, and I am thinking imminently of switching back to Feisty where I had no problems at all.  

Dave

---

### Post by bwallum on 2007-11-18
This is an old bug and diddly squat is being done about it I'm afraid.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/125947](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/125947)

I have the same problem, perhaps if you added your voice it may help.

Regards
Bob

---

### Post by DaveDH on 2007-11-19
> **bwallum said:**
> This is an old bug and diddly squat is being done about it I'm afraid.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/125947](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/125947)

I have the same problem, perhaps if you added your voice it may help.

Regards
Bob

Thanks Bob... been there and done that now.

---

### Post by hades_6_6_6 on 2007-11-19
> **bwallum said:**
> This is an old bug and diddly squat is being done about it I'm afraid.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/125947](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/125947)

I have the same problem, perhaps if you added your voice it may help.

Regards
Bob
done that too

---

### Post by superm1 on 2007-11-19
Um xserver-xgl?  You guys have that turned on?

Uninstall it.  What do you need it for a myth box?

---

### Post by jackliddlephysics on 2007-11-19
I'm suffer from the same/similar problem.  Sometimes when the screensaver kicks in on the menus, pressing buttons on the remote or keyboard doesn't bring it back to life and I have to restart the machine.

---

### Post by kjfw on 2007-11-20
I too was having a similar problem: the screensaver would come on after 10 minutes in mythtv.  Pressing buttons on the remote was no help, had to press a key on the keyboard or move the mouse.

My machine is running a fresh install of regular Gutsy with some of the mythbuntu packages added afterwards.  Mythtv is running under its own mythtv user.

I tried adding ~mythtv/.xscreensaver as follows:
```

*mode:  off

```
but that didn't help.

And I tried the gconftool2 command suggested in the 2nd post of this thread, but that didn't help either.  I tried uninstalling the screensaver, but aptitude complained about dependencies (like mythtv-frontend) so I rejected that idea as well.

Finally, I tried this variation of the gconftool-2 trick:
```

gconftool-2 --type boolean -s /apps/gnome-screensaver/idle_activation_enabled false

```
and that worked.  No more screensaver while running mythtv!

---

### Post by nzgreen on 2007-12-08
Thanks kjfw, your gconf trick worked for me.

---

### Post by vulture99 on 2007-12-15
> **kjfw said:**
> Finally, I tried this variation of the gconftool-2 trick:
```

gconftool-2 --type boolean -s /apps/gnome-screensaver/idle_activation_enabled false

```
and that worked.  No more screensaver while running mythtv!Same problem here on a new Mythbuntu installation.  Your command worked for me (thanks) but did not survive a reboot.  I placed it in /etc/rc.local and that seemed to do the trick.

BTW, is rc.local the best location for local boot scripts on Ubuntu?  I used to shove commands in rc.local on Fedora, but I am rather new to Ubuntu.  Thanks.

---

### Post by antoniuk on 2007-12-30
I have found that after watching live tv for an hour this happens and nothing brings it out of it. The screen actually goes into a sort of sleep mode and I am forced to reboot.

Can't we just remove the screensaver? Why is there a screen saver on a dvr anyway?

Or even better can you please remove gnome-screensaver as a dependency of myth-desktop?


Just wanted to add that the above does not work and I can no loger watch live tv with out it going into a sleep mode. All I did was run an update to my system and now I can't use it

---

### Post by jw5801 on 2007-12-30
I wouldn't think it is a dependancy. It's not a dependancy of ubuntu-desktop.```
sudo apt-get remove gnome-screensaver
```will kill it.

However, going into a "sleep mode" after an hour isn't a behaviour of a screensaver. That sounds like it's hibernating or suspending, check your power management settings.

---

### Post by carnageblood on 2007-12-31
You  should have tried:```
xset s noblank
```
and you don't have to remove screensaver.
More info here [here[]("http://www.shallowsky.com/linux/x-screen-blanking.html")

---

### Post by jvitkay on 2008-01-04
I had a very similar problem.  In my case, I found that it was due to starting mythfrontend from the .gnomerc file.  

When you start it that way, it seems that something is not setup right for gnome-screensaver-command to communicate with the gnome-screensaver - it thinks the screensaver is not running.  The failure is a dbus related failure, where it fails to find the owner on a bus - I don't claim to understand it, I was just capturing the output of the gnome-screensaver-command --poke command that mythfrontend executes.  It will work fine if you run it from a shell, it only fails from the process context that mythfrontend was started in, or any shell process forked from that.

To fix, I start mythfrontend by using the system/preferences/session menu, and a mythfrontend as a startup app.

Now screensaver kicks in when on myth menus (good for my plasma), but not during playback, and when it does start, my lirc based remote brings it out.

---

### Post by lingenfr on 2008-01-06
As others have said, this is not [SOLVED]. If it were, it would be most helpful for the original poster to modify the first post to include the solution. I was discussing the same problem in a separate thread here

[http://ubuntuforums.org/showthread.php?t=636180](http://ubuntuforums.org/showthread.php?t=636180)

For the individual who asked why you want a screensaver, the answer is because I want my tv to go into power save after about 5 minutes of inactivity in any of the mythfrontend menus. That way I don't have to have two remotes or a multifunction remote. It is simple for the family to use. Just return to the main menu and the tv will go to sleep on it's own. I still don't have mine working correctly and consistently. It is either use two remotes or wait for screen burn.

FWIW, I installed originally with the Feisty alternate CD and the mythbackend/mythfrontend instructions from the wiki. When I did a dist-upgrade to Gutsy, I got mythbuntu'd and was left with this problem, a non-functional remote and lots of other fun stuff. Before a developer chimes in, I'm sure it was my fault. I probably could have prevented the remote problems by retaining my configs. However, this problem is real and it was not caused by using alpha/beta/cvs/svn versions of anything.

---

### Post by nzgreen on 2008-01-06
> **lingenfr said:**
> <snip>For the individual who asked why you want a screensaver, the answer is because I want my tv to go into power save after about 5 minutes of inactivity in any of the mythfrontend menus. That way I don't have to have two remotes or a multifunction remote. It is simple for the family to use. Just return to the main menu and the tv will go to sleep on it's own. I still don't have mine working correctly and consistently. It is either use two remotes or wait for screen burn.


You don't need a screenscaver for this.  MythTV has had DPMS support for quite some time.  I find it doesn't work at the Main Menu but if I leave it in the top level of the "Media Library" menu it will kick in after about 5 minutes and my monitor will enter standby. YMMV.

---

### Post by pja on 2008-05-19
See [http://ubuntuforums.org/showthread.php?p=4993141#post4993141]("http://ubuntuforums.org/showthread.php?p=4993141#post4993141") for my solution based on this and other posts.

Regards,
Peter

---

### Post by oobe-feisty on 2008-09-04
i wrote a small howto hope this helps

[http://ubuntuforums.org/showthread.php?t=905271](http://ubuntuforums.org/showthread.php?t=905271)

---

