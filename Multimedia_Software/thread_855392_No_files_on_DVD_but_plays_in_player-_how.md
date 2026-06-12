---
title: "No files on DVD but plays in player- how?"
date: 2008-07-10
forum: Multimedia Software
---

### Post by ddixonr on 2008-07-10
I just got a dvd from a hospital who recorded my wife's first ultrasound. When I popped it in the drive, nothing showed in the folder view. I thought there was a mistake with the burning, but when I put it in the home dvd player, it played like any movie complete with a title menu. I tried a second computer and had the same results. I want to make copies and post the video online. 

Any programs that may help?

---

### Post by forger on 2008-07-10
try encode it with **thoggen** (Applications > Add/Remove)

install it, then head to Applications > Sound & Video > Thoggen

the rest should be easy - if not, tinker a bit and you'll learn it :)

---

### Post by ddixonr on 2008-07-10
Ok I'll try and let you know.

---

### Post by ddixonr on 2008-07-10
It seems to hang or freeze after starting the encoding process. The progress screen is blue, and the written, elapsed, time left, and speed are blank. The dvd doesn't seem to be spinning either.

---

### Post by ddixonr on 2008-07-10
here is the output of the log error:

 :: g_timer_continue: assertion `timer->active == FALSE' failed

---

### Post by forger on 2008-07-10
close thoggen or any media-related program

Go to System > Administration > Software Sources - make sure you have **universe** and **multiverse** checked, click "Close" and "Reload"

Also, do you have medibuntu repository installed?
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

For hardy heron:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

then install some extra codecs:
```
sudo apt-get install liddvdcss2 libdvdread3 w32codecs lame vorbis-tools flac ffmpeg liblame0 gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libdvdread3 gstreamer0.10-x gstreamer0.10-fluendo-mp3
```

then try again

---

### Post by werries on 2008-07-10
they may have hidden the contents?
maybe mounting with those special options.....that i dont remember.

---

### Post by ddixonr on 2008-07-10
I hate to say it, but still no luck. The only part that didn't work with your code was liddvdcss2 (apt-get part). I thought it might be li**b**dvdcss2 but that didn't work either.

---

### Post by werries on 2008-07-10
he did mean lib. but if you correctly added the medibuntu repositories, everything should either have already been on your computer or added with that code.

---

### Post by mc4man on 2008-07-10
i think maybe you need to look back at this from first post
> nothing showed in the folder view Is there any indication that a filesystem is found? You can't copy/rip/play "nothing".
After the disk is inserted what does dmesg | tail show?

---

### Post by ddixonr on 2008-07-10
I can play the dvd using just about all the media players I have. Not a single file shows in the browser but the properties menu does show udf file system and 990mb used. 

I am trying ogmrip to encode the dvd at the moment since thoggen doesn't seem to go anywhere. ogmrip stopped about half way through, but I hope adding those codecs will do the trick. I appreciate all the help.

---

