---
title: "Converting mp3 to wav when burning?"
date: 2010-03-04
forum: Multimedia Software
---

### Post by bro brian on 2010-03-04
Trying to burn with CD/DVD Creator. I can't find anything in the program (settings wise) that will automatically convert mp3 files to wav files. I used to use k3b, and it used to do that.
  I did try installing k3b, however I am getting glitches in the program. I don't want to covert mp3 files over to wav every time I want to burn a new cd.
  Does anyone have a suggestion as to another program or place to find the burn setting for encoding?
  Thanks in advance! 
PS. Using Karmic os with gnome desktop.

---

### Post by cjhabs on 2010-03-04
> **bro brian said:**
> Trying to burn with CD/DVD Creator. I can't find anything in the program (settings wise) that will automatically convert mp3 files to wav files. I used to use k3b, and it used to do that.
  I did try installing k3b, however I am getting glitches in the program. I don't want to covert mp3 files over to wav every time I want to burn a new cd.
  Does anyone have a suggestion as to another program or place to find the burn setting for encoding?
  Thanks in advance! 
PS. Using Karmic os with gnome desktop.

Using Karmic with Gnome also - once I loaded the libkb6-extracodecs from Synaptec I was able to consistently burn mp3 to audio cd with k3b

---

### Post by bro brian on 2010-03-05
> **cjhabs said:**
> Using Karmic with Gnome also - once I loaded the libkb6-extracodecs from Synaptec I was able to consistently burn mp3 to audio cd with k3b
Yes - That was the problem. I was not able to get K3b to do 2 things (wouldn't load mp3's into project section, and wouldn't convert/burn in wav format).
  After installing libk3b6-extracodecs from the Synaptic Package Manager list, everything worked great.
  Thanks so much! I've always liked using the k3b burning program. I was quite disappointed when it didn't work properly, and knew there must be something missing. It never ceases to amaze me when someone here knows the "fix" for such things.

---

### Post by huangweiqiu on 2010-03-05
I don't there is such app in linux world yet. I had to use Winff to convert the mp3 and then burned ...

---

### Post by cjhabs on 2010-03-05
Glad its fixed - it seems you can do almost anything with Ubuntu!

---

### Post by bro brian on 2010-03-05
> **huangweiqiu said:**
> I don't there is such app in linux world yet. I had to use Winff to convert the mp3 and then burned ...
  I did find something that worked great for "converting mp3 files to wav", and other formats as well. It was called "Sound Converter", which is in the list of aps in the Synaptic Package Manager (System>Administration> Synaptic Package Manager).
  I installed the Sound Converter, and used that to encode the mp3 to wav format. Then, I burned the song using Brasero. Worked great, but more involved.
  The thing is that k3b does all of this for me. I don't have to encode anything. K3b is native to the KDE desktop, but it does work with gnome. I just couldn't get it to run right until I did the stuff mentioned in the posts previously in this thread.

---

### Post by huangweiqiu on 2010-03-05
> **bro brian said:**
> I did find something that worked great for "converting mp3 files to wav", and other formats as well. It was called "Sound Converter", which is in the list of aps in the Synaptic Package Manager (System>Administration> Synaptic Package Manager).
  I installed the Sound Converter, and used that to encode the mp3 to wav format. Then, I burned the song using Brasero. Worked great, but more involved.
  The thing is that k3b does all of this for me. I don't have to encode anything. K3b is native to the KDE desktop, but it does work with gnome. I just couldn't get it to run right until I did the stuff mentioned in the posts previously in this thread.

Thanks,that's good news.

---

