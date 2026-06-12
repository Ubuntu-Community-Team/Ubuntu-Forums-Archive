---
title: "flv to xvid conversion for standalone, keeps freezing? Also mp4 to xvid freeze."
date: 2014-04-28
forum: Multimedia Software
---

### Post by DrDynamic on 2014-04-28
Tried WinFF with the built in script below.

#!/bin/sh
echo -n "\033]0; Converting p360 (1/1)\007"
/usr/bin/avconv -threads 2  -y -i "/home/anthony/Videos/p360.mp4" -f avi -r 29.97 -vcodec libxvid -vtag XVID -vf scale=704:384 -aspect 16:9 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -trellis 1 -flags +aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2 "/home/anthony/Downloads/p360.avi"
read -p "Press Enter to Continue" dumbyvar
rm "/home/anthony/.winff/ff140428212735.sh"

Also tried transmaggedon with the default settings for xvid.

When I burn to disc the results are always the same. Plays for a few seconds then freezes. I fast forward, plays again for a few seconds, then freezes again, etc.

I also tried changing the fourcc to DX50 or DIVX, the results were the same. 

This happens with both mp4 inputs, and flv inputs, to xvid outputs.

Tried on two different standalone divx players, with a bunch of different input files, same results.

Output avis seem to play fine on vlc which is no surprise considering vlc plays pretty much everything.

Any help or advice would be appreciated, thanks.

---

### Post by DrDynamic on 2014-05-02
If anybody is interested, I solved this problem with avidemux. It can be found in the repos. According to avidemux the video I was trying to encode was using b-frames as reference and this can cause skipping. I'm not really sure what that means, but avidemux gave a one click solution. Literally, a popup window came up and basically said press this button to fix. voila fixed. 
      So,** if you want to encode flv or mp4 to xvid definitely try avidemux**, highly recommended.

---

