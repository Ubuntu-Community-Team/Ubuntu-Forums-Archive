---
title: "firefox will not play audio through USB headset"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by mjkelly on 2007-09-05
Just like the title says pretty much. I can play system sounds through the usb headset after it was changed in the prefernces > sound option.

Also, XMMS will play MP3 files just fine through my USB headset so i know its not the headset. Firefox does play audio just fine through the stock speakers on the laptop, unfortunately they suck and i need to use my headset for decent audio.

So how can i direct Firefox to use my USB device over the built in speakers?

Im using Feisty with a plantronics usb headset. Ive searched all over the forums for a solution but so far no luck.


[SOLVED]
It comes down to getting alsa to use the right card.
Type    "asoundconf list"

Then "asoundconf set-default-card INSERTCARDNAMEFROMLISTHERE"

Then alsa has a default card to look for and flash and youtube will work.

---

### Post by pappan on 2007-09-22
thank you very much for posting the solution ! I had been searching for this solution for many months.. :)

---

### Post by ideas1 on 2007-09-25
thanks i just upgraded to feisty and it broke my usb head set this worked great.:popcorn:

---

### Post by tehceej on 2008-04-17
Getting sound is one thing, using the mic on a logitech 350 is another..
It was enough to make me reinstall XP I can tell you that.

---

### Post by cdvnz on 2008-05-14
awesome, that fixed the problem. :)

do you know of any intuitive method for ubuntu to recognise the headset being added and immediately update the config? or is it a manual edit or script we'll need to run

also, volume control on headset has no effect. gimmick i know but sometimes very useful

---

### Post by cdvnz on 2008-05-14
nevermind, found a hotswap script doco here [http://alsa.opensrc.org/index.php/Hotplugging_USB_audio_devices_(Howto](http://alsa.opensrc.org/index.php/Hotplugging_USB_audio_devices_(Howto))

Note: for ALSA only

---

