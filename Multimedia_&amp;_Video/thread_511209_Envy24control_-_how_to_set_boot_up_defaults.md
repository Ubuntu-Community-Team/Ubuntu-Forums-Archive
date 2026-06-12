---
title: "Envy24control - how to set boot up defaults?"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by SasquatchNC on 2007-07-27
System is as follows:
Kubuntu Feisty (almost completely default)
nForce 2 system
M-Audio Audiophile 24/96

I don't use the onboard sound, so I have a file in /etc/modprobe.d/ to set the M2496 as card 0 for ALSA. Sound works great. I'm not doing anything fancy with the card, I just want the two RCA outputs on the card to default to being mapped to L and R. I know how to do this manually, so I'm not asking for a tutorial.

My problem is that PCM Out 2 (which is the R RCA output of the card) is always muted by default on bootup. I have to manually go into Envy24control to unmute it every time. How do I change the default??? Thanks!

---

### Post by SasquatchNC on 2007-07-29
Bump - anyone have ideas?

---

### Post by twice on 2007-08-01
I don't know that this is the best way, but you can try using envy24control's profiles.  Set it up the way you like it, and save your settings under '1' in the profiles tab.  After that, running 'envy24control 1' will initialize everything to those settings.  I guess you could put that in your startup programs if you want to be sure it happens right away, but I think you'll still be hearing the startup sound out of only one speaker..

By default, it'll save your profiles to ~/envy24control/profiles.conf .  If you'd rather put it somewhere else, you can either set a DEFAULT_PROFILERC environment variable to the filename you want, or set it directly when you run envy24control by using the -f option.

I hope that helps..

---

### Post by twice on 2007-08-02
Okay, there is a better way..  The alsactl command should be getting executed on shutdown to store the current settings in /var/lib/alsa/asound.state, and again on startup to load those settings.  You should have K50alsa-utils in /etc/rc0.d and /etc/rc6.d (for shutdown and restart), and S50alsa-utils in /etc/rc2.d (for startup).

If you do have a /var/lib/alsa/asound.state, it's human-readable so if you want you can check it to see if it's showing the settings you start up with.  For my delta44, a muted right channel would be shown by control.2, named "Multi Playback Switch", having value.0 and value.1 both set to false (if you meant the volume was all the way down, that would be the second "Multi Playback Volume" control set to 0).  If these are the settings you're getting at startup, you can overwrite them with the ones you want by typing 'sudo alsactl store'.  Then, as long as you have the S50 script in /etc/rc2.d, it should load those settings on startup.

---

### Post by SasquatchNC on 2007-08-06
Twice, thanks for the leads. I do have:
/etc/rc0.d/K50alsa-utils
/etc/rc6.d/K50alsa-utils

I do not have:
/etc/rc2.d/S50alsa-utils

That led me to find these two topics:
[http://ubuntuforums.org/showthread.php?t=211142&highlight=S50alsa-utils](http://ubuntuforums.org/showthread.php?t=211142&highlight=S50alsa-utils)
[http://ubuntuforums.org/showthread.php?t=218954&highlight=S50alsa-utils](http://ubuntuforums.org/showthread.php?t=218954&highlight=S50alsa-utils)
which seem to indicate that /etc/rc2.d/S50alsa-utils is outdated as of last year.

You were on the money with /var/lib/alsa/asound.state. It was wrong. I set the correct settings with Envy24control, ran 'sudo alsactl store' and asound.state was updated to be correct.

Rebooted and the right channel is still muted, but /var/lib/alsa/asound.state is still correct. Seems like the problem is that /var/lib/alsa/asound.state isn't being loaded on bootup.

I tried 'sudo ln -s ../init.d/alsa-utils /etc/rcS.d/S50alsa-utils' (from one of the threads I linked above). Rebooted and it didn't work.

The problem seems to be ALSA not loading /var/lib/alsa/asound.state on bootup with the alsa-tools package loaded. Anyone got any help???

---

### Post by twice on 2007-08-08
> **SasquatchNC said:**
> 
That led me to find these two topics:
[http://ubuntuforums.org/showthread.php?t=211142&highlight=S50alsa-utils](http://ubuntuforums.org/showthread.php?t=211142&highlight=S50alsa-utils)
[http://ubuntuforums.org/showthread.php?t=218954&highlight=S50alsa-utils](http://ubuntuforums.org/showthread.php?t=218954&highlight=S50alsa-utils)
which seem to indicate that /etc/rc2.d/S50alsa-utils is outdated as of last year.

Hey, you're right!  Somehow my setup has both S50alsa-utils and the udev rule in /etc/udev/rules.d/85-alsa.rules, but it looks like the S50 symlink was added the day after I installed my distribution.  I doubt there's any harm in setting my levels twice, but I wonder what I did that put it there.

Using udev rules makes more sense than the old way, though, because it means it's set as soon as the card is detected.

> 
I tried 'sudo ln -s ../init.d/alsa-utils /etc/rcS.d/S50alsa-utils' (from one of the threads I linked above). Rebooted and it didn't work.

Well, that rules out a few possibilities, at least..  The symlink you just made and the udev rule you probably already have both run /etc/init.d/alsa-utils.  Can you verify that this script exists?

Assuming it does, try messing up your volume settings in envy24control and running 'sudo /etc/init.d/alsa-utils start'.  Does it set the levels back to what asound.state says?  Does it say anything?

---

### Post by SasquatchNC on 2007-08-08
/etc/init.d/alsa-utils exists. Messed with my volumes then ran 'sudo /etc/init.d/alsa-utils start'. Output was:
```
 * Setting up ALSA...                                                    [ OK ]
```
Sure enough, the volumes I saved earlier (the ones I want to load by default) were loaded from /var/lib/alsa/asound.state.

Here's my /etc/udev/rules.d/85-alsa.rules:
```
KERNEL=="controlC[0-9]*", ACTION=="add", \
	RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/alsa/bogus --startas /etc/init.d/alsa-utils -- start %n"
```

This should be all default, I haven't changed much at all from the default Kubuntu Feisty. My gut feeling is that alsa-tools dorked something up, but I have no idea what.

---

### Post by twice on 2007-08-10
You can try ctrl-alt-f8 to check your boot messages (ctrl-alt-f7 will bring you back to your kde session), and see if the init.d/alsa-utils output is visible.  Does it still say OK?

It may be scrolled off of the screen..  The scripts in /etc/rcS.d/ are run before any of the runlevel scripts.  If the alsa-utils script's output is not visible, you can 'sudo mv /etc/rcS.d/S50alsa-utils /etc/rc2.d/' to put it later in the startup sequence.

This actually may, as a side effect, be a workaround to your problem..  The fact that the command you successfully ran -after- startup fails -during- startup seems to indicate that something's changing between those two points.

> 
This should be all default, I haven't changed much at all from the default Kubuntu Feisty.


Yeah, it is..  It sounds like the only thing that's changed is the alsa card number stuff you mentioned.

You have the audiophile as alsa card 0, right?  If you do a 'udevinfo -a -p /class/sound/controlC0', is there a line 'DRIVERS=="ICE1712"' under the parent device?  This is just to confirm that the device name and alsa card number match up.  When the controlC0 device is added, udev tells the alsa-utils script to restore levels for card 0...  controlC1 triggers card 1, and so on.  I don't know if it's even possible for alsa card 0 to correspond to controlC1, but if somehow it does, it might explain why the udev rule isn't working.

If you don't plan on using the onboard sound any time in the near future, you might consider just disabling it in the bios.  If nothing else, it would simplify things.


Here are some other udev tests you might run, though they'll almost certainly check out:

'grep controlC /var/log/udev'.  You should see at least one entry that looks something like this:

```

UDEV  [1186332953.722066] add      /class/sound/controlC0 (sound)

```

..along with corresponding entries for controlC1.  This is the event that should be triggering udev to restore the levels.

'udevtest --action=add /class/sound/controlC0' should spit out a list of all your udev rules files, and should have a line like this one near the bottom:

```

main: run: '/sbin/start-stop-daemon --start --background --pidfile /var/run/alsa/bogus --startas /etc/init.d/alsa-utils -- start 0'

```

This just makes sure the above udev event is, in fact, triggering the rule and running alsa-utils.

If none of this gets you anywhere, you should probably consider writing to the [alsa-user mailing list]("https://lists.sourceforge.net/lists/listinfo/alsa-user")..  Just link them here if you don't want to explain everything over again.  They'll know what they're talking about much more than I do.

---

### Post by SasquatchNC on 2007-08-15
I verified everything you suggested in your post. Everything is pointing to the right place.

So, I disabled the onboard sound and deleted my file from /etc/modules.d. Still not loading my saved profile on bootup.
I ran 'sudo mv /etc/rcS.d/S50alsa-utils /etc/rc2.d/'. That didn't work, either.

Running 'sudo /etc/init.d/alsa-utils start' after bootup does restore my saved settings, which tells me one of two things:
1. ALSA is loading my settings, but something else after it is overwriting
2. ALSA is failing during the normal bootup

I guess I could add alsa-utils start to my bootup profile in KDE, but that seems like an awful kludge. Any way to verify one of my two scenarios?

---

