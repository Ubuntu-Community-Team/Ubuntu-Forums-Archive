---
title: "Recording from LPs (records)"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by mrmark24 on 2007-07-16
Hey everybody,

With Windows XP, I was able to record my records, or LPs, onto my computer and convert them to digital format.  Now, I'm using Ubuntu almost exclusively (shame me later :) and I get sound through the speakers, but Audacity can't or won't get the signal... In the preferences part of Audacity, there are drop-down menus for "OSS" and "ALSA" mixers; if that needs to be set one specific way, what is it, because I've tinkered with it and couldn't get it to get a signal.

I did read another post on this subject, which said to try plugging the line coming out of the record player into the "line in" port (I previously had it in the "mic" port), so I did and still get sound, loud and clear, but neither Audacity nor ARWizard will recognize a signal, even though it's blasting through my speakers.  Can anyone help me out here???

Thanks,
mrmark24

---

### Post by meanmrmustard on 2007-07-27
Bump

---

### Post by marty0 on 2007-08-13
Bump bump bump.

I'd like to know too although I haven't gotten this far yet. One of my primary uses for the computer is recording my old LPs (the other is genealogy).  Anyone with insight/experience on software tools???

---

### Post by ltk5 on 2007-08-18
This is just a wild guess, because I'm also trying to get Audacity to record  - though in my 
case line out :)

Have you tried installing the latest (beta) version of Audacity. Then, check if it uses alsa and not oss
, also check the sound mixer...
I'm very confused about everything, cos I've been playing with it for hous now :D...

Ok. maybe this is the solution for you: [http://ubuntuforums.org/report.php?p=3194988](http://ubuntuforums.org/report.php?p=3194988)
It helped me, though I got some high-trebled signal, but still  I got it.

---

### Post by BLTicklemonster on 2008-07-15
I can get sound using my mic jack, but not the input jack.

I want to record some of my LPs but am stumped.

---

### Post by timcredible on 2008-07-15
i've done this with audacity - i remember having to turn the mic volume up because the default was so low i thought there was nothing coming through, and i changed it to stereo (mono is default).  audacity also has a filter that will let you 'show' it a pop on the recording, and then it will remove all pops from the recording, which was very useful for me.

amusing aside - i couldn't find the power cord (non-standard) for my turntable since i hadn't used it in years, so I cut off the end of a standard power cable and manually twisted the copper around the power leads on the turntable and secured it with duct tape.  Red Green would have been proud.

---

### Post by snowpine on 2008-07-15
Hi guys, most turntables (unless they are a newer USB turntable designed for that purpose) can't be plugged directly into your computer. You should plug the turntable into the Phono input on your reciever, then the Aux or Tape Out from the receiver to your computer's sound card. You can also buy a USB phono preamp for this purpose.

The signal coming out of a turntable is very different than the signal from a tape deck or CD player, and won't sound good plugged directly into your computer (it will be very quiet, distorted, and trebly).

---

### Post by BLTicklemonster on 2008-07-15
Ahhh, or could I use a preamp?

---

### Post by snowpine on 2008-07-15
> **BLTicklemonster said:**
> Ahhh, or could I use a preamp?

Yes, I would recommend a phono preamp. Older a/v receivers usually have them built in (as part of the "phono" input), plus there are many stand-alone phono preamps, and even usb phono preamps. You don't have to spend more than $50-100 (though there are expensive audiophile ones of course).

There are two problems with phono signals. One is the RIAA eq curve. If they pressed LPs with "flat" eq, phat bass lines would require a huge groove (pun intended). So they cut the bass during the mastering process, and then the RIAA eq in your phono preamp boosts it back up. Now, I think Audacity has an RIAA plugin under Effects-->EQ to solve that problem. 

However, the second problem is that turntables have a different "impedance" than a line in on your computer. Simply speaking, the signal isn't hot enough. If you have an excellent sound card that is very sensitive and has a good signal to noise ratio, you may get acceptable results if you turn the gain way up. However, you will get the best results if you use a "real" phono preamp to match the impedences. Vinyl sounds truly wonderful when played through the correct equipment.

Hope that helps!

(edit: just to clarify, a phono preamp solves both the impedance and RIAA EQ issues, so don't use Audacity's EQ curve in addition to a phono preamp, or you'll be double-boosting the bass. :))

---

### Post by BLTicklemonster on 2008-07-15
I just so happen to have a preamp sitting riiiight over there.

Thanks for your help!

---

