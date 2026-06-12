---
title: "Broken s-Video! help with ATI radeon open drivers and TV-out"
date: 2009-11-29
forum: Multimedia Software
---

### Post by maxxerific on 2009-11-29
hey all - 
so after much fooling around
 i've managed to force  -video out of my ati 9550 card. 

i used: 
 xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
 xrandr --addmode S-video 800x600
xrandr --output S-video --same-as VGA-0
xrandr --output S-video --mode 800x600

so two problems:

1. the resolution of the TV is 800-600 (that's pretty much the max resolution on my TV)  
but its displaying tyhe whole of my main desktop (which is 1400-900)
so if i do fullscreen video most of the image is cut off

 2. video actually won't play back! THe dektop shows up pon the second screen. video is playing back on my main LCD monitor no problem. 
but the same app on the mirrored tv (vlc or whatever) sghow only black where video should be. 

edit: actually just tried youtube and playback is worKing fine on both screens! 
wtf!!!!

any advice?

---

### Post by maxxerific on 2009-12-04
best solution i've found: 
   make your home desktop 800x600. 
 then install xvattr 

and in terminal 
*xvattr* -a XV_CRTC -v *1*

---

