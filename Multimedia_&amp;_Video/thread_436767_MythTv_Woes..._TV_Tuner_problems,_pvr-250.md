---
title: "MythTv Woes... TV Tuner problems, pvr-250"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by zerocle on 2007-05-08
Hey there I just got done setting up my box with ubuntu and Myth TV following this walkthrough: [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend) I then setup Lirc and installed the drivers for my graphics card, setup for myth tv went smooth enough but when I finally booted in and went to "watch TV" all I got was a black screen that the computer just sits at for about 30 seconds then goes back to the main menu. Im not really sure what to do, any help would be greatly appriciated, thank you

Also, if there is somewhere else this would be better posted at please let me know, thanks again  :)

---

### Post by jimp180 on 2007-05-08
More info is really needed,
do you see a error  message like "mythtv could not connect to master backend'?
did you complete the 4 steps of setting up the backend-General,Capture cards, Video sources, input connections ?
did you set you pvr card properly (not using v4l but as a mpeg 2 encoder card) ?

In all actuality you should see some kind of error if you hadn't completted these steps, have you checked the mythtv backend log to see if it helps ?

---

### Post by barney_1 on 2007-05-08
Please post the info from your log.  Try to watch live TV to create the error then run this in the console:
```
tail /var/log/mythtv/mythbackend.log
```

---

### Post by zerocle on 2007-05-08
First of all, thanks for the replys, and second of all theres no errors, I thought I set up the backend properly, and I did use mpeg-2 instead of v4l. that being said I got the log, heres what it says

```
MainServer::HandleAnnounce Playback
adding: mythbox as a client (events: 0)
TVRec(1): Changing from None to WatchingLiveTV
TVRec(1): HW Tuner: 1->1
MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
eno: Bad address (14)
MPEGRec(/dev/video0) Error: Could not set MPEG controls
eno: Invalid Argument (22)
TVRec(1): Changing from WatchingLiveTV to None
Finished recording U.S. Senate: channel 102
```

thanks again for your guys' hep, i really appriciate it

---

### Post by kebes on 2007-05-08
A test to try is to try to record the TV signal without using MythTV. So make sure your TV is turned on and playing something, and that it is connected to your capture card. Then, in a terminal, type:
```
cat /dev/video > test.mpg
```

Let is run for a few seconds, then stop it using "Ctrl+C". You should then have a file called "test.mpg". Try opening that file with any movie player (Kaffeine, mplayer, VLC, etc.). Do you see what was playing on TV? Or do you see only black?

If you can see the TV recording in the file, then your capture card is working, but MythTV is not connecting to it properly.

If you just see black in that test file, then you have not configured your capture card properly, and you need to fix that.

---

### Post by zerocle on 2007-05-08
Okay, i guess my tuner isnt configured correctly because it doesnt seem to record anything when I do that, when I play it in vlc it just gives me a "nothing to play" error. so i guess my question is do you know where I can go to figure out how to setup my capture card?

---

### Post by kebes on 2007-05-08
I believe a capture device like the PVR-250 would show up as "/dev/video" ... what do you get when, in a terminal, you type:

ls -laF /dev/vid*

Does it list any devices?



According to [this]("https://help.ubuntu.com/community/MythTV_Feisty_hardware_list"), the PVR-250 should work "out of the box"... but obviously something is wrong. The driver required to make the Hauppage cards work is called "ivtv", and it is included with recent versions of Ubuntu (which version are you running?). Maybe if you just need to install the packages "ivtv-source" and "ivtv-utils".

Some useful information may be contained in the dmesg log. Try typing this in a terminal:
dmesg | grep ivtv

This will help determine if the card is being detected. (The commands "lspci" and "scanpci" may also be useful.) Hopefully you will be able to get the standard Ubuntu ivtv driver to work. If you're ambitious, you can try to manually build those drivers, from [the ivtv site]("http://ivtvdriver.org/index.php/Main_Page"). If you do a search online, or on the ivtv site, you can find various instructions for how to build and install the driver.

---

### Post by zerocle on 2007-05-08
okay, when I do the ls -laF /dev/vid* I get
crw-rw---- 1 root video 81, 0 2007-05-08 19:01 /dev/video0
when I do dmesg | grep ivtv
I get nothing
and when i do lspci it gives me alot of info, but nothing involving hauppauge or my tuner, it has my graphics card, but no tuner, so is it not recognizing my tuner?


EDIT

now that I look at scanpci it does give me a 
Conexant CX23880/1/2/3 PCI video and Audio Decoder [MPEG Port]
as well as a couple other Conextant things, this does look like my tuner, but why is it reading as Conexant, do they make the chipset?

---

### Post by zerocle on 2007-05-09
well I just found something interesting, if I go into mythphone(or whatever it is) I actually get my tv signal in the upper left?! whats that about?

---

### Post by kebes on 2007-05-09
> **zerocle said:**
> okay, when I do the ls -laF /dev/vid* I get
crw-rw---- 1 root video 81, 0 2007-05-08 19:01 /dev/video0

Okay, try re-running the command I told you before, but using video0 instead:
cat /dev/video0 > test.mpg
(wait a few seconds, then do Ctrl+C and check the file). Does that work, now? (Does it show the video from the TV?) If "/dev/video0" is working, then it might be as simple as running "mythtvsetup" and defining your video sources. (I think it defaults to /dev/video, but you can update that.)


> and when i do lspci it gives me alot of info, but nothing involving hauppauge or my tuner

When I do lspci, my Hauppage PVR-350 shows up as:
00:0d.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)


> well I just found something interesting, if I go into mythphone(or whatever it is) I actually get my tv signal in the upper left?! whats that about?

So in one of the Myth plugins you actually see the video signal from the TV properly? (But not when you try to watch live TV?) Again, I would double-check all the settings in mythtvsetup. Make sure that you've defined a video source that uses your card, and that this is set to be the default capture source.

---

### Post by zerocle on 2007-05-09
alright well i finally got home and had a chance to play with my box, and im still having trouble, I tried the cat /dev/video0 >test.mpg and got nothing, when i tried to play the vid it was a green box, thats all(played it in vlc). I also tried some other things, I tried connecting it by cable, svideo, and composite, and got nothing from each :(

---

### Post by zerocle on 2007-05-09
WOOT! big breakthrough, if I switch my video input to v4l i get video!, although, it looks crappy, but its "working" any idea why it would work there even though every walkthrough says make sure you select mpeg-2? I think it has something to do with the cx88 drivers that ive read about on the ivtv website ([http://ivtv.writeme.ch/tiki-view_faq.php?faqId=1#q46](http://ivtv.writeme.ch/tiki-view_faq.php?faqId=1#q46)) if so, should I assume this is it in its best working condition? or should I download the drivers? and if thats the case, then sorry but i gotta say, im a newb, help?! lol

---

### Post by zerocle on 2007-05-11
anybody have any ideas? please?

---

### Post by kebes on 2007-05-11
> **zerocle said:**
> anybody have any ideas? please?

Can you summarize your current status?

As I understand it, everything works, but the video quality is not as good as you would like. Can you describe what it is that is bad about the video quality? Is it "pixelated"? Is it "jerky"? Is there noise in the signal? Weird blocks overlayed on the image occasionally? (Can you take a screenshot?)


Depending on exactly what about the video looks bad, the first thing I would try is to differentiate between "bad capture" and "bad playback." For instance if you record some TV, and pause it, are there artifacts in the image? Or is the problem just that during playback, your hardware cannot "keep up"?

The reason I ask is that the the Hauppage PVR-250 has an on-card MPEG encoder. However I assume you are outputting the video through a standard video card. This means that your CPU is doing all the work of MPEG decoding. What are your hardware specs? Maybe your machine just can't keep up...


Alternately, it could be that the driver you're using is not taking proper advantage of the 250's encoding capabilities. If this is the case, then yes I would suggest manually downloading and building the ivtv driver from the site. They have lots of FAQs and helpful hints. However I'm also happy to help you through the steps of building the driver.

---

### Post by zerocle on 2007-05-14
thanks for your reply :) my complaint on the video is that it is very delayed, which is acceptable, but then its also laggy and it will get points of pixelation, low resolution, pretty much everything you dont want in video lol. I am assuming this has something to do with the fact that im using v4l instead of MPEG in the tuner selection screen, but that was the only way it would work. Ive actually got a decent setup here:

Motherboard: [DFI lanparty UT nf4 Ultra-D]("http://us.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3471&CATEGORY_TYPE=LP&SITE=US")
Processor: Amd Athlon 64 3500+
Memory: 1G Corsair Value Select
Graphics Card: ABIT ATI X600 Pro HDTV
TV Tuner: PVR-250

---

### Post by kebes on 2007-05-14
Yes, your hardware specs are more than good enough for doing realtime MPEG decoding. So you're probably right: by using the v4l driver instead of MPEG, you're not taking full advantage of the PVR-250's MPEG encoding capabilities.

(As a side note, there is always a minor delay between live TV and what you see on your Myth, since it has to encode the video, save it to the disk buffer, and display it on-screen. The upside is that you can pause/rewind live TV.)


Did you ever install the Ubuntu [ivtv packages]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ivtv&searchon=names&subword=1&version=feisty&release=all")? (ivtv-source and ivtv-utl) These will get you started towards compiling and installing the ivtv driver. Further instructions [here]("http://ivtvdriver.org/index.php/Howto").

Also, an important thing to know is which kernel version you are running:
uname -r

---

### Post by zerocle on 2007-05-14
my ubuntu box is at my house so i cant work on it right now, but i will double check all the ivtv stuff, I was fairly certain i had downloaded and installed everything correctly, but maybe not...

---

