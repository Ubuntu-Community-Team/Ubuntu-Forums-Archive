---
title: "Sound in multiple programs with PulseAudio [fail]"
date: 2009-11-13
forum: Multimedia Software
---

### Post by akoskm on 2009-11-13
Hi!
I've just installed 9.10.
Everything is configured and working without any problem, except PulseAudio:
While I'm plying World of Warcraft with wine (and the sound is Enabled) all other application sounds are blocked (Rhythmbox, Ventrillo(wine)).
What's the problem with my configuration?
Any help appreciated.

---

### Post by HappyFeet on 2009-11-13
When you're not playing WoW, can you hear multiple sources?

---

### Post by akoskm on 2009-11-13
> **HappyFeet said:**
> When you're not playing WoW, can you hear multiple sources?

Thank you for the fast reply!
Yes, of course - example the notification sounds and Rhythmbox.

---

### Post by akoskm on 2009-11-14
On my previous operating system (openSUSE 11.1) I solved this problem by uninstalling all PulseAudio packages.
Unfortunately I can't do that here, because marking libpulse for uninstallation wants to uninstall a lot of gnome libraries and programs too. :-|

---

### Post by kostkon on 2009-11-14
What version of Wine are you using?

---

### Post by akoskm on 2009-11-14
> **kostkon said:**
> What version of Wine are you using?

wine-1.1.30

---

### Post by gej on 2009-11-14
I too have experienced utter failure from both Pulse and Alsa in 9.10.  I don't know what happened but the audio has unusual stops and starts, goes mute between mp3s, has very bizarre hums, buzzes and beeps when adjusting volume.  I just cannot resolve the issue.  It doesn't matter what prog I use - Audacious, Alsaplayer, MPlayer, KMPlayer, Rhythmbox or VLC ... they all have the same issue which points to a driver.

Slightly different topic...
Overall system performance just plain stinks under Ubu 9.10.  The Ext4 filesystem has a fatal flaw for those of you running large files - it corrupts them.

The quality of sound and system performance has deteriorated to the point of driving me to remove 9.10.  I'll attempt either openSuSE, DreamLinux or make a go of FreeBSD.

I really liked the old 8.04/8.10 and even 9.04.  But this latest iteration is severely flawed and may even have the detrimental effect of turning people, especially newbies, away from Linux altogether.

So sad.

---

### Post by akoskm on 2009-11-14
> **gej said:**
> I too have experienced utter failure from both Pulse and Alsa in 9.10.  I don't know what happened but the audio has unusual stops and starts, goes mute between mp3s, has very bizarre hums, buzzes and beeps when adjusting volume.  I just cannot resolve the issue.  It doesn't matter what prog I use - Audacious, Alsaplayer, MPlayer, KMPlayer, Rhythmbox or VLC ... they all have the same issue which points to a driver.

Slightly different topic...
Overall system performance just plain stinks under Ubu 9.10.  The Ext4 filesystem has a fatal flaw for those of you running large files - it corrupts them.

The quality of sound and system performance has deteriorated to the point of driving me to remove 9.10.  I'll attempt either openSuSE, DreamLinux or make a go of FreeBSD.

I really liked the old 8.04/8.10 and even 9.04.  But this latest iteration is severely flawed and may even have the detrimental effect of turning people, especially newbies, away from Linux altogether.

So sad.

As I mentioned before openSUSE 11.1 was my previous operating system, and it's worked without any problems - with regular system updates & removing PulseAudio.
I just wanted to try the new Ubuntu, but here every sound system fails, not just PulseA. :-|

---

### Post by VertexPusher on 2009-11-14
> **akoskm said:**
> On my previous operating system (openSUSE 11.1) I solved this problem by uninstalling all PulseAudio packages.
Unfortunately I can't do that here, because marking libpulse for uninstallation wants to uninstall a lot of gnome libraries and programs too. :-|
You can still do that. You will lose the volume control in the system tray, but you can install gnome-alsamixer as a replacement. Everything else works fine. I am running 9.10 this way. No issues at all.

These are the packages that should be removed:

pulseaudio (and depending packages)
gstreamer0.10-pulseaudio
vlc-plugin-pulse

These are the packages that should be installed:

gnome-alsamixer
gstreamer0.10-alsa

---

### Post by LiteralKaiser on 2009-11-14
I have this problem on 9.04

---

### Post by erikla2002 on 2009-11-15
I also have this problem with 9.10. Its so annoying that I thing about going back to win7 :(

If Firefox is using sound I don't hear sound in Wine or Skype etc. 

How can such a simple thing as audio be such a big problem in Linux?? 

I reinstalled Pulseasuio but no help.

---

### Post by akoskm on 2009-11-15
> **erikla2002 said:**
> I also have this problem with 9.10. Its so annoying that I thing about going back to win7 :(

If Firefox is using sound I don't hear sound in Wine or Skype etc. 

How can such a simple thing as audio be such a big problem in Linux?? 

I reinstalled Pulseasuio but no help.

I don't think that reinstalling PulseAudio would be good idea because it failed with the default installation too.
Try to install ALSA instead, read the previous post:
[http://ubuntuforums.org/showpost.php?p=8316107&postcount=9]("http://ubuntuforums.org/showpost.php?p=8316107&postcount=9").

---

### Post by erikla2002 on 2009-11-15
> **akoskm said:**
> I don't think that reinstalling PulseAudio would be good idea because it failed with the default installation too.
Try to install ALSA instead, read the previous post:
[http://ubuntuforums.org/showpost.php?p=8316107&postcount=9]("http://ubuntuforums.org/showpost.php?p=8316107&postcount=9").


But will Skype work with Alsa? Because in Options-> Sound devices you can only select Pulseaudio server in latest Skype. But maybe it works anyway...

---

### Post by akoskm on 2009-11-15
> **erikla2002 said:**
> But will Skype work with Alsa? Because in Options-> Sound devices you can only select Pulseaudio server in latest Skype. But maybe it works anyway...

On openSUSE 11.1 everything worked with ALSA after completely removing PulseAudio, I hope that here works too.

ps.: ...but why they include a sound system like PulseAudio if it worst then the other, and after all seems nobody have idea how to solve problems like this.

---

### Post by gej on 2009-11-15
After an incredible amount of searching I removed Pulse.. completely from my system and the sound now works.

New problem:  System froze during Asunder rip session.  Restarted system to a login loop which seems to be another common 9.10 experience, at least according to Google.  Oh boy, this one didn't allow me to recover --- AGAIN!!!!  Frustration with 9.10 rears it's ugly head (yeah, I'm ugly).

To get going again I put in the 9.10 CD.  I thought maybe, just maybe, a "Recover" option would appear, no such animal.  The only so-called option I get is to reinstall the OS.  But it does give me the "side-by-side" option.  Since I have no idea what it will do to the 25G of data I might as well just throw on a different distro (openSuSE comes to mind).

I've had it with Ubuntu.  There is absolutely no reason why this version should perform so badly.  It has more issues than Windows Vista ever did, and that's saying a lot.  I was going to tough it out, contrary to my first couple posts, but have come to the conclusion it's just not worth the headaches.

I still believe this version will turn so many people off to Ubuntu, most especially those first-timers who were so hard to win over.  Once gone the disgruntled will never return.  The community is going to lose a lot of potential users over this debacle.

Final post.

---

### Post by akoskm on 2009-11-15
> **VertexPusher said:**
> You can still do that. You will lose the volume control in the system tray, but you can install gnome-alsamixer as a replacement. Everything else works fine. I am running 9.10 this way. No issues at all.

These are the packages that should be removed:

pulseaudio (and depending packages)
gstreamer0.10-pulseaudio
vlc-plugin-pulse

These are the packages that should be installed:

gnome-alsamixer
gstreamer0.10-alsa

Okay, I've tried this and it's worked... partially.
When Wow is running and I start to play some music in Rythmbox the sound becomes shuttering. :-|

---

### Post by mmtowns on 2009-11-29
Wow!  I had this issue with 8.10 and now with 9.10.  I tried out the fix mentioned and now I have sound in multiple programs.  Some programs (rhythmbox, for example) seem to be a bit distorted in their output, but it's a step ahead from where I used to be.

---

### Post by suzenon on 2009-12-09
Hello.

I just want to bump this topic and say i'm suffering from exactly same issue. Only one sound source at time. Most annoying is when i'm listening to music player, stop music to watch youtube vid, unpause music in my player and nothing happens.

I'll try removing pulse audio stuff as mentioned above and post if it works or fails.

EDIT:
well... i can hear to various sound sources at a time, gnome-alsamixer > pulseaudio

---

### Post by markbuntu on 2009-12-11
Well, the wine devs have fessed up to using some non-standard alsa api calls and have been working for over a year now with the pulse devs to fix wine so it works with pulseaudio, which it does now. But that does not necessarily mean wine will work properly with the kludged version of pulseaudio the ubuntu maintainers have cobbled together again.

---

