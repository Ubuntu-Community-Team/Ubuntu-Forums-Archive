---
title: "Can't have my cake and eat it!!!!!"
date: 2013-08-23
forum: Multimedia Software
---

### Post by old_dog on 2013-08-23
Basics first:- HP5780 desktop running 13.04
The problem...........
Recently added "Creative" speakers using USB port ----- Spot On.
Just recently acquired a USB "Creative" webcam and microphone combined.
Using "Hangout" to contact my son, he can see me but not hear me.
So based on posts on here changed /etc/modprobe.d/alsa-base.conf by adding "options snd-hda-intel position index=2" and "options snd-hda-intel position fix=1"
I hasten to add not both at the same time!!!!!
Is that correct?
The result of the above was me losing sound but my son hearing me ....... you name name it  I had various combinations but not ever one that was complete!
I am now back to original on the config file, so microphone not working.
Be aware I'm going to use dirty words now.
Works OK in Windows, my pc is dual boot.
Where do I start, give us a clue
Cheers

---

### Post by mikewhatever on 2013-08-23
Have you tried selecting the USB mic from among the input devices? I don't think Ubuntu does the autoswitch, so:
 - click the speaker icon
 - select Sound Settings
 - switch to Input tab
 - select the second mic if available

A relative of mine has a USB headset with a mic by Microsoft, and that is the way he uses it in Ubuntu.

---

### Post by shantiq on 2013-08-23
well if you run the usb speakers   AND the usb mike and camera combo system might be confused

just while you speak to son    tell **sound settings** that you are using mike/camera combo  for input AND usb speakers for output


 [i have an external soundcard for input and output here but need to tell sound settings when i use Skype otherwise same situation as yours  ==> one way traffic

so flash up sound settings and click on relevant settings]


 [ATTACH=CONFIG]245634[/ATTACH][ATTACH=CONFIG]245638[/ATTACH]    [ATTACH=CONFIG]245635[/ATTACH]


As regards Windows the OS must have been written in a way which says if you do not find it here look elsewhere until it is found

Not so with high customization/freedom in Linux    WE have to do that thinking  ...   Price we have to pay  ...     is what i seem to understand   [i might be wrong]

---

