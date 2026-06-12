---
title: "Mythtv Dist-upgrade"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by napsilan on 2007-10-18
Has anyone tried dist-upgrading a feisty mythtv box to gutsy yet?  I've had things go wrong through regular apt-updates, so I'm not inclined to do a distribution upgrade.  I guess the other option would be re-installing from scratch, and I could actually do it correctly with mythbuntu instead of installing mythtv on top of kubuntu.

---

### Post by napsilan on 2007-10-20
well, running the upgrade now over ssh.  I'll come back with a damage report later.  

[-o<

---

### Post by NTolerance on 2007-10-20
For me the upgrade actually went easier than previous kernel upgrades where lirc would quit working.  I had absolutely no problems and my remote worked immediately without any tweaking.

---

### Post by napsilan on 2007-10-20
This was mythtv installed on top of kubuntu using the medibuntu and mythbutnu repos (apparently not needed after the dist-upgrade).  

needed to apt-get --fix-broken after the dist-upgrade and then apt-get upgrade again.  
needed to re-hack startmythtv.sh to start my keymapper for remote ([http://ubuntuforums.org/showpost.php?p=3547958&postcount=15](http://ubuntuforums.org/showpost.php?p=3547958&postcount=15))
sound didn't work until reboot (onboard)
going to need to redo the permissions for mythweb (apache.conf)
Screensaver starts to kick in during playback (screen fades to black). I had to fix this one in a roundabout way.  I couldn't run gnome-screensaver-preferences over ssh by su'ing to mythtv, I had to log in directly as mythtv.  So I had to change the mythtv password, log in and change the settings, and then re-lock the mythtv password.  
mplayer (mythvideo) is defaulting to XV output (which doesn't work with my ati card, and after my having removed -vo xv from the player command) Needed to add -vo x11 to get it working again (mplayer -fs -zoom -quiet %s -vo x11), or just switch to vlc. 

Otherwise, looks like it works.
Mythstream radio works (been on-and-off for me since I used to manually compile it)
Live TV seems to playback more smoothly and at a higher framerate (p4 3ghz, x800xl, 512mb, pchdtv 5500)
Was able to get the newer xmltv grabber for schedules direct, for some reason the internal grabber was not getting local tv schedules.  PITA to set up (manual info entry for each channel), but now I have lineups for all channels.  

If the screensaver is the biggest problem, I think this is pretty good.

---

