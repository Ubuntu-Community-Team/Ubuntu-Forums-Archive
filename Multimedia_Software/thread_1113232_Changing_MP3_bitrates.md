---
title: "Changing MP3 bitrates"
date: 2009-04-01
forum: Multimedia Software
---

### Post by DeMus on 2009-04-01
Who knows a nice, good working program to change the bitrate of MP3's?
I have songs I want to burn onto a CD and use it in the car. The idea is to lower the bitrate to 96kbps so I can hold a lot of songs on one disc.
Anyone?

---

### Post by steeleyuk on 2009-04-01
sudo apt-get install soundconverter

Great little program that can convert to a few formats. You'll lose some quality by re-encoding from MP3 to MP3.

---

### Post by DeMus on 2009-04-01
> **steeleyuk said:**
> sudo apt-get install soundconverter

Great little program that can convert to a few formats. You'll lose some quality by re-encoding from MP3 to MP3.

Thank you for your answer. Unfortunately something goes terrible wrong here. I start the program, add a folder with 6 MP3 songs, open the preferences and set them as indicated in the attached picture. Then I start the conversion and in 1 second the program is ready. But, the six converted files have a total size of 0 bytes. Which can not be good.
What can be wrong here? I'm sure I do something wrong, but what?

---

### Post by Yashiro on 2009-04-01
Do you have an mp3 ENCODER installed?
Try converting to Ogg as a test. If that works then you just have a missing mp3 encoder.

---

### Post by DeMus on 2009-04-01
> **Yashiro said:**
> Do you have an mp3 ENCODER installed?

At first I did not and so the MP3 possibility was greyed out. The program gave me an opportunity to install an M3 encoder, which I did. I restarted the program and then I could choose MP3 as output format. But, the filesize is still 0.
Flac is working okay, so it must be the MP3 encoder. How to go from here?

---

### Post by steeleyuk on 2009-04-01
Try running soundconverter from the terminal with the command:

soundconverter --debug

---

### Post by DeMus on 2009-04-01
> **steeleyuk said:**
> Try running soundconverter from the terminal with the command:

soundconverter --debug

I found out that I installed version 1.01. I am trying to install 1.4.2 but am having problems how to do that. The program is available in a tar.gz format and I have no idea how to install that.
Can you help me?

---

### Post by steeleyuk on 2009-04-01
It'll mean having to compile it, which should be interesting considering you're still on Hardy. :)

You might be better adding this PPA (deb [http://ppa.launchpad.net/rzr-team/ppa/ubuntu](http://ppa.launchpad.net/rzr-team/ppa/ubuntu) hardy main). It will resolve any dependency problem automatically, hopefully.

---

### Post by DeMus on 2009-04-01
> **steeleyuk said:**
> It'll mean having to compile it, which should be interesting considering you're still on Hardy. :)

You might be better adding this PPA (deb [http://ppa.launchpad.net/rzr-team/ppa/ubuntu](http://ppa.launchpad.net/rzr-team/ppa/ubuntu) hardy main). It will resolve any dependency problem automatically, hopefully.

Thank you very much. Now it's working. So, the old version was causing the problems. Now I can start working on my disc.
Once again, thank you very much for your help.

---

### Post by styleruk on 2009-04-08
I have a problem with soundconverter, read this post and installed it, ran it several times on individual folders to reduce bitrate and it worked fine.  Then I selected 20 or so folders and it just either deleted the files completely or ignored them....mostly it deleted them!
Any ideas, I'm steering well clear of that program for now!

Si

---

### Post by styleruk on 2009-04-08
Works fine if I do one folder at a time and untick the 'delete file after' option.

---

### Post by styleruk on 2009-04-08
Sorry...Stand down!

I found the issue, if you select multi files, it put them all in the top folder, so it did the job and did not delete the files, they are just not in their individual folders now!
OK now. :-)

---

### Post by www.rzr.online.fr on 2009-06-06
hi
I am the author of that ppa :

[http://rzr.online.fr/q/apt](http://rzr.online.fr/q/apt)

feel free to contact me if you want these package to be into official ubuntu

-- 
[http://rzr.online.fr/q/repo](http://rzr.online.fr/q/repo)

---

