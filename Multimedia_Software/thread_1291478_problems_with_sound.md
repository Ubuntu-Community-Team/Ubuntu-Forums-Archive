---
title: "problems with sound"
date: 2009-10-14
forum: Multimedia Software
---

### Post by denisdobrovoda on 2009-10-14
hi i am quite new to ubuntu and first everything worked perfectly fine. however after about two weeks i started to have some problems with my sound. first of all the videos and things on the internet started to have some delays (i thought this was a flash codec problem because the videos would have trouble with colours etc) than the videos on youtube would only play when i start them in a separate window and now the sound doesnt work at all. i was messing around with it for quite some time now but it doesnt seem to help. i tried out different sound card preferences and even though the sound after start up or the test sound will sound the sound with videos and dvds wouldnt. i dont know what to do, however it probably isnt just a flash problem now since it occurs when i play dvds as well. and lately youtube would freeze completely. what shall i do? is it something with the sound car preferences?thanks

---

### Post by jbrown96 on 2009-10-14
Try switching to ALSA. In System-->preferences-->Sound change all the devices to ALSA. Then open a terminal and see if any channels are muted. Use the arrow keys and 'm'. You will need channels like master, pcm, front, etc. You may need to unmute all the channels to find a configuration that works. After you find the correct setup, go back through and mute all the channels that aren't necessary because they can cause feedback (buzzing/hissing).

---

### Post by denisdobrovoda on 2009-10-15
thank you. so i switched to alsa in the sound preferences but i do not really know which command to use in the terminal to find out whether things are mute and so. what should i do? and btw when i try the sound test in the sound preferences nothing happens as if it was really muted.

---

### Post by jbrown96 on 2009-10-15
If you try the sound test and don't get an error that mentions something about sine=512 that is a good sign that it is working but muted. Sorry I forgot to include the command. ```
alsamixer
```

---

### Post by denisdobrovoda on 2009-10-15
actually I have an opportunity to chose from HDA intel conextant digital or analog. the analog one does the mistake you mentioned the sine512 or whatever but the digital one is ok. however, i tried terminal and it seems that nothing is muted, respectivelly all the columns seem to be put to maximum except for the ones in the middle which say IEC958 and IEC 958 D.what should i do?

---

### Post by jbrown96 on 2009-10-15
what kind of audio card do you have? Post the output of ```
lspci | grep Audio
```

Note that | is the pipe character and not a one or lowercase l. just copy and paste the command

---

### Post by denisdobrovoda on 2009-10-16
Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
btw thank you so much for your help really. this is what i love about linux. people are nice:)
so what do you reckon should i do? at first everything worked perfectly....

---

