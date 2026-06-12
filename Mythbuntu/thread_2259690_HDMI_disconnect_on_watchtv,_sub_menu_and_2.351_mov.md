---
title: "HDMI disconnect on watchtv, sub menu and 2.35:1 movie settings"
date: 2015-01-06
forum: Mythbuntu
---

### Post by dibuntux on 2015-01-06
This is sistematic. I just changed my Optoma HD700x 720p projector with an HD25e 1080p. No need to configure anything on my mythbuntu 14.04 amd64  box with 0.27 up to date, it just displays 1080p at 60Hz perfectly. Whenever I select watchtv, however, HDMI disconnect and search again for signal, which is found after a second, and then it displays normally. This also appen if I change channel to a different source or multiplex.
When I go in Videos and select a sub folder with movies, and select a movie, the resolution changes from 1080p to 1922x1080 and the screen flickers. As soon as you press play, HDMI disconnect again and swithced back to 1080p. The movies I tried are all in 720p and works fine if I leave it at default. If I try to see the movie in 2.35:1 with no V-Fill -options that had always worked before on my old 720p projector - it just lose HDMI every 3 seconds or so.
Tried every settings on the projector to no solutions.
Any ideas?

ps: The Optoma connects to a Denon AV Ampli with a 10m HDMI cable...

---

### Post by khPWXxF on 2015-01-06
Might these just be different symptoms to the problem I had solved here last week?

[http://ubuntuforums.org/showthread.php?t=2258886](http://ubuntuforums.org/showthread.php?t=2258886)

Did you mean to type 1922x1080 (not 1920 x 1080)?

I used xrandr to find out what the screen supports.
Matched ubuntu to it with 
  ```
xrandr --output HDMI-0 --mode 1920x1080   
```
  and set the same settings in mythtv frontend menu.
Job done.

Phil

---

### Post by dibuntux on 2015-01-07
Thanks for the fast reply! I tried your suggestions, but outcome is almost the same... In Recordinds seems to be better (no HDMI lost signal) but in Video the problem remains. The most strange of all is the Play on a video, when info are shown: I still get HDMI lost signal and this time new res. is 1924x1080 with a 4:3 aspect ratio! When I press play to show the video, lost signal again and then 1080p. This time it does not seem to lose signal when in 2.35:1. Tried to set Video playing to Normal instead of VDPAU, no change. 
Where do you set resolution in Frontend settings?

I have the problem in XBMC too, the same on local videos, on some videos from the net, not on youtube...Can it be a HW problem from my Gainward nVidia GT9400 1 GB RAM? Maybe the task of 1080p is too hard?
Below the settings after xrandr:

davidino@mitodue:~/Scrivania$ xrandr --output HDMI-0 --mode 1920x1080
davidino@mitodue:~/Scrivania$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 8192 x 8192
DVI-I-0 disconnected primary (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1920x1080      60.0*+   59.9     50.0     24.0     60.0     50.0  
   1600x1200      60.0  
   1440x900       59.9  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1280x800       59.8  
   1280x720      120.0     60.0     59.9     50.0  
   1024x768      120.0     75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   720x576        50.0     50.1  
   720x480        59.9     60.1  
   640x480        75.0     72.8     59.9     59.9  
   480x576        50.0  
   480x480        59.9  
   411x576        50.1  
   411x480        60.0

---

### Post by dibuntux on 2015-01-07
After more testing, I believe it is a HW problem not related to my system: I connected my wife notebook with Win8 and a nVidia Gforce and xbmc and it does the same, even worst, at 1080p. Including 1924x1080 4:3 strange resolution! So, either cable or projector...

---

### Post by khPWXxF on 2015-01-07
> [COLOR=#000000]Where do you set resolution in Frontend settings?[/COLOR]
Frontend > setup > appearance >gui pixels

zero gives full screen
Regards
Phil

---

### Post by dibuntux on 2015-01-08
Dear Phil, thanks for repling again... yes, Frontend > setup > appearance >gui pixels is set to 0...now I remember.

It is definitely the Ampli, Denon AVR1610. If I connect the MythBox directly, it goes OK. Problem is I have a 10mt cable from the projector, with another 2 mt cable and female-female adapter to the Ampli, and then another 2 mt cable to the Myth box. Do not know what to do...I could change the cable to make it direct to the ampli...but to change that 10mt cable is going to be a mess...any ideas?

---

