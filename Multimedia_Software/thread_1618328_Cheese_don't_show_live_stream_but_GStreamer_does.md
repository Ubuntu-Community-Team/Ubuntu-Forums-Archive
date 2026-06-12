---
title: "Cheese don't show live stream but GStreamer does"
date: 2010-11-10
forum: Multimedia Software
---

### Post by gakon77 on 2010-11-10
I followed the instruction in the cheese help tutorial. The changes in
GStreamer to produce the live stream in cheese "try changing from xvimagesink
to ximagesink or vice-versa.", only make both fail if changed to xvimagesink.
As suggested here it goes the log...

Cheese 2.28.1 
Probing devices with HAL...
Found device 041e:4051, getting capabilities...
Detected v4l2 device: USB Camera (041e:4051)
Driver: zc3xx, version: 132608
Capabilities: 0x05000001

Probing supported video formats...
Device: USB Camera (041e:4051) (/dev/video0)
FractionRange: 0/1 - 100/1
video/x-raw-yuv 640 x 480 num_framerates 101
0/1 1/1 2/1 3/1 4/1 5/1 6/1 7/1 8/1 9/1 10/1 11/1 12/1 13/1 14/1 15/1 16/1 17/1
18/1 19/1 20/1 21/1 22/1 23/1 24/1 25/1 26/1 27/1 28/1 29/1 30/1 31/1 32/1 33/1
34/1 35/1 36/1 37/1 38/1 39/1 40/1 41/1 42/1 43/1 44/1 45/1 46/1 47/1 48/1 49/1
50/1 51/1 52/1 53/1 54/1 55/1 56/1 57/1 58/1 59/1 60/1 61/1 62/1 63/1 64/1 65/1
66/1 67/1 68/1 69/1 70/1 71/1 72/1 73/1 74/1 75/1 76/1 77/1 78/1 79/1 80/1 81/1
82/1 83/1 84/1 85/1 86/1 87/1 88/1 89/1 90/1 91/1 92/1 93/1 94/1 95/1 96/1 97/1
98/1 99/1 100/1 FractionRange: 0/1 - 100/1
video/x-raw-yuv 320 x 240 num_framerates 101
0/1 1/1 2/1 3/1 4/1 5/1 6/1 7/1 8/1 9/1 10/1 11/1 12/1 13/1 14/1 15/1 16/1 17/1
18/1 19/1 20/1 21/1 22/1 23/1 24/1 25/1 26/1 27/1 28/1 29/1 30/1 31/1 32/1 33/1
34/1 35/1 36/1 37/1 38/1 39/1 40/1 41/1 42/1 43/1 44/1 45/1 46/1 47/1 48/1 49/1
50/1 51/1 52/1 53/1 54/1 55/1 56/1 57/1 58/1 59/1 60/1 61/1 62/1 63/1 64/1 65/1
66/1 67/1 68/1 69/1 70/1 71/1 72/1 73/1 74/1 75/1 76/1 77/1 78/1 79/1 80/1 81/1
82/1 83/1 84/1 85/1 86/1 87/1 88/1 89/1 90/1 91/1 92/1 93/1 94/1 95/1 96/1 97/1
98/1 99/1 100/1 FractionRange: 0/1 - 100/1
video/x-raw-yuv 640 x 480 num_framerates 101
0/1 1/1 2/1 3/1 4/1 5/1 6/1 7/1 8/1 9/1 10/1 11/1 12/1 13/1 14/1 15/1 16/1 17/1
18/1 19/1 20/1 21/1 22/1 23/1 24/1 25/1 26/1 27/1 28/1 29/1 30/1 31/1 32/1 33/1
34/1 35/1 36/1 37/1 38/1 39/1 40/1 41/1 42/1 43/1 44/1 45/1 46/1 47/1 48/1 49/1
50/1 51/1 52/1 53/1 54/1 55/1 56/1 57/1 58/1 59/1 60/1 61/1 62/1 63/1 64/1 65/1
66/1 67/1 68/1 69/1 70/1 71/1 72/1 73/1 74/1 75/1 76/1 77/1 78/1 79/1 80/1 81/1
82/1 83/1 84/1 85/1 86/1 87/1 88/1 89/1 90/1 91/1 92/1 93/1 94/1 95/1 96/1 97/1
98/1 99/1 100/1 already added, skipping
FractionRange: 0/1 - 100/1
video/x-raw-yuv 320 x 240 num_framerates 101
0/1 1/1 2/1 3/1 4/1 5/1 6/1 7/1 8/1 9/1 10/1 11/1 12/1 13/1 14/1 15/1 16/1 17/1
18/1 19/1 20/1 21/1 22/1 23/1 24/1 25/1 26/1 27/1 28/1 29/1 30/1 31/1 32/1 33/1
34/1 35/1 36/1 37/1 38/1 39/1 40/1 41/1 42/1 43/1 44/1 45/1 46/1 47/1 48/1 49/1
50/1 51/1 52/1 53/1 54/1 55/1 56/1 57/1 58/1 59/1 60/1 61/1 62/1 63/1 64/1 65/1
66/1 67/1 68/1 69/1 70/1 71/1 72/1 73/1 74/1 75/1 76/1 77/1 78/1 79/1 80/1 81/1
82/1 83/1 84/1 85/1 86/1 87/1 88/1 89/1 90/1 91/1 92/1 93/1 94/1 95/1 96/1 97/1
98/1 99/1 100/1 already added, skipping
FractionRange: 0/1 - 100/1
video/x-raw-rgb 640 x 480 num_framerates 101
0/1 1/1 2/1 3/1 4/1 5/1 6/1 7/1 8/1 9/1 10/1 11/1 12/1 13/1 14/1 15/1 16/1 17/1
18/1 19/1 20/1 21/1 22/1 23/1 24/1 25/1 26/1 27/1 28/1 29/1 30/1 31/1 32/1 33/1
34/1 35/1 36/1 37/1 38/1 39/1 40/1 41/1 42/1 43/1 44/1 45/1 46/1 47/1 48/1 49/1
50/1 51/1 52/1 53/1 54/1 55/1 56/1 57/1 58/1 59/1 60/1 61/1 62/1 63/1 64/1 65/1
66/1 67/1 68/1 69/1 70/1 71/1 72/1 73/1 74/1 75/1 76/1 77/1 78/1 79/1 80/1 81/1
82/1 83/1 84/1 85/1 86/1 87/1 88/1 89/1 90/1 91/1 92/1 93/1 94/1 95/1 96/1 97/1
98/1 99/1 100/1 already added, skipping
FractionRange: 0/1 - 100/1
video/x-raw-rgb 320 x 240 num_framerates 101
0/1 1/1 2/1 3/1 4/1 5/1 6/1 7/1 8/1 9/1 10/1 11/1 12/1 13/1 14/1 15/1 16/1 17/1
18/1 19/1 20/1 21/1 22/1 23/1 24/1 25/1 26/1 27/1 28/1 29/1 30/1 31/1 32/1 33/1
34/1 35/1 36/1 37/1 38/1 39/1 40/1 41/1 42/1 43/1 44/1 45/1 46/1 47/1 48/1 49/1
50/1 51/1 52/1 53/1 54/1 55/1 56/1 57/1 58/1 59/1 60/1 61/1 62/1 63/1 64/1 65/1
66/1 67/1 68/1 69/1 70/1 71/1 72/1 73/1 74/1 75/1 76/1 77/1 78/1 79/1 80/1 81/1
82/1 83/1 84/1 85/1 86/1 87/1 88/1 89/1 90/1 91/1 92/1 93/1 94/1 95/1 96/1 97/1
98/1 99/1 100/1 already added, skipping
FractionRange: 0/1 - 100/1
video/x-raw-rgb 640 x 480 num_framerates 101
0/1 1/1 2/1 3/1 4/1 5/1 6/1 7/1 8/1 9/1 10/1 11/1 12/1 13/1 14/1 15/1 16/1 17/1
18/1 19/1 20/1 21/1 22/1 23/1 24/1 25/1 26/1 27/1 28/1 29/1 30/1 31/1 32/1 33/1
34/1 35/1 36/1 37/1 38/1 39/1 40/1 41/1 42/1 43/1 44/1 45/1 46/1 47/1 48/1 49/1
50/1 51/1 52/1 53/1 54/1 55/1 56/1 57/1 58/1 59/1 60/1 61/1 62/1 63/1 64/1 65/1
66/1 67/1 68/1 69/1 70/1 71/1 72/1 73/1 74/1 75/1 76/1 77/1 78/1 79/1 80/1 81/1
82/1 83/1 84/1 85/1 86/1 87/1 88/1 89/1 90/1 91/1 92/1 93/1 94/1 95/1 96/1 97/1
98/1 99/1 100/1 already added, skipping
FractionRange: 0/1 - 100/1
video/x-raw-rgb 320 x 240 num_framerates 101
0/1 1/1 2/1 3/1 4/1 5/1 6/1 7/1 8/1 9/1 10/1 11/1 12/1 13/1 14/1 15/1 16/1 17/1
18/1 19/1 20/1 21/1 22/1 23/1 24/1 25/1 26/1 27/1 28/1 29/1 30/1 31/1 32/1 33/1
34/1 35/1 36/1 37/1 38/1 39/1 40/1 41/1 42/1 43/1 44/1 45/1 46/1 47/1 48/1 49/1
50/1 51/1 52/1 53/1 54/1 55/1 56/1 57/1 58/1 59/1 60/1 61/1 62/1 63/1 64/1 65/1
66/1 67/1 68/1 69/1 70/1 71/1 72/1 73/1 74/1 75/1 76/1 77/1 78/1 79/1 80/1 81/1
82/1 83/1 84/1 85/1 86/1 87/1 88/1 89/1 90/1 91/1 92/1 93/1 94/1 95/1 96/1 97/1
98/1 99/1 100/1 already added, skipping

v4l2src name=video_source device=/dev/video0 ! capsfilter name=capsfilter
caps=video/x-raw-rgb,width=640,height=480,framerate=30/1;video/x-raw-yuv,width=640,height=480,framerate=30/1
! identity


Thanks.

---

### Post by no2498 on 2010-11-13
this program works well for me
its not for 64 bit tho

wxcam

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)


hope you can use it

---

### Post by no2498 on 2010-11-15
cheese has a bug tracker 

5.3.&#8195;My webcam works with gstreamer, but does not work with Cheese. What's wrong?


      Using "gstreamer-properties" mentioned in the above question, try changing from
      xvimagesink to ximagesink or vice-versa. If this still does not work run "cheese --verbose" on
      the command line and copy the logging into a bug report in our 
      
      bug tracker.
    
5.4.&#8195;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?


      See if your webcam works when testing it in "gstreamer-properties". If it works
      there, but not in Cheese, please file a bug report in our 
      
      bug tracker.

---

### Post by gakon77 on 2010-11-15
Thank you for the answer.

I've reported a bug in the cheese bug tracker, but there isn't any answer so far. Any idea why not?

However, in another report from a similar bug, it says that the problem may be the resolution configuration. I'll try to follow the bug to configure if for lower resolution.

---

### Post by no2498 on 2010-11-15
id rather not say what i think about cheese
it was ubuntu that give them all the settings for the webcams
i think it was to fast for cheese

for some reason i can not change any settings on 2 computers now
both cams went to heck 2 weeks ago
804 and 10.04

---

### Post by gakon77 on 2010-11-16
No success with the change to lower resolution and still no answer from the cheese bug tracker, too bad for them. I've installed as you suggested wxcam and seems to work alright, thanks.

I'll take it a step forward and see if I can fix the problem I have with skipe. The webcam works during the test but skipe crashes when I start videoconference.

---

### Post by no2498 on 2010-11-16
glad you got it working
i pin wxcam to the top bar and can start making movies in 3 sec's

but with in the last 2 weeks some thing makes my cams look bad on 2 computers
1 with 804 and 1 with 10.04 on them

---

### Post by gakon77 on 2010-11-19
> **gakon77 said:**
> No success with the change to lower resolution and still no answer from the cheese bug tracker, too bad for them. I've installed as you suggested wxcam and seems to work alright, thanks.

I'll take it a step forward and see if I can fix the problem I have with skipe. The webcam works during the test but skipe crashes when I start videoconference.

Well, it seems that skipe doesn't crash if I have wxcam open (a little step forward), but now the other person can't see me.
I wonder what will happen if I do the same with cheese...

---

