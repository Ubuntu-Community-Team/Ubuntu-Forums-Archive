---
title: "logitech usb headset"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by Scratches on 2007-11-03
Yeah another USB headset post.  Just after I typed in the title, I was shown a list of 5 similiar posts, none of which have a working solution.  Been googling for a few days now and can't find a solution that route either.

So I'm guessing that Rhythmbox is the only software that will play sound through a USB headset, more specifically a Logitech.   I'm using Totem-xine and mplayer doesn't play sound through headset either.

I'm stumped and seems like many others are too.  If anyone has a working solution to this, please, please post it.

Thanks much,

Tom

---

### Post by wombil on 2007-11-03
HI scratches,
I have a plug in logitech headset and get sound in ok but can't speak out.Seemsto be a common problem.
Wombil.

---

### Post by mchaggis211 on 2007-11-05
i have logitech 350 usb headset and gutsy gibbon. sounds wrks in almost everything except for flash.
plz post a solution

---

### Post by aonegodman on 2008-02-05
' BUMP '

Anybody got a working Logitech Headset USB on Ubuntu with Skype?   :)

---

### Post by SiN_AmoR on 2008-02-05
i got a Logitech USB headset too..

totem, rhythmbox works fine..
but Amarok, Audacity and flash from firefox .. all output the sound from the built-in speakers !!

so, i'm waiting for a solution, with ya guys.. :)

---

### Post by papaja1992 on 2008-02-12
hi, 
I also have logitech USB headset. I can 'see' it in volume control, or kmix, but it doesn't play the sound. 

Like you I've been googleing for answer for a long time, but all the things I find, are either about problems with another distributions (e.g. SuSE) or solutions of try-to-recompile-kernel type :/

As I'm lin00b I get completely lost there...

Maybe if everyone has different problems, someone could write an application or driver to solv'em all, huh?

---

### Post by kris kincaid on 2008-02-12
I have a Logitech USB headset that I use with Skype. It is the only one that works for me. I am out of town, so I can't verify my settings. I know I plug it in, then go into the Skype control panel and choose "Logitech USB Headset" as the sound device, the mic, the ringer, etc. 

When I get back, I'll verify everything and report in. 

> **aonegodman said:**
> ' BUMP '

Anybody got a working Logitech Headset USB on Ubuntu with Skype?   :)

---

### Post by ASKorb on 2008-02-13
The following solution worked for me (From [http://ubuntuforums.org/showthread.php?t=543878](http://ubuntuforums.org/showthread.php?t=543878))

"It comes down to getting alsa to use the right card.
Type "asoundconf list"

Then "asoundconf set-default-card INSERTCARDNAMEFROMLISTHERE"

Then alsa has a default card to look for and flash and youtube will work."

---

### Post by aonegodman on 2008-02-13
> **kris kincaid said:**
> I have a Logitech USB headset that I use with Skype. It is the only one that works for me. I am out of town, so I can't verify my settings. I know I plug it in, then go into the Skype control panel and choose "Logitech USB Headset" as the sound device, the mic, the ringer, etc. 

When I get back, I'll verify everything and report in.

Can't wait for report. My Logitech USB Headset does NOT appear as a choice in my Skype options.


I also tried the asound list options and set default sound card.  :(

---

### Post by cdvnz on 2008-05-14
I think by running asound and setting the 'default' sound card, they're actually suggesting you set the sound card that best describes your headset.

so for instance, i used the following to switch to USB logitech

          "asoundconf set-default-card Headset" (pretty certain case is important to with all linux things :P)

to get the mic working, it'll be just the same for the sound but setting the mic to the best match for your headset. how this is done is beneath me of course :)

---

### Post by hoosemon61 on 2008-05-14
> **ASKorb said:**
> The following solution worked for me (From [http://ubuntuforums.org/showthread.php?t=543878](http://ubuntuforums.org/showthread.php?t=543878))

"It comes down to getting alsa to use the right card.
Type "asoundconf list"

Then "asoundconf set-default-card INSERTCARDNAMEFROMLISTHERE"

Then alsa has a default card to look for and flash and youtube will work."

I've got a great one.  I did as directed by the fix above and when I went to Internet Archive to listen to one of the live recordings, the sound came through my speakers, but the volume was controlled by the control on my headset...Guess I'll stick to using it on Windoze for now - bummer.

---

