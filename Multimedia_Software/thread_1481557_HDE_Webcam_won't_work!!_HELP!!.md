---
title: "HDE Webcam won't work!!? HELP!!?"
date: 2010-05-12
forum: Multimedia Software
---

### Post by P-rench on 2010-05-12
Hi, I'm very new to ubuntu 9.10, and have been making the transition from windows for about 1 month now. I'm using Wubi to dual boot 9.10 off windows xp. I have been having very good luck figuring things out using this ubuntu forum, which I am more grateful for than any of you could ever imagine, haha, thank you for this forum! But I have a webcam issue I just can't figure out.

Heres my question. I just recently bought a VERY cheap usb webcam from a company named HDE. There doesn't seem to be a specific name or even model number for this webcam, but here is the web page of the webcam I bought, [http://www.hdeshop.com/USB-3-LED-PC-Webcam-Camera/M/B0015TJNEY.htm](http://www.hdeshop.com/USB-3-LED-PC-Webcam-Camera/M/B0015TJNEY.htm) The website only provides drivers for windows vista and windows xp, but I figured there might be a chance or possibility that I could force this webcam to work on ubuntu 9.10. I plugged in the webcam and it did show up in skype, but the picture is all green and there is a double of me. Plus, the actual webcam device will not show up in skype, I can't select the webcam, but regardless it still shows a green double vision image when I test it or do a video call. Skype seems to be the only thing this webcam kind of works with, It will not work with Cheese though and doesn't show an image in gstreamer. I want to mention that when I go to Cheese Preferences there is a webcam device that appears and sayse "USB 2.0 Camera (/dev/video0)" but I can't select it. I'm not sure what to do about this or how to fix it? I've searched around the internet and read the ubuntu documentation on webcams but really haven't had any luck for my specific webcam. I would just like the webcam to be detected by ubuntu 9.10, to work properly in skype, and work in cheese so I can record video's. Any help and solutions would be GREATLY appreciated! Thank you so much to everyone on here!

---

### Post by Temposs on 2010-05-12
For future reference, you should usually figure out if a hardware device works with Ubuntu before purchasing it. That way you can avoid this kind of trouble.

Sometimes there are webcams that just don't work entirely in Ubuntu. I'm not saying that's the case here, but it is a reality you may have to face.

Here is a page that lists webcams that work with various versions of Ubuntu. This is probably the best way to go about purchasing a webcam:
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by P-rench on 2010-05-12
Right on, Thanks for the reply. The webcam does kind of work, just not entirely. I looked through the entire wiki list and didn't see my webcam, which is a total bummer :(. Theres no way to force it to work or any programs that could detect the webcam or usuable drivers for it? Any other suggestions?

---

### Post by Temposs on 2010-05-12
One thing you need to get is the device ID of the webcam, which you can get with

```
lsusb
```

It will be 8 numbers & letters separated by a colon in the middle. This identifies the actual piece of hardware you're using, regardless of the branding or company that sold it to you. From there you should search around for people writing about a webcam with that device id, because then you can be sure that they are talking about your device.

Also try:

```
lsmod | grep videodev
```

Look for the name of the driver that your webcam uses. This also helps to look for people with webcams that use the same driver, and how they get that to work.

Google is your friend.

---

### Post by P-rench on 2010-05-12
Ok, I tried out both of those commands and I'm a little confused. 

The first one, I don't think it's reading my webcam. 
ghost@ubuntu:~$ lsusb
Bus 002 Device 004: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard
Bus 002 Device 003: ID 1267:0210 Logic3 / SpectraVideo plc 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 1c4f:3002 SiGma Micro 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The second one, to be totally honest, I'm not quite sure what I'm looking at. 
ghost@ubuntu:~$ lsmod | grep videodev
videodev               43360  1 uvcvideo
v4l1_compat            16644  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev

I'm a little confused at the moment? I'm still a noob haha.

---

### Post by P-rench on 2010-05-12
OH! Wait! It is sigma micro! I believe thats the webcam! My webcam ID is 1c4f:3002 SiGma Micro. On this website [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) it says a SiGma Micro ID 1c4f:3000 will work with Ubuntu 9.10, this is not quite the same ID but I might work? Maybe? The website said to open skype in a terminal using this command  "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" without quotes and that the webcam would work, I did that and the webcam is still not working right, it's still green and has double vision. The website also said I needed  to install a library using this command "apt-get install libv4l-0". When I did this command in a terminal I got this message.  
ghost@ubuntu:~$ apt-get install libv4l-0
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? 

I really have no idea what that message means, but I'm pretty sure it didn't work. Any help or ideas?

Also I found a thread on the ubuntu forum here [http://ubuntuforums.org/showthread.php?p=5749085](http://ubuntuforums.org/showthread.php?p=5749085) that says there are drivers for the SiGma Micro ID 1c4f:3000. The driver website is here [http://www.ideasonboard.org/uvc/#download](http://www.ideasonboard.org/uvc/#download) , again it's not quite the same ID but it might work?

---

### Post by P-rench on 2010-05-12
Ok, I found this website that has drivers that MIGHT work for my webcam but for whatever reason I don't understand how to download and use it. [http://www.ideasonboard.org/uvc/#download](http://www.ideasonboard.org/uvc/#download) I'm feelin kind of tarded right now! Hahaha. Any Help would be great!

---

### Post by P-rench on 2010-05-12
Bump.

---

### Post by sandyd on 2010-05-12
```

sudo apt-get install luvcview
luvcview
```
see if it works.

p.s. I was actually supprised that my webcam (a microsoft lifecam cinema 720p) actually works with linux. really.

---

### Post by P-rench on 2010-05-12
Thanks carlee! I installed luvcview and my webcam does work, works pretty well actually, but it only works in luvcview. When I opened my webcam in skype it was still green and made a double of me, like there was me and then this see through ghost version of me. Cheese still doesn't work either. Any suggestions? I'm kind of confused right now.

---

### Post by Temposs on 2010-05-12
For the command you were trying to do previously, it would need to be:

```
sudo apt-get install libv4l-0
```

---

### Post by P-rench on 2010-05-12
Thanks Temposs! I did that install, unfortunately I still can't get the webcam to work right with skype (still looks all funny) and it won't work at all with Cheese still. This website here [http://www.ideasonboard.org/uvc/#download](http://www.ideasonboard.org/uvc/#download) says they have drivers for my webcam but I'm seriously confused by that website in terms of how to install it. I think thats probably what I need is those drivers and then it will work right with skype and hopefully cheese. Oh I'm running Skype 2.1 Beta version if that makes any difference to this situation. But yea any other suggestions or help with the drivers would be awesome! I have a feeling I'm close to having this solved. Thanks to everyone for all the help so for I really appreciate it. :)  

P.S. I recorded a short video of myself using luvcview but I can't find where the recorded video was stored? What is the folder name? Here are the specs for my webcam through luvcview in the terminal if this will help in any way with my situation. 

ghost@ubuntu:~$ luvcview
luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: YUYV (MJPG is not supported by device)
  Frame size:   640x480
  Frame rate:   30 fps

---

### Post by P-rench on 2010-05-12
Bump.

---

### Post by Temposs on 2010-05-12
It seems like according to the uvc driver site, they cover 1c4f:3000, but your webcam is 1c4f:3002, which probably means it's not exactly the same. The page indicates that the uvc driver is already included in linux kernel, which explains why it works at all.

---

### Post by P-rench on 2010-05-13
That would make sense, my webcam works and looks great in luvcview but I still can't figure out why it won't work in Cheese and why the picture is all messed up in skype. That part confuses me. Any one have any ideas on this?

---

### Post by P-rench on 2010-05-13
Bump.

---

### Post by P-rench on 2010-05-13
Bump.

---

### Post by P-rench on 2010-05-13
I went to this website [http://www.ideasonboard.org/uvc/#download](http://www.ideasonboard.org/uvc/#download) which is suppose to have drivers for my webcam, although I don't really understand how I download or install them. In the download section of this page there was this website link [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)   which had a zip file which I downloaded, the name of the file was v4l-dvb-9b63860cd18a I have opened this file and at the moment I have no idea what I'm looking at or how I am supposed to install this, I'm not even sure if these are drivers or if I downloaded the right thing. Any help and suggestions would be great right now as I am pretty confused and trying to get the picture from my webcam to work right on skype and get cheese to work. The only thing working without any problems in Luvcview. What is going on here :confused: ???????

---

### Post by P-rench on 2010-05-13
Ok, I think I figured something out. The webcam I bought is a Sigma Micro ID 1c4f:3002 and it works flawlessly in Luvcview, but in skype the picture is small, green, and there is a double of me. It does not work in Cheese at all. When I use Gstreamer I can't seem to get a picture, it's just static, it won't read the webcam. I decided to boot into windows xp and see if the webcam worked there, and what ya know, it worked great with everything, including skype. Then I also realized that the webcam has pre-installed drivers in it for windows xp and windows vista. So heres my question, is it possible that the windows xp/vista drivers loaded themselves onto ubuntu 9.10? If so, would these drivers be interfering with ubuntu's drivers and causing me the problems I'm having? If that is the case then how do I un-install the windows xp/vista drivers off of ubuntu? Any help and suggestions would be greatly appreciated right now????? :confused:

---

### Post by P-rench on 2010-05-13
Bump.

---

### Post by P-rench on 2010-05-13
Bump.

---

### Post by Temposs on 2010-05-13
> **P-rench said:**
> Ok, I think I figured something out. The webcam I bought is a Sigma Micro ID 1c4f:3002 and it works flawlessly in Luvcview, but in skype the picture is small, green, and there is a double of me. It does not work in Cheese at all. When I use Gstreamer I can't seem to get a picture, it's just static, it won't read the webcam. I decided to boot into windows xp and see if the webcam worked there, and what ya know, it worked great with everything, including skype. Then I also realized that the webcam has pre-installed drivers in it for windows xp and windows vista. So heres my question, is it possible that the windows xp/vista drivers loaded themselves onto ubuntu 9.10? If so, would these drivers be interfering with ubuntu's drivers and causing me the problems I'm having? If that is the case then how do I un-install the windows xp/vista drivers off of ubuntu? Any help and suggestions would be greatly appreciated right now????? :confused:

It is generally not possible to use drivers made for Windows in Ubuntu, unless there is a helper application someone has made to translate how the driver talks to Windows into a form that Linux can understand. So, in your case, you probably can't.

---

### Post by P-rench on 2010-05-13
Thanks! Thats good to know, atleast I know there is no interference with the ubuntu drivers. Well, I'm stuck and about to pull my hair out with this webcam haha. This webcam does work in LUVCview on ubuntu 9.10. But skype on the other hand, the picture isn't right and I dunno what to do with it. I've been searching and trying things non stop with no luck. Anyone got any other suggestions???? :confused:  I would really like to use this webcam in skype and cheese if possible.

---

### Post by P-rench on 2010-05-13
I'm running wubi with Ubuntu 9.10 off of windows xp. My webcam is a SiGma Micro ID 1c4f:3002. This website [http://www.ideasonboard.org/uvc/#download](http://www.ideasonboard.org/uvc/#download) says it has drivers for my webcam but I have no idea how to install this and I'm very confused. Can someone please show me how to install these drivers?? :confused: Any other help or suggestions to get drivers that will make my webcam work would be greatly appreciated! Thanks.

---

### Post by bredman on 2010-05-13
If you read the download section of the link, you will see the text

Linux 2.6.26     and newer includes the Linux UVC driver natively. You will not need  to     download the driver sources manually unless you want to test a newer     version or help with development.

If you are using Ubuntu 9.10, you do not have to download this driver.

---

### Post by P-rench on 2010-05-13
How do I test a newer version of drivers? The webcam I have is working fine in LUVCview, but it's all messed up in skype. So I think I need those experimental drivers then?

---

### Post by P-rench on 2010-05-13
Alright I think I narrowed down my problem. I'm running wubi ubuntu 9.10 through windows xp. My webcam is a SiGma Micro, ID# 1c4f:3002. I have successfully gotten my webcam to work in LUVCview as well as Guvcview. I was able to successfully record video and audio through Guvcview with no problems. Heres my problem though, I can't seem to get my webcam to work in skype 2.1 beta version. Skype does sense my webcam and when I do "test" I can see video through skype, but the picture is all greenish and very small (I can only see about half of my head vertically) and there is a double picture of me, like a ghost image. I don't understand what the problem is. Can anyone please help me with this?? Any suggestions?? :confused:

---

### Post by xc3RnbFO8P on 2010-05-13
Try this:
[http://ubuntuforums.org/showpost.php?p=6063348&postcount=13]("http://ubuntuforums.org/showpost.php?p=6063348&postcount=13")

---

### Post by P-rench on 2010-05-13
Just tried that, and nothing. Still doesn't work, bummer. Thanks for the suggestion though :). Any other suggestions from anyone?

---

### Post by P-rench on 2010-05-13
Bump.

---

### Post by lisati on 2010-05-13
Threads merged

---

### Post by P-rench on 2010-05-13
Bump.

---

### Post by lisati on 2010-05-13
> **P-rench said:**
> Bump.

Your support requests have been combined into a single thread. And please do not "bump" more often than once a day.

---

### Post by P-rench on 2010-05-13
Right on, sounds good.

---

### Post by P-rench on 2010-05-14
So does anyone have any advice or suggestions on how I can get my webcam to work with skype?

---

### Post by P-rench on 2010-05-14
Bump.

---

### Post by P-rench on 2010-05-14
YES! IT'S SOLVED! Thanks to Ringi and user no2498 where I found part of the solution in their reply to this thread [http://ubuntuforums.org/showthread.php?t=1482369](http://ubuntuforums.org/showthread.php?t=1482369). Alright so my webcam is now working in Skype 2.1 Beta Version on Ubuntu 9.10!!! I want to mention that this solve is for a SiGma Micro USB Webcam ID# 1c4f:3002. This webcam is EXTREMELY cheap (about $7 after shipping) and works GREAT! The only downside is, there is no built in microphone. If anyone here is interested in purchasing the same webcam I bought, you can do so at [http://www.amazon.com/Webcam-Camera-...3875133&sr=8-1]("http://www.amazon.com/Webcam-Camera-Vision-Meeting-compatible/dp/B0015TJNEY/ref=sr_1_1?ie=UTF8&s=electronics&qid=1273875133&sr=8-1") through the seller "HDE". OR, you can buy directly from HDE at their home website here [http://www.hdeshop.com/USB-3-LED-PC-...B0015TJNEY.htm]("http://www.hdeshop.com/USB-3-LED-PC-Webcam-Camera/M/B0015TJNEY.htm") This webcam is very much worth the price and purchase, very decent quality at a resolution of 640X480 and very little or no lag between voice and video when chatting it up on skype! =] Ok, now to the answer! I did all of this in the terminal and everything worked great.

 First you will want to set the resolution for skype to the same resolution of the webcam. Before doing this, Shut down Skype and any other video/webcam program before doing anything. Then open a terminal. To do this, go to Applications menu -> Accessories -> Terminal. 
  
Now enter this command in the terminal: 
 
gedit /$HOME/.Skype/(YourUserName)/config.xml   
 
Once the skype xml file is opened then search for this:  
 
<TransferWindow>
<Height>240</Height>
<NoCancelConfirmation>0</NoCancelConfirmation>
<Width>480</Width>
<X>3</X>
<Y>647</Y>
</TransferWindow>   
 
Once found, highlight and delete, and replace with this:  
 
<Video>
<CaptureHeight>480</CaptureHeight>
<CaptureWidth>640</CaptureWidth>
</Video>    
 
Once completed, save and exit. Now return to the terminal.  
 Now you will need the webcam drivers so enter these commands in the terminal (one by one):

cd /tmp
wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
tar xvfj tip.tar.bz2
cd v4l*
make
Wait, until it is finished (it will finish with an error).

Now, enter this in the terminal:

gksudo gedit /tmp/v4l*/v4l/.config

Search for this line in the xml file:
CONFIG_DVB_FIREDTV=m 

and change it to
CONFIG_DVB_FIREDTV=n 

Now click on "Save", close the text editor and get back to the terminal where you enter these commands (one by one):

make
sudo make install

Now, when completed, reboot your computer and your webcam should work.   

Enjoy! =]

---

### Post by puttingau on 2010-05-17
P-rench, I got this working in Lucid and Karmic by simply adding 
<Video>
<CaptureHeight>480</CaptureHeight>
<CaptureWidth>640</CaptureWidth>
</Video>
as you did in config.xml, between the <Lib> braces, no other editing seemed necessary.(in Karmic, there was a already a <Video> section, not so in my xml for Lucid)
Also, the Sigma Micro (1c4f:3002) that I bought off ebay has an inbuilt microphone, as well as led lights, which I presume is for additional lighting. I bought it for a similar incredible price.

---

