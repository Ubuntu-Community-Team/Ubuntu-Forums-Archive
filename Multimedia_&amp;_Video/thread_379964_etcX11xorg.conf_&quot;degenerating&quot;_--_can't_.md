---
title: "/etc/X11/xorg.conf &quot;degenerating&quot; -- can't seem to clean it up"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by Phrawm48 on 2007-03-09
The good news is that I still have 1280 x 1024 video resolution and a working computer.

The less good news is that the lovely nVidia driver installation I did a few weeks ago seems to have somehow changed, or at least partially disappeared from */etc/X11.xorg.conf* and I can't seem to fix it.

_**What I'm trying to do:**_

[LIST]
[*]Clean any contradictory or hurtful stuff out of what appears to be a "messy-ized" */etc/X11/xorg.conf*

[*]Get back the nice GUI nVidia Settings control I had up until recently.
[/LIST]

Per  [http://ubuntuforums.org/showthread.php?t=346595]("http://ubuntuforums.org/showthread.php?t=346595"), I got the correct driver for my nVidia GeForce FX 5500 installed and working beautifully.  Additionally, **Applications | System Tools | nVidia Settings**  provided me with a very full-featured control panel that clearly configured all aspects of the graphics adaptor.  Life was very good!

As of a few days ago, however, if I select nVidia Settings, I receive a nearly empty control panel with NO controls.  In response, I tried to use my old version of Envy, and then the latest version, to re-install my driver.  All that did was clobber X so that I can't boot into graphics mode.   In other words, it seems to further damage /etc/X11/xorg.conf, obliging me to boot into recover mode, then overwrite the updated file with my backup copy.

If I examine my working *xorg.conf* (attached to this thread as *xorg.conf.txt*), it seems to somehow have acquired multiple, slightly contradictory video-related definitions.  I have no idea where or how the extra stuff got into *xorg.conf*.

_**What I've done so far:**_

[LIST]
[*]Tried reinstalling my  nVidia driver per my original, successful installation (described in the cited thread, above)

[*]Loaded the current (as of 2007-03-08 ) 0.9.0 version of the Envy script and ran it to first uninstall then re-install the ostensibly correct driver.
[/LIST]

Alas, both the old and new version of the Envy script breaks X so that I have to boot into recovery mode and overwrite the updated */etc/X11/xorg.conf* with my backup copy.

Can anyone please help me sort this out?  As I said, my computer still works but my *xorg.conf* appears to have a degenerative disease.

Please feel free to ask for extra info, such as logs, etc.

Cheers & thanks,
Ric
SFO

---

### Post by desheikh on 2007-03-09
Hi,

You can revert back to a clean xorg.conf by running 

sudo dpkg-reconfigure xserver-xorg

and then start the installation from there on?
Hope that helps.
Ali

---

### Post by kerry_s on 2007-03-09
Rename, move or delete the messed up xorg.conf and->
in terminal run
sudo nvidia-xconfig
then restart X (ctrl+alt+backspace)

You will then have a fully nvidia compliant xorg-conf.

---

### Post by Phrawm48 on 2007-03-09
Thanks, but neither of those two ideas fixed my central problem.

Stated another way, it appears that I simply cannot change my xorg.conf without breaking X.

No matter which of the three techniques I use -- Envy (which I've now uninstalled), dpkg-reconfigure xerver-xorg, or nvidia-xconfig -- when I boot, the following happens:

[LIST=1]
[*]The computer displays the Kubuntu logo above an animated (left-to-right) progress bar and scrolls a list of startup tasks.

[*]When the computer reaches "Starting additional...[I can't read the rest], it immediately displays the Kubuntu logo above a blank, static progress bar and freezes.

[*]At this point, if I press CTRL+ALT+DELETE, the system goes into animated Kubuntu shutdown mode: The animated progress bar moves right-to-left as a list of shutdown tasks scroll below.
[/LIST]

The key point is that this behavior is identical no matter which of the three techniques I use to clean up my xorg.conf file.  Similarly, all I can do at this point is boot into recovery mode and overwrite the modified xorg.conf with my backup copy (attached to my original post).

By the way, I've tried to look at the log files for this but I can't figure out what, exactly to look for.  I've tried to view the boot log, but receive a **The file '/var/log/boot.log' does not exist.** message(??)

Long story short, I can't seem to get back to a clean, simplified xorg.conf so that I can then incrementally get the right drivers and stuff in place...

Does anyone please have any additional ideas where I can go from here?

Cheers & thanks,
Ric
SFO

---

### Post by xixx on 2007-03-09
Can you post here your xorg log file?

---

### Post by david_2001 on 2007-03-09
> **Phrawm48 said:**
> 
Long story short, I can't seem to get back to a clean, simplified xorg.conf so that I can then incrementally get the right drivers and stuff in place...

Does anyone please have any additional ideas where I can go from here?

Cheers & thanks,
Ric
SFO

I cleaned it up as best I can, deleting everything unnecessary to a basic set-up and leaving the keyboard and mouse settings, and the font paths as in the original.  It should work but no guarantees because I'm not able to test it here.  Note that it uses the nv driver, so nvidia-settings won't work.

---

### Post by Phrawm48 on 2007-03-09
Thank you david_2001!  The cleaned up xorg.conf worked.  It's also obviously much less cluttered than was my version.  I'm going to stick with this new version for the time being insofar as I have the desired screen resolution and all.

Thanks, too, to all for the help and information -- even the tools that didn't work this time are good for me to know about.

Cheers, thanks 'gain, & take care,
Ric
SFO

---

