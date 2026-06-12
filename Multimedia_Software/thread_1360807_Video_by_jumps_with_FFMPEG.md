---
title: "Video by jumps with FFMPEG"
date: 2009-12-21
forum: Multimedia Software
---

### Post by alvaroalo on 2009-12-21
Hello everybody!!!!

I am producing a video using the images coming from the screen, and the audio coming from a null-sink of PulseAudio. 

The point is that, when I produce the output video file without taking into account the sound, the video goes on without problem, but when trying to add the sound, the image goes by with jumps (the sound works well...). 

I would like to know the parameters and the libraries I have to work with in order to solve this problem.

The line I am using is:

[FONT=Courier New]ffmpeg -isync -f x11grab -s 720x576 -r 25 -i $display -isync -ac 2 -f pulse -i $sink_monitor -acodec libmp3lame -r 25 -s 720x576 -g 50  -minrate 3000k -maxrate 3000k -b 3000k -bufsize 1200000 -flags +low_delay -qscale 2 -f mpegts   -me_method zero - output.ts[/FONT]

[FONT=Arial]I really beg you to help me in this problem[/FONT],

Thank you very much!!!!

---

