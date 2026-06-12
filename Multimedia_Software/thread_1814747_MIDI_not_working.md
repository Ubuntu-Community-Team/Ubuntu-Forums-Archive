---
title: "MIDI not working"
date: 2011-07-30
forum: Multimedia Software
---

### Post by Nob on 2011-07-30
I have Ubuntu 10.10 x64 on Sony VAIO NW130j laptop, it has intel-hda onboard soundcard. It has midi port on itself, midi and keyboard worked fine in windows.

Sound is working fine, except for the MIDI. None of my players are playing midi files. Also I have midi keyboard and I want to get working. With reading bunch of threads here, I installed
jackd1
qjackctl
timidity
fluidsynth
qsynth
rosegarden

I followed this tutorial [http://ubuntuforums.org/showthread.php?t=8736](http://ubuntuforums.org/showthread.php?t=8736) to get jack and fluidsynth to work, and when I press keys on keyboard, in Rosegarden there is change in the input and output notes - which mean that keyboard is working, only not playing any sound!

Devices are connected in Jack like this
Keyboard(in) - (in)Rosegarden(out) - (out)fluidsynth with some soundfont

I tried without fluidsynth, then Jack connects to timidity, but still no luck. 

How do I fix this?

---

### Post by shantiq on 2011-07-30
hi there nob simple way is to do **[the following]("http://ubuntuforums.org/showpost.php?p=10528034&postcount=2")** that is all you need    **[extra info here]("http://ubuntuforums.org/showpost.php?p=10744915&postcount=5")**
best of luck


**ps** as regards playing midi files    simple enter ```
timidity nameofthefile.mid
``` in terminal

---

### Post by Nob on 2011-07-30
Nope, not working. Rosegarden was already setup like that. Like I said, it receives input, it generates the output, but **NO sound** from timidity or fluidsynth. For both keyboard and regular midi files.

ps that is not working as well. loads file, writes the information with no errors, but no sound.

---

### Post by shantiq on 2011-07-30
ok nob just to make sure i copied your image and pointed to where it should all link up   [SIZE="3"]bottom 0[/SIZE] is the one you want on the first box   do not know if you did that  ( looks like you linked with top one of the 0's [COLOR="Red"]it is lit up red on your picture[/COLOR] and that will not work you want the bottom one the last one brought up by timidity -iA) may be worth a try again

also make sure about the order

rosegarden open
then   timidity -iA
then manage midi device setting link up 0 to 0 ([SIZE="3"]bottom one[/SIZE]) 


**also** if it does not click in at first shut it down (you will hear a sound as it closes) then reopen rosegarden and do process again     trust me it works....


good luck:KS

---

### Post by Nob on 2011-07-30
I tried all of those and still nothing.

BTW, in the bottom box, you tell me to connect input to [No port]? But then I will not have input from the keyboard?

And that still does not explain why midi files are not played with timidity. Like it is missing a bank or something. I am sure that Rosegarden works well in receiving and sending signal to timidity, but timidity itself fails to play sound.

---

### Post by shantiq on 2011-07-30
ok   no i do not tell you that look at the arrow again it goes to the one above midi through port zero


  so are you playing back through your keystation?
in which case you need to link your first box output to 14.0
but maybe that is not a possibility
 i do not use those boxes have no experience of them (i just compose on midi and then turn to wav
) ; they are just like keyboards are they?   just for input 

if not ====>


**see suggestion on attached image**

======================================

  **But if you are you saying ```
timidity nameofthefile.mid
``` yields no sound at all?** that seems to be the problem here and it baffles me too since i do not think anything needs to be added to ubuntu to play midi



see i have mine at the moment and i get this reading following test from **[here]("http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/setting-up-rosegarden-for-midi-music-in-linux-ubuntu-8-04-a-697198/#post3408082")** this article might be helpful

```
**ps -ef | grep timidity**
timidity  1440     1  0 07:44 ?        00:01:22 /usr/bin/timidity -Os -iAD
shantiq   3104  1713  0 08:38 pts/0    00:00:00 timidity -iA
shantiq   3156  1713  8 08:40 pts/0    00:07:15 timidity -iA
shantiq   3857  3587  0 10:10 pts/2    00:00:00 grep --color=auto timidity

```


maybe run this  ```
ps -ef | grep timidity
```   see what you get



===============================
also just found this never knew of its existence

```
sudo apt-get install timidity-interfaces-extra

```
```
timidity -ig

```   brings up a nice gui

===============================




In any case
you cannot be far now   wish you the best

---

### Post by Nob on 2011-07-30
So I got some .midi file to play using that timidity gui. But still no sound from keyboard.

I tried too hook it up to Qsynth. It is receiving signal from Rosegarden or Keystation, has connected SoundFonts, but no damn sound. 

:(

This saddens me.

---

### Post by shantiq on 2011-07-30
ok so nothing wrong with timidity and playing midi files it looks like


it is to do with your connection

connecting your keyboard in the right way   probably really simple


back to the Manage Midi Device    and getting those connections/permutations  right  

do not give up it is worth the effort;)


i would also look at what [the guy]("http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/setting-up-rosegarden-for-midi-music-in-linux-ubuntu-8-04-a-697198/#post3408082") said about having too many synths confusing the system maybe not timidity AND qsynth at the same time   see what he says

> Some notes:

I found that when I loaded one of the RG files, it reset the MIDI output to the wrong connection, so I had to go back to main menu > Studio > Manage MIDI Devices > Play devices and change the General MIDI Output device to the right connection again.

**[COLOR="Red"]Note that if you already have TiMidity++ running in the background, then QSynth won't work properly.[/COLOR]** While trying to get Rosegarden working, I ran TiMidity++ once --but after it was done, it stayed running in the background (as root!) and I found that things didn't work any more. It could be running the background without you realizing! You can check if it's running with the command:

ps -ef | grep timidity

If it comes back with only one line that says somewhere "grep timidity", then timidity is NOT running. If the response has more than one line, and one or more lines contain the word "timidity" but not "grep timidity", then timidity is running, and you need to use the command "**[COLOR="Blue"]sudo killall -s9 timidity[/COLOR]**" to get rid of it BEFORE you run QSynth.

In the same way, if the JACK software daemon is running in the background, it can make things confusing (since Rosegarden and QSynth will try to use it). If you know how to use JACK, go ahead. (And also tell *me* how to use it!) (And what are you doing reading this guide if you already know how to use JACK?) Otherwise, you can make sure the JACK daemon software is not running using a similar method:

ps -ef | grep jackd

If it comes back with only one line that says somewhere "grep jackd", then jackd is NOT running. If the response has more than one line, and one or more lines contain the word "jackd" but not "grep jackd", then jackd is running, and you need to use the command "[COLOR="Blue"]**sudo killall -s9 jackd**[/COLOR]" to get rid of it BEFORE you run QSynth.

If you already have a hardware MIDI synthesizer on your soundcard, then you don't need QSynth. I guess you would tell Rosegarden to use that connection under main menu > Studio > Manage MIDI Devices. If it doesn't work, then try it with QSynth anyway.




you are nearly there no doubt     Rosegarden is an act of faith but very rewarding once "tamed"

---

### Post by Nob on 2011-07-30
Wow, it works. I had to kill both timidity **AND** jackd, now Rosegarden goes straight to Qsynth without Jack server at all.

Thanks for the help man :)

---

### Post by shantiq on 2011-07-30
:KS:KS:KS:KS:KS   cool    enjoy  
 (mayhaps mark as solved...)

---

