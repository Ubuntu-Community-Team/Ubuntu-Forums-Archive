---
title: "Audio freaks out way too often in intrepid"
date: 2008-11-06
forum: Multimedia Software
---

### Post by djrobthaman on 2008-11-06
Hi

Does anybody know why audio freaks out every so often in intrepid?  I can't play any audio and when I try to test my audio output in System>Preferences>Audio I get the following error message.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! 
gconfaudiosink: Could not open audio device for playback.

Thanks

---

### Post by Yashiro on 2008-11-06
Your Pulseaudio install is screwed up.
There are many reasons for this and also many fixes. Get searching.

As a quick fix try setting your output device to ALSA and not Auto(or Pulseaudio) in the gnome sound applet.

---

### Post by djrobthaman on 2008-11-06
I actually already have everything set to alsa as opposed to autodetect.  Figured that one out a while back.  So, I'm getting this error even with everything set to alsa.

Will search again (already tried searching but didn't find anything), but could you supply some links to possible solutions?

Thanks

---

### Post by dustigroove on 2008-11-06
> **djrobthaman said:**
> I actually already have everything set to alsa as opposed to autodetect.  Figured that one out a while back.  So, I'm getting this error even with everything set to alsa.

Will search again (already tried searching but didn't find anything), but could you supply some links to possible solutions?

Thanks

From what I can see PulseAudio still loads at boot and seems to control the audio despite setting ALSA in the sound properties utility. What I have found to work are two things A) disable PulseAudio from loading on boot and login, or B) remove the 'pulseaudio' package completely.

I would suggest A as opposed to B as the latter removes the ubuntu-desktop meta-package...

Cheers

---

### Post by dy010490 on 2008-11-06
i tried the same thing to fix audio but this is what happened

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback. Device is being used by another application.

my audio initially worked after upgrading to ibex but suddenly just broke

---

### Post by djrobthaman on 2008-11-10
Well dusti, I've removed pulseaudio from my startup commands.  So my fingers are crossed.  Hope your suggestion works.  Thanks for the help.

---

### Post by dustigroove on 2008-11-11
> **djrobthaman said:**
> Well dusti, I've removed pulseaudio from my startup commands.  So my fingers are crossed.  Hope your suggestion works.  Thanks for the help.

Here's a bit more clarification on my earlier statement...

[COLOR=Navy]***1.) Disable Sessions Entry (run at Login)***[/COLOR][INDENT]If you have a standard Ubuntu setup, go to **System** > **Preferences** > **Sessions** and disable the entry **PulseAudio Session Management**.
[/INDENT][COLOR=Navy]***2.) Disable RC Symlink (run at Boot)***[/COLOR][INDENT]For the other I used a great tool called **sysv-rc-conf** ([FONT=Courier New]sudo apt-get install sysv-rc-conf[/FONT]) that will let you modify what services are started at each run-level. Alternately you can manually remove each corresponding symlink under /etc/rc{runlevel}.d/, but this is sooo much easier.
[/INDENT]Hope this helps!

---

### Post by djrobthaman on 2008-11-11
dusti.  your #1 was what I did (actually I deleted it from the list altogether).  I didn't do your #2.  

But I had the problem happen just now again and fixed it (until it happens again).  I noticed pulseaudio was running (I'll check to see if it still starts up with the system the next time I reboot, that would be weird if it just started in the middle of the session all by itself).  So I killed the pulseaudio process, reloaded alsa and restarted banshee and it works fine and the sound tests work fine now.

So at least now I know how to deal with it when it happens without restarting.  Do you think that applying your second suggestion would fix the problem?

Thanks again

---

### Post by psyke83 on 2008-11-11
PulseAudio is now launched by gnome-settings-daemon in Intrepid, so disabling the aforementioned PulseAudio Session Management module won't change that. It's not configured to run as a service in Intrepid either, so neither of dustigroove's proposed actions will disable PulseAudio properly.

I recommend you give PulseAudio an honest chance. See my [recent post]("http://ubuntuforums.org/showthread.php?p=6149347#post6149347") for more information on this issue (or a better way to disable it, if you must).

---

### Post by dustigroove on 2008-11-11
> **djrobthaman said:**
> So at least now I know how to deal with it when it happens without restarting.  Do you think that applying your second suggestion would fix the problem?

The first part only pertains to session management for PA and not loading of the service itself. The second part will prevent PulseAudio from being loaded on runlevels 2-5 (which is what it is set to do by default) and should rectify it running after reboot.

[COLOR=DimGray]*UPDATE - regarding psyke83's comments above, I don't know enough about PA to know if this entry is unnecessary (although it seems odd to include a sessions entry if it is truly not needed) but I can say for sure that there are indeed symlinks to load pulseaudio as a service at boot.*[/COLOR]

Cheers

---

### Post by psyke83 on 2008-11-11
> **dustigroove said:**
> The first part only pertains to session management for PA and not loading of the service itself. The second part will prevent PulseAudio from being loaded on runlevels 2-5 (which is what it is set to do by default) and should rectify it running after reboot.

[COLOR=DimGray]*UPDATE - regarding psyke83's comments above, I don't know enough about PA to know if this entry is unnecessary (although it seems odd to include a sessions entry if it is truly not needed) but I can say for sure that there are indeed symlinks to load pulseaudio as a service at boot.*[/COLOR]

Cheers

Trust me, PulseAudio doesn't run as a service (daemon) by default. It's run as a per-user process for security reasons, forked by gnome-settings-daemon. The startup session entry is to load an extra module into a running PulseAudio server, not to start PulseAudio.

The infrastructure is in place to support running as a system-wide daemon, but it's not enabled. See /etc/pulse/daemon.conf.

---

### Post by dustigroove on 2008-11-11
> **psyke83 said:**
> Trust me, PulseAudio doesn't run as a service (daemon) by default. It's run as a per-user process for security reasons, forked by gnome-settings-daemon. The startup session entry is to load an extra module into a running PulseAudio server, not to start PulseAudio.

The infrastructure is in place to support running as a system-wide daemon, but it's not enabled. See /etc/pulse/daemon.conf.

I stand corrected.

@ djrobthaman:
I would suggest ignoring my uninformed prattle and instead look at psyke83's recommendation.

[http://ubuntuforums.org/showthread.php?p=6149347#post6149347](http://ubuntuforums.org/showthread.php?p=6149347#post6149347)

---

### Post by dustigroove on 2008-11-11
> **psyke83 said:**
> It's run as a per-user process for security reasons, forked by gnome-settings-daemon.

If this is the case, is there a plugins entry in gconf under gnome-settings-daemon that can just be disabled?

---

