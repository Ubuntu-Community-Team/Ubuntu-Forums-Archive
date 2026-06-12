---
title: "A good, free app for .avi to IPOD"
date: 2009-04-30
forum: Multimedia Software
---

### Post by Lakeside5 on 2009-04-30
Guess it's about time I ask here, after messing things up :)  I finally got an Ipod, but it seems I need to convert the .avi's to  view on the iPod.  I tried a few shareware ones, but they are for Windows and just freeze up  trying to run them in Wine. Can someone please help me with one that's made for Linux? thanks.

---

### Post by lukeiamyourfather on 2009-05-01
Handbrake.

---

### Post by binbash on 2009-05-01
+1 for handbrake

---

### Post by Lakeside on 2009-05-01
Thanks guys, I just downloaded/installed handbrake, it was easy to do and looks good :) I don't know anything about iPods- I fianlly got one, and guess I figured I could just plug it into the usb and go!  But I have not idea how to 'put things on it', like I want to take a video (.avi) off my computer's docs folder, and put it in the ipod. But I get error messages, and also, the handbrake doesn't seem to work, I can add the .avi video into handbrake, and pick 'ipod' from the menu on the right, but then nothing seems to happen.  thanks.*edit*  I got handbrake to work, just had to mess around with it, but I am still unclear about the iPod.

---

### Post by Stochastic on 2009-05-01
Moved to Multimedia & Video.

---

### Post by FakeOutdoorsman on 2009-05-01
If you're using Ubuntu Jaunty Jackalope, FFmpeg from the repository will provide the best results in my opinion (excluding compiling bleeding-edge FFmpeg and x264).  First install FFmpeg and the unstripped FFmpeg libraries:
```
sudo apt-get install ffmpeg libavcodec-unstripped-52
```
Now for the command:
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -ac 2 -s 640x480 -vcodec libx264 -vpre hq -vpre ipod640 -b 512k -bt 512k -threads 0 -f ipod output.mp4
```
Options you may want to change are:
[indent]**-s** video frame size
**-b** bitrate
**-bt** bitrate tolerance (usually equal to -b)[/indent]

---

### Post by MartyBuntu on 2009-05-01
WinFF

---

### Post by Lakeside5 on 2009-05-01
Thanks for the great advice, I will give ffmpeg a try sometime. I just got handbrake to work and I now have a converted video ready to put on my ipod. I have gtkpod but I don't think I'm doing it right.  I press 'load ipod' but I dont think it loads. (my ipod is plugged into computer and mounted). I click 'load ipod' but don't get the 'rel' in the left column, as I'm am supposed to see. With 'add file' the file does show up  on left column, and under 'title', but I can't find it on my ipod :(

---

### Post by Lakeside5 on 2009-05-02
I'm just wondering...does  iTunes work with Linux?  My friends don' realize I have Linux I guess, they keep saying iTunes will solve all my problems lol. thanks

---

### Post by Alien260 on 2009-05-07
> **MartyBuntu said:**
> WinFF

Hi, 

I have installed WinFF and have updated my ffmpeg from the medibutu reps. 

I have followed most of the things that people tested out on this thread - [http://ubuntuforums.org/showthread.php?t=969308](http://ubuntuforums.org/showthread.php?t=969308)


Tho when i try and run winFF i get the following error in the terminal window 

```
x-terminal-emulator: error: Expecting zero additional arguments, found: 1
Usage: x-terminal-emulator [options]


```

Dose anyone here have an idea how to fix this?

Regards
[COLOR="Lime"]Alien[/COLOR]

---

### Post by paul.gevers on 2009-05-08
> **Alien260 said:**
> 
```
x-terminal-emulator: error: Expecting zero additional arguments, found: 1
Usage: x-terminal-emulator [options]


```

Dose anyone here have an idea how to fix this?

In Winff, goto Edit -> Preferences -> Linux and change the -e option into -x (or change the terminal executable to something like /usr/bin/xterm). This is a bug in terminator (which I think is your x-terminal-emulator.

---

