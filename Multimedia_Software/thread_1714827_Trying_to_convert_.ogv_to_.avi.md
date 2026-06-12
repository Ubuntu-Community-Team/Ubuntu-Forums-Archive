---
title: "Trying to convert .ogv to .avi"
date: 2011-03-25
forum: Multimedia Software
---

### Post by slashwannabe94 on 2011-03-25
Hey all, 

I would like to convert an ogv file to an avi file so i can upload it to youtube. I have been having trouble though. When you used the command below and the file was converted all the display was distorted, I could not see the video as it was in ogv. Is there some known issue here with converting ogv? 
ffmpeg -i file.ogv copy /home/user/Desktop/file.avi

Is there anything i am doing wrong?

---

### Post by Claus7 on 2011-03-25
Hello,

Just something quick:
...why do you use the string "copy"? If I were in your shoes, I would avoid using it.

Regards!

---

### Post by ron999 on 2011-03-25
Hi
This is a simple command to start with for YouTube videos:-

```
mencoder file.ogv -o file.avi -ovc lavc -oac mp3lame
```


You'll get better results later if you can use commands like this:-

```
ffmpeg -i file.ogv -vcodec libx264 -vpre medium -crf 24 -threads 0 -acodec copy file.mkv
```

---

### Post by slashwannabe94 on 2011-03-25
Thank you ron999 i will try this now.

---

### Post by slashwannabe94 on 2011-03-25
Thanks dude, that worked :) 

I have another question, do you any of you guys know where i could find a good video editing program, i need to blackout some parts of my video containing sensitive information.

---

### Post by ChipOManiac on 2011-03-25
> **slashwannabe94 said:**
> I have another question, do you any of you guys know where i could find a good video editing program, i need to blackout some parts of my video containing sensitive information.

Pitivi and KDENlive should do, but you'll have to make a PNG overlay and put it over the original as a layer. I don't know anything more advanced for Ubuntu (but I could be wrong). :D

---

