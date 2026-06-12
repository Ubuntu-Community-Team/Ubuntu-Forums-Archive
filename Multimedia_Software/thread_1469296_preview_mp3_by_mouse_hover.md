---
title: "preview mp3 by mouse hover"
date: 2010-05-02
forum: Multimedia Software
---

### Post by tommyboy808 on 2010-05-02
im using 10.04, however when i hover over mp3's they dont start playingl like they used to.  In nautilus>preferences i see that the audio is set to preview so i dont get why its not workng?  if any1 can offer me the solution to this, i'd be much obliged.  Thanks.

---

### Post by prshah on 2010-05-02
> **tommyboy808 said:**
> when i hover over mp3's they dont start playingl 

MP3 preview is working fine in 10.04; here are a couple of things you need to checkout:

a) MP3 preview will (by default) only work on local files, not files that are on network locations;
b) It will only work in Icon view (not List view or compact view).
c) Check if sound works at all; when audio preview is running, a small blue "music note" emblem will appear on the file icon in question.
d) check if restricted formats are enabled / installed.

Please post back with more details if none of these tips help.

---

### Post by coffeecat on 2010-05-02
> **tommyboy808 said:**
> im using 10.04, however when i hover over mp3's they dont start playingl 

Do you get the little musical note when you hover the mouse, but no sound? This is what happens for me in my Lucid that started as an Alpha and is now fully updated, even though sound playback is fine otherwise. I didn't notice at which stage it was broken. In a fresh install of Lucid with the final release (on a different partition of the same machine), hover playback is working.

Is your Lucid a fresh install or an upgrade from a development version or Karmic?

Sorry that's not a solution, but I was curious to know if you were getting the same as me. Although a fully-updated Alpha should work just fine (in theory), I always like to do a fresh install of the final in case I'd done something silly to the system in my tweaking during alpha/beta. Which is why I hadn't bothered to investigate this further.

---

### Post by tommyboy808 on 2010-05-02
prshah: they are local files, it's in icon view, when i hover over it the blue icon does appear just no sound, not sure how to check if restricted formats are installed correctly, but it was one of the first things i installed


coffeecat: mines is actually a fresh install, im not sure if it worked initially of if i did something that might have broke it, but yea i was just hovering over an mp3 file and noticed it did not preview but the preview thing is not that important to me honestly, so if it isnt fixed its not a big deal or anything

---

### Post by aceofhertz on 2010-05-05
This is also affecting me as well.  The hover to preview feature was working fine after a fresh install, but at some point (not sure when) something must have happened for it to stop previewing.  I'm not sure what I would have done to cause it to cease functioning properly

---

### Post by Ghost|BTFH on 2010-05-07
Fresh install of 10.04 here, no mods done to the sound, using FLAC instead of mp3, I can verify that the mouse over does not work either.

All formats/drivers are installed that are necessary to play FLAC, mouse over shows the icon change for preview, I have even adjusted preview limitations to include files up to 100mb in size.

Any assistance with this would be nice, as it's one of the best features ever.

Cheers,
Ghost|BTFH

---

### Post by Yellow Pasque on 2010-05-07
If you start nautilus in a terminal, and hover over a file, do you get an error message?

---

### Post by balgaltz on 2010-05-07
Confirming lucid without preview mp3, also started nautilus on terminal, didn't get error messages.

---

### Post by Ghost|BTFH on 2010-05-07
If you can tell me a way to run nautilus in 10.04 via cli without it closing out the line as soon as the window opened, I'd be happy to offer up that information.

---

### Post by Yellow Pasque on 2010-05-07
> **Ghost|BTFH said:**
> If you can tell me a way to run nautilus in 10.04 via cli without it closing out the line as soon as the window opened, I'd be happy to offer up that information.
Hmm. I see. Maybe you could look in ~/.xsession-errors

---

### Post by balgaltz on 2010-05-08
> **Ghost|BTFH said:**
> If you can tell me a way to run nautilus in 10.04 via cli without it closing out the line as soon as the window opened, I'd be happy to offer up that information.
I actually used "sudo" because of that.

---

### Post by meho_r on 2010-05-08
Same here, no sound on hover in Lucid (installed ubuntu-restricted-extras, vorbis tools, mpg321...).

---

### Post by proggy on 2010-05-08
try right click on an mp3 file in your music folder go to properties>open with>choose Rhytmbox see if that works

---

### Post by zedi on 2010-05-09
> **proggy said:**
> try right click on an mp3 file in your music file go to properties>open with>choose Rhytmbox see if that works
I had exactly the same problem; TX to `proggy` it's solved! 
Rhytmbox had muted sound. (sic! - so simple!)
Mine excuse is, I'm not using  Rhytmbox - gmusicbrowser or decibel instead.
BTW, I have audio preview in compact view as well, always had.
PS,
     Ubuntu rocks!):P
PS#2, 
     I'm on a fresh install of Lucid now, not Karmic. Just edited my profile.

---

### Post by meho_r on 2010-05-09
Oh, man, you must've been kidding me?! Yeah, that worked, RB indeed got muted for some reason (actually, not muted when opened, but got muted when I pressed "play"). ](*,) Thanks, proggy.

---

### Post by proggy on 2010-05-10
You`re welcomed :smile:

---

### Post by atari130xe on 2010-05-11
Thanks for the tip, It happed to my friends computer, (Rythmbox muted, etc.) Thanks!

---

### Post by zedi on 2010-05-11
I had exactly the same problem; TX to browsing forum it's solved! 
Rhytmbox had mute sound. (sic! - so simple!)
Mine excuse is, I'm not using  Rhytmbox - gmusicbrowser or decibel instead.

PS,
     Ubuntu rocks!

---

### Post by zedi on 2010-05-11
I had exactly the same problem; TX to browsing forum it's solved! 
Rhytmbox had mute sound. (sic! - so simple!)
Mine excuse is, I'm not using  Rhytmbox - gmusicbrowser or decibel instead.

PS,
     Ubuntu rocks!

---

### Post by dewapur on 2010-05-13
I had the same problem. I currently run amarok instead of rhythmbox. So to enable audio preview (thanks to the forum) I played once with rhythmbox and adjusted the volume then tried audio preview and it worked fine. Previously I removed rhytmbox, so I installed it then removed it again.

---

### Post by mc4man on 2010-05-13
The audio-preview is thru totem (totem-audio-preview), though clearly using rhythmbox to move the volume also works 
(for some reason totem and rhythmbox at any ubuntu release always exhibit some form of misbehavior

---

### Post by DarthBrady on 2010-05-14
> **proggy said:**
> try right click on an mp3 file in your music folder go to properties>open with>choose Rhytmbox see if that works

Thanks proggy! Had all the same problems everyone else did. Rythmbox was just muted. followed your tip, then opened rhythmbox and unmuted it. works fine now.

---

### Post by CrazySat on 2010-06-04
Same problem here today ... Thanks proggy !

---

### Post by immux on 2010-07-11
> **proggy said:**
> try right click on an mp3 file in your music folder go to properties>open with>choose Rhytmbox see if that works

thanks proggy. it's work for me
oh my.. the problem is only mute on RB :D

---

### Post by ArbiterOfTruth on 2010-09-21
Hey thanks a lot! I was getting the same problem. The whole right click & select RhythmBoxz worked. It prompted me to install the gstreamer stuff & the audio preview works now. Thanks again!

---

