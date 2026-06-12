---
title: "How to convert .rm videos to .avi"
date: 2007-10-09
forum: Multimedia &amp; Video
---

### Post by wasim2050 on 2007-10-09
I have some .rm videos and I really need to convert them to .avi so if anyone knows any free or open source softwares then please help me out.

Thank you.

---

### Post by kelbizzle on 2007-10-10
This may get you started.

[http://www.macosxhints.com/article.php?story=20060906153448633](http://www.macosxhints.com/article.php?story=20060906153448633)

---

### Post by wasim2050 on 2007-10-10
> **kelbizzle said:**
> This may get you started.

[http://www.macosxhints.com/article.php?story=20060906153448633](http://www.macosxhints.com/article.php?story=20060906153448633)

I cannot download ffmpegx from the above website as it is showing "404 not found"

Any other way possible.

---

### Post by wasim2050 on 2007-10-10
No one out there that can help me.

---

### Post by RomeReactor on 2007-10-10
Hi. You might want to use Mencoder for that:
```
sudo apt-get install mencoder
```

Once it's installed, use the **cd** command to change to the directory where the .rm file is, and issue the following command:
```
mencoder FILE1.rm -ovc lavc -oac pcm -o FILE2.avi
```
where FILE1 is the name of the .rm file, and FILE2 is the name you want for the resulting .avi file. IF this procedure doesn't work for you, perhaps this one will:
```
mencoder FILE1.rm -ovc lavc -oac mp3lame -o FILE2.avi
```

If you want to do this through a graphical interface, then install **iriverter**:
```
sudo apt-get install iriverter
```
Once it's installed, you'll find it in "Applications->Sound & Video->Iriverter".

Note that I haven't tried these methods, so I can't guarantee they'll work.

---

### Post by wasim2050 on 2007-10-11
I converted a .rm video to .avi with iriverter but the output is in black and white. but eventually mencoder seems to be working.

Thank you very much.

---

### Post by wasim2050 on 2007-10-11
> **RomeReactor said:**
> Hi. You might want to use Mencoder for that:
```
sudo apt-get install mencoder
```

Once it's installed, use the **cd** command to change to the directory where the .rm file is, and issue the following command:
```
mencoder FILE1.rm -ovc lavc -oac pcm -o FILE2.avi
```
where FILE1 is the name of the .rm file, and FILE2 is the name you want for the resulting .avi file. IF this procedure doesn't work for you, perhaps this one will:
```
mencoder FILE1.rm -ovc lavc -oac mp3lame -o FILE2.avi
```

If you want to do this through a graphical interface, then install **iriverter**:
```
sudo apt-get install iriverter
```
Once it's installed, you'll find it in "Applications->Sound & Video->Iriverter".

Note that I haven't tried these methods, so I can't guarantee they'll work.

Although I was able to convert .rm file to .avi file with mencoder yet when I try to make a vcd I got the error "Only MPEG1 and MPEG2 video files are supported" This happens both in k3b and Nero Burning Rom.

Please Help.

---

### Post by wasim2050 on 2007-10-11
No Reply!:(

---

### Post by RomeReactor on 2007-10-11
Have a look at [these]("http://ubuntuforums.org/showthread.php?t=487513") [threads]("http://ubuntuforums.org/showthread.php?t=492445"). For the solution offered in [this other thread]("http://ubuntuforums.org/showthread.php?t=467179"), you need to install ffmpeg before proceeding:
```
sudo apt-get install ffmpeg
```

Have you tried converting the .avi to .mpeg with Iriverter? you could also try with [AviDemux]("http://en.wikipedia.org/wiki/Avidemux"):
```
sudo apt-get install avidemux
```
Once its installed, yoou'll find it in "Applications->Sound & Video->Avidemux".

Hope this helps.

---

### Post by Tectuktitlay on 2008-03-08
> **RomeReactor said:**
> Hi. You might want to use Mencoder for that:
```
sudo apt-get install mencoder
```

Once it's installed, use the **cd** command to change to the directory where the .rm file is, and issue the following command:
```
mencoder FILE1.rm -ovc lavc -oac pcm -o FILE2.avi
```
where FILE1 is the name of the .rm file, and FILE2 is the name you want for the resulting .avi file. IF this procedure doesn't work for you, perhaps this one will:
```
mencoder FILE1.rm -ovc lavc -oac mp3lame -o FILE2.avi
```

If you want to do this through a graphical interface, then install **iriverter**:
```
sudo apt-get install iriverter
```
Once it's installed, you'll find it in "Applications->Sound & Video->Iriverter".

Note that I haven't tried these methods, so I can't guarantee they'll work.

Thanx Romereactor! I've been looking for this! It worked perfectly. Had to download drvc.so from 
[http://www.mplayerhq.hu/design7/dload.html]("http://www.mplayerhq.hu/design7/dload.html"), first, but after that I was finally able to convert some of my old Real Movies I still had from my windows days.

Tec

---

