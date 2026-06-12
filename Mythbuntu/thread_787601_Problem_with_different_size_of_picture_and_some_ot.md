---
title: "Problem with different size of picture and some other things"
date: 2008-05-09
forum: Mythbuntu
---

### Post by malaTG on 2008-05-09
Hi everyone,

I have a couple of questions regarding mythtv

1. I have some problems with the size of my picture. I live in sweden and have a analog hauppauge pvr-150MCE card. 

When I connect the antenna directly to my TV the picture fills both horizontal and vertical(which isn't necessarly a good thing because some channels are in 4:3 and others are in 16:9). However when I go through my tv-card the picture doesn´t fill the screen in either direction for some channels. My settings for resolution is 720x576 and my screen resolution is 1360x768, could it have something to do with that?

2. My next question is which settings I should have regarding the picture in general. I feel that the picture is not as good when I go through the tv-card. Is there anything except the bitrate that I should change?

3. When I push "m" and get the menu in tv-mode the menu flickers a lot and doesn´t look very good. Is this normal behaviour?

/Marcus

---

### Post by oldHat on 2008-05-09
I found that I could get around the flickering by enabling de-interlacing

---

### Post by malaTG on 2008-05-09
Thank you for your response that solves issue number 3 for me!

Is there anyone that can help me with issue number 1. Should I change the playback resolution or something and where do I do that in that case?

---

### Post by dbaldaro on 2008-05-09
You might want to look in the Setup on your frontend.
> [Setup] -> [TV Settings] -> [Playback]
then go "General Playback (2/9)" and setup your "Aspect Ratio" to 16:9 and change the "Zoom" to Full or Stretch.

You might want to have a play with the settings on the next page "Playback Profiles" regarding your image quality,

---

### Post by malaTG on 2008-05-09
Hi again everyone,

Thank you for all the answers I have managed to solve all my problems now except one...

When I play programs recorded on my TV and DVD:s and the motion is fast I get a horizontal line one quarter from the top of the picture which distorts the picture. Since it both happens on the recorded shows and DVD:s my thought was that this might be a codec problem for mpeg2:s because they use the same format. 

Does anyone know if this is true and how to solve it? Or could it be something else...?

/Marcus

---

### Post by malaTG on 2008-08-24
bump....

I still have this problem regarding fast motion on my recordings and my dvd:s. I get lines in the picture when the motion is fast. I know that it probably has to do with my playback profiles but whatever I try I still seem to get lines when I playback in myth. 

Could someone please help me track down this problem? Where should I start? I have decent hardware

cpu : Pentium D 3.4 GHz
Ram : 1 Gb
Graphic card : Geforce 8600 GT 512 Mb

It should be enough to playback 720x576 mpeg2 recordings without any problem at all as I see it..

---

### Post by malaTG on 2008-08-30
bump....

Could this have something to do with modelines or something like that I just plugged my TV into my computer and it worked. Is there some setting that I have to adjust?

/marcus

---

### Post by malaTG on 2008-09-02
bump...

---

