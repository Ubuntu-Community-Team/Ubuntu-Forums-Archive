---
title: "Solution for multiple sound cards in ALSA + non-delayed flash sound in firefox"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by dr.adrian on 2008-02-07
This isn't really a HOW-TO thread as such, just a note of how I solved my Ubuntu sound problems that may be of benefit to others. **The final solution was actually quite simple so don't be intimidated by the wall of text that follows!**

I just recently upgraded to Ubuntu 7.10 Gutsy Gibbon (kernel 2.6.22-14-generic, AMD Athlon(tm) XP 3000+, 1 GB or RAM) from Feisty and found I was getting no sound from my PCI soundcard (SB0400 Audigy2 Value). In addition to the PCI sound card I have a motherboard sound card installed (NVidia nForce 2). I had this problem before, and the old solution was now outdated.

The problem is best described by this ** [ALSA wiki article]("http://alsa.opensrc.org/MultipleCards")**:

> A problem arises when there are multiple devices.

On modern GNU/Linux systems, udev takes care of discovering hardware and loading/unloading Alsa. There is one drawback to udev. Udev will load Alsa modules in an undefined order. After each reboot or plugging/unplugging a device, there is no guarantee that a device is renamed using the same hw:x,y numbers. For example, if you have two USB devices on your systems, for example an Audeon USB and an Edirol UA-25, after each reboot, a card can be "hw:0,0" and the other "hw:1,0", each time randomly. 

[COLOR="DeepSkyBlue"]**SOLUTION FOR SOUND CARD ROULETTE:**[/COLOR]

1. Enter this into your terminal
```
less /proc/asound/modules
```

You should see a list of sound modules roughly corresponding to different sound devices 

```
 0 snd_intel8x0
 1 snd_emu10k1
 2 snd_mpu401
```

mpu401 corresponds to a midi processing unit, emu10k1 to the Audigy sound card, intel8x0 to the motherboard sound card. Since I'm using the Audigy sound card I need snd_emu10k1 to be in the 0 position.

Before doing this I made sure that in System -> Preferences -> Sound under  "Default mixer tracks" my Audigy Value 2 card was selected (it wasn't). I also did this just in case since there's a couple of posts recommending it as a solution (didn't work on its own for me though)

```
sudo asoundconf list #gets a list of sound devices
sudo asoundconf set-default-card Audigy2 #your preferred default device from the list 
```

Then most importantly I edited alsa-base

```
sudo gedit /etc/modprobe.d/alsa-base
```

I left everything as is but added the following two lines at the end of the file:

```
options snd-intel8x0 index=-2
options snd-mpu401 index=-2
```

This prevents the drivers associated with the MIDI unit and motherboard sound card from grabbing index 0 (default).

I reboot and behold, sound is back. I reboot again to make sure it wasn't just luck.

I start Firefox go to YouTube and other websites with Adobe Flash content and find the sound isn't working. I had this problem before, but once again the solution is now outdated.

[COLOR="DeepSkyBlue"]**SOLUTION FOR FLASH SOUND PROBLEMS:**[/COLOR]

Almost every thread I found that dealt with the problem recommended using **[using  the libflashsupport deb from SendDerek&#8217;s Blog]("http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/")**

Well it worked for me too, but not quite right. Sound in every Flash or YouTube video I played was noticebly delayed. In the end removed libflashsupport.

The problem was some old config files ~/.asoundrc and ~/.asoundrc.asoundconf, which should have been deleted. If you don't feel comfortable deleting the files rename them:

```
mv ~/.asoundrc .asoundrc.deleteme
mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.deleteme
```

After restarting Firefox the flash problem was finally fixed, with no annoying delays!

Note: I tried installing the latest Flash player release. This didn't fix the problem and I don't recommend this, but here are the steps anyway:

**[COLOR="Red"]<MOST USERS DON'T NEED TO UPGRADE FLASH>[/COLOR]**

I removed flashplugin-nonfree v9 r48 using Synaptic Package Manager. I then downloaded the latest flash plugin RPM from Adobe and used alien to convert it to a deb:

```
sudo apt-get install alien
sudo alien -k flash-plugin-9.0.115.0-release.i386.rpm 
```

I installed the resulting flash-plugin_9.0.115.0-release-1_i386.deb by double clicking on the file (I prefer GUIs; make sure Synaptic is closed).

I then setup the proper symlinks, etc using

```
cd /usr/lib/flash-plugin/
sudo ./setup
```

After logging out from Ubuntu and logging back in (yeah you have to do this) I confirmed the plugin installation by typing about:plugins into the Firefox address bar

**[COLOR="Red"]</MOST USERS DON'T NEED TO UPGRADE FLASH>[/COLOR]**

---

### Post by tomjennings on 2008-02-16
Thanks, this worked great for me.

My problem was, I have a machine dedicated to music production, with an M-Audio 2496 card attached to two (LOUD!) powered speakers, a USB audio card for headphones, and the built-in sound card, and upon boot the system would assign card0 to the M-audio -- the Ubuntu boot-up song played at full blast 300 watts/channel is Not Good.

Card0 is now mapped to the built-in, and used for system sounds and casual browser use. The fancy-pants cards mixxx and jackd know about. The world is a better place.

---

### Post by thextal on 2008-03-02
Thank you very much! This solution worked for me, and I fortunately had no problems with flash to begin with. :)

I am very glad I came across this after blindly mucking around with gstreamer-preferences and nearly breaking everything.

One possible correction to your how-to follows:
> **dr.adrian said:**
> ```
sudo asoundconf list #gets a list of sound devices
sudo asoundconf set-default-card [COLOR="Red"]**snd_emu10k1**[/COLOR] #your preferred default device from the list 
```

I believe you meant to type "snd_emu10k1" instead of "Audigy2".  Anyhow, I followed these instructions, swapping your values for those of my my PCI and onboard sound cards, and everything works! Thanks again, doc!

---

