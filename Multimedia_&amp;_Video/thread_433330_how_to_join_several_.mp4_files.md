---
title: "how to join several .mp4 files"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by joy83 on 2007-05-04
I was wondering how to join several .mp4 files. I have like 10 .mp4 files which I would like to join together so that I dont have to play them seperately. is there any seperate software that I have to install. 

I am using feisty.

---

### Post by LuisGMarine on 2007-05-04
You can try Audacity, you can find more information about it [here.]("http://audacity.sourceforge.net/")

To download follow this:
```
sudo apt-get install audacity
```

Of course this is hoping that you have your extra repos enabled, try restarting gnome ( logging in and out ) or this:
```
killall gnome-panel
```

Then you can find Audacity under Applications > Sound & Video > Audacity

Good Luck

---

### Post by joy83 on 2007-05-04
sorry i forgot to mention that the .mp4 files are all video files. I think audacity is for audio files. I need a software which can join video .mp4 files together.

---

### Post by LuisGMarine on 2007-05-04
In that case search around for Ubuntu Studios.  I'm not sure exactly what it is, but I hear its a nice array of programs that do things from video editing, up to image editing.  I'm not sure like I said exactly what it is, but I hear a lot of things about it.  Might want to check it out!

Good Luck

---

### Post by rsambuca on 2007-05-04
I think the quickest and easiest way to join them together is to use the command line.  Open a terminal and move to the directory where all of the files are located.  Then just enter```
cat file1.mp4 file2.mp4 file3.mp4 > outputname.mp4
```

This command will just join the files end-to-end in the order that they are listed.  I have never tried it for video, but it certainly works great for mp3's etc.  As far as I know, you can join as many files together at once as you like.

Let us know how it goes.

---

### Post by joy83 on 2007-05-04
> **rsambuca said:**
> I think the quickest and easiest way to join them together is to use the command line.  Open a terminal and move to the directory where all of the files are located.  Then just enter```
cat file1.mp4 file2.mp4 file3.mp4 > outputname.mp4
```

This command will just join the files end-to-end in the order that they are listed.  I have never tried it for video, but it certainly works great for mp3's etc.  As far as I know, you can join as many files together at once as you like.

Let us know how it goes.

I tried this, even though it does not give any error but when i play it, its only the first file. So it actually does not do anything in my case.

---

### Post by rsambuca on 2007-05-04
> **joy83 said:**
> I tried this, even though it does not give any error but when i play it, its only the first file. So it actually does not do anything in my case.

Darn.  Does the file length change?

---

### Post by joy83 on 2007-05-04
> **rsambuca said:**
> Darn.  Does the file length change?

yes the file length changes. The final file has the total length of all the files but surprisingly plays only the first part. thats kinda strange.

---

### Post by rsambuca on 2007-05-04
hmmm.  Try another player out of curiosity.

Also, if it doesn't work, you can try avidemux or cinelerra for editing the videos together.

---

### Post by dyssident on 2007-05-25
> **rsambuca said:**
> I think the quickest and easiest way to join them together is to use the command line. 

binary joins were usually successful with mpeg1/2, but im not sure if they are possible with mp4. in any event theyre really a hack that always has the potential for causing problems.

ive been successful with mp4box in the past. [http://en.wikipedia.org/wiki/MP4Box](http://en.wikipedia.org/wiki/MP4Box)

---

