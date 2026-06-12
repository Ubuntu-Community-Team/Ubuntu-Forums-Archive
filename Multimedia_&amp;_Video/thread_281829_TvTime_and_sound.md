---
title: "TvTime and sound"
date: 2006-10-21
forum: Multimedia &amp; Video
---

### Post by lehardi on 2006-10-21
When I quit TvTime sound is still playing - I have to mute it in sound mixer. How to manage TvTine stop sound playback on exit? I have Audigy and WinFast 2000 XP Expert - problem occurs in various Ubuntu editions.
-- 
LeHardi

---

### Post by daller on 2006-10-21
Wow that sound weird!

The TV sound keeps playing?

What happens if you run "killall tvtime" after quitting tvtime?

---

### Post by lehardi on 2006-10-22
It says that tvtime: no process killed - and sound is still playing unfortunately.
-- 
LeHardi

---

### Post by theorem on 2006-11-03
I had the same problem and managed to fix it by doing the following:

1. Open the system tvtime.xml file in Gedit by entering the following command in a terminal
```
sudo gedit /etc/tvtime/tvtime.xml
```

2. Then look for the part of the file that looks like this
```
<!--
    This sets the mixer device and channel to use.  The format is device
    name:channel name.  Valid channels are:
      vol, bass, treble, synth, pcm, speaker, line, mic, cd, mix, pcm2,
      rec, igain, ogain, line1, line2, line3, dig1, dig2, dig3, phin,
      phout, video, radio, monitor
   -->
  <option name="MixerDevice" value="/dev/mixer:line"/>
```
and change
```
value="/dev/mixer:line"
```
to
```
value="/dev/mixer:line1"
```
"line1" may not be the correct channel for your setup, so you may need to try some of the other options.

3. While you're at it make sure that the part of the file that looks like this
```
<!--
    This setting controls whether tvtime should mute its mixer device on
    exit.  This can be used to work around noisy capture cards.
  -->
  <option name="MuteOnExit" value="1"/>
```
is set to
```
value="1"
```
and not
```
value="0"
```

4. Save the file and exit.

Now, if your setup is like mine, you should be able to properly adjust the volume from within Tvtime and the volume should mute between Tvtime sessions.

Good luck!

---

### Post by cblanquer on 2006-11-11
Does any of you know how to get the sound from both speakers ? 
I get only one side, even if both work (I can try simultaneously to play with Totem and the sound is output on both).
I al so noticed that dual TV broadcasts (NiCam) are not selectable so that I get always 1 of the languages by default (actually what I would have called "lang2"). Can both problems be related ?
(TV car is ASUS Dual with Philips decoder SAA7133)

---

### Post by drphilngood on 2006-11-11
I am using TVtime with the same tuner and sound card(audigy 2 platinum & WinFast 2000 XP) as the OP.  My problem is that I get no sound at all.:-k
My version of the tuner has a cable that connects to the sound card's aux input.
Any help would be appreciated.

edit:
Found my fix [here]("http://www.ubuntuforums.org/showpost.php?p=266708&postcount=5").  I hope this helps someone else! :)

---

