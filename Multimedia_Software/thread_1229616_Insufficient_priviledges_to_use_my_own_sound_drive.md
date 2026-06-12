---
title: "Insufficient priviledges to use my own sound driver?"
date: 2009-08-02
forum: Multimedia Software
---

### Post by PhantomPholly on 2009-08-02
Hi all,

First - I am an Ubuntu nOOb but have 30 years' experience with PCs, and am only asking because I can't find an answer searching extensively.

Second, I originally posted at the tail end of a three week old thread [here]("http://ubuntuforums.org/showpost.php?p=7718380&postcount=310"), but suspect that that thread is "dead" as OP got his problem solved.  Apologies for double post...

**Problem**:  Sound driver installs ok, but appears to lack permission to run

**Scenario**:  Fresh install of Ubuntu 9.04 on Asus A7N8X Deluxe mobo with SoundStorm.  After install, sound does work.  Successfully installed latest Wine, then Ventrilo under Wine.  Ventrilo works, but everyone reports mic is "very weak."  Search for "SoundStorm Ubuntu Install" and successfully install SoundStorm drivers, then switch all settings to OSS per the instructions in [this thread]("http://ubuntuforums.org/showpost.php?p=1478381&postcount=1").  So far, so good.

Now I launch Ventrilo, but it says, "Cannot find mixer."  Hmm, I just ran it ok.

Everything seems ok if I run "sudo gstreamer-properties" and/or "sudo gnome-sound-properties" from terminal - the tests work ok.  "sudo nvmixer" works just fine, too.  However, I do see the following errors when I launch gstreamer-properties:

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

**Permissions Problem?**

Now this sounds like a privileges thing.  Look at this image:
[IMG]http://www.atlantaspin.org/images/AudioDoesntWork.png

On the left I used "sudo gnome-sound-properties" from a terminal window.  All tests work ok.

On the right I simply went to "System"==>"Preferences"==>"Sound" none of the tests work, and if I try one it says:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. You don't have permission to open the device.

Going to "Administration" ==> "Users and Groups" I cannot change any of my privileges. "sudo users-admin" will not launch from a terminal - sudo gives an error.

What am I doing wrong?

Thanks in advance for your help!

---

### Post by joriad on 2009-08-02
Can't help with your specific sound issue but as for privileges > Going to "Administration" ==> "Users and Groups" I cannot change any of my privileges. Open up "Administration" ==> "Users and Groups" left click on your user then at the bottom of the panel there should be an unlock button, click on that and an autheticate window will pop up, enter system password and click authenticate, you should be able to change your user privileges in the user settings window.

---

### Post by PhantomPholly on 2009-08-02
Doh, should have seen that - thanks!

---

