---
title: "Firefox prevents music playing??"
date: 2009-11-05
forum: Multimedia Software
---

### Post by JamesSmith on 2009-11-05
I have recently noticed (that's not to say it hasn't been happening all along) that whenever I have Firefox/Firefox+Facebook open, I cannot play music through Spotify or Audacious or Rhythmbox or VLC etc.  This only happens if Firefox is open first.

Spotify complains that there is a problem with the sound card
Audacious sits at 00:00 and hangs
Rhythmbox sits at 00:00
VLC looks like it's playing, but there is no sound.

I have read a page that tries to deal with the prob in Spotify, by using ALSA as the sound device and deleting everything in the ...windows\profiles\[username]\App Data\Spotify... dir (i.e. profile settings) and starting afresh. This worked at first but not thereafter.

I don't know whether it is Firefox allround, or just pages like Facebook that have sounds (e.g. FB chat "pop").

Anyone any ideas? It's really starting to bug me! Cheers

*edit:* It's the same problem the other way too: if audacious is playing before I start Firefox, I then don't get any sound from youtube vids or any other page.

---

### Post by JamesSmith on 2009-11-06
bump.

---

### Post by JamesSmith on 2009-11-06
anyone?

---

### Post by kostkon on 2009-11-06
What version of Ubuntu do you have?

---

### Post by JamesSmith on 2009-11-07
9.04

I have Firefox 3.0 and 3.5 installed and the problem occurs with both.  I only have the normal add-ons installed like Flash/Shockwave, Media Playe 10, DivX, VLC, Silverlight, Quicktme etc.
Adacious is conofigured to use PulseAudio, Spotify under Wine is ALSA, VLC is whatever default is.  What is firefox configured to use? Can this be configured and how?  Will it help?

Cheers :)

---

### Post by Truckerpunk on 2009-11-07
I don't know anything about face book, but I used ALSA to make it possible to run multiple audioplaybacks on 9.04. The command in terminal would be: "aoss firefox". Unfortunently for me it looks like ALSA doesn't work on 9.10, so I'm sad that I upgraded. Hope it helps.

---

### Post by erikla2002 on 2009-11-07
> **JamesSmith said:**
> I have recently noticed (that's not to say it hasn't been happening all along) that whenever I have Firefox/Firefox+Facebook open, I cannot play music through Spotify or Audacious or Rhythmbox or VLC etc.  This only happens if Firefox is open first.

Spotify complains that there is a problem with the sound card
Audacious sits at 00:00 and hangs
Rhythmbox sits at 00:00
VLC looks like it's playing, but there is no sound.

I have read a page that tries to deal with the prob in Spotify, by using ALSA as the sound device and deleting everything in the ...windows\profiles\[username]\App Data\Spotify... dir (i.e. profile settings) and starting afresh. This worked at first but not thereafter.

I don't know whether it is Firefox allround, or just pages like Facebook that have sounds (e.g. FB chat "pop").

Anyone any ideas? It's really starting to bug me! Cheers

*edit:* It's the same problem the other way too: if audacious is playing before I start Firefox, I then don't get any sound from youtube vids or any other page.

I have the exact same issue but its not jsut firefox. If I play a song in VLC Spotify won't work for example. 

[http://ubuntuforums.org/showthread.php?p=8261009#post8261009](http://ubuntuforums.org/showthread.php?p=8261009#post8261009)

---

### Post by JamesSmith on 2009-11-07
> **Truckerpunk said:**
> I don't know anything about face book, but I used ALSA to make it possible to run multiple audioplaybacks on 9.04. The command in terminal would be: "aoss firefox". Unfortunently for me it looks like ALSA doesn't work on 9.10, so I'm sad that I upgraded. Hope it helps.

Cheers Truckerpunk. Can anyone confirm this?  When I type "aoss firefox" in terminal I get "The program 'aoss' is currently not installed.  You can install it by typing: "sudo apt-get install alsa-oss".  I've read about the package in Synaptic so I understand, but is Firefox 3.0 really written to still use OSS? If so, it appears that so is FF 3.5 "Shiretoko".

---

### Post by michaelzap on 2009-11-07
The same thing happened to me in Jaunty. If I played sound in any application no other one could do so. It works properly now in Karmic, although I've lost my 5.1 sound and have other problems.

---

### Post by JamesSmith on 2009-11-07
> **michaelzap said:**
> The same thing happened to me in Jaunty. If I played sound in any application no other one could do so. It works properly now in Karmic, although I've lost my 5.1 sound and have other problems.

You're right, I hadn't noticed before but lots of media apps won't play sound at the same time.  Is this a thing with Jaunty then? There must be a fix by now...!

---

### Post by michaelzap on 2009-11-07
> **JamesSmith said:**
> You're right, I hadn't noticed before but lots of media apps won't play sound at the same time.  Is this a thing with Jaunty then? There must be a fix by now...!

It was never fixed for me in Jaunty, but it does work using Pulse Audio in Karmic (although as I said I've only been able to get stereo sound so far).

---

### Post by JamesSmith on 2009-11-07
Sadly, running firefox with aoss doesn't allow other apps to play sound, the problem is still there. :(

---

### Post by Truckerpunk on 2009-11-07
Hmm.. Not sure if this helps. But you could try to run both applications with the aoss-wrapper. Say you were listning to banshee mediaplayer the same time as watching a youtube clip, try to launch firefox with "aoss firefox" and (if it was banshee): "aoss banshee".

---

### Post by JamesSmith on 2009-11-15
In fact, this is not necessarily a Firefox issue, none of the media apps will play together.  I also used to get a "preview" of a music track when hovering the mouse pointer over the file either in nautilus or on the deskto.  That doesn't happen now either.  So what's stopping things being able to output simultaneously?  Any more ideas, please, this is getting a little frustrating now!

---

### Post by andreasj80 on 2009-12-03
Still no fix for this in 9.10?

---

### Post by JamesSmith on 2009-12-03
> **andreasj80 said:**
> Still no fix for this in 9.10?

Do you have this issue as well?  It's still there for me, and it's really irritating.  I don't think the same problem exists in Hardy on my desktop.

---

