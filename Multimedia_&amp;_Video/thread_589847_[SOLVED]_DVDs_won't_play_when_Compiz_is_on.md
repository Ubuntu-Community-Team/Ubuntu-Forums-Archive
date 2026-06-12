---
title: "[SOLVED] DVDs won't play when Compiz is on"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by mkc on 2007-10-24
When compiz is doing stuff ( I've switched GL desktop effects on) and I try to play a DVD the DVD Playing program just shuts down. I've tried with VLC, Totem, and ogle.all do exactly the same.... switch off GL effects and it works fine... any ideas?

I'm not sure what logs etc would be useful so just let me know and I'll add them. I'm running 7.10 on a samsung Q45 with an intel gfx card.

I also appreciate that if I want to watch a DVD I could just switch off GL effects but if I can fix it so I don't have to that'd be lovely!

Cheers in advance

mark

---

### Post by jaakan on 2007-10-24
is anything under /var/crash/ for Totem or any movie player?

gedit /var/log/messages

look at the log around the time totem shutdown

Do you have Totem-gstreamer or Totem-xine installed?

it could be an issue with the hardware/driver

---

### Post by bwallum on 2007-10-24
I use VLC player and run full Compiz. It plays ok but then the screen goes blank. It is the screensaver cutting in I think. If you just lose the video (and audio keeps playing) then waggling the mouse may bring back the video.

I am trying to find the VLC control that suspends the screensaver so if anybody out there knows, do tell.

Bob

---

### Post by rahulthewall3000 on 2007-10-24
For GStreamer players (such as totem, the default movie player in GNOME, Ubuntu and so on), you need to run from the command line the command
gstreamer-properties
(with older distributions such as Ubuntu 6.06 there is an option in System/Preferences for this).
and pick
Video, then for Default Video Plugin choose X Window System (No Xv). Click on test to verify that it actually works. Click Close and you are set.
VLC is not installed by default in Ubuntu 6.10 or 7.04. You need to install manually using the Synaptic Package Manager (under System/Administration), once you have activated the Universe repository in Repositories.Or you can use the terminal, "sudo apt-get install vlc" after activating Universe repository. 
Start VLC and click on Settings, then Preferences. Expand Video and then expand Output modules. You will notice several options for output device. How do we actually choose which one should be the active output device? Well, it appears it&#8217;s a bit tricky. Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device. Pick X11 video output, click on Save and you are set!

---

### Post by mkc on 2007-10-25
Super! That worked a treat. Is there any way to set X11 as the default output for all my players? - If not no worries but it just saves effort in future

Cheers again

Mark

---

### Post by rahulthewall3000 on 2007-10-28
Well, I would believe that you would either use VLC to play your video files or the default movie player (which is based on gstreamer) so this should fix your problem for most movie players out there. However, if there is still a movie player which still has issues, do get back to me and I will see if there is a way to make this universal. 

However, there is another way which should work. It is working for me. What you could do is to enable video playback in compiz fusion settings. It is under utility. After that revert the options for gstreamer and VLC back to their default values. And then try to play the video. This should work and this would solve your problem for all the media players.
If you do not have compiz fusion settings, install them by typing
sudo apt-get install compizconfig-settings-manager 
and the command to run them is ccsm

Cheers

---

