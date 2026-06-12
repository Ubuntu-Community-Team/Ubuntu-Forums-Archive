---
title: "Firefox Audio Problems"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by dean20007 on 2007-06-03
Hi 

I am using Logitech V20 USB speakers and now have them configured for most applications. However, when viewing youtube videos etc in firefox I get no audio. This seems like a configuration issue i.e. I have set the other applications to use Logitech USB, but I can't suss out how to tell firefox to do the same

Additionally I have tried to set firefoxrc  to the suggested "aoss" but still nothing. I think it may still be looking at the sound card rather than the USB speakers

Any help would be greatly appreciated.

Cheers

---

### Post by mohnkern on 2007-06-04
Based upon my imperfect understanding of Ubuntu/Linux Audio and Flash
-------------------------------------------------------------------------------------------

I see the same problem, but not just with a Logitech USB headset (which I have) but any sound.  It's my understanding it's not an issue with Firefox, it's the Flash plugin for Firefox, which isn't doing sound correctly.

I don't know whether there's a workaround (If there is I'd love to hear it), it may just be a matter of waiting for the plugin to get updated.

---

### Post by claytor on 2007-06-06
I am not sure this will help (since I have been using linux **(ubuntu studio 7.04)** for approx. 5 hrs), but if I have a JACK control interface connected, all my other audio (including movie and youtube audio) will not work.

As long as I don't have the JACK audio server connected, all other audio seems to work...

Seems to work the other way too...if I have any other audio in a browser or program running, then I am unable to start the JACK server...

Again, I don't know if this will help or not...

I am nub, watch me learn...

---

### Post by mohnkern on 2007-06-06
You may be right, however, more data is that I plugged in a SB Live sound card this week, and the Flash audio is now working.  (System updates to Firefox happened as well).

It's possible updating to the most recent update of firefox would solve the problem.  Also, running a "real' sound card (as opposed to using on board) might do it, even if it shouldn't.

---

### Post by satbunny on 2007-06-06
I also have this problem, I have the latest Firefox and the latest Flash plugin but no sound at all on YouTube.

---

### Post by mohnkern on 2007-06-06
Can you go to the terminal window and do:

ps -ef | grep jack

and see if jackd is running?

---

### Post by satbunny on 2007-06-07
Yes, I got this:

thomas    5271  5248  0 18:46 pts/0    00:00:00 grep jack

How do I turn it off and what effect would it have on my USB headphones?

---

### Post by Mujaheiden on 2007-06-13
Same here. My [onboard soundcard]("http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1115409") doesnt work in ubuntu, so i use an usb audio device instead.

Most apps  works fine, only i assume flash is still streaming to the built in device, so i cant hear a thing.

Im gonna try to disable the onboard sound in BIOS.

EDIT: Nope, no avail.

---

### Post by dean20007 on 2007-06-15
I managed to fix this. From another post (I forget which one unfortunately) I managed to set the USB card as the default rather than the on board sound card. YouTube, flash etc work a treat now

---

### Post by Mujaheiden on 2007-06-18
nice, thanks for the tip :sad:

---

### Post by VortexICS on 2007-07-11
It would be nice to tell us how you did, I am having the same problem... thanks !

---

### Post by dean20007 on 2007-07-12
I have done some digging around and it was this how-to I eventually used to allow me to order my sound cards

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

hope it helps

---

### Post by scuffster on 2007-10-30
> I managed to set the USB card as the default rather than the on board sound card.

how do you set it as the default card?

---

### Post by dean20007 on 2007-10-31
This part of the HOWTO is about setting up default cards

```
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
options snd-A index=1 options snd-B index=2


```

---

### Post by cyli on 2007-11-26
There is another [how-to on getting Flash to work]("https://help.ubuntu.com/community/RestrictedFormats/Flash") that says:

> 
External soundcards

If you have an external soundcard (e.g. a USB sound device) you will have to explicitly select it as default.
```

         $ asoundconf set-default-card "name of soundcard"

```        

...where your "name of soundcard" is seen in square braces in the output of:
```

         cat /proc/asound/cards

```         

Running the asoundconf command as a user will make the change for that specific user. Running it as root will not make the change for all users.


You can also get a list of your device names by typing asoundconf list.

---

### Post by John9537 on 2007-12-02
cyli's find worked for me! Thanks :)

---

### Post by daviddowney2 on 2008-05-19
Hi,

I have a Trends ud-10.

When I installed it, I set up the System-Preferences-Sound for usb audio, but it wouldn't work in the browser.

I went to Applications-Accesories-Terminal and did a asoundconf list and it listed the soundcards as sb and default.  I then did a sudo asoundconf set-default-card default.

It works now.

---

