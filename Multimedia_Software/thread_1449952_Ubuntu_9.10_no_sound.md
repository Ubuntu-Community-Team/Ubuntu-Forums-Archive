---
title: "Ubuntu 9.10 no sound"
date: 2010-04-08
forum: Multimedia Software
---

### Post by trouts2 on 2010-04-08
No sound after intalling Ubuntu.  

The install seemed to go ok without error.  I found the forum and went through some of the things in the sticky which are below.

Aplay shows I have a device 0 + 4 of Intel 82881DB-ICH4
lspci -v shows Multimedia audio controller above rev 01
Device 82881DB-ICHFlags: bus master, medium devsel, latency 0, IRQ17
Kernel driver in use: Intel ICH
Kernel modules: snd-intel8x0

A driver check showed  &#8220;ALSA driver for your sound card exists&#8221;

sudo modprobe snd-
Module snd_ not found.

I executed:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
Which removed things.

sudo apt-get install linux-sound-base alsa-base alsa-utils
Report was not found.

Then 
Ubuntu Software Center load of a Alsalayer

Now aplay -l reports No such file or directory.

I executed sudo apt-get install alsa-utils
Now aplay is available.

When I execute 
aplay test.wav 

The text output seemed to indicate the wav was being played but no sound.

The speakers are on and work when plugged into another machine.  The working speakers from another machine when plugged into this machine do not get sound.

Still:
Sudo modprobe snd-  still reports FATAL: Module snd_ not found.

It seems the suggestions from the sticky are not working and I don't have the snd- files.  If I reinstall I'm not so confident they will then appear.  

The machine is a stock Emachines D2823 with 256MB with a Celeron 325 which works fine with XP.

---

### Post by ajgreeny on 2010-04-08
First thing to do when this happens is to run ```
alsamixer
``` in terminal and make sure things are not muted or levels set too low, which they often seem to be.  Use cursor keys to move L & R, and to raise and lower levels, "M" to mute/unmute, and esc to save and quit.

---

### Post by trouts2 on 2010-04-08
Previously I found System>Preferences>Sound and found Sound Preferences.  I set thing to ¾ loud no mute then played a .wav which did not get sound.

I set the controls high with alsamixer - - still no sound.

Although my install seemed to be clean and my hardware should be ok my computer has &#8220;frozen&#8221; several times since the install yesterday.   Possibly something went wrong with the install.  Some of the freezes happened before I ever executed any commands to load things.  Sound should be there by default.  I can play a wave from terminal mode and it seems to be playing but without sound out of the speaker.  

I guess there is no point in going further with this and I'll reinstall to get sound and hope it runs without  going catatonic.

---

### Post by trouts2 on 2010-04-08
Reloaded Ubuntu 9.10 again and got sound.  Ugh.

**UPDATE:** 
The success was shortlived.  Sound was lost after installing Adobe Flash.  That is probably what happeend last time.  

SO: Two loads of Ubuntu and there was sound at first.  After loading Flash no sound.  

Is Adobe Flash Player a problem with Ubuntu?

**UPDATE 2:**
Sound is back.  
I figured I try the movie files from the Ubuntu package so uninstalled Adobe.  The window appeared to said it was installing and finished cleanly.  Adobe should have been removed.  

I tried a sound file again with aplay and no sound.  

I did not install a Ubuntu sourced player. 

Just for yucks I tried a movie and it played which was odd as I had removed flash.  I checked sound preferences and the sound levels were half way but the mute was checked this time.  It was checked in the Applications section but not the Sound Effects section.  Weird, I always check mute and it was not checked off at any time in my previous checks, many.  Something checked off mute since my last check, possibly Adobe.  Possibly this happened during the first install but I checked for mute and the level to be high **many times**.  

Currently, no issue with Morzilla streaming, Utube on Movie Player, .wav with Movie Player or .way with aplay.

**UPDATE 3:**
I tried to play a Utube video but no luck.  It worked before but not now.  After going back to a .wav in Movie Player I lost sound.  A check of Preferences>Sound showed mute checked.  I certaily did not check mute and was getting sound just before this.  **Something is checking mute on its own. **

Playing Utube clips worked before this but now it does not.  I tried one and it said I needed a plug in.  It loaded GStreamer but it's faulting with a "general supporting library error".  I thought that might have been the program that flipped mute but mute is still unchecked so ok.  

Tried playing a Utube clip from Morzilla and it worked fine both video and sound so it's broke in Media Player but ok in Mrozilla.

I reinstalled GStreamer but get the same "general supporting library error".

---

### Post by spf on 2010-04-09
ALSA in 9.10 seems to have some strange muting system;

This worked for me.

  edit

 /etc/init.d/alsa-utils and replace the following line (which is line 372)

 mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
 
with the following line:

# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1

 i.e. comment it out, then reboot and see if it helps

spf

---

### Post by trouts2 on 2010-04-09
spf: You have identified something interesting.  
   
   The sound was there last night. I loaded gstreamer(SP)again and other things from update last night and shutdown. This morning sound went missing again.  The box in sound preferences output volume was set to level 0 and mute checked.  As a note when mute was checked yesterday by some program and the level was also 0.  So probably the line you mentioned is doing it.  
  I tried to modify it but don't have permission.  I've been away from Unix for a while so will have to man chmod and will comment out that line.  Thank you for the post.

  This has got to be a minor user bug.

---

### Post by lidex on 2010-04-11
Are you using skype?

---

### Post by spf on 2010-04-12
> **lidex said:**
> Are you using skype?
Hi, I don't know about the other contributers here but I'm not using skype

---

### Post by spf on 2010-04-12
> **trouts2 said:**
> spf: You have identified something interesting.  
   
   
  I tried to modify it but don't have permission.  I've been away from Unix for a while so will have to man chmod and will comment out that line.  Thank you for the post.

  This has got to be a minor user bug.

 you probably won't be able to chmod either as this file is likely owned by root
Just prefix your editor command with sudo and type in root password when prompted i.e.

sudo "trouts_favourite_text_editor" /etc/init.d/alsa-utils

---

### Post by trouts2 on 2010-04-14
Ajgreeny &#8211; alsamixer won't respond to much but System>Sound Preferences allows setting levels.  They get changed back but I can at least go there and restore sound.

Spf &#8211; I did not edit alsa-utils for a few days to see what conditions trigger the reset of mute and level.  I'm not sure who's causing the reset of the levels and have given up.  

Today I edited alsa-utils and see what happens.  If it works, great and if not it will not be a big deal as I can get back sound through Sound Preferences.  It's a pain but I'll at least have sound but hopefully the edit will remove the irritation. 

Lidex &#8211; No Scype.  Thanks for the references.

   All in all this seems like a minor bug.  This does not happen when poking around the same sights with XP so it seems like some part of Ubuntu thinks it necessary to lower the levels and set mute. 

    I've been away from Unix platforms for several years so the input very helpful.
Thank You
David

---

### Post by lidex on 2010-04-14
Can you give me some more info please? Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by trouts2 on 2010-04-14
Output link:
[http://www.alsa-project.org/db/?f=b874c3f446a4bc80d473eaa6c0beacf957bd98b8](http://www.alsa-project.org/db/?f=b874c3f446a4bc80d473eaa6c0beacf957bd98b8)

Note: I have mute_and_zero_levels commented out as mentioned in an earlier post.

---

### Post by trouts2 on 2010-04-14
I ran compiz-check and got a warning for the check, hardware/setup problems.  The warning listed PCI ID 8086:2562 detected.

Interesting.  I ran the script a few more times.  The first few times it got the warning but now runs and gets all OK's.

---

### Post by lidex on 2010-04-14
First go here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Work through that page and make sure to install the alsa-backports. Post your results.

---

### Post by trouts2 on 2010-04-14
The results for what, the alsa-utils?

---

### Post by lidex on 2010-04-14
Is your sound fixed?

---

### Post by lidex on 2010-04-14
Next go here and work through the relevant sections:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by trouts2 on 2010-04-14
I have sound and have had it for a few days.  The issue is some application is turning the volume level to zero and turning on mute.  I have to open Sound Preferences and reset the level and uncheck mute.  When I do that the sound is fine.  Often I'll loose sound and found it's due to the level being zero and mute set.  I don't know what application is doing that.  That has never happened on this system running XP so probably due to something in Ubuntu.

At the suggestion of a prior post I have commented out a call that sets mute but have not run very long to see if it works.  It happens randomly over time.

---

### Post by lidex on 2010-04-14
Follow 'Part A' of the thread I linked to above then go into alsa-mixer and set the levels to your liking. Now run this command in a terminal:
```
sudo alsactl store 0
```

---

