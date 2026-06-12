---
title: "Sound problems with GNOME after Feisty Fawn distro upgrade"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by Ali1985 on 2007-04-20
Hey folks,

I'm quite satisfied with the whole distribution, but since i upgraded to Feisty Fawn today I can't figure out how to make sound work in Gnome.

Situation as follows:

I'm the owner of an Audigy LS sound card, in linux better known as CA0106. Sound works well in some applications that (i assume) not get their sound configuration from gnome, like amaroK or Kaffeine. Both play sound well, but Gnome system sounds for example dont work. I experienced the same sound problems in some games (OpenTTD, PlanetPenguinRacer).

Configuration as follows:

In the audio center of Gnome (in german distribution just known as "Audio") all settings are at auto-detectm and mixer device is CA0106. If i manually switch the playback device to "alsa" and then play a test sound i get the following error:

audiotestsrc wave=sine freq=512 ! audioconvert  ! audioresample ! gconfaudiosink: Unable to open the resource for writing (this is translated to englisch by myself, for i am a user of a german distribution). 

Nevertheless, If I play a test sound with autodetect on I hear the frequency sound, but as I said, system sounds don't work.

Just to anticipate the question: All relevant channels are unmuted and at proper volume ;-)

Thanks for your help,

Sebastian

---

### Post by battletux on 2007-04-20
I have a similar issue too. The differance for me is that I did a clean install of 7.04 using both the desktop i386 cd and the alt. i386 cd and for each of them the sound output from my audigy player is really poor. I dont get any errors, I just get garbbled sounds, as if the speakers are underwater.

Any Ideas?

---

### Post by battletux on 2007-04-20
Sorry, just found the fix:


[http://ubuntuforums.org/showpost.php?p=2452588&postcount=4](http://ubuntuforums.org/showpost.php?p=2452588&postcount=4)

---

### Post by beow on 2007-04-22
The answer is in that post but in very terse form. Since many seems to be affected by this problem I will try to detail the solution:

1. Open a Terminal (from Application/Accessories meny)
2. write

alsamixer 

after the prompt (with $ sign)

3. A text mode graphics with volume bars etc comes up in the terminal

4. Can't use your mouse there, so go with your right arrow until 

"Audigy Analog/Digital Output Jack"

appears under "Item:" in the upper left corner

5. Press the "M" key to toggle the setting to [Off]

6 Quit alsamixer by pressing Esc

Thats it! :popcorn:

---

### Post by ..::benjamin::.. on 2007-04-22
hi Beow,

I had the similar problem and your solution really helped me out ! Thanks!

Ben

---

