---
title: "Ubuntu VCD mpeg .dat to .mp3"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by Sirhanz on 2007-02-10
Hi I am a fairly new Ubuntu user and I have fully switched to Linux. I have a vcd disk that I want to take the audio off of and save in mp3 format to listen to with a mp3 player. This is a foreighn disc and I am not sure it is a standere video format. After quite a bit of fiddling I now able to view the videos with only  VLC Media Player ,Xine crashes and every other player does not have supported plug-in. Question is: How can I rip the audio portion of this disk to mp3 format. Is there an application for this? Can anyone help me with determining what file format I am dealing with  with? I could always run a patch cable from line out to line in on my soundcard  and record  with Sound Recorder, but I need to get the cable, or make one.    Thanks in advance for any help with this.

---

### Post by exidez on 2008-04-06
It is most probably a VCD 2.0 disk
i have the same that i brought back from indonesia. I used windows to copy one cd to mp3 using a program from [http://www.av2mp3.com/faq/convert-vcd-to-mp3.htm](http://www.av2mp3.com/faq/convert-vcd-to-mp3.htm)
However windows doesn't recognize the other discs...
i haven't tried this program though xine though. i might just have to copy the image through linux and transfer it to windows that way....

---

### Post by exidez on 2008-04-06
you could also try ripping the files from the cd using k3b
Click on Further Actions > Rip Video files

I just tried this this the cd that windows would not recognize and it worked
This will extract the files to mpg format...
Then you can manipulate it from there

---

### Post by swarup on 2008-07-20
Your suggestion to use k3b worked great. It is a fantastic tool-- allowed me to extract the files off the VCD so I ended up with .mpg files. But then I tried to use Sound Converter to convert those .mpg files to mp3, and it didn't do the job. It accepted the task, allowing me to bring in the .mpg file and assign it to an mp3 destination format, but once I gave the command to "start", it went on endlessly with a "time left" window that just kept increasing into the thousands of hours. Someone on another thread suggested using mplayer instead in a customized terminal command. And that actually worked. But it would have been very convenient to use the Sound Converter as that way I could do a batch command of all the .mpg files. 

When you say that once you have the .mpg files, "Then you can manipulate it from there", what did you have in mind. What program did you use to convert the .mpg to mp3?

---

