---
title: "Tip to Boost Sound on Laptop for Video Playback"
date: 2015-01-18
forum: Multimedia Software
---

### Post by shantiq on 2015-01-18
This is really for ubuntu beginners although it might be of use to older users who have never come across this

If you use a laptop [which I personally had never done until recently on Ubuntu] you will find the sound volume on dvd and video playback can be so low as to be quasi inaudible.

Of course you could take a lead to a stereo or use speakers but often this is not feasible

SO EASY WAY ROUND

&#9679;   Use VLC as the player and boost sound there to 125%  - this will already improve matters
&#9679;   Install Pavucontrol ```
sudo apt-get install pavucontrol
```
&#9679;   Open pavucontrol click on Playback and push volume cursor to maximum or to what you need this will surely be enough now

see here >>  [http://s20.postimg.org/o4h2hvhqz/volume_boost_2.png]](http://s20.postimg.org/o4h2hvhqz/volume_boost_2.png])

&#9679;    If you want to make this permanent do the boost on Output Device instead of Playback and leave it like that Your sound will be permanently boosted   then control sound from players if playing music

---

### Post by Gaylaird_Culbreth on 2015-01-18
> **shantiq said:**
> This is really for ubuntu beginners although it might be of use to older users who have never come across this

&#9679;&#9679;&#9679;    If you want to make this permanent do the boost on Output Device instead of Playback and leave it like that Your sound will be permanently boosted   then control sound from players if playing music

This has never survived reboot for me (and I reboot daily). Please let me know how to make the audio boost on Output Deice stick if possible. Thanks.

---

### Post by shantiq on 2015-01-18
well GC i am using this on a Mac laptop with Ubuntu 14.04   and i am pretty sure it has not moved since i set it to maximum volume
maybe it is different on a PC  no doubt someone will come along with a permanent way to fix that for you  ...    i do not know where the changes are kept on the system as yet   ....    any of you learned chaps?


[B]EDIT


[/B]looking around I found [this]("http://askubuntu.com/questions/97936/terminal-command-to-set-audio-volume") might be of use [i have** not** tested it] if it remains after reload and there must be a way to make that constant

[COLOR=#333333][FONT=UbuntuRegular]You can do it using PulseAudio itself . If you have only one soundcard you may use [pactl]("http://manpages.ubuntu.com/manpages/trusty/en/man1/pactl.1.html"):[/FONT][/COLOR]
```
pactl set-sink-volume 0 +10%

``` [COLOR=#333333][FONT=UbuntuRegular]This makes the volume 10% up. 
If you want it 10% down:[/FONT][/COLOR]
```
pactl set-sink-volume 0 -- -10%

```[COLOR=#333333][FONT=UbuntuRegular]If you need to rock the entire place:[/FONT][/COLOR]
```
pactl set-sink-volume 0 150%
```



[B]EDIT 2

[/B]to do with pavucontrol settings remaining after a reboot i tested it on my PC and it remained even on one specific player [vlc]  so maybe it is meant to remain once set; something might be resetting your setup which should not  and again sorry no clue as to what ...

---

### Post by Gaylaird_Culbreth on 2015-01-19
thanks shantiq "pactl set-sink-volume 0 +x%" survives reboot!

---

