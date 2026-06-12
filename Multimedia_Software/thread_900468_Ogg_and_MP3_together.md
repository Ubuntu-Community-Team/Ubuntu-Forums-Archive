---
title: "Ogg and MP3 together"
date: 2008-08-25
forum: Multimedia Software
---

### Post by baronferg on 2008-08-25
G'Day Everyone,
Greetings and best wishes.

I just completed the ripping of all my CDs onto an Ubuntu workstation box using Sound Juicer..(.Ogg files) I would also like to copy/move all my MP3s from my Windows XP box onto the new Ubuntu box and be able to play any and all .ogg and or .mp3 at any time. I do not have the original CD for most of the mp3 tracks I have.

**_QUESTION:_**
#01. - Which single application can play .ogg and .mp3 all from within the same library? Maybe Rythmbox can do this but it is frustrating me some just with the .ogg files.

#02. - Which is the best (reads easiest way) to copy ALL my mp3 files from the windows box over to the Ubuntu box given that they are both on the same LAN.

Many thanks for your help and attention.

---

### Post by forger on 2008-08-25
1) Install codecs:
- this command in Applications > Accessories > Terminal will install most if not all the codecs necessary:
```

sudo apt-get install lame vorbis-tools flac ffmpeg liblame0 gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libdvdread3 gstreamer0.10-x gstreamer0.10-fluendo-mp3

```
- install soundconverter:
```
sudo apt-get install soundconverter
```
Then go to Applications > Sound & Video > Sound converter

2) No idea, I would just transfer the hard drive to the ubuntu machine to ease up the process :)

---

### Post by baronferg on 2008-08-25
Ok. Thanks.
I got it all done, but what is SoundConverter.

I do not wish to convert anything.  

Help me out here. Thanks

---

### Post by forger on 2008-08-25
Ah wait, I misread your post :) anyway, the answer was correct, except for the soundconverter installation.
You got the codecs, now you can play both ogg and mp3 :)

---

### Post by baronferg on 2008-08-26
Thanks for the reply. Also, here is what I did on the mp3 copy question:
sudo apt-get update
sudo apt-get install vsftpd ssh sysv-rc-conf
Then I went to the WindowsXP box, launched WinSCP and copied the mp3s over tothe ubuntu box.
I will try to get Rythmbox to play the mp3s later.

Thanks

---

### Post by baronferg on 2008-08-29
Everything is working great......Thanks

---

