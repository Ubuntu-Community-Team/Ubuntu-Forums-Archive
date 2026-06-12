---
title: "Devede menu problem"
date: 2012-05-03
forum: Multimedia Software
---

### Post by Ghost_Mazal on 2012-05-03
Lo All ,

I have a problem with Devede. It just keeps crashing with the error "unable to create menu" I have tried various different options on the menu but nothing helps.

If I create the dvd without a menu then it works and builds the dvd. But I can't work without menus. The dvd must have menus.

Anybody else had this problem before and know how to fix it ?

Thank you

---

### Post by colin-m on 2012-05-06
This tip I found in the Ubuntu forums, fixed the DeVeDe menu crash problem for me;-

Open a terminal and enter the following
sudo add-apt-repository ppa:jon-severinsson/ffmpeg
sudo apt-get update
sudo apt-get upgrade

If you haven't installed ffmpeg, then replace
sudo apt-get upgrade with sudo apt-get install ffmpeg

If you prefer not to usse PPAs, another fix is to open DeVeDe and select 'Preferences'  and uncheck the 'Use FFMPEG instead of Mencoder' box.

I hope that one of these tips fixes the problem.

---

### Post by jromer on 2012-05-07
Installing this PPA worked for me. Thanks!

---

### Post by Ghost_Mazal on 2012-05-08
I Just unchecked the "use ffmpeg" option in preferences and that solved the problem for me thanx.

---

### Post by colinpat on 2012-05-09
I also unchecked the "use ffmpeg" option and the menu system worked.
I then upgraded from the Ubuntu installed ffmpeg 4:0.8.1 to 4:0.10.2 and then ran DeVeDe again with the "use ffmpeg" option selected and the menu system also worked this time.

---

### Post by veroslav on 2012-05-09
EDIT: Nevermind my post, didn't see the PPA posted right above, sorry!

Regards,
Veroslav

---

### Post by OzzyFrank on 2012-05-09
> **veroslav said:**
> Nevermind my post, didn't see the PPA posted right above, sorry!

Hi buddy. Did this fix any issues?

---

### Post by veroslav on 2012-05-10
Hi, OzzyFrank!

I can gladly confirm that it did! Added the PPA and upgraded ffmpeg yesterday, works as a charm! The menus are visible again and the playback doesn't stutter :)

For me, the problem is resolved. Will keep an eye on DeVeDe forum however, as I am still unsure whether it is ffmpeg or mencoder or DeVeDe related problem originally.

Thanks.

Kind Regards,
Veroslav

---

### Post by OzzyFrank on 2012-05-11
> **veroslav said:**
> Added the PPA and upgraded ffmpeg yesterday, works as a charm!

I haven't tried it yet, back I can tell you it KILLED my tovid GUI! I can't encode anything with it now. In case you're wondering why I use 2 programs, besides the fact earlier DeVeDe only used Mencoder, and I prefer FFMPEG coz of the smaller files sizes, tovid GUI lets you pick Quality, meaning 10 might give you an output of 1Gb - 1.5Gb for a 45 min episode, while setting it to 8 would mean between 600Mb and 1Gb. Some shows I left at 10, but increasingly used 8 because that would mean between 4-8 episodes per disc. In DeVeDe there is no reliabilty in estimated filesizes, so I stuck with tovid GUI coz 1) I could pretty much guess the size of the output 2) I could then add them up and correctly know how many will fit on a disc once authored in DeVeDe.

I know this stuff up is because of changes in FFMPEG, and I'm still using an earlier tovid GUI (0.31 - in 0.33, todisc GUI got renamed as tovid GUI, and not only is it nothing like the former, the interface is ghastly and thoroughly confusing!). Still not happy though, hehe...

---

### Post by veroslav on 2012-05-11
Sorry to hear about your problems with tovid GUI, OzzyFrank :(

I am no video editing expert by any means, I am just using DeVeDe for authoring, as I use VOB files as input to DeVeDe and thus no encoding is needed.

What I usually do is that I have some dvd footage already but some of it might be filled with commercials or spread across multiple dvd:s.

So I import the VOB:s in AviDemux and edit them, exporting to a single VOB I want to make a dvd of. I do this from within DeVeDe, where I also create custom menu and add menu music. Always worked perfectly until 12.04.

Do you see any benefits for me in using tovid GUI? I installed it out of curiousity and it looks a bit advanced.

I also apologize for hi-jacking the thread with an irrelevant discussion about other stuff.

Regards,
Verolav

---

### Post by izombie666 on 2012-05-19
Sorry to say, none of the DEVEDE fixes have worked for me.  Now it is worse. It won't even covert the file.  Before it would convert the file but not play on my PC. Now it does nothing.  Any ideas what the issue may be??????

---

### Post by izombie666 on 2012-05-20
Fixed the problem.  It was really dumb.   I went back to the terminal and loaded the info as directed and everything appears to be working well.  Thanks!

---

