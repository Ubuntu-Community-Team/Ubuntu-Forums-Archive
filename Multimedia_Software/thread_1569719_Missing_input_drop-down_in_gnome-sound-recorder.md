---
title: "Missing input drop-down in gnome-sound-recorder"
date: 2010-09-07
forum: Multimedia Software
---

### Post by earthhere on 2010-09-07
Hello, I am using Dell Latitude e4200 with Ubuntu 10.04. 
I want to record a streaming-audio (not capture), to use an alarm sound. I opened up gnome-sound-recorder, but I don't see input drop-down menu. I tried Audacity, but it's missing the menu, too.
 
I saw the specification sheet of my laptop, but it only says Mobile Intel® GS45 Express Chipsets, I'm not sure if it manages sound, too, but the sheet doesn't have any information about sound chip set. 

Thank you in advance and hopefully get a solution, here... :)

add: It seems like I can't change this to 'solved'. I cannot say it is solved, as I don't yet see the drop-down menu in gnome-sound-recorder, but with PulseAudio I can perform the task, so it can be regarded as solved?

---

### Post by earthhere on 2010-09-09
I reply to my question! I found a solution par hasard. 
Follow is my blog entry, I just copied it. 

> Such a perfect timing, I was exactly looking for how to record sound playing on the computer. I tried gnome-sound-recorder, but it didn't show sound input drop-down, so all I can record was from the internal mic. Not anymore! I found the information at Ubuntu Weekly Recipe &#25216;&#34899;&#35413;&#35542;&#31038;: "[&#31532;137&#22238;&#12288;PulseAudio&#12434;&#27963;&#29992;&#12377;&#12427;]("http://gihyo.jp/admin/serial/01/ubuntu-recipe/0137")". The solution is using PulseAudio.

Steps:
1. Install pavucontrol. (aptitude or synaptics) This is GUI PulseAudio volume control frontend.
2. Run gnome-sound-recorder.
3. Push the record button. Now go to pavucontrol, and see the Playback tab. You will see "Record stream from". Choose "Monitor from analog stereo" from the drop-down menu on the right.
4. Good to go!

---

