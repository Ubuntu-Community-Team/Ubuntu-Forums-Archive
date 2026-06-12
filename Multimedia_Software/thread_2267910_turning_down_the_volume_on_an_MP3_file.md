---
title: "turning down the volume on an MP3 file"
date: 2015-03-04
forum: Multimedia Software
---

### Post by grizdog on 2015-03-04
Hello,

The thread title pretty much says it all, I want the default volume on this mp3 to be lower.  I downloaded audacity and tried exporting the file after loading it and lowering the output volume, but that didn't work.  

This part probably isn't necessary, but just in case you want to know why I want to do this - Until now, I have always used the preloaded tones on my phone for the default ring, individualized rings, notifications, alarms, etc.  Then I found a ringtone I wanted to use as the default ringtone (an mp3 file).  No problem installing it, but it is so much louder than the preloaded ones that I either have to turn the volume so low I can barely hear any of the other tones when they ring, or up so that one blares out far too loud.

Thanks for any help.  I don't do much with multimedia editing, so I may need some very rudimentary instructions.

Thanks.

---

### Post by shantiq on 2015-03-05
hi grizdog    you can do this with SoX an easy to use command-line program

```
[COLOR=#555555][FONT=consolas]sudo apt-get install sox libsox-fmt-all[/FONT][/COLOR]
```


now your program is installed

run this in your terminal:


 ```
sox Test.mp3  Testlowsound.mp3 [COLOR=#800000]gain -20[/COLOR]

```

-20 is good but you can also go to -25 -30   whatever you want and you can go + as well of course if you need to



also to test the volume you can use SoX in this way too when you are editing


```
play Testlowsound.mp3
```

---

### Post by Bucky Ball on 2015-03-05
One easy answer: Audacity. Install from repos (SCentre, Synaptic or terminal)> launch> load the file> Effect tab> Amplify and take the volume down. 

When happy, export as an MP3.

---

### Post by Bucky Ball on 2015-03-05
One easy answer: Audacity. Install> launch> load the file> Effect tab> Amplify and take the volume down. 

When happy, export as an MP3. 

Audacity is great for making your own tones, too. Easy to edit a sound file once you get your head around the software (and that doesn't take too long). 

Good luck. ;)

---

### Post by grizdog on 2015-03-05
Thanks guys.  Since I already had audacity installed, I used that, but I also appreciate the SoX response.

Thanks again.

---

### Post by Bucky Ball on 2015-03-05
Good news you got somewhere. I love Audacity. The audio equivalent of a swiss army knife! ;)

---

### Post by shantiq on 2015-03-05
ha Bucky this how SoX describes itself   ::]]   
> SoX(1)                                                          Sound eXchange                                                         SoX(1)

NAME
       SoX - Sound eXchange, the Swiss Army knife of audio manipulation





PS   grizdog    **audacity is ace**    you can add more plugins [this way]("http://ubuntuforums.org/showthread.php?t=2216829&p=12986941#post12986941")   1.   to add them   2.   to make sure they are seen


1.  ```
[COLOR=#000000]*sudo apt-get install tap-plugins rev-plugins cmt liquidsoap-plugin-ladspa bs2b-ladspa invada-studio-plugins-ladspa mcp-plugins libladspa-ocaml ladspa-foo-plugins swh-plugins libasound2-plugins liquidsoap-plugin-all wah-plugins audacity-data swh-plugins*[/COLOR]
```

2.  ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ln -s /usr/lib/ladspa /usr/share/audacity/ladspa[/FONT][/COLOR]
```


then see in Audacity  under effects  206 plugins !!    all sorts of tricks

---

### Post by Bucky Ball on 2015-03-05
> **shantiq said:**
> ha Bucky this how SoX describes itself ...

Ha! Oddly coincidental. Never used SoX and never seen that description. There ya go. ;)

---

### Post by shantiq on 2015-03-05
it's a sign Bucky :)      it is ace    as good as audacity and even more stable i would say ....    but if you want to edit music Audacity is way easier to control as it has this ace Gui

---

### Post by Bucky Ball on 2015-03-05
I've used it a lot, and for creating a few ringtones over the years. Love it. When I did music tech at uni I used it a LOT. ;)

---

