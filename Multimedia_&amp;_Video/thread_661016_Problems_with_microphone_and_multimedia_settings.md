---
title: "Problems with microphone and multimedia settings"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by boblevien on 2008-01-07
I seem to be having 2 problems with my microphone...

Am running Ubuntu 7.10.
Have a USB Plantronics headset.

When I run Applications>sound&video>sound recorder I get an error message saying:

Your audio capture settings are invalid. Please correct them in the Multimedia settings.

But (as many people have pointed out on various forums) there isn't a "Multimedia settings" option anywhere.

So, I try the system>preferences>sound - devices tab and select USBAudio for audio playback and capture. Audio works OK when tested - Capture does allow me to hear myself but then throws an error message:

Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

I've followed advice on this forum to run 
asoundconf list

which says:
ICH5
Headset
Live

I've then tried 

asoundconf set-default-card ICH5 and Headset
also
sudo asoundconf set-default-card ICH5 and Headset
but neither makes an difference.

Please can anyone help?

Bob Levien

---

### Post by boblevien on 2008-01-10
Hi,

I going around in circles trying to fix this (and I really need to get the microphone working as I need to use Dragon) so I'm bumping this thread...Bob

---

### Post by roro100 on 2008-02-21
bobleviem, have you solved this problem? I have the same problem with my Sound Recorder.

---

### Post by MRTA on 2008-02-22
so do i...

---

### Post by ranser on 2008-02-23
So do I. It seems the problem is with new update released 3 weeks ago. I have been trying to solve this for the last 2 weeks and nothing so far. I uninstalled/installed alsa driver and no go. Then I uninstalled alsa and installed oss instead and still no go for my microphone. I have noticed that as time goes by less posts get answered in the forums so I guess mostly noobs are visiting these. 
I run Ubuntu Gutsy and except for this problem it runs quite well.

---

### Post by Arrgoss on 2008-02-24
Same problem here... If someone find a solution, please post it. I installed Ubuntu Gutsy/64 one week ago and most of the rest is fine...

---

### Post by roxyisgoofy on 2008-03-07
me too. . . I have also posted this in other forums. Still looking for an answer because I need to record with ubuntu studio

---

### Post by ranser on 2008-03-08
I have found this and it solved my problem (finally):

Comprehensive Sound Problem Solutions Guide v0.5e
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

You'll have to follow through all the steps and eventually alsa should be working fine. If this won't work I don't know what will.:popcorn:

---

