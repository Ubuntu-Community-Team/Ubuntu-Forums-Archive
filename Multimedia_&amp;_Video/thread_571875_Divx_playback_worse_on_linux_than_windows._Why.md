---
title: "Divx playback worse on linux than windows. Why?"
date: 2007-10-09
forum: Multimedia &amp; Video
---

### Post by arjones85 on 2007-10-09
I have tried playing back a divx-encoded video using xvid, as well as divx on ubuntu, and I just cannot get the quality to be as good as divx playback on my windows computer. Either the file is pixelated in full-screen mode on xvid, or when there are darks and whites right next to each other in the video it seems to flash back and forth on divx. Neither of these problems are present on my Windows machine with just regular Divx installed.

What can I do to troubleshoot this?


Thanks for your help!

---

### Post by Digitallysick on 2007-10-09
have you tried to play them with VLC? mine works great in ubuntu, the same as it did in windows

---

### Post by arjones85 on 2007-10-09
I have. They all look the same which leads me to believe its the codec :(  It just looks bad compared to Divx on Windows. I don't understand it

My video card is an ATI radeon xpress 200m, running latest ati restricted drivers

---

### Post by rsambuca on 2007-10-09
Keep in mind that DivX is a proprietary format, and the linux development by the company is way behind that of windows.

---

### Post by arjones85 on 2007-10-09
Well even when I was using the Xvid codec, it still looked pixelated.... It's weird. Other people are saying they don't notice a difference at all which makes me think its a problem with my configuration


Edit: Removing the flgrx driver had no effect, still the same problems

---

### Post by sdowney717 on 2007-10-15
I use totem-xine and get great quality. Dont use this with compiz-fusion or I get frame drops

---

### Post by eye208 on 2007-10-15
> **arjones85 said:**
> the file is pixelated in full-screen mode
For reasons unknown to anyone except ATI, the proprietary ATI video driver has its XVideo extension disabled by default. XVideo is required for smooth, non-pixelated scaling of video. It will also decrease CPU load during playback since the scaling and overlay is handled by the video card.

You can enable XVideo by entering the following command into a terminal:

sudo aticonfig --ovt Xv

You have to restart the system once for the new setting to take effect.

---

### Post by BlueFiberOptics on 2007-10-15
> **eye208 said:**
> For reasons unknown to anyone except ATI, the proprietary ATI video driver has its XVideo extension disabled by default. XVideo is required for smooth, non-pixelated scaling of video. It will also decrease CPU load during playback since the scaling and overlay is handled by the video card.

You can enable XVideo by entering the following command into a terminal:

sudo aticonfig --ovt Xv

You have to restart the system once for the new setting to take effect.

Why weren't you around when I asked a question about pixelated video?  :P
Good information, I'll try it tonight!

---

### Post by lonce on 2007-10-15
I was going to say the same thing.  Sometimes its a little setting like that.  

When I was trying to get 1080P to work correctly it took forever working with the different codecs and settings to get it butter smooth with mplayer.

---

### Post by lucksin on 2007-10-17
Hi 

i am a newbie in the world of linux... though i have been very happy with ubuntu for wateve days i have been using it. but there is this one issue that is really bugin me. the pixelated movies in full screen mode. i tired Mplayer, VLC  but the end result are same. the movie seems good when it is in half screen mode. but as soon as i go full screen the movie gets pixelated. the sound is perfect and there are no frame drops or delay. 

my main use for my laptop is for music and movies and surfing net. can anyone please help me out in it.. i hate going back to windows.. 

i am having ubuntu 7.04 with 855GM chipset. centrino 1.7 with 512 mb of RAM

any help appriciated

---

### Post by lucksin on 2007-10-18
Help Please !!!!!!!!!

---

### Post by lazka on 2007-10-18
fglrx doesn't do video aliasing very well...  try the open source one instead.

---

### Post by lucksin on 2007-10-19
Hi Lazka,

thanks for the reply, but i do not use ATI card on my machine. i have intel 855GM graphic driver installed, which comes packaged with Ubuntu 7.04. 

as far as i know fglrx is for ATI card users. 

:(

---

