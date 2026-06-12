---
title: "just installed Ubuntu 10.04 now video players have no sound?"
date: 2011-01-14
forum: Multimedia Software
---

### Post by forgetfullove on 2011-01-14
My speakers are plugged in and work fine, so does my sound card because  every time I login to the computer it makes the welcome ubuntu sound and  it comes through the speakers, I also get the sound when errors and warnings come up. However, when I go to youtube or any  kind of video viewing site there is no sound, I have both my speakers  turned up and the volume on the video turned to high, plus my computer  has a built in speaker. Why am I not getting any sound when I watch the videos, but I get sound when my computer is just making simple pop up noises? I did not have this problem before I upgraded.

---

### Post by BicyclerBoy on 2011-01-14
Open the mixer.
May need to install gnome-alsa-mixer or alsamixergui

Or in a terminal enter:
alsamixer
then press F3

What is hopefully happening is that the volume is set to zero on some sources.

---

### Post by forgetfullove on 2011-01-14
> **BicyclerBoy said:**
> Open the mixer.
May need to install gnome-alsa-mixer or alsamixergui

Or in a terminal enter:
alsamixer
then press F3

What is hopefully happening is that the volume is set to zero on some sources.

I tried that and put full volume on all the levels, but its still silent at youtube and megavideo. I am still getting system sounds though just fine.

---

### Post by BicyclerBoy on 2011-01-14
So when you say videos you really mean flash media player plug-in inside firefox browser ?

VLC or mplayer or totem are media players.

What happens if you run RhythmBox or Totem and play anything ?

Could install the VLC plug-in for firefox & try that.

There must be an audio config for Firefox but I can not find it right now...

---

### Post by forgetfullove on 2011-01-14
> **BicyclerBoy said:**
> So when you say videos you really mean flash media player plug-in inside firefox browser ?

VLC or mplayer or totem are media players.

What happens if you run RhythmBox or Totem and play anything ?

Could install the VLC plug-in for firefox & try that.

There must be an audio config for Firefox but I can not find it right now...


Alright I just went and got a few Mp3's to try and they work fine. I tried playing videos on youtube, vidweed, megavideo and a few anime sites and there is still no sound, so there has to be something wrong with flash or java. Any advice on how to fix it?

---

### Post by forgetfullove on 2011-01-15
Okay, so I think I found one solution, however, I have run to another problem. I am fairly new to linux. here is the solution I found:

1.  install the package, alsa-oss.
2. $ sudo gedit /etc/firefox/firefoxrc.
3. Changed the line FIREFOX_DSP="none" to FIREFOX_DSP="aoss".
4. Save and quit.
5. Restart Firefox.

I am getting stuck at step 2 when I put the command in the terminal brings up the application, but it is blank there is nothing to edit, am I missing something? I have double checked the code several times and have redone it, but it still does it.

---

### Post by lidex on 2011-01-15
I would hold off on that for now. If it's just streaming media take a look at this page:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
Scroll down to the section on streaming and check out the gecko media player.
You probably want to peruse these pages as well to properly set up multimedia:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by forgetfullove on 2011-01-15
> **lidex said:**
> I would hold off on that for now. If it's just streaming media take a look at this page:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
Scroll down to the section on streaming and check out the gecko media player.
You probably want to peruse these pages as well to properly set up multimedia:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Well now I can get videos in Itunes to work with sound, but youtube, megavideo, animefreaks.tv and any other video viewing site that uses flash I try is still silent while the video plays fine. This is becoming annoying, I feel like I have tried everything and still no sound.

---

### Post by BicyclerBoy on 2011-01-16
punch in "about:config" into the address bar of firefox.

enter audio into the filter bar.

What's it set to ? default is okay..

Or install libflashsupport ...
[http://support.mozilla.com/en-US/kb/Flash-based%20videos%20and%20sound%20do%20not%20play%20correctly](http://support.mozilla.com/en-US/kb/Flash-based%20videos%20and%20sound%20do%20not%20play%20correctly)

---

### Post by forgetfullove on 2011-01-16
> **BicyclerBoy said:**
> punch in "about:config" into the address bar of firefox.

enter audio into the filter bar.

What's it set to ? default is okay..

Or install libflashsupport ...
[http://support.mozilla.com/en-US/kb/Flash-based%20videos%20and%20sound%20do%20not%20play%20correctly](http://support.mozilla.com/en-US/kb/Flash-based%20videos%20and%20sound%20do%20not%20play%20correctly)
its set to default....

I installed libflashsupport a little while ago and restarted the computer. It still won't work. I even tried epiphany and chromium and there is no sound there either. I have checked alsa and my sound settings, nothing is on mute and all are set to high. Itunes trailers play fine, and any video file I play, plays fine...I have uninstalled and reinstalled flash player and installed a couple others that said they were related to flash. I am at a total loss.

---

### Post by BicyclerBoy on 2011-01-16
Bizarre it is not...
I have never had an audio problem with any browser on windoze or linux..

Your Firefox user is a member of pulse-access & audio groups ?
There is a VLC firefox plug-in ..

[http://support.mozilla.com/en-US/kb/Video%20or%20audio%20does%20not%20play#Other_solutions]("http://support.mozilla.com/en-US/kb/Video%20or%20audio%20does%20not%20play#Other_solutions")

Cookies disabled 
Some pop-up blocker plug-in ?

I don't have the flash plug-in installed at all so hard to experiment here..

Open the error console window & try to access flash video..
Any clues..

---

### Post by forgetfullove on 2011-01-16
> **BicyclerBoy said:**
> Bizarre it is not...
I have never had an audio problem with any browser on windoze or linux..

Your Firefox user is a member of pulse-access & audio groups ?
There is a VLC firefox plug-in ..

[http://support.mozilla.com/en-US/kb/Video%20or%20audio%20does%20not%20play#Other_solutions](http://support.mozilla.com/en-US/kb/Video%20or%20audio%20does%20not%20play#Other_solutions)

Cookies disabled 
Some pop-up blocker plug-in ?

I don't have the flash plug-in installed at all so hard to experiment here..

Open the error console window & try to access flash video..
Any clues..
pop up blocker is off.
I am not sure how to check the cookies on this version of mozilla...:-k 
the shockwave flash add-on is enabled.
I think I have tried every current solution google has to offer and I feel like this should be super simple to fix, but so fare nada.... thank you for trying to help me. Its late where I am so I am going to head off to bed, but if you think of a solution I will be sure to try it tomorrow and I appreciate the help. :)

---

### Post by forgetfullove on 2011-01-16
could someone tell me how to check the cookies in mozilla?

---

### Post by BicyclerBoy on 2011-01-16
Re-reading previous ..

"iTunes with video" What's that ?

Is it a web browser application or stand-alone app ?

Open Firefox menu:Tools/error console window

Do flash player stuff....

Did you check the posted links about ubuntu-restricted-extras package & medibuntu repos ???

---

### Post by forgetfullove on 2011-01-16
> **BicyclerBoy said:**
> Re-reading previous ..

"iTunes with video" What's that ?

Is it a web browser application or stand-alone app ?

Open Firefox menu:Tools/error console window

Do flash player stuff....

Did you check the posted links about ubuntu-restricted-extras package & medibuntu repos ???
I meant this [site]("http://trailers.apple.com/"), I can watch the videos fine, maybe because it uses quicktime and not flash?
I tried the menu thing, but it gave me an error that there was no such thing. 
I went to youtube and clicked on a video then I went to Tool>manage Plugins and it said it was in use.

Edit: oh and yes I did check the links, they helped me to get the Itunes site to work, which hadn't previously. I am wondering if I shouldn't just downgrade to my old version of 8.04.1?

---

### Post by BicyclerBoy on 2011-01-16
Did you install the flash-plug-in via synaptic package manager or by some other direct means ?

In synaptic there is a flash plugin installer package, maybe this will fix your problems.

---

### Post by forgetfullove on 2011-01-17
> **BicyclerBoy said:**
> Did you install the flash-plug-in via synaptic package manager or by some other direct means ?

In synaptic there is a flash plugin installer package, maybe this will fix your problems.
Tried that and restarted the computer, nothing. I read somewhere that if you have flashplayer 9 and 10 on the same computer it can cause problems, especially if you converted the computer to linux. However, I am not sure how to check to see if I still have 9 on here, it wouldn't show up in the program area. Is there a command I can use? I am still getting used to using commands.

---

### Post by efflandt on 2011-01-17
Do you have more than one flash plugin installed (like gnash or anything)?

When I upgraded a system from 9.04 to 9.10 I had a problem of the then most recent flashplugin-installer appearing to be installed.  But it did not even show up as a plugin in Firefox.  And reinstalling ubuntu-restricted-extras (which had become uninstalled during the upgrade) did not fix it.  But it worked after marking flashplugin-installer for reinstallation in Synaptic.

Although, I had no problems recently upgrading that same system to 10.04.

Did you do anything unusual before with alsa (special ppa's or anything) to resolve any earlier sound issues?  Adobe flash uses default alsa sound, which usually follows what you set with Sound Preferences, unless you have multiple sound devices that are not properly configured.

Do you hear the sound if you do:
aplay /usr/share/sounds/alsa/Front_Center.wav

---

### Post by forgetfullove on 2011-01-17
> **efflandt said:**
> Do you have more than one flash plugin installed (like gnash or anything)?

When I upgraded a system from 9.04 to 9.10 I had a problem of the then most recent flashplugin-installer appearing to be installed.  But it did not even show up as a plugin in Firefox.  And reinstalling ubuntu-restricted-extras (which had become uninstalled during the upgrade) did not fix it.  But it worked after marking flashplugin-installer for reinstallation in Synaptic.

Although, I had no problems recently upgrading that same system to 10.04.

Did you do anything unusual before with alsa (special ppa's or anything) to resolve any earlier sound issues?  Adobe flash uses default alsa sound, which usually follows what you set with Sound Preferences, unless you have multiple sound devices that are not properly configured.

Do you hear the sound if you do:
aplay /usr/share/sounds/alsa/Front_Center.wav

Yes I hear the sound. As far as I know I have made no changes to Alsa other than uping volume and unmuting channels, which I did after the problem started. I have both Gnash and something called swfdec flash player installed, I installed those after the problem began. I just reinstalled flashplugin-installer and restarted the computer, still nothing on any of the browsers I have. I went from version 8.04.1 to 10.04.

---

### Post by BicyclerBoy on 2011-01-17
Previous poster asked about multiple flash plug-ins..
So remove gnash

install 
pavucontrol

check selected audio device then set levels & mutes

---

### Post by forgetfullove on 2011-01-17
> **BicyclerBoy said:**
> Previous poster asked about multiple flash plug-ins..
So remove gnash

install 
pavucontrol

check selected audio device then set levels & mutes
I removed gnash and I already have pavucontrol installed, everything is set to the should be settings, nothing is muted. Still silent. I just don't understand it, everything that doesn't use flash works great on here, yet something is eluding me.

---

### Post by lidex on 2011-01-17
I would advise using the flash-aid extension. It makes it easy to remove conflicting plug-ins and install the correct flash version.
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by VanillaMozilla on 2011-01-17
> **forgetfullove said:**
> However, when I go to youtube or any  kind of video viewing site there is no soundhttp://ubuntuforums.org/showthread.php?t=1657740
I just had two somewhat similar problems, and we worked through several possible causes.  You might check my [solved] threads here:
[http://ubuntuforums.org/showthread.php?t=1657740](http://ubuntuforums.org/showthread.php?t=1657740)
[http://ubuntuforums.org/showthread.php?t=1654511](http://ubuntuforums.org/showthread.php?t=1654511) .

---

### Post by forgetfullove on 2011-01-17
So I found out something weird today...my mother was over using the computer on her account (which is normal nothing special account) and youtube worked great for her there was sound and everything, however there is still none on mine. I called my dad and asked him for his password. Youtube works on his as well...I have checked all my sound settings and everything is up and not muted, why is it working on their accounts and not mine? I am an admin.

---

### Post by forgetfullove on 2011-01-17
So I found out something weird today...my mother was over using the computer on her account (which is normal nothing special account) and youtube worked great for her there was sound and everything, however there is still none on mine. I called my dad and asked him for his password. Youtube works on his as well...I have checked all my sound settings and everything is up and not muted, why is it working on their accounts and not mine? I am an admin.

Edit: I just made another account real quick and it works on there, still nothing on mine though. This is very frustrating.

---

### Post by BicyclerBoy on 2011-01-17
I can't remember if I asked you if the user was in the audio & pulse-access groups ?

---

### Post by forgetfullove on 2011-01-17
> **BicyclerBoy said:**
> I can't remember if I asked you if the user was in the audio & pulse-access groups ?
I am still a bit of a newbie when it comes to linux, how do I check that? Sorry, I am tired.

---

### Post by BicyclerBoy on 2011-01-17
There is Gnome desktop help built into your install...

System/Administration/Users & Groups: manage groups..
& select a group & check its properties (members).

---

### Post by forgetfullove on 2011-01-18
> **BicyclerBoy said:**
> There is Gnome desktop help built into your install...

System/Administration/Users & Groups: manage groups..
& select a group & check its properties (members).
I'm marked there with the others....

Don't worry about it anymore, now that I know I can watch videos on the other accounts I'll just use one of them and use this one for when I need to make changes. 

Thanks for trying help, I appreciate it.

---

