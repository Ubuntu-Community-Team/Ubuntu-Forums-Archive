---
title: "DVD codecs / plugins where how... newbie."
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by Sextant on 2007-05-25
Hi all,

I am brand spanking new to ubuntu and barely have the dew off the lily when it comes to Linux in general.

I've installed fiesty on an IBM T42 and have it running pretty darn well (very pleased with my self)

One thing I haven't figured out yet is how to play dvd's seems I am missing codecs and I would bet quite a bit else.

Totem tells me:

Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.

Please install the necessary plugins and restart Totem to be able to play this media.

when I try to play a DVD but I do not know where or how to get these plug ins.

Any kind soul out there want to help a new guy figure this out?

Thanks MUCH

---

### Post by swudee on 2007-05-26
Take a look in the community docs.

[https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)

You will find it under restricted formats.

I assume you are using Feisty Fawn (7.04)?

---

### Post by Sextant on 2007-05-26
Yes, the latest 7.04, thanks by the way, I will go look at the docs you suggested.

---

### Post by Sextant on 2007-05-27
Hi again... I really could use some help, I'm sorry, I'm new to all this and I appear to be not doing something right.

Here are the details:
IBM T42 Notebook
Feisty Fawn 7.04
arch = i686
Intel Pentium M Processor 1.8GHz
2GB RAM

I went to [https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia) and followed the instruction to ad to the repository
"wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O - | sudo apt-key add -"
then
"sudo apt-get update"

I also followed the instructions to add libdvdcss2
"sudo apt-get install libdvdcss2"

I also ran:
"sudo apt-get install w32codecs"

Forgot to mention, I also added the Ubuntu restricted extras from the applications manager (or what ever that is called)

I still get the can't play DVD's I get this message:

Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
Please install the necessary plugins and restart Totem to be able to play this media.

What am I missing????  HELP:confused:

I am VERY new to all this and have to look up and learn each step, which is fine, I'm learning but if you have advice, please keep in mind I might not know the "presumes" or your advice.

Thanks so much!

Pete

---

### Post by RomeReactor on 2007-05-27
Hi. Make sure you have **totem-xine** installed instead of **totem-gstreamer**, as totem-gstreamer can't handle dvd playback yet; since you already installed w32codecs and libdvdcss2 (assuming they installed properly):
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libdvdnav4 libdvdplay0 libdvdread3
```

---

### Post by Sextant on 2007-05-27
your a rock star RR, I am up and playing, thanks!  I'm having a great time with all this... now if I could figure out how to install the 1.4 version of skype....................

---

### Post by burt_57 on 2007-05-28
> **RomeReactor said:**
> Hi. Make sure you have **totem-xine** installed instead of **totem-gstreamer**, as totem-gstreamer can't handle dvd playback yet; since you already installed w32codecs and libdvdcss2 (assuming they installed properly):
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libdvdnav4 libdvdplay0 libdvdread3
```

I get this error when I ran your command 
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Angelbeast on 2007-05-29
> **RomeReactor said:**
> Hi. Make sure you have **totem-xine** installed instead of **totem-gstreamer**, as totem-gstreamer can't handle dvd playback yet; since you already installed w32codecs and libdvdcss2 (assuming they installed properly):
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libdvdnav4 libdvdplay0 libdvdread3
```

i was having the sme problem but thi fixed it sort of. Now i am having an error dialog that says i cannot play encrypted dvd's without libdvdcss. How do i get this?

---

### Post by burt_57 on 2007-05-29
> **Angelbeast said:**
> i was having the sme problem but thi fixed it sort of. Now i am having an error dialog that says i cannot play encrypted dvd's without libdvdcss. How do i get this?
Thank, that was my problem. Xine.
I have now the liddvdcss.. but not sure how to do that install.
Anyway movie work with xine-totem.
So far :popcorn:

---

### Post by RomeReactor on 2007-05-29
Angelbeast, for adding the medibuntu repositories and installing libdvdcss2, look [here]("http://ubuntuforums.org/showpost.php?p=2727375&postcount=3").

---

### Post by Angelbeast on 2007-05-31
> **RomeReactor said:**
> Angelbeast, for adding the medibuntu repositories and installing libdvdcss2, look [here]("http://ubuntuforums.org/showpost.php?p=2727375&postcount=3").

Thank you. That did the trick wonderfully. Now however i seem to have lines during video playback like there is an interlace problem but turning interlacing on and off doesn't do anything. It actually looks like scan lines on a crt monitor but i'm on a laptop with an lcd display. I've noticed it occurs mostly during fast motion and during scenes with bright spots like fires or explosions or bright daylight. Is there a way to remedie this?

---

### Post by wadesmart on 2007-05-31
Im on Fiesty and have been reading up on dvd playback. On my system all I had to install was totem-xine. Everything else was already installed. Still through all see is hundreds of little squares that kinda make up the background. 

wade

---

