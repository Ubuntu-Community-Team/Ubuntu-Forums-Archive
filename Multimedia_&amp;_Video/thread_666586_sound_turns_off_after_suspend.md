---
title: "sound turns off after suspend?"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by at0myx on 2008-01-13
Im having strange issues with my sound.  It turns off after a suspend and I have to restart to bring it back.  Is the sound card "powered off" and not brought back or what?

EDIT:  I have a Sound Blaster Audigy SE.

---

### Post by at0myx on 2008-01-14
Bump!

---

### Post by at0myx on 2008-01-16
Does no one have a response for this?

---

### Post by mjziegle on 2008-01-18
Me too ..

---

### Post by wlgyyk on 2008-01-18
Me too!

---

### Post by at0myx on 2008-01-19
Ok...I guess no one can help with this problem.  :(

---

### Post by Plaid Phantom on 2008-01-19
I have the same problem, so if someone could help, I'd appreciate it.

I'd try to figure it out myself, but I really don't know where to start.

---

### Post by at0myx on 2008-01-20
> **Plaid Phantom said:**
> I have the same problem, so if someone could help, I'd appreciate it.

I'd try to figure it out myself, but I really don't know where to start.

I know in windows there was a checkbox that mentioned allowing the computer to turn off a device to save power.  I am wondering if the same is happening here but I looked and couldn't find anything.  Maybe I could access device options with the terminal but I am not familiar with the terminal commands yet...

---

### Post by neatokino on 2008-01-20
for what it's worth, I have the same problem.  Everything else seems to work ok after suspend, though, which is better than it used to be....

---

### Post by at0myx on 2008-01-21
> **neatokino said:**
> for what it's worth, I have the same problem.  Everything else seems to work ok after suspend, though, which is better than it used to be....

I guess it's not an easy fix

---

### Post by Shmargin on 2008-01-21
Yeah, I was having the exact same problem and was having it almost the same time as you, you started this thread right around when i came in to start one :) I'm using an Audigy 2, but was getting the "working at first, now nothing" thing. [This guide]("http://ubuntuforums.org/showthread.php?t=205449") helped a ton:
[URL="http://ubuntuforums.org/showthread.php?t=205449"]
http://ubuntuforums.org/showthread.php?t=205449[/URL]

I'll tell you what part of it I used, since its a huge overwhelming guide, I did this first, to get my sound working again:

[B]Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop
[/B]

But then, it wanted to make my on board sound from my mother board the default sound device, but my on board sound is fried, so I had to do this, to make it work for me:

[B]
Configuring default soundcards / stopping multiple soundcards from switching

Note: This section assumes that you have installed each soundcard properly.

    *
      In a shell, type
      Code:

      cat /proc/asound/modules

    *
      This will give the the name and index of each soundcard you have currently. Make a note of the names, and decide which one you want to be the default card.

    *
      Now type
      Code:

      sudo nano /etc/modprobe.d/alsa-base

    *
      At the very end of the file, add the following (assuming you have 3 cards with module names A, B and C and you want to have them in the order CAB)

Code:

options snd-C index=0
options snd-A index=1 
options snd-B index=2

[/B]

Then after that I used this part of the guide just in case:

[B]Saving Sound Settings
Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do
Code:

sudo alsactl store 0

or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1. Many thanks to xpix for trying this out.- [/B]

Check the [link]("http://ubuntuforums.org/showthread.php?t=205449") to the [guide]("http://ubuntuforums.org/showthread.php?t=205449"), for proper formatting and all the details, but those are the steps I used to fix MY problem, hopefully yours can be fixed as easily

---

### Post by at0myx on 2008-01-21
Mine simply requires a reboot for the sound to work again,  It isn't permanently broken but maybe I can try it out (I disabled my onboard sound in the bios so I wouldn't have a conflict  like you had).

Thanks

---

### Post by Shmargin on 2008-01-21
Well, I'm not totally sure, but that last thing I did (I'm still a Linux noob, apologies for me referring to steps as "things" and "that doohickey") says that it saves your sound set up and loads it up every time you boot, but yeah, thats weird.

Check that guide and maybe do all the steps even if its not exactly you're problem, thats what I did to get mine back to functioning properly.

---

