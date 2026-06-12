---
title: "Bose Companion 5 (USB Audio) Help"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by MonsterX on 2007-01-15
Hello everyone,

I got the Bose Companion 5 usb-audio card/speakers for Christmas.

I now have them working with oss, but some applications don't have sound coming out.  I figure this is because the application is set to use ALSA.  Instead of worrying that each application is set properly I would rather have the speakers configured using ALSA.  Anyone have any experience with these speakers?  

I've also run into the problem where I can't get sound from tvtime anymore.  The sound is coming in via line in on my onboard soundcard, but I can't figure out how to get that sound to come out of my usb audio.  Any ideas how I could do that?

Thanks!

---

### Post by MonsterX on 2007-02-05
anyone?

---

### Post by scientus on 2007-04-07
I also am wondering how to choose the Companion 5 as sound card instead of the onboard.  I'm using Kubuntu and KMix recognizes it as a sound card, but i cant get anything out of it.  Hopefully this will bump this topic a bit.

---

### Post by Rubberducky on 2007-05-03
Bump. Need help getting these to work also.

---

### Post by SchighSchagh on 2007-05-06
I got my speakers to work, just not as well as I'd like them to work.

For those of you that can't even get a sound out of them, here's what I did. Go to System-> Preferences-> Sound. Select USB Audio for all the dropdown menus except for the Sound Capture. I still haven't figured out which setting there will make my mic work, but that's a different, much smaller issue.

Here's my issues: it seems the speakers can only be controlled exclusively by one app at a time. So if I have my music playing, no other app can have sound. My other concern is that I probably need to tell the OS somewhere to treat the Bose speakers as a 5.1 surround sound system, or I lose that effect. The default movie player has an option for that, but it's only for that app, and I need a system-wide setting.

---

### Post by Zimmer on 2007-05-06
> **SchighSchagh said:**
> I got my speakers to work, just not as well as I'd like them to work.

For those of you that can't even get a sound out of them, here's what I did. Go to System-> Preferences-> Sound. Select USB Audio for all the dropdown menus except for the Sound Capture. I still haven't figured out which setting there will make my mic work, but that's a different, much smaller issue.

Here's my issues: it seems the speakers can only be controlled exclusively by one app at a time. So if I have my music playing, no other app can have sound. My other concern is that I probably need to tell the OS somewhere to treat the Bose speakers as a 5.1 surround sound system, or I lose that effect. The default movie player has an option for that, but it's only for that app, and I need a system-wide setting.

[http://ubuntuforums.org/showthread.php?t=434169&highlight=audio+usb](http://ubuntuforums.org/showthread.php?t=434169&highlight=audio+usb)
might help with the mic issue...
I came across these threads searching for USB audio info as I am going to try and plug a Line 6 PODxt effects box into mine and attempt to record using Audacity....
There are many helpful threads and official documents regarding configuring sound for Gnome, requiring the editing of asound.conf  and esd.conf.
Whether they are valid for your USB needs (or Feisty) I do not know...
Regards
Zimmer

---

### Post by tamagotchi on 2007-12-08
Hi, 

This is how I got Amarok and friends to play through the Bose speakers, even though my motherboard has a build in sound card, which is used by default.

The trick seems to be to tell ALSA to use the second (Bose USB) sound card as default card.

$  asoundconf list
Names of available sound cards:
V8235
Audio

$ asoundconf set-default-card Audio

Check out alsamixer. In my case there is only a volume control.

After that Amarok started using the Bose system. 
And I can play sound from different apps a the same time. ALSA seems to take care of mixing the sounds sources together.

Hope that helps, 

Cheers,

-tamagotchi

---

