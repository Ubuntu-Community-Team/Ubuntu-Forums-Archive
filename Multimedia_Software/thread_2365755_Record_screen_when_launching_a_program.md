---
title: "Record screen when launching a program"
date: 2017-07-10
forum: Multimedia Software
---

### Post by riverio on 2017-07-10
Hi!

First of all, please forgive me if I make some mistakes when writing this, I am new in the forum and non-native english, so I don't speak the language so well as I wish

Well, my problem is the following one: I want to run in Ubuntu 16.04 LTS a software for a submarine Remote Operated Vehicle (ROV), this one: [http://docs.bluerobotics.com/brov2/software-setup/](http://docs.bluerobotics.com/brov2/software-setup/). The issue here is that I want to record my screen (the full desktop, but it would be good also to only record the software window) when I am working with this ROV software.

I studied some options for screen recording in Ubuntu: Kazam, RecordMyDsqesktop, Simple Screen Recorder, an integrated option in VLC.... But none of these options give me the specific possibility that I would like to achieve: **begin the screen recording automatically when launching the ROV software. **If this is way too difficult, it would be great also to begin the recording when intiallizing Ubuntu, but I would prefer to begin the recording when launching a specific program.

Is there a simple way in order to do this? Or would I need to modify the execution code of the software in order to force the beginning of the screen recording automatically? I am very unexeprienced in Linux programming, but if this is the only way, well, I will try! :p

Thank you kindly in advance!

Greetings

---

### Post by ajgreeny on 2017-07-10
You may be able to do this with a simple shell script using ffmpeg to record the desktop and then adding a separate line with whatever command is needed for the ROV application; something like
```
#!/bin/bash
ffmpeg -f x11grab -s 1440x900 -r 15 -i :0.0 -s 720x450 -r 15 -qscale 0 Desktop/video.avi
ROV-command
```
you may also be able to edit the .desktop file for the ROV application to ```
bash -c "ffmpeg -f x11grab -s 1440x900 -r 15 -i :0.0 -s 720x450 -r 15 -qscale 0 Desktop/video.avi ;ROV-command"
```
You can edit the ffmpeg part of the command to choose your own screensize, etc etc, and also add sound recording which I have never needed.

---

### Post by riverio on 2017-07-10
Thanks! I haven't thought in that option, launching both the software and the screen recording simultaneously with a script, seems what I was looking for! I will try that and post the results, thank you for your fast answer! :D

---

### Post by riverio on 2017-07-11
> **ajgreeny said:**
> You may be able to do this with a simple shell script using ffmpeg to record the desktop and then adding a separate line with whatever command is needed for the ROV application; something like
```
#!/bin/bash
ffmpeg -f x11grab -s 1440x900 -r 15 -i :0.0 -s 720x450 -r 15 -qscale 0 Desktop/video.avi
ROV-command
```
you may also be able to edit the .desktop file for the ROV application to ```
bash -c "ffmpeg -f x11grab -s 1440x900 -r 15 -i :0.0 -s 720x450 -r 15 -qscale 0 Desktop/video.avi ;ROV-command"
```
You can edit the ffmpeg part of the command to choose your own screensize, etc etc, and also add sound recording which I have never needed.

I tried this today, and the separate lines in the script worked well: I can separately record the screen (ffmepg works stunningly well, thanks!!) and open the ROV software with the typical cd /softwarefolder/ ./software lines. 

But there is a problem. Now, my code is the following:

```

#!/bin/bash
echo Open ROV software
cd /home/user/
./QGroundControl.AppImage
echo Start screen recording
ffmpeg -f x11grab -s 2560x1440 -r 30 -i :0.0 -s 1920x1080 -r 30 -qscale 0 /home/user/Desktop/video.avi

```

But this first opens the software, and only begins the screen recording when closing the ROV software window. I tried in the opposite way, beginning the screen recording first, but that makes that the ROV software only opens when you stop the screen recording.

I know that this must be easier than I think, but, is there a way to have these two processes at one time? Sorry if it is a too newbie question

Thanks again!!!

---

### Post by &amp;KyT$0P# on 2017-07-11
Try this -
```

#!/bin/bash
cd /home/user/
echo Start screen recording
ffmpeg -f x11grab -s 2560x1440 -r 30 -i :0.0 -s 1920x1080 -r 30 -qscale 0 /home/user/Desktop/video.avi &
echo Open ROV software
./QGroundControl.AppImage

```

---

### Post by riverio on 2017-07-11
That worked perfectly!!!!!! Thanks sincerely for all the help ^^

---

### Post by ajgreeny on 2017-07-11
Thanks halogen2 for that script edit.

I wonder if the script I suggested would have worked if the first command line was ended with an ampersand, &; I am no great scripter but at least my suggestion gave a clue to the OP which ended in success.

---

### Post by &amp;KyT$0P# on 2017-07-11
You are both welcome.

> **ajgreeny said:**
> I wonder if the script I suggested would have worked if the first command line was ended with an ampersand, &;
That would only work when run from [FONT=Courier New]/home/user[/FONT] *.  Aside that, it's equivalent.


* That is, assuming that there's a specific reason to go [FONT=Courier New]cd /home/user/; ./QGroundControl.AppImage[/FONT] instead of just doing [FONT=Courier New]/home/user/QGroundControl.AppImage[/FONT] .

---

