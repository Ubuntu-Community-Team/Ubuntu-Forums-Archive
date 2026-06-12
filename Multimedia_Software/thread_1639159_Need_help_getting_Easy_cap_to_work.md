---
title: "Need help getting Easy cap to work"
date: 2010-12-06
forum: Multimedia Software
---

### Post by Crazy K on 2010-12-06
I recently purchased the EasyCap video capture device; this: [http://www.dealextreme.com/details.dx/sku.5707](http://www.dealextreme.com/details.dx/sku.5707) 

And I need to know how to get it to work. I found a thread on it, but it wasn't any help. I already downloaded the drivers and extracted them in my home folder. [http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/) 

I just need to know how to run it through VLC or another media player. I'd also like to be able to copy old family videos so I can put them on DVD. 

Thanks!

---

### Post by Crazy K on 2010-12-06
I just need step-by-step help with this.

---

### Post by Crazy K on 2010-12-07
Can anyone help me out with this?

---

### Post by Crazy K on 2010-12-10
Hey guys, every topic I look into, nothing seems to help. I'd like to make DVD copies of my old family videos.

---

### Post by ozybushwalker on 2010-12-17
See reply #100 in [http://ubuntuforums.org/showthread.php?t=924504&highlight=easycap&page=5]("http://ubuntuforums.org/showthread.php?t=924504&highlight=easycap&page=5") for detailed instructions on building the driver. 

There are some instructions for recording from the easycap at [http://easycap.blogspot.com/p/recording.html]("http://easycap.blogspot.com/p/recording.html")

---

### Post by Crazy K on 2010-12-19
I'm sorry, but that's for the server edition of 10.04. Wouldn't it not be the same since I use Ubuntu 10.04 lts? 

Actually I need to know how to build up the driver. I got no help from that whatsoever.

Oh wait, I think I may have it.

---

### Post by Crazy K on 2010-12-19
Actually I got everthing to work except for this prompt: 

Now you can plug an analog video input and test your device with mplayer:
```
user@pc:~$ sudo ./easycap/test.sh
```

To work as user without sudo, add permitions every time, you plug in the device:
```
user@pc:~$ sudo ./easycap/permit.sh
```

Both of those don't work, so I'm guessing I don't have a permit.sh file on my system. Where do I get that, and how?

---

### Post by ozybushwalker on 2010-12-19
Please elaborate on "don't work", for example, when I type *sudo ./easycap/test.sh* at the shell prompt I see ... but I expected to see ...

---

### Post by Crazy K on 2010-12-19
I get this: 
```
sudo: ./easycap/test.sh: command not found
```
and this:
```
sudo: ./easycap/permit.sh: command not found
```

---

### Post by Crazy K on 2010-12-20
Any idea on what I did wrong?

---

### Post by ozybushwalker on 2010-12-21
Some of the documentation I have read refers to test.sh but in the driver I downloaded there is a family of test*.sh files:

In my home directory:
```

$ find . -name 'test*.sh'
./easycap_dc60.0.8.5/testNTSC.sh
./easycap_dc60.0.8.5/testPAL.sh
./easycap_dc60.0.8.5/test4NTSC.sh
./easycap_dc60.0.8.5/test4PAL.sh
$ 
```

So to test my easycap from my home directory I could type ```
./easycap_dc60.0.8.5/testPAL.sh 
```

(I have a multistandard VCR and I wanted to play a PAL tape to be captured by the easycap.)

I have both NTSC and PAL tapes. The PAL test display seems a bit jerky and the NTSC test display is in black and white rather than colour. I haven't checked for updates nor have I yet tried to capture to a file.

---

### Post by Crazy K on 2010-12-22
Hmm, I tried that too and it gave me the same error.

---

### Post by Crazy K on 2010-12-22
I was able to figure it out, but I don't think my computer is capable or viewing the video. So I think I'll just give it another shot on another computer.

---

### Post by ozybushwalker on 2010-12-22
Crazy K: In what way do you think the computer is deficient (what more does it need) and why?

I've recently noticed the easycap driver reports my easycap (also purchased from DealExtreme, same SKU as yours) as the one with 4 video inputs. The labels on the leads on my easycap are: S-VIDEO input, CVBS, AUDIO(L) and AUDIO(R). I wonder if the apparent misidentification is related to testPAL.sh playing my PAL video jerkily and testNTSC.sh playing the NTSC video in grey rather than colour.

---

### Post by Crazy K on 2010-12-26
I honestly don't know. I have an older computer, but I have a nice amount of Ram (1GB or so). Not sure how much memory my video card possess though. 

I'm able to get it to work with no errors, but no video will show up.

---

### Post by ozybushwalker on 2010-12-28
The different test files invoke different applications to display the captured video. I wonder if your system is missing the necessary applications (mine was).

Please provide the output when you repeat the "working command" but with "sh -x " on the line before the command, for example,
```
sh -x ./easycap_dc60.0.8.5/testPAL.sh
```

What did you do to make it "work"? (I'm also curious that you describe it as "working" but no video shows up.)

---

