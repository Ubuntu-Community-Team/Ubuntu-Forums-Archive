---
title: "echo indigo without stereo sound"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by maomao.fluffy on 2007-02-11
Hello youall, I just switched to Ubuntu 6.10; and I have an echo indigo card. After reading all the  posts on indigo, I have installed all the needed alsa files, hotplug; and my indigo does play sound. but it's not stereo, the 2 channels have the same sound. Plus the sound quality is not as good. It seems that it cannot play digitally. Thank you in advance for any help!!!:)  
maomao@maomao-laptop:~$ aplay -l
**** PLAYBACK&#30828;&#20214;&#35774;&#22791;&#21015;&#34920; ****
&#21345; 0: I82801DBICH4 [Intel 82801DB-ICH4], &#35774;&#22791; 0: Intel ICH [Intel 82801DB-ICH4]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791;&#65306;#0: subdevice #0
&#21345; 0: I82801DBICH4 [Intel 82801DB-ICH4], &#35774;&#22791; 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791;&#65306;#0: subdevice #0
&#21345; 1: Indigo [Indigo], &#35774;&#22791; 0: PCM [Indigo]
  &#23376;&#35774;&#22791;: 7/8
  &#23376;&#35774;&#22791;&#65306;#0: subdevice #0
  &#23376;&#35774;&#22791;&#65306;#1: subdevice #1
  &#23376;&#35774;&#22791;&#65306;#2: subdevice #2
  &#23376;&#35774;&#22791;&#65306;#3: subdevice #3
  &#23376;&#35774;&#22791;&#65306;#4: subdevice #4
  &#23376;&#35774;&#22791;&#65306;#5: subdevice #5
  &#23376;&#35774;&#22791;&#65306;#6: subdevice #6
  &#23376;&#35774;&#22791;&#65306;#7: subdevice #7
maomao@maomao-laptop:~$

---

### Post by ish4269 on 2008-06-26
Find a program called echomixer installed with alsa-utils or alsa-tools* then press the gang button this will lift the volume level of both the left and right channels. I am using gutsy 7.10 and found the channels were crossed for some stupid reason.

---

