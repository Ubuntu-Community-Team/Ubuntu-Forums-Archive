---
title: "[SOLVED] Mp4 Converter Needed"
date: 2008-10-21
forum: Multimedia Software
---

### Post by Pinejoker on 2008-10-21
I was wondering if what kind of mp4 software can use for my ubuntu hardy please someone give me some idea.. because i will convert my mpeg files to mp4.. to upload to my psp thank you in advance...

---

### Post by wolfen69 on 2008-10-21
try ffmpeg. you will probably want a [gui frontend]("http://code.google.com/p/winff/") for it too.

---

### Post by Pinejoker on 2008-10-21
ohh what is this sir? XD is this the converter?:confused:

---

### Post by Pinejoker on 2008-10-21
family@family-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

---

### Post by SuperSonic4 on 2008-10-21
```
sudo apt-get install update
```

```
sudo apt-get install ffmpeg
```

you might want to use synaptic to look for a GUI frontend. Avidemux is my favourite

```
sudo apt-get install avidemux
``` hopefully ffmpeg will be installed as a dependency

---

### Post by Pinejoker on 2008-10-21
i dont know whats wrong but can you check this...

when i used this sudo apt-get update

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by SuperSonic4 on 2008-10-21
It means something else is using the apt function. Is synaptic, updates or another apt-get in action at the moment?

---

### Post by Pinejoker on 2008-10-21
its okay now but its said invalid operation for sudo apt-get ffmpeg

---

### Post by SuperSonic4 on 2008-10-21
Oops I made a typo

```
sudo apt-get install ffmpeg
```

---

### Post by wolfen69 on 2008-10-21
> **Pinejoker said:**
> its okay now but its said invalid operation for sudo apt-get ffmpeg

you want ```
sudo apt-get *install* ffmpeg
```

---

### Post by Pinejoker on 2008-10-21
question i installed first this avidemux?:confused: you think there will be a problem?

---

### Post by SuperSonic4 on 2008-10-21
No I don't see any problems there

---

### Post by Pinejoker on 2008-10-21
ok now my question since i have this software.. name Avidemux GTK+ how could i use it to convert mpeg to mp4? final sir.. thank u thank u just pls help me XD :):lolflag:

---

### Post by SuperSonic4 on 2008-10-21
Just a quick question, do you have codecs installed already? You might need the ubuntu-restricted-extras

open Avidemux by pressing alt+f2 and typing Avidemux or using the launcher. Open the mpeg file in the obvious way.

Select MP4 in the format box on the left and leave audio/video as copy or change it depending on what you want (copying is easier IMO). Finally save it in the standard way

---

### Post by Pinejoker on 2008-10-21
ohhh thank you its working Thumbs Up for you.. can you be the President of United States than Mcain or Obama hehehe joking.. ^_^ thank u again

---

### Post by SuperSonic4 on 2008-10-21
'Fraid not, I'm not American :]

Don't forget to mark as solved and a [IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG] wouldn't go amiss ;)

---

### Post by Pinejoker on 2008-10-21
Problem Solved.

thanks to **SuperSonic4**

---

### Post by SuperSonic4 on 2008-10-21
You can mark a thread as solved by going to thread tools at the top and then mark as solved ;)

---

### Post by Pinejoker on 2008-10-21
last question what kind of mpeg - 4 ASP (Xvid4), ASP AVC (x264), ASP (lavc) which one is the standard?

---

