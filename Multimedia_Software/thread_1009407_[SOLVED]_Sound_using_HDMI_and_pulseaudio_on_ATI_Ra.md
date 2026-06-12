---
title: "[SOLVED] Sound using HDMI and pulseaudio on ATI Radeon 2600 HD + others"
date: 2008-12-12
forum: Multimedia Software
---

### Post by notlistening on 2008-12-12
Hi I am just adding this for clarity for those people struggling to get their sounds working through pulseaudio using the ATI drivers and HDMI interface.

What this enabled you to do is play multiple sound stream at the same time from  a number of different programs. For example a messenger app and music app. 

What i did to solve this problem:

```

aplay -l

```

this gave me details of all my sound cards and their devices:


```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```


I cheated slightly here and disabled the integrated sound card on my motherboard. If ypu still have this enabled there maybe more listed from this command.

Next you must go and edit the pulseaudio config file /etc/pulse/default.pa


```
sudo nano /etc/pulse/default.pa
```


find this section


```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
```


Add this line after that comment:

```
load-module module-alsa-sink device=hw:0,3
```

Notice that device=hw:0,3 correspond to:

card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]

This should give you audio, not at the login screen but straight after a valid logpn. 

Rock on .... Tom  
:guitar:

---

### Post by sabrateur on 2009-02-27
Dude, this definitely works~!

Previously I had to manually set the device in System -> Preference -> Sound, but this gives me no sound through Flash.

Now, EVERYTHING works!

Thanks, man!

---

### Post by mister_doctor on 2009-03-27
Excellent, thats one less cable going into my TV/stereo!

---

### Post by oneiromancer on 2009-05-25
OK, I'm puzzled...  this FIXED my hdmi sound problem, ie now when I test sound in Preferences->Sounds over HDA ATI HDMI (Alsa Mixer) I get a test tone, and before this I didn't...  but it doesn't seem to be working system-wide.  Login and other sounds don't play, VLC and SMplayer wouldn't play, though bizarrely regular MPlayer did...  So clearly this is just a configuration issue in Ubuntu right?  But I'm struggling with what to do next.

---

### Post by oneiromancer on 2009-05-25
OK, I can get SMplayer to work by going into preferences and selecting the output manually, but I'd like to get the system knowing where to put things by default, including some software that doesn't have ability to manually configure audio output.  So progress, but help still appreciated.

For reference, I'm on Jaunty and my aplay -l output is:
```
oneiros@AntecFusion:~/Desktop/brainworkshop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and I edited my default.pa file correspondingly

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
...
#load-module module-pipe-sink
load-module module-alsa-sink device=hw:1,3
```

Not sure what else to offer...  modprobe -l|grep alsa shows:
```
oneiros@AntecFusion:~/Desktop/brainworkshop$ modprobe -l|grep alsa
kernel/arch/x86/crypto/salsa20-i586.ko
kernel/crypto/salsa20_generic.ko
kernel/drivers/media/video/saa7134/saa7134-alsa.ko
kernel/drivers/media/video/cx88/cx88-alsa.ko
kernel/drivers/media/video/em28xx/em28xx-alsa.ko

```

and I was about to install new alsa drivers into kernel from [this bug]("https://bugs.launchpad.net/ubuntu/+bug/352556")'s problems when I decided to try this first, and thought this seemed lower risk.  Hope someone can help, or I think of/find an answer soon...

(I briefly "broke" even the test working, but that was just because I unchecked the IEC958 switch in volume control, trying to "fix" things...  Why are there so many seperate panels configuring sound??)

---

### Post by notlistening on 2009-05-25
* Update *

After about ten fresh installs of 9.04 I have found the combination of reasons behind my sound problems. I have installed the latest ATI drivers version 9.5 (at the time of writing) from ati.com. This solved a lot of issues with the shipped graphics driver with 9.04 and also ended up leading me to the problem and a working solution. 

The sound would just stop working all together for no reason and not work again even after a completely fresh install. You would think that after a completely fresh install that if it worked the first time it would work again in the future. This totally threw me. Then in an attempt to resolve the issue i installed the ATI drivers, great the sound worked again problem solved? No, a few restarts later the sound died again and would not return weird. Another fresh install and again no sound. Install the ATI driver and sound works again three restarts and nothing. During these restarts I was installing and changing my system setting, I have a HDTV as a monitor, a Samsung 1080p that will run up to 60hz refresh rate. So naturally I want the highest refresh rate possible. When i set the refresh rate to 60hz and restart no sound, set it to any of the lower values it starts working again. This 60hz settning was being saved/retain even through a fresh install. That was what i could not work out. After installing the ATI driver it set it back to 24hz by default and that meant that the sound worked, I still had to complete the remaining steps detailed below to get the sound working. I was always setting the refresh rate to maximum and the sound always disappeared after one or two restarts and never comes back. I now have the ATI card set to 30hz which the TV does at 60hz, will be onto to ATI with a bug report & ubuntu.    

** Warning ** My system would freeze at the login screen this morning :(. Due to my experience trying to fix this problem I got the solution straight away but please make a note of this command if you can not login. You have to go into recovery mode and then type in: 

su $yourusername 

asoundconf unset-pulseaudio

sudo shutdown -r now

Please only do this if your confident you can fix your system and you should be be in! Please if not wait for some feedback from other users. I think this was only required as i had been messing with my configuration somewhat while testing. Please report your experiences.
-----------------------------------------------------------------

Original Post:

I am back and after days of fluffing about with a new 9.04 installation with this hardware I have some gems to give you all.

The release as of 20th May 2009 of 9.04 will not work with this sound setup. The pulseaudio version shipped is just terrible but there is a workaround :).

What i recommend you do. Follow the instructions above and edit your default.pa file to test that the sound is functioning on the system before trying an update.

See the bottom of this post for details of how you deal with no sound working at all after editing your default.pa or some applications not using pulseaudio

-------------------------------------------
Follow these instructions if your audio is stuttering on first audio playback. 

[http://webupd8.blogspot.com/2009/05/how-to-install-latest-pulseaudio-0915.html](http://webupd8.blogspot.com/2009/05/how-to-install-latest-pulseaudio-0915.html)

When the main Ubuntu Repos catch up to this version you can removed them and stay with the normal packages. 

What this gives you:

* Forget all the information you have read above this new version of pulseaudio now detects my card (ATI Radeon HD 2600HD aka ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series)
 automatically. 

* The initial sound clipping you may have experienced is now fixed

* When pulseaudio puts the sound card to sleep there was a audiable sound like a small click which is also gone. 

All in all Brilliant :)
-------------------------------------------

No sound working at all or system wide sound not using pulseaudio

Try:

sudo apt-get install asoundconfig-gtk

then in a terminal type:

asoundconfig-gtk

in this little app set the sound card to be used as pulseaudio. That worked for me but before doing this i testd direct sound access to the card by choosing HDA ATI HDMI ATI HDMI (Alsa) if you hear the test sound then your half way there. Then change to pulseaudio and test again pray that everything is okay. 

Tip:

To check your pulseaudio changes have been sucessful in a terminal try:

killall pulseaudio

pulseaudio -vv

Look at the output for any errors. 

 
Tom (Hearing again)

---

### Post by oneiromancer on 2009-05-27
OK...  your problems sound different from mine, but first, the pkg name you meant is asoundconf-gtk not asoundconfig-gtk, for anyone confused, but also...  er...  hmm.  The refresh rate huh?  Probably not my issue, and I'm going to try the asoundconf-gtk to see if that can redirect my systemwide audio, since our setups sound similar, but, not 100% sure...  crossing fingers, wish me luck :-)

---

### Post by oneiromancer on 2009-05-27
OK, I think I'm still where I was before, after installing audioconf-gtk, but I have new questions and new data...  first, I hadn't noticed it before so I'm not sure if something I did recently installed it or if I just missed it before, but I now have PulseAudio Preferences under System->Preferences, with a checkbox on third tab for "Add virtual output device for simultaneous output on all local sound cards".  This sounds good but didn't obviously change anything when selecting PulseAudio server as source (which I did in the audioconf-gtk gui, as well as selecting HDMI, which also didn't seem to help for getting audio there by default for the system as a whole).

I have a lot of options though on the System->Preferences->Sound panel that I'm not sure I understand properly, and don't know where they're documented, including the role and relevance of selections made in Device Mixer Tracks to the above tests and to overall system settings...  There's similar/the same devices (though more I think for some options that only have "Master" in Sound preferences Mixer) in Volume Control preferences, by right clicking on volume icon and selecting "Preferences"...  There are so many different places that might be effecting things, that don't appear clearly documented in help or anywhere I've easily found online, I despair!

Attached are screenshots of some of these panels and their myriad options.

[[EDIT ]] I finally got audio in VLC to work via advanced preferences... still would like to have system audio working, among other things for the brainworkshop.pyw module which needs sound output for dual-n back mode, but at least I can finally watch videos...
[[/EDIT]]

So far, nothing I've done has ever gotten audio in VLC to work, which is my preferred media player.  Audio generally works via MPlayer, and via test of HDMI as described above, but not for the system sounds or for VLC, including playing with VLC preferences -> Audio -> Sound output.  It has options for Default, Alsa and OSS Audio output via /dev/<device> which defaulted to /dev/dsp and I thought maybe since I was using device-1 instead of device-0 (see above) that /dev/dsp2 would work, but no luck there or a few other /dev's I tried.  Still need help!  Thanks.

---

### Post by notlistening on 2009-05-28
Your VLC should be configures like this:

sudo apt-get install vlc-plugin-pulse

Then in VLC under prefrences->audio tick the use S/PDIf when available change to pulseaudio, if your pulseaudio is configured correctly which i think it is not you should get sound.  

You sound setting should all say pulseaudio in your sound configuration panel. Run the test on each one when testing and see if that works for each one.

Lastly try:

sudo apt-get install padevchooser 

you will find in under Applications->Sound & Video-> Pulseaudio device chooser. 

This gives you a little icon in your notifications area. Right click on it and choose volume control them have a play around in there for your output and configurations. 

Best way to do this testing is with applications that are not working properly running making sound. 

Good luck again,

NL

Oh and thanks for the correction to my typo

---

### Post by markbuntu on 2009-05-28
If you really want to fix those problems you should try pulseaudio0.9.15. It is much better at detecting devices like HDMI and the pulseaudio volume control is much improved so you can control them.

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

---

### Post by gotigersducksvols on 2009-05-31
I too am having issues along the same lines:

What works: 
Playing an Audio CD in Rythmbox or VLC

What doesn't work:
Any sound trying to come out of Firefox.

If it helps, I'm running an HD 3650 desktop video card. If I go to 
System>Preferences>Sound 
I can get the test sound to play if I choose PulseAudio or HDA ATI HDMI ATI HDMI (ALSA)

Thoughts? I imagine I'm missing something simple.

Edit:  I'm using Intrepid with Catalyst 9.5. Jaunty killed this machine (boot, when it got to gdm, it would show some nice colors and lock up)

---

### Post by notlistening on 2009-05-31
I had the same problem for the startup issue with the graphics card. This is described earlier in the post how to get around this issue, well it worked on my machine if your game to try it again. the:

asoundconf unset-pulseaudio

Got me into 9.04
 

Depends what your using in firefox, trying the ubuntu-restricted package might give you some joy?

NL

---

### Post by oneiromancer on 2009-06-16
EDIT 2: OK, leaving the rest up for reference, but it turns out upgrading ATI Drivers (as suggested above by NotListening, though I didn't notice until tonight) fixed both my Boxee problem and my PulseAudio/Server config problems (though the latter probably just because of the install more than the upgrade, since that was working before).  Boxee's not perfect still, but the specific consistent lag problem (and a related problem where FF/RW buttons that on Mac skip 30 seconds either direction, were speeding up and rewinding playback, and also messing with audio sync like pause problem) seems to be basically fixed, so that's very good news...  I was really at the end of my rope!

Thanks again all.

I sat down 30 minutes ago to thank you all for your help, and mention the one weird remaining problem I had, which I thought I was unlikely to find help for here, that being that Boxee, which is a little unstable but basically pretty awesome, has weird issues with PulseAudio apparently...  The only suggestions I've found for resolving my problems there were basically removing PulseAudio from the system.

What's interesting is, throughout my audio troubles, Boxee has had an almost magical ability to get ITS audio to work regardless of how borked other settings were, and the other day, when trying out XBMC or something did something weird to break audio, running Boxee still worked, AND fixed it so the same settings were working after running it once that hadn't worked before (best guess that it auto-killed and relaunched some sound server or something that was locked or frozen or otherwise unaccessible?  Dunno)




That was 30 minutes ago, and all audio had been working across the system for about a week, with only occasional playing to try and fix Boxee's problems and whatnot (audio works, but on unpause, audio decouples from video, video plays too fast, weird things happen). 

EDIT: I remembered what the likely real culprit is, which is I installed Freevo right before this happened, 
to try out, but I think it broke pulseaudio somehow...  only uninstalling it didn't fix it... I'm going to research a bit, but man, am I sorry I installed it....


 I ran asoundconf-unset-pulseaudio after checking there was inverse method asoundcong-set-pulseaudio, just to check/verify it didn't do anything different than changing default sound card via asoundconf-gtk (like, for instance, simulate removing pulseaudio so that Boxee might bypass it or stop having problems with it or whatever), but it didn't help...  Sound still worked in Boxee, but I had a crash, restarted, and now, no sound works at all, anywhere in system, despite checking and rechecking all the settings ayou guys helped me painstakingly figure out over the last few weeks and restarting again...

Oh, and I did upgrade pulseaudio to 9.15, though the PulseAudio manager client information says: Linked to Library Version: 0.9.15, Compiled with Library Version: 0.9.14.  Is that discrepency significant?

I thought this would be a good excuse to try uninstalling PulseAudio, see if that fixed Boxee (and whether/how other things worked in its absence), and then reinstall it, hoping that would fix whatever got borked, but it looks like ubuntu-desktop depends on pulseaudio?  So I can't remove without removing the desktop?  I can resinstall both via command line no problem, but not sure if that's likely to fix...  fairly weired out by how fragile the system seems though, I may just have to go back to mainly using OS X, I dunno....

---

### Post by markbuntu on 2009-06-16
The ubuntu-desktop is just a sort of meta list of installed applications to help with upgrading. It is really not necessary unless you are upgradong in which case you should reinstall it before you do. It will not remove your gnome or kde or xfce or whatever you use for a desktop.

---

### Post by oneiromancer on 2009-06-23
Minor update, curious if anyone can illuminate...  just installed  2.6.28-13 kernel update, and two bits of strangeness, don't know for sure if either is PulseAudio or HDMI related, but thought I'd mention here...

First, after update, default kernel was  2.6.28-13-server, and I left that alone, as I'm still a little fuzzy on the server vs generic kernel distinction, but under the server kernel I couldn't get sound working at all, though PulseAudio and all sounds settings seemed the same (though in either kernel I'm still having to manually select HDMI as sound sink in PulseAudio Device Chooser, despite explicitly setting in default.pa...  probably need a second setting or to adjust something there).  I restarted and selected  2.6.28-13-generic and, other than having to select sink, everything works again.  Anyone know why, if there's a fix, or explain what kernel type matters for?

Second, bit weird, but VLC seems to be having weird audio speed/pitch problems since the update.  SMPlayer is working fine, maybe better than before, but this is annoying, and I'm not sure if it's kernel related or something else (I think it started after update but before I restarted with new kernel, which seems weird). Curious if anyone has any insight.  I'm psyched for new boxee release tonight though!  Maybe stable/fast enough to use now!

---

### Post by jbraveman on 2009-08-04
This worked for me.  Thanks!

---

### Post by ub-newbie on 2009-08-07
NotListening's patch worked for me with my Asus M3N78-EM mobo running Jaunty X64, after I upgraded to Firefox 3.5 from [https://help.ubuntu.com/community/FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion")

I ran ```
aplay -l 
``` and got 
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

So I went to /etc/pulse/default.pa and put in
```
load-module module-alsa-sink device=hw:0,3
```

then a reboot, opened APPLICATIONS, SOUND AND VIDEO, PULSE AUDIO CONTROL.  From there I could click the little "down arrow" (in the top right corner) to select MOVIE STREAM, and there I could select HDA NVIDIA - NVIDIA HDMI

--------------------------
In my previous attempt to solve my "no sound from flash in Firefox" I had downloaded Firefox 3.5 (which was REQUIRED), removed and re-installed the 64bit Flash plugin v10.0 r32, and had no-joy.  When I would open PULSE AUDIO CONTROL I could see the volume bar moving, but no sound was being played.  (also, I had to install the PULSE AUDIO CONTROL, it was not present by default [APPLICATIONS, ADD/REMOVE]).

NotListining... thanks for the save.  :popcorn:

---

