---
title: "firefox flash sound issues after upgrade to 10.04 - please help!"
date: 2010-05-02
forum: Multimedia Software
---

### Post by margiwarg on 2010-05-02
I just upgraded to 10.04 from 8.04, and am now having issues with sound in firefox. Sound outside of firefox (movies, music, etc.) is fine.

Streaming video works, but there is no sound. Myspace tells me that I need to upgrade to the newest version of flash... which I have done, with no effect.

If I reinstall flashplugin-installer, and restart firefox, I get sound for streaming video (although Myspace still says I need new version of flash), but ONLY until I close firefox. If I open it again, the sound is gone... so I then need to reinstall flash, and restart firefox to get sound back. I don't really see this as a long term solution!

Any help please?

---

### Post by gp2x on 2010-05-02
same issue here. Found anything?

---

### Post by sunk8 on 2010-05-02
I faced a similar issue.
Install the latest plugin from [adobe site]("http://get.adobe.com/flashplayer/").
Solved it for me...

---

### Post by margiwarg on 2010-05-02
Yes, I have tried installing flash in many ways, including through the pugin on the Adobe website. The problem is that even though it shows up as being installed, it only works until I close firefox. And when it does work, only the sound on streaming video works, there is still no sound or functionality for streaming audio.

Any other ideas?

---

### Post by sunk8 on 2010-05-02
Try another browser...
Like Chromium perhaps...
It works better than the fox for me...

---

### Post by Ad@m on 2010-05-02
Personally I would never performance an upgrade as it can cause many issues.

Can you perform a clean install?

Perhaps try removing firefox and reinstalling it.

If using Ubuntu 10.04 64-bit, try using the native 64-bit flash plugin. If you need to know how to do this, let me know.

---

### Post by margiwarg on 2010-05-02
Using a different browser or reinstalling firefox doesn't help. I'm using 32-bit Ubuntu. 

I may try a clean install as this is not the only glitch that has come up, just the most annoying thus far. A clean install just seems daunting and time consuming.

---

### Post by jerrylamos on 2010-05-02
Me too.  With intel hardware.  Some sites with audio, others not example Whitehouse.gov, BBC news, ...  

Used to work but the "dreaded update" struck again.  When will I ever learn with Ubuntu "if it isn't broken don't fix it" and NOT do updates.

With ati hardware, Lucid firefox flash v-e-r-y--s-l-o-w and jerky.

Let me look for a different distro, I've recently used Slax, Slitaz, and Debian LXDE.  They were much easier with Grub Menu.lst, a bit of a bear with Grub2's 40_custom.

Jerry

---

### Post by lidex on 2010-05-02
Try out this thread:
[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")

---

### Post by eklypze on 2010-05-02
I also have this issue and I have already done the steps that lidex has posted in his link but still no avail.

---

### Post by ratcheer on 2010-05-02
Flash will only use the first sound card as seen by ALSA. If you have multiple sound modules and ALSA sees the wrong one first, you will get no sound from Flash. In that case, you must force that sound module to be second to ALSA.

Tim

---

### Post by eklypze on 2010-05-02
Can you be more specific on how to fix this please ratcheer?

Thanks.

---

### Post by gh_freeman on 2010-05-02
Hi, 
This is a solution it works fine with me
use this commands:

```
sudo aptitude install alsa-oss
sudo gedit /etc/firefox/firefoxrc
 FIREFOX_DSP=”aoss”

```
Then, restart firefox
:P

---

### Post by ratcheer on 2010-05-02
> **eklypze said:**
> Can you be more specific on how to fix this please ratcheer?

Thanks.

I just told someone in a different thread, yesterday.

[http://ubuntuforums.org/showthread.php?t=1467170&page=2](http://ubuntuforums.org/showthread.php?t=1467170&page=2)

See post #15.

Tim

---

### Post by margiwarg on 2010-05-03
I only have one sound card so that wasn't the issue. I had also tried gh_freeman's solution... and pretty much anything else I could find with google... to no avail. 

In the end I did a clean install, then installed flash, and everything is a-ok. I wish I had just done the clean install in the first place. After upgrading I felt like I was using a glitchy version of my previous system (8.04) with some updated software. Clean install looks much better and is running much smoother! So far anyway...

---

### Post by disperso on 2010-05-03
Same problem. After upgrading from Hardy Heron to Lucid Lynx, I have  sound for all applications save the web browsers (no audio on youtube,  Jango, lastfm and so on).  I have tried with Firefox, Chrome, Epiphany,  Konqueror and Opera. It seems that something doesn't work fine with the  ALSA-plugins. I have reinstalled almost every browser twice (including  plugins), but they still don't work. Sometimes I get them work, but then  when I reboot, the sound is gone (as was the case when I tried with the solution suggested by lidex, the thread [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)).  On the other hand, if I see a video requiring Moonlight, everything works. Does anyone have an idea how to fix it? Thanks guys!

---

### Post by gp2x on 2010-05-03
This worked for me

[http://www.willmcgugan.com/blog/tech/2010/5/2/no-audio-in-flash-on-ubuntu-1004/](http://www.willmcgugan.com/blog/tech/2010/5/2/no-audio-in-flash-on-ubuntu-1004/)

Basically youve got 2 versions of flash installed, so rm ~/.mozilla/plugins/libflashplayer.so to get rid of 9.

Hooray! \o/

---

### Post by disperso on 2010-05-03
Thanks gp2x, your solution worked for me too.

Hurrah (the italian way)!

---

### Post by claus on 2010-05-03
> **lidex said:**
> Try out this thread:
[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")

I just tried it, but still no sound. Are there any other solutions, besides switching to a different browser?

Claus

---

### Post by claus on 2010-05-03
> **claus said:**
> I just tried it, but still no sound. Are there any other solutions, besides switching to a different browser?

Claus

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

This worked for me.

Claus

---

### Post by Sputnik82 on 2010-05-04
> **gp2x said:**
> This worked for me

[http://www.willmcgugan.com/blog/tech/2010/5/2/no-audio-in-flash-on-ubuntu-1004/](http://www.willmcgugan.com/blog/tech/2010/5/2/no-audio-in-flash-on-ubuntu-1004/)

Basically youve got 2 versions of flash installed, so rm ~/.mozilla/plugins/libflashplayer.so to get rid of 9.

Hooray! \o/

This also worked for me! Thanks! :D

---

### Post by RamahX on 2010-05-05
tried everything on this thread to no avail, no sound from flash on ff3...

upgraded from 9.10 to 10.04 UNR.

I had this problem before upgrading but cant remember what I did.

---

### Post by lidex on 2010-05-05
> **RamahX said:**
> tried everything on this thread to no avail, no sound from flash on ff3...

upgraded from 9.10 to 10.04 UNR.

I had this problem before upgrading but cant remember what I did.

Can't remember...or don't want to remember? ;)
What is reported in firefox='Tools>AddOns>Plugins'?

---

### Post by monkeys on 2010-05-06
I had the same problem and ended up solving it by removing "flashplugin-installer" and installing "adobe-flashplugin" through Synaptics.

I had previously used this code:

> sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree

from [http://lovinglinux.megabyet.net/?page_id=220](http://lovinglinux.megabyet.net/?page_id=220) but when I checked Synaptic, I didn't have flashplugin-nonfree installed. Prior to I had used this: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) to install Flash.

Hope that helps somebody (: Sorry I can't explain better. I'm a bit of a novice.

---

### Post by monkeys on 2010-05-06
Double-posted, sorry.

---

### Post by lidex on 2010-05-07
I would tweak those commands a bit:
```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-installer
```
Then go here:
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")

---

### Post by Magick93 on 2010-05-09
I also have no sound in flash after upgrading.

Ive checked the sound levels using alsamixer and followed the tips in this thread - but still no sound.

Any other ideas?

---

### Post by RickThorpe2006 on 2010-05-09
Same problem.  As with gp2x, the sound problem appears to have resulted from Firefox still using a v9 plugin despite having installed v10.  You may need to remove more than one file, however.  The following worked for me:
1.  Uninstall the adobe flash plugin and any related installer packages (I went into the Synaptic package manager and searched on "flash" to confirm.)
2.  Open Firefox, enter "about:config" in the address line.  Scroll down to find the line "plugin.expose_full_path".  Double click that line to set the variable to yes.
3.  Enter "about:plugins" in the address line.  Scroll down to the "Shockwave Flash" section.  Right below the bold header, if your problem is the v9 one, you will see a file location followed by the version of flash.  Open a terminal and sudo rm -f [file location].
4.  Close Firefox, reopen, go to about:plugins.  You may still find a Shockwave Flash section with a different v9 file listed.  Remove that file as well, close and repeat until this doesn't show any v9 flash files.
5.  Reinstall the v10 flash plugin.

---

### Post by Magick93 on 2010-05-10
> **RickThorpe2006 said:**
> Same problem.  As with gp2x, the sound problem appears to have resulted from Firefox still using a v9 plugin despite having installed v10.  You may need to remove more than one file, however.  The following worked for me:
1.  Uninstall the adobe flash plugin and any related installer packages (I went into the Synaptic package manager and searched on "flash" to confirm.)
2.  Open Firefox, enter "about:config" in the address line.  Scroll down to find the line "plugin.expose_full_path".  Double click that line to set the variable to yes.
3.  Enter "about:plugins" in the address line.  Scroll down to the "Shockwave Flash" section.  Right below the bold header, if your problem is the v9 one, you will see a file location followed by the version of flash.  Open a terminal and sudo rm -f [file location].
4.  Close Firefox, reopen, go to about:plugins.  You may still find a Shockwave Flash section with a different v9 file listed.  Remove that file as well, close and repeat until this doesn't show any v9 flash files.
5.  Reinstall the v10 flash plugin.

That fixed it. Thanks :)

---

### Post by monkeys on 2010-05-11
yeee-up, my fix ended up being temporary, as described in the original post. followed up with Rick's suggestion. will update when i find out whether it works.

**edit:** it works! (:

---

### Post by davidmaxwaterman on 2010-05-15
> **monkeys said:**
> I had the same problem and ended up solving it by removing "flashplugin-installer" and installing "adobe-flashplugin" through Synaptics.
.

This worked for me, though I used apt from the command line. Oh, and I also removed flashplugin-nonfree.

---

### Post by davidmaxwaterman on 2010-05-16
> **davidmaxwaterman said:**
> This worked for me, though I used apt from the command line. Oh, and I also removed flashplugin-nonfree.

Ok, so I spoke too soon. It has stopped working again :(

---

### Post by roganjosh on 2010-05-16
> **lidex said:**
> Try out this thread:
[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")

This worked for me! Many thanks.

---

### Post by montysan on 2010-05-17
RickThorpe2006's solution fixed my problems. I had more than 2 versions of flash installed. I'm pretty sure I've never installed them myself, so I guess it's been a mess up with the automatic updates.

I think there was also a pulse audio update that fixed up some other issues I was having with sound. I had to manually check for updates, as it didn't seem to spot that there were some available like it normally does.

---

### Post by Rybers on 2010-06-02
> **RickThorpe2006 said:**
> Same problem.  As with gp2x, the sound problem appears to have resulted from Firefox still using a v9 plugin despite having installed v10.  You may need to remove more than one file, however.  The following worked for me:
1.  Uninstall the adobe flash plugin and any related installer packages (I went into the Synaptic package manager and searched on "flash" to confirm.)
2.  Open Firefox, enter "about:config" in the address line.  Scroll down to find the line "plugin.expose_full_path".  Double click that line to set the variable to yes.
3.  Enter "about:plugins" in the address line.  Scroll down to the "Shockwave Flash" section.  Right below the bold header, if your problem is the v9 one, you will see a file location followed by the version of flash.  Open a terminal and sudo rm -f [file location].
4.  Close Firefox, reopen, go to about:plugins.  You may still find a Shockwave Flash section with a different v9 file listed.  Remove that file as well, close and repeat until this doesn't show any v9 flash files.
5.  Reinstall the v10 flash plugin.

Thanks to RickThorpe2006, 
this is the first thing I did about this problem, and solved it!

---

### Post by aeilos on 2010-08-12
Guys, I just want to let you know these solutions worked...which one, exactly, I'm not sure. 

I tried everything and nothing worked. Then I remembered that I had a Firefox addon that let me switch between versions of flash for development purposes. I think it was called Flash Switcher or something similar. Well, after I disabled that, it works. If you have something similar installed, you might want to disable it.

---

### Post by peterVG on 2010-09-03
For me the sound in Firefox suddenly stopped working on my Ubuntu 10.04 install. System sound was working fine elsewhere (e.g. Rhythmbox). Firefox/Flash sound had been working fine for a couple of months. I thought it might be a duplicate Flash install like others are reporting (since Flash video on YouTube was also playing at 3x regular speed). However, that was not the case for me. After reading through some more forum posts I tried changing System -> Preferences -> Sound -> Output -> Internal Audio Analog Stereo (it had been set to HD48x0 audio Digital Stereo (HDMI)). That fixed my audio issue (as well, strangely, the 3x Flash video play speed).

---

